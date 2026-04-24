# Store Submission Checklist

Launch-readiness checklist for **Ascion** on the **Apple App Store**
and **Google Play**.

This checklist is based on the current legal documents in this repository and on
current official Apple and Google platform guidance as checked on
**2026-04-23**. It is an operational checklist, not legal advice.

## Blockers before submission

- **Account deletion must be available in-app.**
  Apple requires apps that support account creation to let users
  initiate account deletion within the app.
- **Account deletion must also be available outside the app for Google
  Play.**
  Google Play requires a readily discoverable in-app deletion path and
  a web link where users can request account deletion.
- **Privacy policy must be public, stable, and linked both in-store and
  in-app.**
  Apple requires a privacy policy link in App Store Connect and within
  the app. Google Play requires a privacy policy in the designated Play
  Console field and within the app.
- **Store privacy disclosures must match the real SDK behavior.**
  Apple App Privacy labels and Google Play Data safety answers must
  match the app and the policy for Apple Sign-In, Google Sign-In,
  Firebase Analytics, Firebase Cloud Messaging, Mixpanel, Sentry, push
  tokens, IP-based coarse location, purchase receipts, and account
  identifiers.
- **Payment flows for digital goods must use platform billing.**
  Apple requires in-app purchase for digital goods and subscriptions.
  Google Play billing is required for digital goods and subscriptions
  distributed on Google Play.
- **Subscription screens must be explicit.**
  If `Ascion Prime` is offered, the purchase screen and related store
  metadata should clearly state price, billing period, auto-renewal,
  what benefits are included, and how cancellation works.

## High priority before launch

- **Make the in-app delete flow easy to find.**
  Put it in account/settings, not hidden behind support friction.
- **Add a public web deletion page for Google Play.**
  A simple support page or form is sufficient if it clearly lets users
  request account deletion without reinstalling the app.
- **Prepare App Review / Play review access.**
  Since the game has login, provide reviewer instructions, a test path,
  or another way for reviewers to access the app without getting stuck.
- **Confirm Sign in with Apple is offered on iOS anywhere Google Sign-In
  is used for the primary account.**
  Apple requires an equivalent Sign in with Apple option when a
  third-party or social login is used for the app’s primary account.
- **Keep all metadata consistent.**
  App descriptions, screenshots, age ratings, subscription messaging,
  privacy answers, and the policy URLs should all describe the same
  product and same data practices.
- **Verify deletion and retention behavior operationally.**
  The app and backend should do what the policy says: delete account
  data on request except for data you retain for fraud, security,
  accounting, or legal obligations.

## Conditional checks

- **If you sell any randomized paid rewards or loot boxes, disclose the
  odds before purchase.**
  Apple and Google both require clear pre-purchase odds disclosure for
  paid randomized virtual items.
- **If analytics cookies, SDK storage, or similar technologies require
  consent in target jurisdictions, implement that consent flow before a
  worldwide launch.**
  The current policy text preserves this caveat, but product and legal
  review still need to decide whether consent is required in practice.
- **If the app targets or can attract minors despite the 16+ rule,
  verify store age ratings and content settings carefully.**
  The store ratings questionnaire must reflect actual game content and
  monetization.

## Already reflected in the current legal documents

- Minimum age set to **16+ worldwide**.
- Apple and Google sign-in disclosed.
- Apple and Google platform billing now reflected in Terms and Privacy.
- In-app purchases described as platform-processed rather than
  developer-processed.
- Privacy policy explains analytics, crash reporting, push tokens,
  coarse location, deletion requests, and retention at a high level.
- Czech governing law language is softened to preserve stronger
  mandatory consumer rights in the user’s home jurisdiction.

## Still recommended for counsel review

- Whether Firebase Analytics and Mixpanel can rely on legitimate
  interest in all target markets, or whether consent is needed in some
  jurisdictions.
- Whether the virtual-item and no-property language is enforceable as
  drafted under Czech and other consumer laws.
- Whether the jurisdiction and dispute wording is optimal for a
  worldwide consumer game.
- Whether retention periods are sufficiently justified and specific.

## Official source links checked on 2026-04-23

- Apple App Review Guidelines:
  [developer.apple.com/appstore/resources/approval/guidelines.html](https://developer.apple.com/appstore/resources/approval/guidelines.html)
- Apple account deletion guidance:
  [developer.apple.com/support/offering-account-deletion-in-your-app/](https://developer.apple.com/support/offering-account-deletion-in-your-app/)
- Apple subscriptions guidance:
  [developer.apple.com/app-store/subscriptions/](https://developer.apple.com/app-store/subscriptions/)
- Google Play User Data policy:
  [support.google.com/googleplay/android-developer/answer/10144311](https://support.google.com/googleplay/android-developer/answer/10144311)
- Google Play account deletion guidance:
  [support.google.com/googleplay/android-developer/answer/13327111](https://support.google.com/googleplay/android-developer/answer/13327111)
- Google Play subscriptions guidance:
  [support.google.com/googleplay/android-developer/answer/9900533](https://support.google.com/googleplay/android-developer/answer/9900533)
- Google Play payments policy:
  [support.google.com/googleplay/android-developer/answer/10281818](https://support.google.com/googleplay/android-developer/answer/10281818)
- Google Play Developer Program Policy:
  [support.google.com/googleplay/android-developer/answer/16549787](https://support.google.com/googleplay/android-developer/answer/16549787)
