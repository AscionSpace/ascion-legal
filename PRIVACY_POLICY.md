---
version: 2026-08-15-draft-1
status: DRAFT — pending product, processor, and counsel review
effective: (pending)
---

# Privacy Policy

> **Review draft.** This version reflects Ascion's current account, gameplay,
> social, chat-translation, organization, direct-trading, analytics, Discord,
> and in-app-purchase features. It is not effective until it has completed
> product and legal review and is published through Ascion's release-tracked
> legal process.

This Privacy Policy explains how **1101 Capital s.r.o.** collects, uses,
shares, retains, and protects personal data when you use the **Ascion** mobile
application and related online services (the "**Service**"). It is written
with the EU General Data Protection Regulation ("**GDPR**") in mind and also
applies to users in the United Kingdom, Switzerland, and other regions,
subject to applicable local law.

## 1. Controller and contact

The controller is **1101 Capital s.r.o.**, a Czech limited liability company
with registered office at Lidická 700/19, Veveří, 602 00 Brno, Czech Republic
(IČO: 07180969; Data Box ID: `zi6aisw`).

For privacy questions or requests, email **privacy@ascion.space**. We have not
formally appointed a Data Protection Officer. If that changes, we will update
this Policy.

## 2. Personal data we collect

### 2.1 Account, authentication, and preferences

Depending on the sign-in and optional features you use, we process:

- a stable Apple- or Google-issued account identifier;
- your email address, relay email address, name, and profile image where the
  sign-in provider makes those fields available;
- your Ascion username, internal account identifier, profile/avatar image,
  preferred language, timezone, onboarding state, and settings;
- your confirmation that you are at least 16 and the confirmation timestamp;
- the versions and timestamps of Terms and Privacy Policy acceptances;
- authentication and session records, including a Sign in with Apple refresh
  token where available so we can revoke the Apple connection on deletion; and
- if you choose to link Discord: your Discord user ID, username, global display
  name, avatar URL, connection timestamp, and whether an Ascion subscription
  role is recorded as assigned. Discord access tokens used during OAuth are not
  retained as account profile data after the connection flow.

We do not collect your date of birth.

### 2.2 Social, chat, organization, and player-created content

When you use social features, we process content and relationship data such as:

- world, organization, and direct chat messages, message type, sender, thread,
  timestamps, edit/deletion state, read state, and thread membership;
- on-demand chat translations, target language, translated text, a hash of the
  source text, translation provider/model, and timestamps;
- player search results, friend requests, friendships, relationship status,
  interaction counts, and any private nickname or note you save for a friend;
- online presence, short-lived connection state, and last-seen time;
- organization names, tags, descriptions, images, visual identity, membership,
  roles, invitations, membership requests, and accompanying messages;
- direct item-trade offers, participants, item and quantity, price, reservation,
  response, settlement, expiry, and failure state; and
- usernames, avatars, achievements, contributions, marketplace activity, and
  other profile or gameplay information intentionally displayed to other
  players through Service features.

Do not include information in player-created content that you do not want other
authorized users of the relevant social space to see.

### 2.3 Safety reports, moderation, and appeals

Where reporting, moderation, or appeal features are available, we process the
reporter and reported account, the reported message/profile/organization/
invitation/trade, category, explanation, relevant thread or organization,
timestamps, status, and a limited evidence snapshot or hash. We also process
moderation decisions, policy basis, restrictions, reviewer notes, notices,
appeals, and decision history.

We use these records to investigate abuse, protect users, enforce our Terms,
prevent repeat or retaliatory reporting, support appeals, and comply with legal
notice-and-action duties. Automated filters or risk signals may help prioritize
review, but we do not make decisions producing legal or similarly significant
effects solely by automated means.

### 2.4 Gameplay, transactions, and purchases

We process the gameplay state needed to provide the Service, including your
agents, ships, inventory, storage, missions, organizations, virtual-credit
balance, progression, activity history, and transactions with other players or
game systems.

Apple or Google processes your payment instrument and billing details. We do
not receive your full payment-card number or billing address. We receive and
retain the purchase information needed to verify and administer entitlements,
including the store, product ID, transaction or order identifier, purchase-token
or receipt hash, verification environment and time, subscription expiry and
renewal state, and refund, revocation, or manual-review outcome. Raw Google
purchase tokens and raw Apple receipt payloads are not stored in the purchase
ledger after verification.

### 2.5 Device, notifications, logs, analytics, and diagnostics

We process:

- app-generated device identifiers, operating system, platform, app version,
  build number, and device-model information;
- push tokens and delivery/receipt status if you enable notifications;
- IP address, user agent, request metadata, timestamps, authentication events,
  rate-limit and security signals, and operational logs;
- app interactions, screens, sessions, gameplay actions, purchase funnel events,
  product IDs, failure categories, and related product analytics;
- your internal account ID and Ascion username in Mixpanel user profiles;
- approximate country, region, or city inferred from IP address by analytics or
  infrastructure providers; and
- crash reports, stack traces, performance traces, and diagnostic context.

We configure Sentry with default personally identifying information disabled
and apply redaction filters, but diagnostic data can still contain account,
device, route, or event context needed to investigate a fault.

### 2.6 Chat translation and AI processing

Translation is initiated for an individual chat message when an authorized user
selects the translation action. The source message and requested target language
are sent to **OpenAI** solely to generate the translation. The request is made
with provider-side response storage disabled. OpenAI states that API data is not
used to train its models by default, although limited temporary retention for
abuse monitoring or legal compliance may still apply under OpenAI's service
terms unless a qualifying zero-data-retention arrangement is active.

We store the resulting translation in Ascion so authorized readers requesting
the same message and language can reuse it without another provider request.
The cached translation is linked to the source message and is deleted when the
source message is deleted during account erasure.

When you first request a translation, the Service explains that the selected
message text and requested language will be sent to OpenAI and asks for your
permission before sending them. You can withdraw that permission in Settings.
The server rejects new translation requests unless the current disclosure has
been accepted.

### 2.7 Data we do not intentionally collect

We do not intentionally collect precise GPS location, contacts, calendars,
photos, microphone or camera content, biometric data, advertising identifiers,
or payment-card details. The Service does not currently serve third-party ads,
sell personal data, or request App Tracking Transparency permission for
cross-company tracking.

## 3. Where personal data comes from

We receive personal data:

- directly from you when you create content, choose settings, make requests,
  link Discord, or contact us;
- from Apple, Google, Discord, and the applicable app store when you use their
  authentication, distribution, billing, or notification services;
- automatically from your app, device, and network when you use the Service;
- from other players when they invite, message, trade with, report, or otherwise
  interact with you; and
- from our service providers when they return delivery, verification, analytics,
  security, translation, or diagnostic results.

## 4. Why we process personal data and our legal bases

| Purpose | Main GDPR legal basis |
| --- | --- |
| Create and operate accounts; authenticate users; provide gameplay, social features, organizations, chat, direct trades, purchases, entitlements, and requested translations | Performance of a contract, Art. 6(1)(b) |
| Display usernames, avatars, presence, messages, organizations, achievements, contributions, and transaction context to the users who are entitled to see them | Performance of a contract, Art. 6(1)(b), and legitimate interests, Art. 6(1)(f) |
| Prevent fraud, cheating, abuse, account compromise, and service disruption; enforce rules; investigate reports; moderate content; handle appeals | Legitimate interests, Art. 6(1)(f), and legal obligation where applicable, Art. 6(1)(c) |
| Verify age-gate completion and protect minors | Legal obligation, Art. 6(1)(c), and legitimate interests, Art. 6(1)(f) |
| Send transactional push notifications | Performance of a contract, Art. 6(1)(b), with device permission requested through the operating system |
| Measure feature use and improve the Service through product analytics | Legitimate interests, Art. 6(1)(f), subject to your right to object and any consent required by ePrivacy or local law |
| Diagnose crashes, monitor performance, maintain logs, and secure infrastructure | Legitimate interests, Art. 6(1)(f) |
| Keep purchase, accounting, tax, deletion, and legally required records; respond to authorities and legal claims | Legal obligation, Art. 6(1)(c), and legitimate interests, Art. 6(1)(f) |

Where we rely on legitimate interests, those interests are operating, securing,
improving, and enforcing a fair multiplayer service, protecting users and our
legal rights, and maintaining reliable transaction records. You may object as
described in Section 11.

## 5. Who can see or receive personal data

### 5.1 Other users

Your username, avatar, online/last-seen status, public profile and achievement
information, organization identity and membership, public marketplace or
contribution activity, and content posted in shared social spaces may be visible
to other users. Direct messages, direct trades, private organizations, and
friend-only information are limited to the participants or authorized members,
subject to moderation and operational access.

### 5.2 Service providers and platforms

We disclose personal data only as needed to operate the relevant function:

- **Apple** — Sign in with Apple, App Store/TestFlight distribution, in-app
  purchases, refunds, and server notifications;
- **Google** — Sign in with Google, Google Play distribution and billing,
  Firebase Cloud Messaging, and Google Play purchase/lifecycle verification;
- **Expo / 650 Industries** — app build/update services and Expo push delivery;
- **OpenAI** — on-demand translation of the selected chat message;
- **Discord** — optional account linking, guild membership checks, and Commander
  or Prime-related role assignment/removal;
- **Mixpanel** — EU-hosted product analytics using the internal account ID,
  username, platform/app context, and recorded product events;
- **Sentry / Functional Software** — crash, error, and performance monitoring;
- **Railway** — application hosting and Redis-backed operational services;
- **Neon** — managed PostgreSQL database hosting;
- **Amazon Web Services** — object/media storage and related delivery services;
- **Cloudflare** — domain, content-delivery, and administrative-access security;
- **Resend** — closed-testing invitation email delivery where that program is
  used; and
- other hosting, security, delivery, and professional service providers acting
  under contract and only as needed for the Service.

We require processors and other recipients handling personal data on our behalf
to protect it consistently with this Policy and applicable law.

We may also disclose information to professional advisers, courts, regulators,
law-enforcement bodies, or other parties where required by law or reasonably
necessary to establish, exercise, or defend legal claims; protect users or the
Service; investigate fraud or harm; or complete a corporate transaction subject
to appropriate safeguards.

We do not sell personal data and do not share it with advertising networks.

## 6. International transfers

Some recipients may process personal data outside the EEA, United Kingdom, or
Switzerland. Where required, we rely on an applicable adequacy decision,
European Commission Standard Contractual Clauses, the UK International Data
Transfer Addendum or other lawful transfer mechanism, together with
supplementary safeguards where appropriate. Contact us for information about
the safeguard used for a particular transfer.

## 7. Retention

We retain personal data only for as long as reasonably necessary for the stated
purpose, then delete or anonymize it. Our intended standard periods are:

- **Account, profile, settings, gameplay, social graph, organization membership,
  chat messages and translations, and direct-trade data:** while the account is
  active, then handled through the deletion process in Section 10. Shared world
  objects may remain after attribution to your account is removed.
- **Live socket presence:** normally expires within approximately three minutes
  after the connection stops refreshing. The account's last-seen timestamp is
  retained with the account until deletion.
- **Safety reports, moderation actions, evidence, and appeals:** while a case is
  active and generally for up to 24 months after closure; longer where needed
  for repeat-abuse prevention, legal claims, or a legal preservation duty.
- **Operational logs containing IP address or request metadata:** generally 30
  to 90 days; longer only for a documented security incident, fraud review, or
  legal claim.
- **Product analytics:** according to the configured Mixpanel project retention
  and for no longer than reasonably needed for product analysis. Before release,
  the configured period must be recorded in the processor inventory and store
  disclosures.
- **Crash and performance telemetry:** generally up to 90 days in identifiable
  form, subject to the configured Sentry retention period; aggregate statistics
  may be kept longer.
- **Push tokens:** until replaced, invalidated, permission is withdrawn, or the
  account is deleted. Delivery receipts are retained only for operational retry
  and troubleshooting needs.
- **Purchase, subscription, refund, reversal, sales, and accounting records:**
  up to 10 years where required by Czech accounting or VAT law, or longer if a
  legal hold applies. We minimize or detach account attribution where possible.
- **Deletion and enforcement audit records:** for the period necessary to prove
  deletion, prevent circumvention, protect users, resolve disputes, and meet
  legal obligations. These may retain the former internal account ID and limited
  identity or transaction context where necessary for the audit purpose.

These periods are maximum defaults, not promises to retain data for the full
period. A shorter period may apply where the data is no longer needed.

## 8. Your choices and controls

You can:

- change supported profile, language, notification, and social settings in the
  Service;
- decline or disable push notifications through device settings;
- choose whether to link Discord and disconnect it through Settings;
- choose whether to request translation of an individual message;
- leave organizations or end social relationships through available controls;
- object to analytics or other legitimate-interest processing by contacting us;
  and
- request access, correction, export, restriction, or deletion as described
  below.

Some processing is necessary to provide the Service. If you object to or ask us
to delete data required for account operation, we may need to close the account.

## 9. Minimum age

The Service is not offered to anyone under **16**. We record only confirmation
that the age requirement was met, not date of birth. If we learn that we have
collected personal data from a child under 16, we will take steps to delete it.

## 10. Account deletion

You can request deletion in-app through **Settings → Danger Zone → Delete
Account**, through `https://ascion.space/account-deletion`, or by contacting
**privacy@ascion.space**. The request starts a **30-day grace period** during
which you may cancel deletion by signing in and selecting **Cancel deletion**.

Deletion may pause if necessary to safely resolve pending purchases, trades,
market orders, rentals, jobs, shared assets, or organization leadership. For
example, a sole organization leader must transfer leadership before deletion
can complete. We use the pause only to prevent corruption of another user's or
shared game state and will expose or communicate the required action where
practicable.

After the grace period and required cleanup:

- we delete the account profile, sign-in identifiers, Apple refresh token,
  Discord link, push tokens, player-specific gameplay records, chat messages and
  their translations, chat memberships, friendships, organization membership,
  invitations, membership requests, and notifications;
- we revoke the Apple sign-in connection where the necessary token is available;
- shared world assets may remain but are detached from your identity or
  reassigned to a system account so other users' state remains consistent; and
- purchase, subscription, sales, enforcement, activity, and deletion-audit
  records may be reassigned to a deleted-user system record and retained for the
  periods and purposes in Section 7.

Technical backups may retain deleted data for a limited disaster-recovery cycle,
during which the data is isolated from ordinary use and removed through normal
backup rotation. Information already received by another user, such as a push
notification preview or a lawful copy they made outside the Service, is not
controlled by our deletion process.

## 11. Your data-protection rights

Subject to applicable law, you may have the right to:

- be informed about processing and obtain **access** to your personal data;
- receive a **copy** of data we hold about you;
- **correct** inaccurate or incomplete data;
- request **erasure**;
- **restrict** processing in specified circumstances;
- **object** to processing based on legitimate interests;
- receive eligible data in a structured, commonly used, machine-readable format
  and exercise **data portability**;
- withdraw consent where processing is based on consent, without affecting prior
  lawful processing; and
- lodge a complaint with a supervisory authority.

The Czech supervisory authority is the **Úřad pro ochranu osobních údajů
(ÚOOÚ)** at `https://uoou.gov.cz`. You may also complain to the authority where
you live or work. We generally respond to verified GDPR requests within one
month, subject to lawful extensions. Rights may be limited where necessary to
protect other users' rights, comply with law, or establish, exercise, or defend
legal claims.

## 12. Security

We use measures including encryption in transit, access controls, secret
management, account and transaction authorization, server-side purchase
verification, monitoring, rate limits, and redaction of sensitive telemetry.
No system can be guaranteed completely secure. Protect the Apple, Google, or
Discord account and device you use with Ascion.

If a personal-data breach is likely to create a risk to individuals, we will
notify the competent authority and affected users where required by law.

## 13. Changes to this Policy

We may update this Policy when the Service, recipients, or law changes. The
version and status appear at the top and bottom of the document. Material
changes will be announced in-app and, where required, we will request renewed
acceptance or consent. The server records the version you accepted.

## 14. Contact

Email **privacy@ascion.space** for privacy rights, account deletion, or questions
about this Policy. Postal mail may be sent to 1101 Capital s.r.o., Lidická
700/19, Veveří, 602 00 Brno, Czech Republic. Czech administrative
communications may be sent to Data Box ID `zi6aisw`.

For social-safety reports or appeals, use the in-app reporting/appeal features
when available or email **safety@ascion.space**.

## 15. Version

- **Version:** `2026-08-15-draft-1`
- **Effective:** Pending review and publication.
- **Status:** Draft; the previously published Privacy Policy remains active.
- **Acceptance tracking:** Publication requires a new release tag and updated
  consumer pins. Users whose recorded accepted version differs from the bundled
  published version will be asked to review and accept it on next launch.
