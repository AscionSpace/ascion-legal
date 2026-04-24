---
version: 2026-04-23-release-1
status: ACTIVE
effective: 2026-04-23
---

# Privacy Policy

This Privacy Policy explains how we collect, use, share, and protect
personal data when you use the **Ascion** mobile application and
related online services (the "**Service**"). It is written with the
**EU General Data Protection Regulation (GDPR)** in mind and is
intended to serve EU/EEA, UK, Swiss, and global users alike, as
supplemented by local law.

## 1. Who we are (the controller)

The **controller** of your personal data for the purposes of applicable
data-protection law is **1101 Capital s.r.o.**, a Czech limited
liability company with registered office at Lidická 700/19, Veveří,
602 00 Brno, Czech Republic (IČO: 07180969; Data Box ID: `zi6aisw`).

**Privacy contact:** For any privacy or data-protection matter —
including questions about this Policy and requests to exercise your
rights described in §10 — email **privacy@ascion.space**. We have not
formally appointed a Data Protection Officer at this stage; the
address above is the single privacy contact. If our processing grows
to a scale that requires a DPO under Article 37 GDPR, we will appoint
one and update this Policy accordingly.

## 2. What personal data we collect

We collect only what is needed to operate and secure the Service.

### 2.1. You provide directly

- **Sign-in provider identifiers.** When you sign in with **Apple** we
  receive a stable Apple-issued user identifier and, optionally, the
  email address and name you choose to share; if you use Apple's "Hide
  My Email" feature we receive a relay email address, not your primary
  address. When you sign in with **Google** we receive a stable
  Google-issued user identifier and the email address associated with
  that Google account, plus the name and profile-picture URL where
  Google exposes them. We receive only the fields the respective
  sign-in provider sends; we do not scrape additional data from your
  Apple ID or Google account.
- **Username** you choose.
- **Age-gate confirmation.** During onboarding you confirm that you
  meet the minimum-age rule by checking the relevant age-gate prompt.
  We record the result of that confirmation and the associated
  timestamp. We do **not** collect or store your date of birth.

### 2.2. Automatically, as you use the Service

- **Device identifiers** (a device-level identifier we generate; the
  operating-system and app version; non-persistent device-model
  information).
- **Push-notification token** if you grant push permission, used to
  deliver transactional in-game notifications.
- **Server logs**, including timestamped records of the in-app actions
  you take, for operational, anti-fraud, anti-abuse, and debugging
  purposes. Logs may contain IP address, user-agent, and request
  metadata.
- **Event analytics** — the in-game actions you take (e.g., starting a
  mission, completing a craft, an in-app purchase), session events, and
  screen transitions, sent to our product-analytics processor in
  pseudonymous form to help us understand how the Service is used and
  improve it. See §7 for the named processors.
- **Coarse location** — country, region, and city inferred from your
  IP address by our analytics processors, used to report the
  geographic distribution of active users in aggregate. We do **not**
  collect precise (GPS-level) location.
- **Crash and performance telemetry.** Personally identifying context is
  scrubbed at the source where possible.
- **Gameplay state**, which is inherent to operating the Service (your
  agents, ships, credits balance, progression state, purchase history,
  and similar).

### 2.3. A pseudonymous internal account identifier

The Service assigns every account a **pseudonymous internal identifier**
that the system uses as a stable reference for operating the Service,
attributing actions to accounts, and maintaining consistency across
backend services. This identifier is not linked to your real-world
identity, does not by itself reveal personal data, and is not shown to
other users. It is technical infrastructure for the Service.

Depending on how the Service is operated internally, this identifier
may be derived from or reference a cryptographic key generated and held
by the Service on your behalf. **We do not provide the identifier, any
associated cryptographic material, or access to any underlying
infrastructure to you as a user, and no user-facing cryptocurrency or
"wallet" functionality is offered through the Service at this stage.**
Users do not manage this identifier directly through the Service as it
currently operates. If that changes materially, we will update this
Policy before the relevant feature is rolled out.

### 2.4. Payment data

In-app purchases are processed by the applicable platform operator,
such as **Apple** or **Google**. We do not see, store, or process your
payment-card, billing-address, or equivalent payment data. The platform
operator provides us with transaction records or purchase receipts that
we validate to credit your account.

## 3. What we do **not** collect

We do not collect:

- Precise geolocation.
- Contacts, calendar, photos, microphone, or camera content.
- Biometric data.
- Advertising identifiers (IDFA on iOS, AAID on Android). The Service
  does not serve advertisements and does not integrate with advertising
  networks; we explicitly disable advertising-personalization signals
  in our analytics processors and do not request App Tracking
  Transparency permission on iOS.
- Payment-card data.

## 4. Legal bases for processing (GDPR Art. 6)

We process your personal data under the following legal bases:

| Purpose                                                                    | Legal basis                              |
| -------------------------------------------------------------------------- | ---------------------------------------- |
| Creating and operating your account, enabling gameplay, processing IAPs   | Performance of a contract (Art. 6(1)(b)) |
| Enforcing minimum-age rule                                                | Legal obligation and legitimate interest (Art. 6(1)(c), 6(1)(f)) |
| Fraud prevention, anti-abuse, server-log retention, security investigations | Legitimate interest (Art. 6(1)(f))       |
| Sending transactional push notifications                                  | Performance of a contract (Art. 6(1)(b)) with consent for device-level notification permission (given via OS prompt) |
| Crash and performance telemetry                                           | Legitimate interest (Art. 6(1)(f)) |
| Product analytics (feature use, session patterns, aggregate geographic distribution of active users) | Legitimate interest (Art. 6(1)(f)); subject to your right to object under Art. 21 GDPR and any consent requirement imposed by applicable ePrivacy or similar rules |
| Responding to legal claims and requests from authorities                  | Legal obligation (Art. 6(1)(c))          |

We do **not** rely on consent as the legal basis for core service
operation; consent is relied upon only where it is the correct basis
under law (for example, device push permission and, where required by
applicable law, certain analytics or device-storage technologies).

## 5. How we use your data

We use the data described above to:

- Authenticate you and maintain your session.
- Provide gameplay, progression, rewards, and subscription benefits.
- Credit in-app purchases to your account.
- Deliver transactional push notifications (e.g., "your mission is
  complete").
- Detect and prevent fraud, cheating, abuse, and security incidents.
- Diagnose bugs and improve stability.
- Comply with legal obligations and respond to lawful requests.

We do not use your personal data for third-party advertising. We do
not sell your personal data.

## 6. Minimum age

The Service is not offered to users under **16 years of age**, in any
region. We enforce this through an onboarding age gate and block
further use of the Service below this threshold. We do not operate a
parental-consent flow.

If we learn that we have inadvertently collected personal data from a
user under 16, we will delete it promptly. You can also contact us to
request deletion.

## 7. Who we share data with

We share data only with the following categories of recipients, and
only to the extent necessary for the purposes above:

- **Apple Inc.** — authentication (Sign in with Apple), payment
  processing (App Store IAP), and app distribution (App Store /
  TestFlight).
- **Google LLC** — authentication (Sign in with Google); app
  distribution and payment processing through Google Play where the
  Android version is offered there; **Firebase Cloud Messaging** for
  transactional push notifications; and **Firebase Analytics** for
  usage analytics and active-user reporting at country, region, and
  city granularity, configured with advertising-personalization
  signals disabled.
- **Mixpanel, Inc.** — product analytics (events, funnels, retention).
  Processing is performed on Mixpanel's EU infrastructure
  (`api-eu.mixpanel.com`). We identify users to Mixpanel by the
  pseudonymous internal account identifier only; no email, real name,
  payment data, or precise location is sent to Mixpanel.
- **Functional Software, Inc.** (operating as **Sentry**) — crash and
  performance telemetry. Sentry is configured with personally
  identifying context scrubbed at the source (default PII disabled and
  a purpose-built redaction filter applied).
- **Cloud infrastructure providers** that host the Service (such as
  server hosting, managed database, object storage, and content
  delivery providers). They process data on our instructions as data
  processors under written contracts and may change from time to time
  as we operate the Service.
- **Professional advisors** (legal, accounting, compliance) where
  necessary.
- **Authorities, courts, or other parties** where we are legally
  required to share data or where we have a legitimate interest in
  protecting the Service, its users, or others from fraud or harm.

We do **not** sell personal data, and we do **not** share data with
advertising networks.

## 8. International transfers

Some of our processors may be located in, or may access personal data
from, countries outside the European Economic Area, the United Kingdom,
or Switzerland. Where we transfer personal data internationally, we do
so under an appropriate safeguard recognised by applicable
data-protection law, typically the European Commission's **Standard
Contractual Clauses (SCCs)**, the UK International Data Transfer
Addendum or equivalent UK safeguard, the Swiss recognised transfer
mechanism, or — where available — an applicable adequacy decision.

You may contact us using the details in Section 12 if you would like
more information about the safeguards used for a particular category of
transfer.

## 9. Retention

We keep personal data only as long as necessary for the purposes for
which it was collected, after which we delete or anonymise it.

Our standard retention periods are:

- **Account data and gameplay state:** for the life of the account, and
  up to **12 months** after deletion or prolonged inactivity, for fraud
  prevention and dispute handling.
- **Server logs with IP and request metadata:** typically **30–90 days**
  for operational purposes, longer only where a specific investigation
  requires it.
- **Purchase and receipt records:** for the period required by tax and
  accounting law in our jurisdiction (typically several years), in a
  minimal form.
- **Crash / performance telemetry:** **up to 90 days** in identifiable
  form, after which aggregated statistics only.

**Account deletion process.** When you request deletion (in-app via
**Settings** → **Danger Zone** → **Delete Account**, via the public
form at `https://ascion.space/account-deletion`, or by email to the
address in Section 12), your account enters a **30-day grace period**
during which you can cancel the request by signing in again and
selecting **Cancel deletion**. At the end of that period, we
permanently delete your profile, gameplay data, sign-in identifiers
(Apple ID or Google ID), device-binding tokens, and retire the private
key of your in-game managed wallet. Where you signed in with Apple, we
also revoke your Apple refresh token so that Ascion no longer appears
in your Apple ID's "Apps Using Apple ID" list.

**On-chain assets.** Before the managed wallet key is retired, any
tokens and NFTs it holds are transferred on-chain to the Ascion
treasury address on Polygon. Because a public blockchain is an
immutable ledger, the on-chain transaction history itself cannot be
erased — only the association between the wallet address and your
personal identity is removed from our systems.

**What is retained, in minimal and de-identified form.** In-app
purchase records (for Czech accounting and VAT law, up to 10 years);
enforcement records where you were sanctioned for a Terms violation,
to prevent circumvention; and audit entries pertaining to the
deletion event itself. These records are stripped of direct
identifiers where possible.

## 10. Your rights

Subject to applicable law, you have the right to:

- **Access** the personal data we hold about you.
- **Rectify** inaccurate or incomplete personal data.
- **Erasure** ("right to be forgotten") of personal data we hold about
  you, subject to our legitimate retention grounds above.
- **Restrict** or **object** to certain processing based on legitimate
  interests.
- **Data portability** — receive a copy of data you provided, in a
  structured, commonly used, machine-readable format, where processing
  is based on contract or consent.
- **Withdraw consent** at any time where processing is based on consent
  (this does not affect the lawfulness of processing before the
  withdrawal).
- **Lodge a complaint** with your national data-protection authority.
  In the Czech Republic, this is the **Úřad pro ochranu osobních údajů
  (ÚOOÚ)**, `https://www.uoou.cz`.

To exercise any of these rights, contact us at the address in Section
12. We will respond within the timeframes required by applicable law
(generally within one month under GDPR). We may ask you to verify
your identity before fulfilling a request.

## 11. Security

We apply industry-standard technical and organisational measures to
protect personal data, including encryption in transit, access controls
on backend systems, secret management, and security monitoring. No
system is ever perfectly secure. We recommend you protect the Apple ID
or Google account used to sign in and the device you sign in from.

If we become aware of a personal-data breach that is likely to result
in a risk to your rights and freedoms, we will notify the competent
supervisory authority and, where required, affected users, in the
timeframes required by law.

## 12. Contact

**Account deletion.** The fastest path is in-app:
**Settings** → **Danger Zone** → **Delete Account**. You can also use
the public form at `https://ascion.space/account-deletion`. See
Section 9 for the full deletion process, including the 30-day grace
period and how on-chain assets are handled.

For other rights, questions about this Policy, or any other
data-protection matter, email **privacy@ascion.space**.
Postal mail may be sent to 1101 Capital s.r.o., Lidická 700/19,
Veveří, 602 00 Brno, Czech Republic. Czech administrative
communications may also be sent to our Data Box (ID `zi6aisw`). No
formal DPO is appointed at this stage; the contacts above are the
single privacy contact.

## 13. Changes to this Policy

We may update this Policy from time to time. The current version is
always identified by the **version string** at the top of this
document. Material changes will be announced in-app. Each accepted
version is recorded server-side against your account.

## 14. Version

- **Version:** `2026-04-23-release-1`
- **Effective:** `2026-04-23`
- **Status:** Active.
- **Acceptance tracking:** The server records the accepted version
  string on your account. When this version string changes, you will
  be asked to review and accept the updated Policy on next launch.
