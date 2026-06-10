# Rewarded Ads Implementation Plan

Implementation plan for adding rewarded video ads to the Ascion React Native
mobile app using Unity LevelPlay mediation.

This plan assumes the first ad-supported feature is:

```text
Watch a rewarded video -> receive 100 credits
```

The goal is to maximize ad revenue while protecting retention, user trust, store
compliance, and the in-game credit economy.

## Product Decision

- Use **Unity LevelPlay** as the mediation SDK.
- Launch with **rewarded video ads only**.
- Do not launch with banners, app-open ads, or forced interstitial ads.
- Reward amount at launch: **100 credits**.
- Give credits only after the SDK confirms the rewarded ad was completed.
- Keep ad availability optional and user-initiated.

## Recommended Placements

Start with one placement, then expand after analytics confirm retention is safe.

| Placement | Launch? | Reward | Notes |
| --- | --- | ---: | --- |
| `reward_credits_100` | Yes | 100 credits | Main shop or wallet entry point. |
| `reward_daily_bonus` | Later | 100 credits or multiplier | Add after basic flow is stable. |
| `reward_continue` | Later | Continue / revive | Use only if it fits gameplay fairly. |
| `reward_low_balance` | Later | 100 credits | Show when the user lacks credits for an action. |

## Economy Guardrails

Initial safe defaults:

- Daily cap: **5 rewarded ads per user per day**.
- Cooldown: **60 seconds** between completed rewarded ads.
- Server-side reward grant required for production.
- Client should never be the source of truth for final credit balance.
- Reward amount should be remotely configurable before wider launch.

Remote-config values to support:

```text
rewardedAds.enabled = true
rewardedAds.creditReward = 100
rewardedAds.dailyCap = 5
rewardedAds.cooldownSeconds = 60
rewardedAds.minAppVersion = <current release>
```

## Technical Flow

1. User taps `Watch ad` in the app.
2. App checks feature flag, daily cap, cooldown, login state, and SDK readiness.
3. App requests or shows a loaded Unity LevelPlay rewarded ad.
4. User watches the full ad.
5. Unity LevelPlay fires the reward completion callback.
6. Client sends a reward grant request to the backend.
7. Backend validates the request and grants 100 credits idempotently.
8. Client refreshes credit balance and shows success UI.

Do not grant credits when:

- the ad starts,
- the ad opens,
- the ad is clicked,
- the ad fails,
- the user closes the ad before completion,
- the backend grant request fails.

## React Native Integration Tasks

Use Unity's official React Native package:

```bash
npm install unity-levelplay-mediation
```

Implementation tasks:

- Add the Unity LevelPlay package to the mobile app.
- Add iOS configuration, pods, and required permission/privacy metadata.
- Add Android Gradle configuration and manifest requirements.
- Initialize the SDK once after app startup and consent/privacy state is known.
- Create a small ads service module, for example `rewardedAdsService`.
- Expose methods:
  - `initializeRewardedAds()`
  - `loadRewardedAd(placementName)`
  - `showRewardedAd(placementName)`
  - `isRewardedAdAvailable(placementName)`
- Subscribe to rewarded ad events in one place.
- Route completion events through the backend reward grant endpoint.
- Add UI states for loading, unavailable, capped, cooling down, completed, and failed.

## Backend Tasks

Add a production-safe reward grant endpoint.

Suggested endpoint:

```text
POST /rewards/rewarded-ad-credit
```

Request fields:

```json
{
  "placement": "reward_credits_100",
  "sdkRewardId": "provider-event-id-if-available",
  "clientEventId": "uuid-v4",
  "adNetwork": "unity-levelplay"
}
```

Backend behavior:

- Require authenticated user.
- Enforce daily cap server-side.
- Enforce cooldown server-side.
- Validate known placement names.
- Grant the configured credit amount.
- Store an idempotency key using `clientEventId`.
- Log provider metadata for fraud review.
- Return updated credit balance and cap status.

Suggested response:

```json
{
  "granted": true,
  "creditsGranted": 100,
  "creditBalance": 1234,
  "remainingAdsToday": 4,
  "cooldownEndsAt": "2026-05-03T12:34:56Z"
}
```

## Privacy And Compliance Tasks

Before release, update store disclosures and legal docs based on the final SDK
behavior.

Required checks:

- Confirm Unity LevelPlay, Unity Ads, and mediated networks used at launch.
- Confirm whether Google AdMob, Meta, AppLovin, Liftoff/Vungle, DT Exchange, or
  Mintegral are enabled as demand sources.
- Update Apple App Privacy labels for ad identifiers, coarse location, diagnostics,
  product interaction, and tracking if applicable.
- Update Google Play Data safety answers for advertising SDK behavior.
- Confirm ATT prompt strategy on iOS if any network uses tracking.
- Confirm consent flow requirements for EEA/UK users.
- Confirm the app remains aligned with the current **16+ worldwide** product rule.
- Update `PRIVACY_POLICY.md` if ad SDK data collection is materially different
  from current analytics/crash/push disclosures.

Do not enable child-directed treatment unless the product strategy changes. The
current legal docs assume the service is not for users under 16.

## Ad Quality Controls

Configure Unity LevelPlay and mediated networks to block categories that do not
fit Ascion's brand or audience.

Initial block list:

- adult/dating
- gambling/casino
- misleading finance
- political persuasion
- religious persuasion
- fake system warnings
- deceptive install prompts
- low-quality or misleading gameplay creatives

Operational tasks:

- Enable ad quality review tools where available.
- Review early creatives during internal testing.
- Create a support path for users to report bad ads.
- Track problematic ad network, creative ID, country, placement, and timestamp
  where available.

## Analytics Events

Track the full funnel so revenue can be improved without guessing.

Recommended events:

```text
rewarded_ad_button_seen
rewarded_ad_button_tapped
rewarded_ad_unavailable
rewarded_ad_started
rewarded_ad_completed
rewarded_ad_closed_without_reward
rewarded_ad_reward_grant_requested
rewarded_ad_reward_granted
rewarded_ad_reward_failed
rewarded_ad_daily_cap_reached
rewarded_ad_cooldown_blocked
```

Include properties:

```text
placement
rewardAmount
country
platform
appVersion
adNetwork
mediationProvider
errorCode
remainingAdsToday
```

Key metrics:

- rewarded ad impressions per DAU
- completion rate
- reward grant success rate
- ad ARPDAU
- credit inflation from ads
- D1/D7 retention for ad watchers vs non-watchers
- session length after watching ads
- crash rate after SDK integration

## Rollout Plan

1. **Development**
   - Integrate SDK in a feature branch.
   - Use test mode / test ad units only.
   - Implement one placement: `reward_credits_100`.

2. **Internal QA**
   - Verify rewarded completion callback.
   - Verify no credits are granted for skipped or failed ads.
   - Verify daily cap and cooldown.
   - Verify offline and poor-network behavior.
   - Verify app startup and crash-free sessions on iOS and Android.

3. **Closed Testing / TestFlight**
   - Enable for internal testers only.
   - Monitor crashes, fill, completion rate, and reward grant failures.
   - Review ad creative quality.

4. **Soft Launch**
   - Enable for a limited country or percentage of users.
   - Compare retention and credit economy before broader rollout.
   - Adjust reward amount, cap, and cooldown using remote config.

5. **Production Rollout**
   - Expand gradually.
   - Add more rewarded placements only after the first placement is stable.

## Acceptance Criteria

- Rewarded ad button appears only when the user is eligible.
- User can watch a rewarded video and receive exactly 100 credits.
- Credits are granted only after ad completion.
- Backend enforces idempotency, daily cap, and cooldown.
- App handles SDK unavailable/failure states gracefully.
- Store privacy disclosures match the final SDK setup.
- No forced ads are shown.
- Ad quality filters are configured before production rollout.
- Analytics show the full rewarded-ad funnel.

## Open Decisions

- Final daily cap: start with 5, tune after testing.
- Final cooldown: start with 60 seconds, tune after testing.
- Whether to include AppLovin as a mediated demand source inside LevelPlay.
- Whether to enable AdMob demand source at launch or after first validation.
- Whether EEA/UK consent is required before ad SDK initialization.
- Whether the reward grant endpoint should accept provider server-to-server
  callbacks if Unity LevelPlay supports them for the chosen setup.
