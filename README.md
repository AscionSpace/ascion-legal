# Ascion legal — DRAFT copy pending counsel review

This repository is the **single source of truth** for Ascion's user-facing
legal copy (Terms of Service, Privacy Policy). Both the backend
(`ascion-server`) and the marketing site (`ascion-website`) consume it as a
git submodule pinned to a tag — never edit these files inside those repos.

These documents have been written by the developer from industry templates
and **have not been reviewed by counsel**. Do **not** ship to production /
App Store review / TestFlight distribution wider than closed
friends-and-family until a qualified lawyer (preferably Czech-jurisdiction,
versed in EU consumer protection, GDPR, and virtual-goods law) has reviewed
and signed off on each document.

Every user-facing document is versioned with a `version` field at the top
(e.g., `version: 2026-04-20-draft-1`) and each publish cuts a matching git
tag (e.g., `v2026-04-20-draft-1`). The server's `auth.acceptTerms` endpoint
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
| `TERMS_OF_SERVICE.md`   | `2026-04-20-draft-3`  | DRAFT  | Not reviewed by counsel. Apple + Google Sign-In. Named operator = 1101 Capital s.r.o. |
| `PRIVACY_POLICY.md`     | `2026-04-23-draft-4`  | DRAFT  | Not reviewed by counsel. Named sub-processors (Google/Firebase, Mixpanel, Sentry). Event analytics + coarse-location disclosed. Advertising-personalization signals disabled. |

## Constraints these drafts are written under

Locked decisions (do not re-open without product-level reason):

- **Minimum age: 16+ worldwide, including EEA.** COPPA-safe by exclusion;
  EEA parental-consent flow is explicitly not built.
- **Governing law: Czech Republic** (the provider's jurisdiction).
- **Sign-in: Apple Sign-In is the sole production authentication path.**
  ToS/Privacy must not promise other auth methods.
- **No Web3 vocabulary in user-facing clauses.** Blockchain / crypto
  specifics are disclosed only where legally required, and prefer
  infrastructure-agnostic language (e.g., "pseudonymous internal account
  identifier" rather than "wallet address").
- **No financial-product language.** Virtual credits are virtual credits,
  licensed to the user, not property, not a security, not a token.
- **iOS-only at MVP.** Android-specific clauses are not included yet.

## What a counsel reviewer will specifically need to look at

1. The arbitration / dispute-resolution clause — drafted as CZ-court
   exclusive jurisdiction with an optional pre-litigation negotiation step.
   Needs cross-check against EU consumer-rights rules (the "weaker party"
   cannot be forced into disadvantageous arbitration).
2. The "virtual items are licenses not property" language — needs
   validation against Czech consumer-protection statutes and the
   Digital Services Act where applicable.
3. The privacy legal bases — currently claims `contract` for core service
   operation and `legitimate interest` for fraud/abuse logs. A reviewer
   should confirm the balancing tests hold.
4. International data transfer language — placeholder SCC wording is
   included; reviewer needs to confirm actual processor list and adequacy
   status.
5. Data retention periods — ranges are defensible defaults, not
   individually justified.
6. DPO contact block is a placeholder. Real contact must be supplied
   before public release.
7. The "pseudonymous internal account identifier" framing — reviewer
   should confirm this is defensible disclosure given the identifier is,
   technically, an on-chain address. The current framing is deliberately
   infrastructure-agnostic; lawyer may need to strengthen the disclosure
   if crypto specifics become legally necessary.

## How to update

1. Edit the relevant file.
2. Bump the `version` field at the top of the file (date-based).
3. Update the Status table above.
4. On next client release, the server will re-prompt acceptance for any
   user whose `Account.tosAcceptedVersion` or `Account.privacyAcceptedVersion`
   is not the current version.
