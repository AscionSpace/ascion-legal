---
version: 2026-04-20-draft-1
status: Planning — paired with MVP_PLAN.md (2026-04-20)
scope: How, not what. When disclosure happens — never the tokenomics content.
---

# Ascion — Web3 Staged Disclosure Plan

## 1. Premise + non-negotiables

**Premise.** Ascion is two products sharing one codebase: a mobile idle/sim
space game, and a longer-term on-chain ownership story for digital goods.
Shipped together at full volume, the Web3 half repels the game audience we
need to survive the first year, and Apple rejects us. Shipped apart, the
Web3 half is dishonest to the infrastructure that actually runs under the
game. A staged plan exists because the honest answer is "both true, in
order." The mobile app never becomes the disclosure channel; disclosure
happens on surfaces we control (website, Discord, devlogs, press) on our
timeline, to audiences we can identify, at a depth we can justify.

**Non-negotiables.** The mobile client stays 100% Web3-invisible at every
phase of this plan — no vocabulary, no links, no deep-links, no footer
crumbs, no About-screen lore, no support articles that cross-reference
on-chain content. The app's `<meta>` and App Store listing stay
game-only. External wallets (MetaMask, WalletConnect, Rainbow, any
deep-link intent), bridges, and on-chain user-facing withdrawal UX are
out of scope for phases 0–2 and explicitly flagged as "revisit at phase
3 or later." No public copy, at any phase, makes tokenomics promises or
uses securities-adjacent framing ("yield", "returns", "airdrop",
"guaranteed", "investment"). The Vault stays a corp prize pool in every
player-facing surface until phase 3, regardless of what the website
says elsewhere. Dev-phase on-chain status is disclosed honestly wherever
the topic comes up — we never imply user custody exists when it does not.

---

## 2. Phases

### Phase 0 — Quiet (now → MVP live)

- **Trigger condition to exit:** MVP public on TestFlight with ≥50 real
  (non-friends) installs and at least one week of D1/D7 data that doesn't
  immediately fail (D1 ≥ ~25%, D7 ≥ ~8%). If retention is broken, no
  amount of disclosure matters — stay in phase 0 and fix the game.
- **Publicly visible:** game-only landing page (single URL, email capture,
  TestFlight invite button), Discord with the four MVP channels, dev X as
  a low-effort mirror. The legal docs are linked in the footer but the
  "pseudonymous internal account identifier" clause does not lead anywhere
  curious eyes can pull on. **Mobile app: nothing.**
- **Language:** entirely diegetic. Corp, agents, credits, missions,
  Chronicle, Vault-as-prize-pool. Infra terms (wallet, chain, token,
  mint, on-chain) appear **zero times** on any player-facing surface
  including the website. Internal code keeps its existing names; player-
  visible strings don't.
- **Audience:** thoughtful mobile gamers who love idle/sim. The website
  speaks only to them. Crypto-natives who stumble in see a normal mobile
  game and either bounce or sign up as players — both fine.
- **Measure:** TestFlight retention, Discord signal-to-noise, first
  purchase data per §3 of the MVP plan. Disclosure is not measured yet
  because nothing is disclosed.

### Phase 1 — A deeper page exists (post-MVP, pre-Prime-cycle validation)

- **Trigger condition to exit:** retention confirmed (phase 0 bar held
  for 3+ weeks), **and** first monetization signal landed — at least 20
  paying accounts across credits IAP and/or Prime, at least one Prime
  cohort nearing the 30-day renewal mark. You have enough product to be
  worth talking about honestly.
- **Publicly visible:** a new page at an **unlinked** URL
  (`ascion.game/build` or `/architecture` — not `/web3`, not `/token`).
  Not in the main nav. Not in the footer of the game landing page. Only
  findable via (a) direct link from a devlog, (b) Discord pin, (c) a
  future press contact. It explains, in plain English: "Ascion records
  item ownership on a public ledger as infrastructure. The game does not
  require or expose this to play. Here's why we chose this; here's what
  it does and does not mean for you today." Dev-phase status stated
  plainly. No token name, no price, no promises.
- **Discord:** a new read-only `#architecture-notes` channel (not
  `#web3`, not `#tokenomics`) mirrors the page content. Main community
  channels unchanged.
- **Devlog:** one honest post on the blog + Reddit `/r/incremental_games`
  explaining the **layered disclosure approach itself** — "we're a game
  first and we're going to stay that way; there's infrastructure under
  the hood and here's where we talk about it if you care." Posting this
  post *is* part of the disclosure; it pre-empts any "gotcha" framing.
- **Mobile app:** **still nothing.** The app does not link to the deeper
  page. Support articles do not reference it. This is the single biggest
  App Review risk knob; keep it at zero.
- **Language:** on the deeper page, infra terms are allowed but framed as
  infrastructure, not product. "Public ledger," "smart-contract-recorded
  ownership," "dev-phase." Still no "on-chain ownership" as a marketed
  feature; it's a fact of how we built it. "Token" appears only if
  unavoidable, and never with price/supply/utility claims.
- **Audience:** existing engaged players who are curious, crypto-native
  visitors who find the page via a devlog, a small press tier. Not new
  signups — the game landing page is still the front door.
- **Measure:** page views vs. game-landing views (expect <5%), Discord
  sentiment in response to the devlog (does the game audience feel
  betrayed or informed?), TestFlight retention unchanged before/after
  the post. If game-audience sentiment sours on phase 1, you do not
  advance; you refine.

### Phase 2 — Ownership story, soft-landed (Prime cohort validated)

- **Trigger condition to exit:** at least one full 90-day Prime cohort
  with >30% month-2 retention; sustained DAU baseline the dev can name
  without flinching (concrete number to set at phase entry, not now);
  Discord community that polices its own tone (not you doing every
  reply); legal review (§6) complete on all phase-2 copy.
- **Publicly visible:** deeper page moves from "unlinked" to **one
  footer link** on the main game site, labelled neutrally (e.g., "How
  it's built" or "Ownership"). The page itself expands: explains that
  items players earn in-game are *recorded* as theirs on a public
  ledger, that this is currently for continuity and future portability,
  and what "future portability" honestly does and does not imply
  (framed as a direction, not a promise). Still dev-phase unless the
  custody story has actually changed — if custody is still
  server-managed, say so.
- **Website meta:** main site `<meta description>` remains game-only.
  The deeper page gets its own `<meta>` and `<title>` that reference
  ownership/infrastructure; it can index in search without the game
  landing page doing so.
- **Discord:** `#architecture-notes` stays read-only, a new `#ownership`
  channel opens for discussion. Moderation ground rule: tokenomics
  speculation by community members is allowed; speculation amplified or
  confirmed by staff is not. Staff answers with the same spine every
  time (§3).
- **Mobile app:** **still nothing.** No deep-link, no footer, no
  "learn more about how Ascion works" in settings, no support article
  that cross-links. This remains a phase-3+ conversation, not phase 2.
- **Language:** "on-chain ownership" becomes explicit on the deeper
  page. Still not in the app, not in App Store metadata, not in
  push-notification copy, not in support articles that load in the app.
  ToS/Privacy get a version bump if the language strengthens past
  "pseudonymous internal account identifier" — see §6.
- **Audience:** all of phase 1, plus press that writes about both games
  and Web3 infra, plus new signups who clicked the footer before
  installing. Signup flow itself unchanged.
- **Measure:** what % of new installs came via the deeper page vs. the
  game landing page; whether the game-audience retention curve flinches
  after the footer link lands; whether Discord split-brains into two
  cultures that hate each other (if so, you went too fast).

### Phase 3 — Full ownership story landed (gated; out of scope to commit to here)

- **Trigger condition to exit:** phase 2 held for at least a full
  quarter without retention damage or App Review incident, **and** a
  specific external event makes it real — e.g., the custody model
  actually changes (server-managed → optional self-custody via a
  non-mobile surface), or a regulatory clarification makes on-chain
  player-facing UX defensible in our jurisdiction, or a cohort of
  players actively asks for it in a way that isn't a vocal minority.
  Absent one of those, stay at phase 2 indefinitely. Phase 3 is not
  inevitable.
- **Publicly visible:** full ownership page, wallet-adjacent UX on a
  **web surface** (not mobile), documentation, possibly a separate
  Web3-audience site that cross-links to the game site. Press outreach
  to both communities.
- **Mobile app:** **revisit decision.** The bright line of §1 holds
  until this phase's entry; at phase 3 entry, a specific decision is
  made about whether the app can link *out* to a web-ownership surface
  (never *host* wallet UX). Apple policy review required. Default
  assumption: the app still doesn't change. External-wallet connect,
  bridges, withdrawal UX — all of these are phase-3 topics that this
  plan flags but does not pre-decide.
- **Language:** aligned with whatever the custody reality is. Still no
  securities-adjacent framing, regardless of audience excitement.
- **Audience:** both, explicitly.
- **Measure:** whether the two audiences coexist or one drives the
  other out. This plan does not pre-commit to a phase-3 success bar;
  setting one now would be theatre.

---

## 3. Messaging spine

Four sentences. These survive every phase, rehearsed verbatim by the
dev and by moderators. Every "wait, you're crypto?" question gets a
variation of these and nothing more.

1. **Ascion is a space-sim idle game; that's the product, and that's
   what you play.**
2. **Under the hood, we record item ownership on a public ledger
   because we think long-lived digital worlds should outlive the
   company that runs them — not because the game is about crypto.**
3. **We don't put any of that infrastructure in front of players; the
   app is a game, and will stay a game. If you want the details, they
   live on our build page, not in the app.**
4. **We don't make financial promises about any of it, and we won't.
   If someone tells you Ascion is an investment, they're wrong, and
   our terms say so.**

The spine is the answer in phase 0, phase 3, and every phase in
between. Consistency is the thing that converts "wait, crypto?" into
"okay, I get it."

---

## 4. Risks + countermeasures

**(a) Trust-breaking pivot — game audience feels rug-pulled when the
deeper page appears.** Mitigation: the phase-1 devlog about the
layered disclosure approach ships **before or with** the deeper page
going live, never after. Framing is "we told you there was a game,
and there's still a game; here's what's underneath if you want." The
spine (§3) is pre-rehearsed so the first 50 community replies don't
drift. If sentiment in Discord or Reddit threads skews negative
(>20% of reactions), phase 1 is paused — not advanced through.

**(b) Apple App Review — the app cross-links to Web3 content.** The
single biggest existential risk. Mitigation: a CI check on the mobile
repo that greps every user-facing string, every `Linking.openURL`
destination, every push-notification template, and every in-app
support article for the deeper page's URL, any subdomain of it, or any
vocabulary from the banned list in §7 of the MVP plan. Fails the
build. App Review's pattern-match is URL-based as much as it is
vocabulary-based; the URL check is as important as the grep. Revisit
before every phase transition.

**(c) Regulatory / securities-adjacent language.** Mitigation: every
word of public copy at phase 1+ is reviewed against a short banned
list ("yield", "returns", "airdrop", "guaranteed", "investment",
"ROI", "appreciation", "utility token") before publishing. ToS/Privacy
get re-versioned when public copy drifts from the "pseudonymous
internal account identifier" baseline — the legal README (§7 of
`legal/README.md`) already flags this framing as a specific
watch-item. At phase 2, before the footer link lands, public-facing
copy goes through a counsel pass, not just a self-edit.

**(d) Community polarization.** Mitigation: Discord structure keeps
`#general` game-first through every phase. Architecture/ownership
channels are opt-in and read-only (phase 1) or separately moderated
(phase 2). Staff moderation rule: tokenomics speculation is not
confirmed, even playfully, at any phase before phase 3 and possibly
never. If two cultures form that hate each other, that's the "slow
down" signal — not the "ship more" signal.

---

## 5. What the website specifically does per phase

**Phase 0.**
- `ascion.game` — game landing, email capture, TestFlight invite,
  screenshots, the four-sentence spine in friendlier marketing
  language, footer links to ToS/Privacy and Discord only.
- `<meta description>`: game-only. No infra vocabulary. Same on
  OpenGraph.
- `robots.txt` and `sitemap.xml` include only the game landing, legal
  pages, and Discord redirect.
- No subdomains live.

**Phase 1.**
- New page at `ascion.game/build` (or similar), **not linked** from
  the main site nav or footer. Linked only from: one devlog post,
  one Discord pin, and direct links shared with press.
- The page has its own `<meta>` (infra-honest) and its own canonical
  URL. The main game landing's meta does not change.
- `robots.txt`: the `/build` page is allowed; it will index over time.
  That's intentional — the page is public, it's just not promoted.

**Phase 2.**
- `/build` (or rename to `/ownership`) gets a **single footer link**
  from the main game landing, neutrally labelled.
- Main landing `<meta>` unchanged; the ownership page `<meta>` can now
  reference on-chain ownership explicitly.
- Possible second surface: a dedicated `docs.ascion.game` or
  `build.ascion.game` subdomain if the content grows past one page. If
  so, it does **not** cross-link from the mobile app at any point.

**Phase 3.**
- Potential separate Web3-audience site; cross-links possible between
  web properties; mobile app's link-out behavior decided at phase
  entry, default unchanged.

The main game landing's `<meta description>` is game-only across every
phase of this plan. It only changes at phase 3, and only if the
phase-3 decision explicitly calls for it.

---

## 6. Checklist — before each phase boundary

### Before phase 1 launch
- [ ] MVP retention bar held for 3+ weeks (D1 ~25%+, D7 ~8%+).
- [ ] First-purchase data exists (≥1 paid account, not a friend).
- [ ] Legal reviewer has read the `/build` page copy; no
      securities-adjacent language flagged.
- [ ] Devlog draft reviewed against the spine (§3) for drift.
- [ ] CI check in `ascion-client-mobile` includes the deeper-page URL
      in its banned-link list (even though the page isn't linked,
      prove it's not linked).
- [ ] Discord moderator brief written and saved somewhere the dev can
      paste from in 30 seconds.
- [ ] A "pause" condition is written down: what sentiment signal,
      quantified, means phase 1 is not advancing.

### Before phase 2 launch
- [ ] Phase 1 held for 3+ months without retention damage or App
      Review incident.
- [ ] Prime cohort data shows month-2 retention viable.
- [ ] ToS/Privacy reviewed for language drift; version bumped if
      public copy now says things the legal docs' "pseudonymous
      internal account identifier" framing can't carry.
- [ ] Counsel pass on all public phase-2 copy (not just self-edit).
- [ ] Footer link copy A/B-reviewed for neutrality (not "crypto", not
      "NFT", not clickbait-curious either).
- [ ] Mobile app CI check re-run, confirming no new leakage.
- [ ] Discord structure decision for `#ownership` channel made and
      documented.

### Before phase 3 consideration
- [ ] A specific external trigger has occurred (custody change,
      regulatory clarification, clear player demand).
- [ ] Apple App Review policy re-checked against the specific
      link-out proposal.
- [ ] Legal review of the full phase-3 proposal, not just copy.
- [ ] This plan is re-opened and rewritten from phase 2 forward —
      phase 3 here is a placeholder, not a spec.

---

## 7. Open questions — to validate

- **When, if ever, does ASC-pay become thinkable?** Earliest
  conceivable point is phase 2, and only on the web surface, never on
  mobile. The signal that would unlock the question (not the answer)
  is: a non-trivial fraction of the phase-2 audience asking for it
  unprompted. This plan does not commit to it.
- **Does the mobile app ever link out?** Default through phase 2 is
  no. Phase 3 may revisit. The decision is bound to App Review policy
  at that time, not to our preference.
- **Is there a healthy version of the "you found the deeper thing"
  mechanic?** Possibly — framed as transparency rewarded (curious
  player finds honest dev), not as a retention gimmick (gated secret
  that players chase). The line is whether the deeper page exists for
  people who want it, or whether the game hints at its existence to
  drive engagement. Only the former. If the instinct to hint creeps
  in, that's the sign the plan is being corrupted.
- **Does the Vault's in-fiction framing ever change?** Through phase
  2, no. Phase 3, unknown — tied to whatever the custody reality is.
- **Does Android release change the disclosure calendar?** Android's
  store policy is materially more permissive on crypto; that does
  **not** mean we use that permission. The plan stays identical on
  Android; Play Store's tolerance is not a reason to disclose faster.
- **Press strategy timing.** Not decided here. Earliest is phase 1
  (single honest devlog amplified by friendly press). No crypto-press
  outreach before phase 2.
- **Whitepaper / tokenomics publication.** Out of scope for this plan
  entirely. If ever published, it's gated on phase 3 and a separate
  legal pass.

---

*Paired with `MVP_PLAN.md` (2026-04-20). This plan governs when and
how disclosure happens; it does not decide what is disclosed in
content terms. Re-open at each phase boundary; do not fork.*
