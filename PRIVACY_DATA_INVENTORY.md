# Ascion privacy data inventory

Status: working code-to-policy inventory  
Prepared: 2026-08-15  
Policy draft: `2026-08-15-draft-1`

This inventory records the implemented data flows reviewed for the Privacy
Policy draft. It is not a substitute for a processor register, records of
processing activities, transfer assessment, store disclosure, or legal advice.

## Data-flow inventory

| Category | Data and source | Purpose / recipients | Retention and deletion | Implementation status |
| --- | --- | --- | --- | --- |
| Authentication | Apple/Google subject ID, email, optional provider name/image, Apple relay email, Apple refresh token | Account access; Apple and Google | Account life; deleted after 30-day deletion grace; Apple token revoked where available | Implemented |
| Profile and preferences | Internal account ID, username, avatar, language, timezone, settings, age confirmation, legal acceptance versions/times | Core service; authorized players see public profile fields | Account life; deleted with account except limited deletion audit context | Implemented |
| Discord link | Discord ID, username, global name, avatar URL, connection time, role-sync marker | Optional linking, guild membership, Commander/Primer role sync; Discord | Until disconnect or account deletion; Discord-side history follows Discord's policy | Implemented; production QA pending |
| Chat | Message text/type, sender, thread, sent/edit/delete/read state, membership | World, organization, and direct chat; authorized players | Account life; deleting account deletes authored messages and translations | Implemented |
| Chat translation | Selected source message, target language, translated text, source hash, provider/model | OpenAI generates on demand with `store:false`; cached in Ascion for authorized readers | Provider may temporarily retain API content under its terms; Ascion cache follows source message | Implemented; first-use third-party-AI disclosure/permission is a release gate |
| Friend/social graph | Requests, relationship status, blocking fields, last interaction, counts, private nickname/note | Social connections, direct-chat authorization, player discovery | Account life; relationships deleted with either deleted account | Partially implemented; complete block/unblock UX remains gated |
| Presence | Short-lived socket/account presence, persistent last-seen timestamp | Online indicators and friend presence | Socket presence expires in about 3 minutes; last-seen follows account | Implemented |
| Organizations | Name, tag, description, media, visual identity, member roles, invitations/requests and messages | Organization identity, membership, organization chat | Membership/invites/requests deleted with account; shared organization may remain; sole leader must transfer leadership | Implemented; end-to-end QA pending |
| Direct trades | Parties, item, quantity, price, reservation, response, expiry, settlement/failure | Private player-to-player offers and settlement | Operational/account life; account deletion resolves entanglements and deletes/reparents affected records according to integrity needs | Implemented; QA pending |
| Reports and moderation | Reporter/target, content/context, category, evidence snapshot/hash, action, appeal, reviewer history | Safety review, enforcement, appeals, legal duties | Draft target: active case plus generally 24 months after closure; longer for repeat abuse or legal hold | Policy-covered release target; durable models and complete UX not yet implemented |
| Gameplay | Agents, ships, inventory, balances, progression, missions, world actions, transactions | Provide and secure the game | Account life; player-specific records deleted; shared world objects may remain without personal attribution | Implemented |
| Purchases/subscriptions | Store, product, transaction/order ID, receipt/token hash, environment, expiry, renewal, refund/reversal/manual-review state | Apple/Google verification, entitlement, accounting, fraud/disputes | Ledger retained up to 10 years where legally required and reparented to deleted-user record on deletion | Implemented; store lifecycle/device QA gated |
| Notifications | Push token, platform, active state, delivery tickets/receipts, notification content/status | Expo Push, APNs/FCM delivery and troubleshooting | Token until invalid/replaced/permission withdrawal/deletion; receipts only for retry/troubleshooting | Implemented |
| Mixpanel analytics | Internal account ID, Ascion username, platform, app/build context, named app/gameplay/purchase events and properties; provider-inferred coarse location | EU-hosted product analytics; Mixpanel | Configured project retention must be recorded before release; account deletion/objection workflow must be verified | Implemented; policy previously understated username sharing |
| Crash/performance | Errors, stack traces, routes, device/app context, timings, scrubbed diagnostic fields | Sentry | Draft target up to 90 days identifiable; configured project retention must be verified | Implemented with default PII disabled and custom scrubbers |
| Server/security logs | IP, user agent, request/time/path metadata, authentication/rate-limit/security signals | Railway/application logs, security and debugging | Generally 30-90 days; longer for documented incidents or legal holds | Implemented; hosting retention configuration needs read-back |
| Infrastructure | Database rows, Redis presence/cache, media URLs/objects, delivery metadata | Neon, Railway, AWS, Cloudflare and related infrastructure | Follows the relevant data category; backups rotate separately | Implemented; processor/transfer register needs review |
| Closed testing | Waitlist email, platform, Discord identity/status, invitation result | Resend and platform invitation operations | Until testing administration no longer needs it or deletion/objection applies, subject to necessary invitation records | Implemented for testing operations |

## Code reconciliation findings

- Mobile Mixpanel calls `identify(accountId)` and sets `username` and `$name`.
  The prior policy's claim that Mixpanel received only a pseudonymous account ID
  was inaccurate.
- Firebase Analytics is not integrated. Firebase Admin/Cloud Messaging is used
  for push delivery; it must not be declared as analytics.
- Sentry uses `sendDefaultPii: false` and custom event/breadcrumb scrubbers on
  mobile and server. This reduces but does not eliminate diagnostic context.
- On-demand translation sends selected chat text to OpenAI and saves a shared
  per-message/per-language translation. Provider response storage is disabled.
- Discord linking stores Discord profile identifiers and synchronizes Service
  roles from Ascion account and Prime-entitlement state.
- The deletion worker deletes authored chat and translations, social membership,
  friendships, notifications, and player-specific rows. It reparents limited
  purchase, subscription, sales, activity, and audit records to a deleted-user
  system account and may preserve shared world objects without player attribution.
- Complete report, moderation-action, appeal, and directional block models are
  still release-gated. Policy wording covers the intended data flow conditionally
  and does not establish that those workflows are currently available.

## Store-disclosure mapping to verify before publication

The App Store privacy labels and Google Play Data safety form should be reviewed
against at least these categories: contact information, user IDs, usernames,
user-generated content, social graph, purchases, app interactions, other gameplay
activity, approximate location inferred from IP, crash data, diagnostics, and
push/device identifiers. Each form must also account for third-party SDK and
processor collection, especially Mixpanel, Sentry, Expo/FCM, OpenAI translation,
and sign-in/billing providers.

## Publication gates

- Verify configured retention in Mixpanel, Sentry, Railway logs, Neon backups,
  Redis, and relevant platform/provider consoles.
- Confirm processor agreements, SCCs/adequacy coverage, subprocessors, and
  controller-versus-processor roles.
- Add a clear first-use disclosure and any required permission before sending
  chat text to OpenAI.
- Confirm the lawful analytics consent/objection design and provide any consent
  or opt-out control required by applicable law and app-store rules.
- Reconcile Apple privacy labels and Google Play Data safety answers with this
  inventory and the shipped binary.
- Complete product review and external Czech/EU privacy counsel review.
- Publish/tag only after approval, update consumer submodule pins, regenerate
  bundled legal content, and require acceptance of the new version.
