# Ascion legal — release-tracked user-facing copy

This repository is the **single source of truth** for Ascion's user-facing
legal copy (Terms of Service, Privacy Policy). Both the backend
(`ascion-server`) and the marketing site (`ascion-website`) consume it as a
git submodule pinned to a tag — never edit these files inside those repos.

The active release remains the last published tag. The Terms file on
`main` may be a review draft ahead of a new legal release; its frontmatter
controls that status. External counsel review remains strongly recommended,
especially for EU consumer protection, GDPR, virtual-goods law, user-generated
content and moderation, and any future Web3 or portability disclosures.

Every user-facing document is versioned with a `version` field at the top
(e.g., `version: 2026-04-24-release-1`) and each publish cuts a matching git
tag (e.g., `v2026-04-24-release-1`). The server's `auth.acceptTerms` endpoint
records the accepted version string on the `Account`. Any material change
to a document means a new version string, a new tag, and re-prompting the
user for acceptance on next launch.

## Consumers

- `ascion-server` — submodule at `legal/`. Endpoint `auth.acceptTerms`
  stores the accepted `tosVersion` / `privacyVersion` on each `Account`.
- `ascion-website` — submodule at `src/content/legal/`. Rendered at
  `/terms` and `/privacy` (public URLs required by App Store submission).

Both consumers pin a specific tag; bumping is a deliberate two-step: (1)
push a new tag here, (2) update the submodule pointer in each consumer.

## Status

| Document                | Version               | Status | Notes                                                |
| ----------------------- | --------------------- | ------ | ---------------------------------------------------- |
| `TERMS_OF_SERVICE.md`   | `2026-08-11-draft-2`    | DRAFT   | Records Apple-only IAP, monthly-only Prime, safe refund/revocation handling, `safety@ascion.space`, chat/UGC moderation, organizations, and trading. Pending product and counsel review; not published. |
| `PRIVACY_POLICY.md`     | `2026-08-15-draft-1`    | DRAFT   | Covers social/chat/translation, organizations, trading, Discord, purchases, analytics, retention, deletion, and rights. Pending processor/configuration verification, store-disclosure alignment, product review, and counsel review; the last published tag remains active. |
| `STORE_SUBMISSION_CHECKLIST.md` | n/a | WORKING | Apple App Store + Google Play launch-readiness checklist based on current official platform guidance. |
| `LEGAL_RELEASE_READINESS_TODO.md` | n/a | WORKING | Ordered implementation and release checklist for social safety, moderation, IAP reliability, privacy, legal acceptance, QA, and publication. |

## Constraints these documents are written under

Locked decisions (do not re-open without product-level reason):

- **Minimum age: 16+ worldwide, including EEA.** COPPA-safe by exclusion;
  EEA parental-consent flow is explicitly not built.
- **Governing law: Czech Republic** (the provider's jurisdiction).
- **Sign-in: Apple Sign-In and Google Sign-In are supported production
  authentication paths.** ToS/Privacy should stay aligned with the
  actual shipped sign-in methods.
- **No Web3 vocabulary in user-facing clauses.** Blockchain / crypto
  specifics are disclosed only where legally required, and prefer
  infrastructure-agnostic language (e.g., "pseudonymous internal account
  identifier" rather than "wallet address").
- **No financial-product language.** Virtual credits are virtual credits,
  licensed to the user, not property, not a security, not a token.
- **Mobile launch: Apple App Store and Google Play.** Legal copy,
  privacy disclosures, and store metadata should stay aligned across
  both platforms. Google Play billing is implemented but remains unavailable
  for public claims until its catalog, deployed configuration, and device QA
  gates are complete.

## What external counsel should specifically review next

1. The governing-law / dispute-resolution clause — drafted as
   Czech-law plus competent-Czech-court language with an optional
   pre-litigation negotiation step. Needs cross-check against EU
   consumer-rights rules so consumer forum rights are preserved where
   mandatory law requires them.
2. The "virtual items are licenses not property" language — needs
   validation against Czech consumer-protection statutes and the
   Digital Services Act where applicable.
3. The privacy legal bases — currently claims `contract` for core service
   operation and `legitimate interest` for fraud/abuse logs. A reviewer
   should confirm the balancing tests hold.
4. International data transfer language — safeguard wording is
   included; reviewer needs to confirm actual processor list, adequacy
   status, and transfer documentation.
5. Data retention periods — ranges are defensible defaults, not
   individually justified.
6. Privacy contact and DPO determination should be confirmed on an
   ongoing basis. If no DPO is legally required, the policy should
   keep a clear privacy point of contact such as `privacy@ascion.space`.
7. The "pseudonymous internal account identifier" framing — reviewer
   should confirm this is defensible disclosure given the identifier is,
   technically, an on-chain address. The current framing is deliberately
   infrastructure-agnostic; lawyer may need to strengthen the disclosure
   if crypto specifics become legally necessary.
8. The social/UGC clauses and actual moderation operation — confirm DSA
   classification and notice/action duties, response and appeal handling,
   retention of reported content, and whether a dedicated legal contact
   point is required.
9. The IAP clauses — confirm treatment of consumable credits, repeatable
   permanent storage, permanent accommodation entitlements, subscription
   renewal/cancellation, refunds/revocations, and cross-platform access.
10. Review the `2026-08-15-draft-1` Privacy Policy against the processor
    agreements and configured retention periods, especially OpenAI chat
    translation, Mixpanel username profiles, Discord role synchronization,
    moderation-evidence retention, and the limited records retained after
    account deletion.

## How to update

1. Edit the relevant file.
2. Bump the `version` field at the top of the file (date-based).
3. Update the Status table above.
4. On next client release, the server will re-prompt acceptance for any
   user whose `Account.tosAcceptedVersion` or `Account.privacyAcceptedVersion`
   is not the current version.
