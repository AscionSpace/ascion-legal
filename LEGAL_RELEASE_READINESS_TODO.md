# Legal, Social, and IAP Release Readiness

Status: working implementation plan
Prepared: 2026-08-11
Scope: the `2026-08-11-draft-2` Terms release and the product changes needed
to make its social and purchase statements true in production.

This is an implementation checklist, not legal advice. Keep the affected
features unavailable in a public release until the applicable critical gates
below are complete, or explicitly reduce the release scope.

## Decisions recorded on 2026-08-11

- Prime remains monthly-only. The yearly SKU must not be exposed or accepted.
- IAP remains Apple-only until Google Play backend verification, acknowledgement,
  restore/query, lifecycle notifications, refund handling, and QA are complete.
- Refunded Prime is revoked automatically. Credits, storage, and accommodation
  entitlements are reversed automatically only when player state remains valid;
  unsafe cases go to guarded manual review without an immediate deduction.
- `safety@ascion.space` is the public social-safety and appeal address. Monitoring
  ownership and response targets still need to be assigned.
- Ascion does not sell randomized containers or randomized rewards. Any future
  change to that decision reopens product, legal, odds, age-rating, and store
  disclosure review.

## Release gates

| Gate | Requirement | Release blocker |
| --- | --- | --- |
| G0 | Product and legal decisions are recorded | Yes |
| G1 | Chat reporting, blocking, filtering, moderation, and appeals work end to end | Yes for social launch |
| G2 | IAP restore, secure notifications, lifecycle handling, and product copy work end to end | Yes for IAP launch |
| G3 | Terms, Privacy Policy, community rules, and operational policies are approved and aligned | Yes |
| G4 | Device, two-account, security, deletion, and store-compliance QA pass | Yes |
| G5 | Legal documents are versioned, published, propagated, and re-accepted | Yes |

## Current-state summary

Already present:

- Chat supports world, organization, and direct threads, persisted messages,
  soft-deletion fields, friendship-gated direct chat, and server-side access
  checks.
- Usernames have a server-side forbidden-word check.
- IAP purchases are server-verified and transaction IDs are idempotent.
- Prime renewal and cancellation-status notifications have deployed handlers.
- Account deletion removes chat messages, memberships, invitations, and
  friendships from the deleting account.
- Mobile embeds versioned Terms and Privacy content and records acceptance
  timestamps and versions.

Known gaps:

- No player-facing report-message or report-user workflow.
- No usable block/unblock workflow; `FriendshipStatus.BLOCKED` exists but is
  not exposed as a complete player safety feature.
- No moderation queue or moderation audit/appeal surface in Command.
- Chat, organization descriptions, and invitation text do not use a shared
  content-safety filter.
- Restore Purchases is exposed to normal players in Settings and the Prime
  purchase screen. It reconciles each available store transaction through the
  idempotent server verification path and reports full success, no purchases,
  partial failure, pending items, and retry guidance. Reinstall and same-store-
  account device QA remain outstanding.
- Full Apple server-notification JWS verification is deployed for the outer
  notification and nested transaction/renewal payloads. The production Apple
  app ID, live schema, and V2 Sandbox/Production notification URLs are verified,
  and an Apple-originated Sandbox `TEST` delivery succeeded on 2026-08-11.
- Safe refund/revocation reconciliation is deployed for Prime, credits,
  storage, and accommodation entitlements, including guarded manual review for
  unsafe cases. Real Sandbox cancellation, expiry, refund, revocation, replay,
  and operator-workflow QA remain blocking MVP evidence.
- Apple's production Server API returns 401 while Ascion 1.0 remains
  `PREPARE_FOR_SUBMISSION`; repeat the production notification `TEST` after the
  first public App Store release unlocks production API access.
- Prime is monthly-only in mobile, the local server whitelist, and the draft
  Terms. Any dormant yearly product must remain unavailable in store metadata.
- The server accepts any non-empty Terms and Privacy version submitted by a
  client and does not enforce the current published versions on gameplay APIs.
- The active Privacy Policy predates chat, friendships, presence,
  organizations, reports, moderation, and the expanded entitlement catalog.

## G0 — decisions to make first

- [ ] **G0.1 Decide the public launch scope.**
  - Decide whether chat, organizations, direct trading, and every IAP category
    launch together or in phases.
  - If any critical gate cannot be completed, keep that feature disabled by a
    production feature flag rather than relying on Terms text alone.
  - Done when the launch matrix names each feature and its target release.

- [ ] **G0.2 Decide the moderation contact and response ownership.**
  - `safety@ascion.space` is the selected public address and works through the
    domain catch-all. Confirm a monitored destination and named owners before
    launch.
  - Name the people responsible for first response, urgent escalation,
    moderation decisions, and appeals.
  - Define target response times for ordinary, urgent-safety, and allegedly
    illegal-content reports.
  - Done when the contact works, is monitored, and has an owner rota/runbook.

- [ ] **G0.3 Decide the moderation policy.**
  - Approve report categories, prohibited-content categories, warning versus
    removal rules, temporary and permanent social restrictions, account-ban
    thresholds, and appeal rules.
  - Decide what automated filtering will block, hold for review, or merely
    flag; avoid a naive substring list as the only chat safety control.
  - Done when engineering has an approved, versioned policy specification.

- [x] **G0.4 Decide the Prime catalog.**
  - Decision: monthly-only for now. The yearly SKU is removed from the local
    server whitelist and yearly wording is removed from the draft Terms.
  - Confirm the exact current benefits and ensure the paywall, App Store
    metadata, feature registry, and Terms say the same thing.
  - Done when there is one authoritative product/benefit matrix.

- [x] **G0.5 Decide the refund/revocation policy for each IAP type.**
  - Cover credits, repeatable storage, permanent accommodation entitlements,
    and Prime.
  - Define safe behavior when credits were spent, storage is occupied, or an
    accommodation is assigned when a refund arrives.
  - Preserve database-only operation; blockchain settlement must remain
    optional and cannot be required to correct an entitlement.
  - Decision: revoke refunded Prime automatically. Reverse credits, storage,
    and accommodations automatically only when the database state remains
    valid; otherwise preserve player state and create a guarded manual review.
  - Done when every product type has an automatic or explicit manual-review
    outcome that cannot corrupt player state.

- [x] **G0.6 Decide whether randomized containers are purchasable.**
  - Map every path from real-money IAP credits to a randomized container or
    randomized reward.
  - If such a path exists, approve the odds presentation and age/store-rating
    treatment before enabling it.
  - Decision: Ascion does not sell randomized containers or randomized rewards.
    Re-open this gate before any product or economy change creates such a path.
  - Done when every affected purchase screen has a documented odds source.

- [ ] **G0.7 Obtain legal classification advice.**
  - Ask Czech/EU counsel to review consumer-law wording, the Digital Services
    Act classification and applicable small-business duties, notice/action and
    appeal handling, virtual items, subscriptions, player trading, and
    retention of moderation evidence.
  - Done when required wording and operational obligations are recorded.

## G1 — social safety and moderation implementation

### Server and data model

- [ ] **G1.1 Add durable social-safety records.**
  - Add a directional player block model rather than relying solely on the
    existing friendship row.
  - Add content-report records with reporter, target account, optional message,
    organization/thread context, category, description, status, timestamps,
    and an immutable content snapshot/hash.
  - Add moderation-action and appeal records with policy basis, reason,
    moderator/source, duration, notification state, and decision history.
  - Define deletion and retention behavior for all new records.
  - Done when schema validation, production `db:push`, generated types, and
    focused model tests pass.

- [ ] **G1.2 Add player report endpoints.**
  - Support reporting a message, player profile/identifier, organization,
    invitation, and direct trade offer.
  - Require a reason category, accept optional context, deduplicate abusive
    repeats, rate-limit submissions, and return a report reference.
  - Preserve enough evidence for review even if the visible message is later
    deleted, while minimizing copied personal data.
  - Done when authorization, privacy isolation, rate-limit, and idempotency
    tests pass.

- [ ] **G1.3 Add block and unblock endpoints with full enforcement.**
  - Enforce blocks in player search, friend requests, direct-thread creation,
    direct messages, direct-trade offers, organization invitations, presence,
    push notifications, and unread counts.
  - Hide blocked-player world/organization messages locally or server-side as
    the approved policy specifies.
  - Cancel or safely resolve pending direct offers when a block occurs.
  - Never reveal to the blocked player more relationship state than necessary.
  - Done when two-direction and race-condition tests cover every social path.

- [ ] **G1.4 Apply a shared content-safety pipeline.**
  - Cover username, organization name/tag/description, invitation text, world
    chat, organization chat, direct chat, and trade-offer messages.
  - Normalize Unicode and common evasion safely; separate hard legal/safety
    blocks from softer profanity policy.
  - Return neutral player-facing errors and keep the matched rule out of public
    API responses.
  - Add rate limits and spam/flood controls in addition to text filtering.
  - Done when adversarial, false-positive, Unicode, and localization tests pass.

- [ ] **G1.5 Add moderation actions and reason notices.**
  - Allow authorized operators to remove/restore content, rename identifiers,
    restrict posting, remove organization membership where permitted, and
    suspend accounts.
  - Make soft-deleted chat content disappear from thread previews, message
    pages, unread counts, notifications, and realtime updates.
  - Notify the affected user with a clear policy basis and appeal path unless
    law, safety, or investigation integrity prevents it.
  - Done when every action is authorized, audited, reversible where intended,
    and visible consistently across clients.

- [ ] **G1.6 Add an appeal workflow.**
  - Let an affected user appeal an eligible moderation decision electronically.
  - Prevent the same operator from silently overwriting history; append review
    decisions and record reversals.
  - Done when submission, review, notice, and restoration/restriction outcomes
    are tested.

### Mobile

- [ ] **G1.7 Add message and profile safety actions.**
  - Add Report to message actions and Report/Block to player/profile actions.
  - Include clear categories, optional details, confirmation, report reference,
    safety guidance, and a link to the applicable rules.
  - Do not require a player to remain friends with someone in order to report or
    block them.
  - Done when a normal player can report and block in a few clear steps.

- [ ] **G1.8 Add blocked-player management.**
  - Add a Settings screen listing blocked players with an explicit Unblock
    action and consequences.
  - Done when state refreshes immediately across search, friends, threads, and
    notifications.

- [ ] **G1.9 Add moderation-decision and appeal UI.**
  - Show the affected content/account action, reason, duration, policy link,
    and appeal control where eligible.
  - Done when notice remains accessible after push dismissal and supports
    accessibility/localization.

### Command and operations

- [ ] **G1.10 Build a least-privilege moderation queue in Command.**
  - Filter by urgency, category, surface, status, and age.
  - Show only necessary context, related reports, prior actions, and relevant
    account risk signals.
  - Require a reason for every action and prevent casual access to unrelated
    private messages.
  - Done when permissions, auditing, redaction, and action tests pass.

- [ ] **G1.11 Publish and rehearse the moderation runbook.**
  - Cover illegal content, child-safety material, threats, self-harm, fraud,
    impersonation, privacy exposure, IP complaints, law-enforcement requests,
    evidence preservation, appeals, and false reports.
  - Done when an owner has completed a tabletop exercise for urgent and routine
    reports.

## G2 — IAP implementation and disclosure

- [ ] **G2.1 Expose Restore Purchases to normal players.**
  - Implemented 2026-08-11: visible actions are present in Settings and the
    Prime screen.
  - Implemented: every available transaction is reconciled through the existing
    idempotent server verification path, and the UI explains that consumed
    credit/storage purchases are not replayed as new grants.
  - Implemented: per-product success, no-purchases-found, partial failure,
    pending, and retry results are shown.
  - Done when restore works after reinstall and on another device using the same
    store and Ascion accounts. This device QA remains blocking evidence.

- [ ] **G2.2 Fully verify App Store server-notification JWS payloads.**
  - Replace decode-only parsing with certificate-chain, bundle, app, environment,
    and signed-data verification using Apple's supported server library/process.
  - Reject unverifiable notifications without mutating player state.
  - Deployed progress: Apple's `SignedDataVerifier` validates the certificate
    chain, signature, bundle, app ID, and environment for the notification and
    verifies nested signed transaction/renewal claims before invoking any
    entitlement handler. Tamper, environment, and handler-isolation tests pass;
    Apple recorded a successful signed Sandbox `TEST` delivery to the deployed
    V2 endpoint on 2026-08-11. Keep this unchecked until the real Sandbox
    lifecycle scenarios pass and a production `TEST` succeeds after the first
    public App Store release unlocks production Server API access.
  - Done when valid production/sandbox fixtures pass and tampered fixtures fail.

- [x] **G2.3 Make notification processing retry-safe and idempotent.**
  - Implemented locally 2026-08-11: verified notification UUID/hash, environment,
    type, transaction identity, signed time, attempt count, status, error, and
    handler outcome are persisted in `IapStoreNotification`.
  - Implemented: exact successful replays return the recorded outcome without
    rerunning entitlement logic; concurrent claims return retryable HTTP 503;
    failed claims retry immediately; abandoned processing claims can be safely
    reclaimed; UUID reuse with different signed content is rejected.
  - Implemented: invalid verification receives HTTP 400, transient Apple
    verification failure receives 503, and post-verification processing failure
    receives 500 and a durable `FAILED` outcome.
  - Implemented: refund/revocation reconciliation remains terminal/idempotent,
    renewal expiration only moves forward, and auto-renew status updates use the
    signed Apple event time so older or concurrent events cannot overwrite newer
    state.
  - Local replay, out-of-order, DB failure/recovery, stale-claim, concurrency,
    and identity-conflict tests pass. Closed 2026-08-13 after `npm run db:push`
    (no migration), successful Railway deployment, a fresh Apple Sandbox `TEST`
    recorded by Apple as `SUCCESS`, production inbox read-back as `SUCCEEDED`,
    and an identical deployed-webhook replay returning `duplicate: true` while
    the persisted `attemptCount` remained `1`.

- [ ] **G2.4 Complete subscription lifecycle handling.**
  - Cover subscribe, renew, renewal-status changes, billing retry/grace period,
    failed renewal, expiration, renewal extension, refund, and revoke events.
  - Reconcile `Account.primeUntil`, active subscription, subscription history,
    and player-visible state from authoritative store data.
  - Emit operational alerts for unknown products/accounts and unreconciled
    events.
  - Implemented locally 2026-08-13: verified `SUBSCRIBED`, `DID_RENEW`,
    `DID_CHANGE_RENEWAL_STATUS`, `DID_FAIL_TO_RENEW` with and without grace,
    `GRACE_PERIOD_EXPIRED`, `EXPIRED`, and `RENEWAL_EXTENDED` events now
    reconcile the Apple transaction ledger, `AccountSubscription`, and
    `Account.primeUntil`. Cancellation retains access through the paid expiry;
    grace retains access only through Apple's signed grace deadline; failed
    renewal without grace, grace expiry, and terminal expiry remove access.
    Signed event-time guards prevent older lifecycle events from overwriting
    newer state, and unknown products/accounts or otherwise unreconciled events
    fail retryably with Sentry alerts instead of being silently acknowledged.
    The focused IAP suite passes 56 tests and the server build passes. Keep G2.4
    unchecked until the real StoreKit sandbox lifecycle matrix and deployed
    database read-back pass.
  - Done when the lifecycle matrix is covered by tests and sandbox events.

- [ ] **G2.5 Implement safe refund/revocation reconciliation.**
  - Implement the approved G0.5 behavior for Prime, credits, storage, and
    accommodations.
  - Create a manual review queue for cases that cannot be reversed safely.
  - Keep database state authoritative and separately reconcile any optional
    blockchain settlement.
  - Deployed progress: automatic safe reversal and guarded manual
    review/resolution endpoints are implemented with focused tests; production
    schema, configuration, deployment, and signed Sandbox notification delivery
    are verified. Real Sandbox refund/revocation, replay, and operator-workflow
    evidence remains the blocking MVP boundary.
  - Done when every refund event reaches a terminal audited outcome.

- [ ] **G2.6 Align the server catalog, mobile UI, and store catalog.**
  - Deferred from the active implementation queue on 2026-08-15. This item is
    not waived: it is a hard MVP release gate that must be reopened and closed
    before App Store or Google Play submission.
  - Remove or hide dormant SKUs, or expose them intentionally.
  - Verify product type, localized name, description, price, territory,
    availability, benefit, and server grant for every SKU.
  - Do not use a hard-coded fallback price as if it were the store price.
  - Done when catalog read-back matches a checked-in reviewed product matrix.

- [ ] **G2.7 Complete purchase-screen disclosures.**
  - Show localized price and period, what is granted, whether the product is
    consumable/restorable/repeatable, auto-renewal, cancellation path, and
    functional Terms and Privacy links at the point of subscription purchase.
  - Implemented locally 2026-08-15: the Prime purchase screen now uses only the
    localized store price, identifies the monthly auto-renewable subscription
    as optional and restorable, explains platform billing/renewal/cancellation,
    retains Restore Purchases and subscription-management actions, and links
    directly to the in-app Terms and Privacy readers. The Credits purchase
    screen now identifies packs as exact-grant, one-time consumables that may be
    purchased repeatedly but are not restored, includes platform charging copy,
    and links to Terms and Privacy. Purchase, restore, management, and legal
    actions expose screen-reader roles, labels, hints, disabled state, and busy
    state. Focused disclosure tests and mobile TypeScript verification pass.
    Keep G2.7 unchecked until signed-in screenshots and device accessibility
    review confirm the final presentation before confirmation.
  - Randomized-reward odds are not applicable to the approved catalog. Re-open
    G0.6 and this requirement before introducing any such product.
  - Done when screenshots and accessibility review confirm disclosure before
    confirmation.

- [ ] **G2.8 Define the Android boundary.**
  - The implementation is no longer Apple-specific. The Android client loads
    localized Google Play products and subscription offers, binds purchases to
    the signed-in Ascion account with an obfuscated account ID, handles pending
    purchases, and exposes the shared restore/query flow. The server verifies
    purchase tokens against the Google Play Developer API, checks product and
    account ownership, grants idempotently, then consumes consumables or
    acknowledges durable products and Prime after the entitlement transaction.
  - Authenticated Real-time developer notifications validate the Pub/Sub OIDC
    identity and Android package, then re-query authoritative Play state before
    reconciling Prime renewal, cancellation, grace, hold, pause, expiry,
    revocation, one-time purchases, and voided/refunded purchases.
  - Focused tests cover purchase parsing, account binding, rejected pending/held
    purchases, consume/acknowledge behavior, acknowledgement races, Pub/Sub route
    authentication, package validation, test-notification parsing, subscription
    activation, scheduled cancellation, account-hold suspension, revocation,
    voided refunds, and one-time notification fulfillment.
  - Keep Android IAP out of public availability claims until Play Console catalog
    and service-account permissions are read back, Pub/Sub OIDC configuration and
    a Play Console test notification succeed against the deployed server, and an
    internal-track physical-device matrix records transaction and database
    evidence. G2.6 catalog alignment and G2.9 device QA remain separate hard
    gates.
  - Done when store availability, deployed configuration, recorded Play
    evidence, and legal wording all match actual Android support.

- [ ] **G2.9 Run the IAP device/sandbox matrix.**
  - Test success, cancel, pending, duplicate callback, network loss before and
    after store confirmation, reinstall, restore, account mismatch, renewal,
    cancellation, grace period, expiration, refund, revoke, and server outage.
  - Include credits, every storage size, every accommodation product, and each
    enabled Prime period.
  - Done when grants are exactly-once and every failure has a recoverable UX.

## G3 — legal documents and operational policy

- [ ] **G3.1 Revise the Privacy Policy.**
  - Disclose chat content, usernames and organization content, friendships and
    social graph, presence/last-seen status, invitations, reports, blocks,
    moderation evidence/actions/appeals, direct trades, purchase receipts,
    subscription and permanent-entitlement records, and related notifications.
  - State purposes, legal bases, recipients/processors, international transfer
    treatment, retention periods, account-deletion effects, and user rights.
  - Reconcile Mixpanel/Firebase/Sentry payloads with actual code and store privacy
    disclosures.
  - Done when the data inventory and policy match field by field.

- [ ] **G3.2 Finalize the Terms draft.**
  - Apply G0 decisions and counsel changes to `TERMS_OF_SERVICE.md`.
  - Resolve monthly versus yearly Prime, Apple-only versus multi-platform IAP,
    reporting contact, moderation/appeal promises, refund wording, and
    randomized-reward wording.
  - Keep mandatory consumer rights and actual product limitations explicit.
  - Done when product, engineering, operations, and counsel approve one final
    release candidate.

- [ ] **G3.3 Create a public Community and Content Policy.**
  - Convert the approved moderation rules into concise player-facing rules with
    examples, enforcement range, reporting route, and appeal route.
  - Link it from first social use, chat safety actions, moderation notices, the
    website, and store support metadata where appropriate.
  - Done when it is versioned and accessible without signing in.

- [ ] **G3.4 Create an electronic illegal-content/reporting route.**
  - Based on counsel's DSA advice, provide the necessary public mechanism and
    contact point, required notice fields, acknowledgements, decision notices,
    and appeal information.
  - Keep ordinary Terms violations distinct from allegations of illegal content
    where the workflow or notice requirements differ.
  - Done when a signed-out reporter can submit a sufficiently specific notice
    and receive the required communications.

- [ ] **G3.5 Approve the retention and deletion matrix.**
  - Cover visible messages, deleted messages, direct trades, reports, report
    snapshots, blocks, moderation actions, appeals, purchase records, receipts,
    subscription events, and security logs.
  - Define what is deleted, anonymized, retained, or legally held after account
    deletion and reflect it in code and the Privacy Policy.
  - Done when deletion tests match the approved matrix.

- [ ] **G3.6 Make legal acceptance server-authoritative.**
  - Build current published Terms/Privacy versions into server configuration or
    a reviewed release artifact.
  - Reject arbitrary or stale acceptance versions.
  - Enforce current acceptance on protected gameplay/social/purchase APIs while
    preserving sign-in, legal reading/acceptance, support, and account-deletion
    access.
  - Define how old app versions receive a required-update/legal-update response.
  - Done when an old client cannot continue affected use without accepting the
    current documents and valid acceptance remains timestamped.

## G4 — QA, security, and store readiness

- [ ] **G4.1 Run two-account social safety QA.**
  - Cover world, organization, and direct chat; report; block/unblock; search;
    invitations; push; realtime updates; unread counts; direct trades;
    moderation removal; notice; appeal; and reversal.
  - Include simultaneous actions, stale clients, offline recovery, and blocked
    users attempting alternate entry paths.

- [ ] **G4.2 Run account-deletion and data-rights QA.**
  - Verify chat/social/purchase/moderation behavior during the 30-day grace
    period and after hard deletion.
  - Verify retained records are minimized and de-identified as promised and do
    not break thread or moderation history.

- [ ] **G4.3 Perform abuse and security testing.**
  - Test report spam, block evasion, Unicode/evasion text, oversized content,
    unauthorized moderation access, private-thread access, notification data
    leakage, forged IAP notifications, receipt replay, and account/transaction
    mismatch.

- [ ] **G4.4 Update store declarations and metadata.**
  - Re-answer Apple App Privacy and Google Play Data Safety from the final data
    inventory.
  - Update age-rating/content questionnaires for chat, user-generated content,
    direct trading, and the declaration that no randomized rewards are sold.
  - Verify privacy, Terms, support, account-deletion, and content-report URLs.
  - Update subscription and IAP metadata and App Review instructions.

- [ ] **G4.5 Collect release evidence.**
  - Save approved document versions, counsel/product approvals, test results,
    store screenshots, product catalog read-back, moderation runbook rehearsal,
    and production configuration read-back.

## G5 — publish and enforce the legal release

- [ ] **G5.1 Cut final legal versions.**
  - Replace draft frontmatter with an approved date-based release version and
    effective date in both Terms and Privacy.
  - Remove the draft notice and update `README.md` status/counsel notes.
  - Run formatting, frontmatter parsing, link, and diff checks.

- [ ] **G5.2 Commit, push, and tag `ascion-legal`.**
  - Use one reviewed legal release commit and matching immutable tag.
  - Do not move an existing legal tag.

- [ ] **G5.3 Update every consumer deliberately.**
  - Update the legal submodule pointer in `ascion-server`.
  - Update the legal submodule pointer in `ascion-website` and verify public
    `/terms` and `/privacy` pages.
  - Update the legal submodule pointer in `ascion-client-mobile`, regenerate
    `src/content/legal.generated.ts`, and verify both documents render.
  - Commit and push each nested repository separately without including
    unrelated work.

- [ ] **G5.4 Deploy in the safe order.**
  - Deploy server-side version validation/enforcement and public legal pages in
    coordination with the client release so no valid client is accidentally
    locked out.
  - Publish the mobile build/update only after server and web read-back pass.

- [ ] **G5.5 Verify re-acceptance and audit records.**
  - Confirm an existing account is prompted for both changed documents, can
    read them, cannot bypass acceptance, and records the exact released
    versions and timestamps.
  - Confirm refusal still allows support and account deletion.
  - Verify acceptance counts/errors after release without logging document
    content or unnecessary personal data.

- [ ] **G5.6 Record feature status after production verification.**
  - Update the Ascion feature registry only after production/device QA.
  - Record changes for social chat/safety, player organizations, direct chat
    trading, Prime, storage IAP, accommodation IAP, and legal acceptance.
  - Do not mark a feature `SHIPPED` while required production QA remains.

## Suggested implementation order

1. Complete G0 decisions.
2. Build G1 social safety and G2 IAP reliability in parallel.
3. Draft G3 documents against the implemented behavior, then obtain review.
4. Complete G4 QA and store updates.
5. Execute G5 as one coordinated legal/product release.

## Primary implementation anchors

- Legal source: `ascion-legal/TERMS_OF_SERVICE.md`,
  `ascion-legal/PRIVACY_POLICY.md`
- Social server: `ascion-server/src/routers/social.ts`,
  `ascion-server/prisma/schema/communication.prisma`,
  `ascion-server/prisma/schema/social.prisma`
- Organizations: `ascion-server/prisma/schema/organization.prisma`,
  `ascion-server/src/routers/organization.ts`
- Social mobile: `ascion-client-mobile/src/screens/FriendsScreen.tsx`,
  `ascion-client-mobile/src/screens/SocialThreadScreen.tsx`,
  `ascion-client-mobile/src/domain/atoms/social.ts`
- IAP server: `ascion-server/src/routers/iap.ts`,
  `ascion-server/src/routes/iap.ts`, `ascion-server/src/services/iap/`
- IAP mobile: `ascion-client-mobile/src/domain/atoms/iap.ts`,
  `ascion-client-mobile/src/screens/Prime/PrimeScreen.tsx`,
  `ascion-client-mobile/src/screens/BuyCredits/BuyCreditsScreen.tsx`,
  `ascion-client-mobile/src/screens/SettingsScreen.tsx`
- Legal acceptance: `ascion-server/src/services/auth/elementary/accept-terms.ts`,
  `ascion-client-mobile/src/screens/Terms/TermsScreen.tsx`
- Command: add a dedicated moderation area under `ascion-command/src/pages/`

## External requirements to re-check before release

- Apple App Review Guidelines, especially user-generated content and IAP:
  <https://developer.apple.com/app-store/review/guidelines/>
- Apple purchase restoration guidance:
  <https://developer.apple.com/documentation/storekit/restoring-purchased-products>
- Google Play user-generated-content moderation guidance:
  <https://support.google.com/googleplay/android-developer/answer/12923286>
- Google Play payments policy:
  <https://support.google.com/googleplay/android-developer/answer/9858738>
- EU Digital Services Act user-rights overview:
  <https://digital-strategy.ec.europa.eu/en/factpages/user-rights-under-digital-services-act>
