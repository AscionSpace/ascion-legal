---
version: 2026-04-20-draft-3
status: DRAFT — not reviewed by counsel
effective: (pending)
---

# Privacy Policy

> **DRAFT NOTICE.** This document is a developer-written draft and has
> not been reviewed by a qualified lawyer. It is placed in the repository
> to support engineering scaffolding and consent tracking. It must be
> reviewed and revised by counsel before any public release. Do not rely
> on this document as a compliance artefact.

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
rights described in §7 — email **team@ascion.space**. We have not
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
- **Age confirmation.** On first launch you confirm via a single
  checkbox that you meet the minimum-age rule (see Section 6). We
  record only the timestamp of that confirmation — we do **not**
  collect or store your date of birth.

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
- **Crash and performance telemetry** where you have not opted out.
  Personally identifying context is scrubbed at the source where
  possible.
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
"wallet" functionality is offered through the Service.** You have no
obligation, right, or ability to manage this identifier yourself.

### 2.4. Payment data

In-app purchases are processed by **Apple**. We do not see, store, or
process your payment-card, billing-address, or equivalent payment data.
Apple provides us with a purchase receipt that we validate to credit
your account.

## 3. What we do **not** collect

We do not collect:

- Precise geolocation.
- Contacts, calendar, photos, microphone, or camera content.
- Biometric data.
- Advertising identifiers for ad tracking (the Service does not serve
  third-party advertising).
- Payment-card data.

## 4. Legal bases for processing (GDPR Art. 6)

We process your personal data under the following legal bases:

| Purpose                                                                    | Legal basis                              |
| -------------------------------------------------------------------------- | ---------------------------------------- |
| Creating and operating your account, enabling gameplay, processing IAPs   | Performance of a contract (Art. 6(1)(b)) |
| Enforcing minimum-age rule                                                | Legal obligation and legitimate interest (Art. 6(1)(c), 6(1)(f)) |
| Fraud prevention, anti-abuse, server-log retention, security investigations | Legitimate interest (Art. 6(1)(f))       |
| Sending transactional push notifications                                  | Performance of a contract (Art. 6(1)(b)) with consent for device-level notification permission (given via OS prompt) |
| Crash and performance telemetry                                           | Legitimate interest (Art. 6(1)(f)); you may opt out |
| Responding to legal claims and requests from authorities                  | Legal obligation (Art. 6(1)(c))          |

We do **not** rely on consent as the legal basis for core service
operation; consent is relied upon only where it is the correct basis
under law (e.g., device push permission, where required).

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
region. We enforce this via a date-of-birth check during onboarding
and block further use of the Service below this threshold. We do not
operate a parental-consent flow.

If we learn that we have inadvertently collected personal data from a
user under 16, we will delete it promptly. You can also contact us to
request deletion.

## 7. Who we share data with

We share data only with the following categories of recipients, and
only to the extent necessary for the purposes above:

- **Apple Inc.** — authentication (Sign in with Apple), payment
  processing (App Store IAP), app distribution (App Store / TestFlight).
- **Cloud infrastructure providers** that host the Service (server
  hosting, managed database, object storage). They process data on our
  instructions as data processors under written contracts.
- **Push-notification service provider** used to deliver transactional
  notifications.
- **Crash and performance telemetry provider** (if any), with PII
  scrubbing configured.
- **Professional advisors** (legal, accounting, compliance) where
  necessary.
- **Authorities, courts, or other parties** where we are legally
  required to share data or where we have a legitimate interest in
  protecting the Service, its users, or others from fraud or harm.

A current list of sub-processors will be published and kept up to date
in the Service before public release.

We do **not** sell personal data, and we do **not** share data with
advertising networks.

## 8. International transfers

Some of our processors may be located outside the European Economic
Area. Where we transfer personal data outside the EEA, we do so under
an appropriate safeguard recognised by GDPR, typically the European
Commission's **Standard Contractual Clauses (SCCs)**, and where
applicable supplementary measures, or — where the Commission has issued
an adequacy decision — on the basis of that decision.

The specific list of processors and transfer mechanisms will be
published before public release.

## 9. Retention

We keep personal data only as long as necessary for the purposes for
which it was collected, after which we delete or anonymise it.

Indicative retention periods (to be finalised by counsel):

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

On account deletion, we delete personal data except where retention is
required by law or necessary to resolve disputes, enforce agreements,
or prevent fraud.

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

To exercise your rights, ask questions about this Policy, or contact
us about any data-protection matter, email **team@ascion.space**.
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

- **Version:** `2026-04-20-draft-3`
- **Status:** DRAFT — not reviewed by counsel.
- **Acceptance tracking:** The server records the accepted version
  string on your account. When this version string changes, you will
  be asked to review and accept the updated Policy on next launch.
