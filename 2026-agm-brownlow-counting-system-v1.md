# The Brownlow Medal Counting System — 2026 AGM, Owners Corporation PS640556E

> ### *"No vote-counting challenges in over 100 years."*

*Verification and counting procedures for nominations, proxies, pre-votes and meeting votes, modelled on the AFL Brownlow Medal count.*

| Document control | |
|---|---|
| **Version** | 1.4 |
| **Date** | 28 August 2026 |
| **Status** | Version 1 — for review before filing under Order 2 (due 5:00pm, 2 September 2026) |
| **Changes** | v1.1: rebranded as the Brownlow Medal Counting System; added "Why the Brownlow model works". v1.2: added slogan. v1.3: removed controversies discussion; added time budget. v1.4: scoped to the committee election only; ballots of up to 7 candidates per lot; tie rule for the 7th seat |
| **Diagrams** | Six process diagrams in `diagrams/` (see index at the end of this document) |

**Prepared for:** Submission under Order 2 of the Orders of Judge M Tran, Vice President, dated 28 August 2026 (OC1951/2025) — proposed guidelines and procedures for the conduct of the 2026 AGM (due 5:00pm, Wednesday 2 September 2026).

**Scope:** This system governs the **election of the committee only**. All other motions at the 2026 AGM are conducted under the chair's ordinary procedure and are outside this proposal. The election is where the 2025 AGM produced two rival committees and this litigation, and it is the one item where the count itself — not the merits — was the battleground. The registers built in Parts 0–3 exist to serve the election; the owners corporation is free to reuse them for other business, but nothing here requires it.

**The ballot:** Each lot casts **one ballot listing up to 7 candidates** (the committee maximum under s 103(1)). The 7 candidates with the most ballots are elected.

**Constraint:** The only software available is **Zoom Web Chat**, **email**, and **Excel**. No third-party voting platforms. Every step below uses only these three tools.

**Design principle:** Every failure at the 2025 AGM was a *verification* failure — instruments (pre-votes, proxies, nominations) arrived through channels that could not be tied to the lot owner, and validity was decided *after* the meeting, behind closed doors. This system moves all verification **before or during** the meeting, makes every acceptance/rejection **visible to all parties in real time**, and leaves a complete **audit trail** (email records, saved Zoom chat log, meeting recording, and a single Excel workbook).

---

## Why the Brownlow model works

The system is modelled on the counting method of the **Brownlow Medal** — the AFL's best-and-fairest award, counted every season since 1924. More than 100 counts have now been completed, deciding an award of enormous public, professional and commercial value, live in front of a national audience — and in over 100 years, **the count itself has never been challenged**: no court, so far as we are aware, has ever been asked to look at a Brownlow tally, and no count has ever been found to contain a vote-counting error. A century of contested stakes, zero disputes about the arithmetic.

That record is not luck. It comes from five design features, and every one of them is carried into this system:

| Brownlow Medal feature | Equivalent in this system |
|---|---|
| **Votes are sealed at the source.** The field umpires complete the 3‑2‑1 voting card immediately after each match and it goes straight into secure custody, untouched until count night. | Every instrument arrives via the lot owner's registered email (or is confirmed by challenge–response to it) and is logged with a timestamp in the `Inbox` sheet the moment it lands. No instrument is handled, filtered or "interpreted" by an interested party on the way in. (Part 0) |
| **The chain of custody is unbroken and documented.** Sealed envelopes, secure transport, opened only on stage. | One dedicated returning-officer inbox named in the notice; a complete `Inbox` log producible to the Tribunal as-is. (Parts 0.4, 5) |
| **Eligibility rules are fixed before a single vote is cast.** A player suspended during the season is ineligible no matter how many votes he polls — a rule applied since 1931, known to everyone in advance. | Every eligibility rule — arrears (s 89B), proxy caps (s 89D), form requirements, one vote per lot (s 87) — is published in the AGM notice and applied by pre-built, inspectable formulas. No rule is invented after the count, which is precisely what owners allege happened in 2025. (Parts 1–4) |
| **The count is live, public, and not pre-tallied.** Envelopes are opened round by round on stage; not even the organisers know the result in advance, so nobody *can* shade it. | Votes appear in the Zoom chat, attributed and timestamped, and land in the screen-shared tally in real time, with a scrutineer from each side watching the same screen. (Parts 4.2–4.4) |
| **The result is complete before the room empties.** The medal is hung around the winner's neck the same night, on the same stage the votes were read. | The finished workbook is emailed to every owner **on camera, before the meeting closes**, endorsed by both scrutineers in the chat. (Part 4.7) |

A dispute cannot get traction against a count that everyone watched happen under rules everyone knew beforehand. That is the standard proposed for the 2026 AGM: not a meeting whose *outcomes* nobody disputes — owners will always disagree about motions — but a meeting whose ***count*** leaves nothing to dispute.

---

## The problem, broken into parts

| Part | What must be verified | Statutory anchor |
|---|---|---|
| 0 | **Identity foundation** — who owns each lot, and what is each owner's address of record | OC register; s 87 (one vote per lot) |
| 1 | **Committee nominations** — eligibility and authenticity of nominees | s 103 |
| 2 | **Proxies** — form, authenticity, currency, holder limits, arrears bars | ss 89C–89F; reg 8, Sched 1 |
| 3 | **Pre-votes** — whether they are authorised at all; if allowed, authenticity and precedence | ss 80, 83–86, 89; reg 7B |
| 4 | **Votes at the meeting** — entitlement to vote, one vote per lot, arrears, polls, live tally | ss 77, 87, 89, 89A, 89B |

Parts 1–4 all depend on Part 0. Each part below states the rule, the verification procedure, the Excel structure, and the timeline.

---

## Part 0 — Identity Foundation (the Verified Contact Register)

Nothing can be verified against a register nobody trusts. This is where 2025 broke: Above OCM rejected 107 voting papers because they came "from an unknown party" and could not be matched to "known contact details of any lot owner" — but owners had never been asked to confirm those contact details.

### 0.1 The Register (Excel: sheet `LotRegister`)

One row per lot, columns:

- Lot number · Owner name(s) (per title/OC register) · **Registered email** (address of record) · Phone · Lot entitlement · Lot liability · Arrears amount and as-at date · Arrears-cleared date (for the s 89B four-business-day rule) · Contact-verified flag · Notes.

### 0.2 Contact confirmation campaign (email)

At least **28 days before the AGM**:

1. The manager (or returning officer — see Part 5) emails every owner at the address currently held in the OC register: *"You are recorded as the owner of Lot X. Reply to this email to confirm this address as your address of record for the 2026 AGM, or to nominate a different one. Instruments sent from any other address will require additional verification."*
2. Replies are logged in `LotRegister` (Contact-verified = YES, date).
3. Owners who do not reply get one reminder at 21 days. Non-response does not disenfranchise anyone — it just means their instruments go through challenge–response (0.3).
4. A change of address of record after the campaign closes requires a reply from the *old* address or a signed request with supporting ID — this prevents last-minute redirection of a lot's voting channel.

### 0.3 The universal verification rule (challenge–response)

For **every** instrument received (nomination, proxy, pre-vote if permitted, registration):

- **Green lane:** sent from the lot's registered email → accepted, logged, acknowledged by reply.
- **Amber lane:** sent from any other address (including bulk submissions by a third party) → the returning officer sends a **challenge email to the registered address**: *"We received [instrument] purportedly from you. Reply CONFIRM to accept it or DENY to reject it."* Confirmed → accepted. Denied or no reply by the relevant deadline → rejected, with a written reason code sent to both the sender and the registered address.
- **No instrument is ever silently discarded.** Every rejection appears on the `Flags` sheet with a reason code, and the affected owner is told before the meeting wherever the deadline allows.

This single rule replaces the 2025 approach (after-the-fact bulk exclusion) with a symmetric, testable one: it does not matter *who* forwards a document; what matters is whether the owner, contacted at the address of record, stands behind it.

### 0.4 Audit log (Excel: sheet `Inbox`)

Every inbound email touching the AGM is logged: timestamp received, sender address, lot(s) concerned, instrument type, lane (green/amber), verification outcome, reason code if rejected. This sheet is producible to the Tribunal as-is.

---

## Part 1 — Verifying Committee Nominations (s 103)

### 1.1 The rules being enforced

- Committee of 3–7 members, or up to 12 if the OC so resolves by ordinary resolution (s 103(1), (1A)).
- Members must be **lot owners or hold proxies** on behalf of lot owners (s 103(2)).
- **Not more than one member from any one lot** (s 103(3)).
- Nomination may be **in writing**, or **orally at the AGM** if the owner is present (s 103(4)).
- A lot owner in arrears (or their proxy) is **not eligible** for election (s 103(7)(a)).

### 1.2 Procedure

1. **Written nominations** open with the AGM notice and close **5:00pm, 3 business days before the AGM** (so eligibility checks finish before the meeting). Each nomination states: nominee name, lot relied on, whether nominee is owner or proxy holder for that lot, and is submitted by email subject to the Part 0 verification rule.
2. **Eligibility check** per nominee, recorded in Excel (sheet `Nominations`): identity verified (green/amber lane outcome) · lot ownership or verified proxy confirmed against `LotRegister` · arrears check as at the meeting date (s 103(7)) · one-per-lot check (duplicate-lot nominations flagged; the lot's owner decides which stands, failing which the earlier-received stands).
3. **Publication:** the verified candidate list (name, lot, owner/proxy basis) is emailed to all owners **2 business days before the AGM**, with any rejected nominations listed by lot and reason code. Objections may be emailed before the meeting and are put to the chair at the meeting.
4. **Oral nominations at the AGM** (s 103(4)(b) cannot be excluded by procedure): the nominee or nominating owner states name and lot in the meeting (voice or Zoom chat); the returning officer checks `LotRegister` and arrears **live** and the nominee is admitted to the ballot or refused with the reason stated on the record, before voting opens.
5. **Election vote** proceeds under Part 4: each lot casts one ballot listing up to 7 candidates; the 7 highest vote-getters are elected, with s 89(3) entitlement-poll available on demand.

### 1.3 Excel: sheet `Nominations`

Nominee · Lot · Basis (owner / proxy for lot) · Received datetime · Sender address · Lane · Verified? · Arrears OK? · One-per-lot OK? · **Eligible?** (formula over the three checks) · Reason code if not.

---

## Part 2 — Verifying Proxies (ss 89C–89F)

### 2.1 The rules being enforced

- Prescribed form (Sched 1 of the Regulations); must authorise **an individual**; delivered to the secretary (s 89C(3)).
- Effective from the first meeting after delivery; **lapses 12 months** after it is given, or earlier if stated (s 89C(4), (6)). Not transferable (s 89C(5)).
- **Holder cap** (s 89D): with more than 20 occupiable lots, no person may vote as proxy for **more than 5% of lot owners** — except family members, or where one owner owns multiple lots and appointed the same person for each (reg 8A). The same cap applies to powers of attorney (s 89F(2)).
- A lot owner **in arrears may not act as proxy** for another lot (s 89C(10)).
- A **non-owner** proxy may not vote on matters affecting that person concerning delegation of powers or the appointment/payment/removal of the manager (s 89C(7)) — directly relevant to any motion about the OC manager.
- Revocation in writing to the secretary at any time; the owner may attend and vote instead of the proxy (s 89E).
- Grantor in arrears: the *lot's* vote is barred on ordinary resolutions regardless of who casts it (s 89B).

### 2.2 Procedure

1. **Deadline for emailed proxies: 5:00pm, 2 business days before the AGM**, to allow challenge–response to complete. (The Act allows delivery up to the meeting; therefore proxies **may still be delivered at the meeting**, but a late proxy is only *counted* once verified — see step 5.)
2. Each proxy form received is checked into Excel (sheet `Proxies`) and passed through the Part 0 lanes: green if sent from the **grantor's** registered email; amber (challenge–response to the grantor's registered address) otherwise — including any proxy submitted by the *holder*.
3. **Automated checks in Excel:** prescribed-form fields present · dated and within 12 months · names an individual · grantor signature field completed · grantor arrears status (flag: barred on ordinary resolutions per s 89B) · **holder arrears** status (s 89C(10): holder barred entirely) · holder is/isn't a lot owner (drives the s 89C(7) flag on manager-related motions) · **running count per holder** against the 5% cap with family/multi-lot exceptions recorded.
4. **Cap overflow rule (proposed):** where a holder exceeds the cap, proxies are counted in order of *verified receipt* up to the cap; excess proxies are ineligible to be voted but the grantors are notified before the meeting so they can attend, appoint someone else, or grant a directed proxy to an eligible holder.
5. **Proxies delivered at the meeting** are announced by the chair (holder, grantor lot), checked live against `LotRegister`, and — if the grantor's identity cannot be verified in the green lane — a challenge email is sent to the grantor's registered address during the meeting; the proxy counts only if confirmation arrives before the relevant vote closes. Otherwise the vote for that lot is recorded as **provisional** (Part 4.6) rather than silently included or excluded.
6. **Conflicts:** if the owner of a lot attends, the proxy for that lot is inoperative for that meeting (s 89E(1)(b)). If two instruments conflict (two proxies, or proxy + pre-vote), the **later-dated verified instrument** prevails; same-day conflicts are resolved by asking the owner via the registered address, failing which the lot's vote is provisional.
7. **Admittance of proxies** is a listed agenda item (as in 2025): the full proxy register — holder, grantor lot, directed/undirected, verified status, cap position — is displayed by screen-share **before any vote is taken**, so every participant sees exactly who is voting for whom before it matters, not in the minutes two weeks later.

### 2.3 Excel: sheet `Proxies`

Grantor lot · Grantor name · Holder name · Holder lot (if any) · Dated · Expiry · Directed? (with per-motion directions transcribed) · Received datetime · Sender address · Lane · Verified? · Grantor arrears flag (s 89B) · Holder arrears bar (s 89C(10)) · s 89C(7) flag · Holder running count / cap position · **Operative?** · Reason code.

---

## Part 3 — Pre-votes: whether to allow them, and how to verify them if allowed

### 3.1 The threshold question (Order 1 submission, due 1 September)

The recommended primary position is that **pre-voting on meeting resolutions is not authorised by the Act**, and that the 2026 AGM should not use it:

1. Section 80(1) exhaustively lists how a lot owner may participate in a general meeting: **in person, by teleconference/videoconference (reg 7A), or by proxy**. A "pre-vote" is a vote by a person participating in none of these ways.
2. Section 89 governs voting **"at a meeting"**; s 89(3)–(5) lets any owner demand a poll *before or after* a vote is taken, and floor amendments and chair rulings can change what is actually voted on. A vote cast days earlier cannot respond to a poll demand, an amended motion, or debate — which is precisely why the Act's mechanism for deciding matters **without** assembling is the **ballot** (Division 5, ss 83–86), a separate procedure with its own 14-day notice, closing date, and quorum rule. Pre-voting grafts a ballot onto a meeting without either procedure's safeguards.
3. The 2025 AGM is the case study in what then happens: 107 photographed and re-forwarded "voting papers" arriving via a Gmail account and WeChat 90 minutes before the meeting, unverifiable in the time available, followed by mass exclusion after the meeting and this proceeding.
4. The Act already provides a fully-serviceable channel for an owner who cannot attend: a **directed proxy** (s 89C(4) expressly permits the authorisation to "set out how a proxy is to vote on particular matters"). A directed proxy achieves everything a pre-vote does, *and* is subject to the Act's built-in integrity controls (prescribed form, delivery to the secretary, holder caps, arrears bars, revocation).

**Fallback position** — if the Tribunal holds that pre-voting is available (e.g. as a reg 7B "prescribed manner" form completed in advance, or under the s 80(2) procedural discretion) — then it should be permitted only under the verification regime in 3.2.

### 3.2 If pre-votes are allowed: verification regime

1. **One channel:** a pre-vote is the reg 7B-compliant voting form (containing all reg 7B(a)–(k) fields, including signature and date) emailed **by the lot owner from the registered email address** (green lane) or verified by challenge–response (amber lane). **Bulk submissions by third parties are not accepted as green-lane**; each one triggers individual challenge–response to the owner — third parties may encourage voting, but the confirming click must come from the owner's own address of record.
2. **Deadline: 5:00pm, 2 business days before the AGM** (not one hour — verification must be completable). Each verified pre-vote is acknowledged by reply to the registered address, stating exactly which motions it covers.
3. **One vote per lot (s 87):** a pre-vote is void for a lot if the owner (or an operative proxy for the lot) attends the meeting; the later-dated verified instrument always prevails.
4. **Scope limits:** a pre-vote counts only for a motion put to the meeting **in the exact text noticed**. If a motion is amended at the meeting, pre-votes on it lapse (recorded as such, not converted). If a s 89(3) poll is demanded, verified pre-vote forms count as the written votes of those lots for the poll, at their entitlements.
5. **Arrears (s 89B)** applies identically to pre-votes.
6. **Disclosure:** before voting opens, the chair screen-shares the pre-vote register (lot, motions covered, verified status — not the direction of the vote) so the meeting knows exactly which lots are voting in advance. Directions are revealed motion-by-motion in the tally.
7. **Excel: sheet `PreVotes`** — Lot · Owner · Received datetime · Sender address · Lane · Verified? · Motions covered · Per-motion direction (Y/N/Abstain) · Arrears flag · Superseded-by (proxy/attendance/later instrument) · **Operative?** · Reason code.

---

## Part 4 — Verifying Votes at the AGM (Zoom + Chat + Excel)

### 4.1 Registration and admission

1. Zoom registration (name + lot number + email) closes 30 minutes before the meeting. The registration list is reconciled against `LotRegister` **before** the meeting.
2. **Waiting room** admission: a registrant whose email matches the lot's registered address is admitted directly. Any mismatch is verified in the waiting room by challenge–response email, or by voice check of details already held on the register. Admission is never refused silently — unresolved registrants are admitted as **observers** (renamed accordingly) who can be upgraded mid-meeting if verification completes.
3. On admission each participant is **renamed** by the host to a standard label, which is the participant's voting identity for the chat log:
   - `Lot 304 – A. Carson (Owner)`
   - `Lots C9,C37,602 – J. Chin (Proxy)`
   - `Observer – S. Saint-John (Above OCM)`
4. The `Attendance` sheet records: label, lot(s), capacity (owner / proxy / attorney / observer), admission time, verification lane. Quorum (s 77) is computed live: count of lots represented ÷ total lots; if below 50%, entitlement fallback; the chair announces quorum status on the record (interim-resolution consequences under s 78 stated if applicable).

### 4.2 The election ballot, by Zoom chat

The election vote is a **typed message in the Zoom chat, visible to everyone** — one ballot per lot, listing **up to 7 candidates** by name (and candidate lot, to disambiguate):

```
Lot 304: CARSON (507), CHIN (C9), XU (206), PETTIT (C27), JOHNSTON (C67)
Lots C9, C37, 602: CARSON (507), LEE (314)     ← a proxy casts each lot's ballot explicitly
Lot 1106: ABSTAIN
```

A ballot may list 1 to 7 candidates. Chat is used rather than hands or voice because every message is **attributed to the renamed participant, timestamped, ordered, and saved** — the chat log export is the primary voting record, and the meeting recording is the secondary record. (Judge Tran is reviewing the 2025 AGM video for exactly this reason; the 2026 design makes the record self-proving.)

The count runs once:

1. Chair reads the **verified candidate list** (Part 1) — name, lot, owner/proxy basis — plus any candidates validly added by oral nomination at the meeting, and opens a **timed voting window** (5 minutes, announced; longer than a Yes/No vote because ballots take longer to type).
2. Participants type ballots. Owners with operative directed proxies/pre-votes do not vote (their instrument already votes); if they do, their live ballot **supersedes** the instrument (s 89E logic) and the tally sheet swaps it automatically.
3. **Live correction, not silent rejection:** the returning officer prompts in chat the moment a ballot has a defect — more than 7 candidates, an unrecognised name, a duplicate — and the voter may resubmit within the window (last message counts). A ballot still defective at close is invalid with a reason code; a duplicate candidate on an otherwise valid ballot is simply counted once.
4. Window closes; a **reconciliation pause** (~2 minutes) while the returning officer and scrutineers confirm the sheet matches the chat; chair then announces the count for **every candidate** (not just the winners), the 7 elected, and any flagged/provisional ballots (4.6).

**Who does what during a vote — the chair does not read votes out, and does not touch the workbook:**

| Role | During the voting window |
|---|---|
| **Participants** | Type the ballot in chat. The chat message *is* the public declaration of the vote — visible to all, attributed, timestamped. No oral repetition is needed or evidentially useful. |
| **Returning officer** | Keys each ballot into the lot's row in `VoteTally` as the messages arrive, on the live shared screen, and prompts in chat for correctable defects. Each voter watches their own ballot land in the grid seconds after typing it. |
| **Scrutineers** | Cross-check chat against sheet in real time; object in chat (`Point of order: Lot 610's ballot entered without CARSON, chat includes CARSON`) the moment an entry is wrong or missed. |
| **Chair** | Speaks only at the edges: reads the candidate list, opens/closes the window, states flagged or provisional ballots with reasons, announces the count. Never operates the workbook. |

The separation is deliberate: in 2025 the chairing, the counting, and the commercial interest in the outcome sat with the same organisation. Here the chair conducts, the returning officer records, and the scrutineers check — three different hands.

**Voice fallback:** a participant who joined by telephone or cannot type states their ballot aloud ("Lot 105: Carson, Chin, Xu"); the chair repeats it back for the recording; the returning officer enters it flagged `voice vote` in the log. This is the only case in which a ballot is read aloud.

**Time budget — approximately 25 minutes for the whole election count:**

| Step | Time |
|---|---|
| Chair reads the verified candidate list (incl. any oral nominations checked live) | ~5 min |
| Ballot window (chat ballots of up to 7 candidates typed, RO keys them live) | 5 min |
| Reconciliation pause (RO + scrutineers confirm sheet = chat, defects resolved) | ~5 min |
| Chair announces every candidate's count, the 7 elected, any flagged ballots | ~5 min |
| Buffer for provisional-ballot rulings and a runoff if the 7th seat ties (4.5) | ~5 min |

Because this system applies **only to the committee election**, it adds roughly **25 minutes** to the meeting — the rest of the agenda runs under the chair's ordinary procedure and is unaffected. Directed proxies and pre-verified instruments cost no meeting time at all, since the tally sheet applies them automatically. For comparison: the 2025 AGM ran 75 minutes in total, and its election count is now in its second year of litigation. Twenty-five minutes of counting in the open is the cheapest insurance in this document.

### 4.3 The tally engine (Excel: sheet `VoteTally`)

One row per lot; **7 candidate columns** (Choice 1–7) plus validity columns; one results block with a row per candidate. For each lot's ballot the sheet validates against the other sheets, all by lookup on lot number:

- Lot is represented (in `Attendance`, or has operative proxy/pre-vote) — else no ballot.
- Voter matches the lot's operative channel (owner present > later instrument > earlier instrument).
- **s 87:** one ballot per lot — duplicate chat entries for a lot are flagged; the *last* message within the window from the operative voter counts, and any conflict between different persons for the same lot is a provisional ballot (4.6).
- **Ballot validity:** at most 7 candidates; every name matches the verified candidate list (data-validation dropdowns in the choice columns make an unrecognised name impossible to key); a candidate appearing twice on one ballot is counted once.
- **s 89B:** arrears lots blocked (auto-lifted where `LotRegister` shows payment in full ≥ 4 business days prior, or cash).
- **s 89C(10), 89D:** proxy bars — an arrears proxy holder cannot cast ballots for others; ballots beyond a holder's 5% cap are not counted.
- **Candidate totals:** one `COUNTIF` per candidate across the choice columns of valid ballots; the 7 highest totals are elected. Poll mode (s 89(3)): a toggle switches each `COUNTIF` to a `SUMIF` of lot entitlements, so a demanded poll re-ranks by entitlement instantly. The chat message *is* the written vote required by s 89(4).

Formulas are ordinary `COUNTIF`/`SUMIF`/`XLOOKUP` — no macros, so the workbook is inspectable by any party.

### 4.4 Tellers and transparency

- A **returning officer** (Part 5) operates the workbook, **screen-sharing the tally sheet continuously** while voting is open.
- **Two scrutineers** — one nominated by each side of this proceeding — watch the shared screen and the chat and may raise objections in real time ("Point of order" in chat). Because the workbook is formula-driven and visible, both camps are checking the same arithmetic at the same moment.
- Nothing about a vote's validity is decided after the meeting. That is the central lesson of 2025.

### 4.5 Ties for the final seat

If two or more candidates tie for the 7th seat, an immediate **runoff ballot** is held between the tied candidates only (same chat mechanics, 2-minute window, one name per lot). If the runoff also ties, the seat is decided by a random draw conducted by the chair **on camera** (e.g. drawing lot-numbered slips shown to the meeting) — announced as the tie-break method before the election window opens, never chosen after the numbers are known.

### 4.6 Provisional votes

Any ballot failing live verification (identity unresolved, conflicting instruments, cap dispute) is recorded as **provisional with a reason code**, announced in the running tally as such, and resolved by challenge–response during or immediately after the meeting **only where the provisional ballots could change which candidates are elected**. If they cannot change the result, the election stands and the provisional list is simply published. If they can, the chair states on the record which seats await resolution of the named provisional lots by a stated deadline (48 hours), after which the final tally is published showing exactly how each provisional ballot resolved. No ballot moves from counted to excluded, or vice versa, without a published reason.

### 4.7 Live dispatch of the completed workbook (before the meeting closes)

The final integrity step happens **on camera, while the screen share is still running**:

1. After the last motion is decided, the returning officer saves the workbook twice, with the date-time in the filenames: the working copy with formulas intact (`AGM-2026-Tally-FORMULAS.xlsx`), and a values-frozen snapshot (`AGM-2026-Tally-FINAL.xlsx`, paste-as-values) so the dispatched result can never silently recalculate.
2. Still sharing the screen, the returning officer composes the email in view of the meeting — both files attached, addressed to the dedicated AGM address, **BCC to every registered email in `LotRegister`**, CC to both scrutineers and any administrator — and **clicks send while everyone watches**. The sent item, timestamped inside the meeting, is captured in the recording.
3. The chair states on the record that the workbook as dispatched is the voting record of the meeting, and each scrutineer confirms in the Zoom chat (`Scrutineer [name]: workbook as sent reflects the tally displayed`).
4. Only then is the meeting closed and the chat log saved.

The effect: the recording shows the tally being built, the same file being sent, and both scrutineers endorsing it — so any later document that differs from what landed in every owner's inbox during the meeting is provably not the record. Provisional votes (4.6) are the one open item; their resolution is published as a **supplementary email within 48 hours** that changes only the flagged lots and references the dispatched workbook, never a reissued one.

### 4.8 After the meeting

Within 14 days (s 81, and s 78(2) if quorum failed): minutes including, as attachments or annexures — the saved Zoom chat log, the `Attendance`, `Proxies`, `PreVotes` (if any), `VoteTally`, and `Flags` sheets, and the per-motion results. Every excluded or provisional vote appears with its lot, reason code, and resolution. The meeting recording is retained by the OC.

---

## Part 5 — Who runs this: the Returning Officer

Given the history, the person operating the register and tally should not be a person with a financial interest in any motion (Above OCM has an interest in the management-contract motion; s 89C(7) reflects the same concern). Proposed:

- The Tribunal designates (or the parties agree) a **returning officer** — an independent person (e.g. the administrator if one is appointed, an independent OC manager engaged for the meeting only, or a person nominated by the Tribunal) — who runs Parts 0–4.
- Each side of the proceeding nominates **one scrutineer** with the real-time rights in 4.4.
- The returning officer's inbox for the AGM is a single dedicated address stated in the notice; all instruments go there; the `Inbox` log is complete and producible.

---

## Part 6 — Timeline (working back from the AGM)

| When | What |
|---|---|
| AGM − 28 days | Contact-confirmation campaign opens (Part 0.2) |
| AGM − 21 days | Reminder to unconfirmed owners |
| AGM − 14 days | **Notice of AGM** (s 72): agenda, motions text, financials, budget, proxy form (Sched 1), these procedures, the dedicated email address, all deadlines below |
| AGM − 3 business days, 5pm | Written nominations close (Part 1) |
| AGM − 2 business days, 5pm | Emailed proxies close (Part 2); pre-votes close, if allowed (Part 3) |
| AGM − 2 business days | Verified candidate list and rejection notices emailed to all owners |
| AGM − 1 business day | Proxy register finalised; cap-overflow and arrears notices sent; challenge–responses completed |
| AGM − 30 min | Zoom registration closes; waiting-room verification begins |
| AGM | Runbook: quorum → other AGM business under the chair's ordinary procedure → proxy/pre-vote registers displayed → oral nominations checked live → **election count** (candidate list → 5-min ballot window → reconciliation → every candidate's total announced) → **workbook emailed to all owners on live screen share before close** (4.7) |
| AGM + 48 hours | Provisional votes resolved (only where outcome-determinative) |
| AGM + 14 days | Minutes + full annexed registers and chat log to all owners |

---

## Process diagrams

Each diagram is a separate Mermaid file in `diagrams/`, viewable in any Mermaid renderer (GitHub, VS Code, mermaid.live):

| File | Shows |
|---|---|
| `diagrams/01-end-to-end-timeline.mmd` | The full timeline: contact campaign → notice → deadlines → meeting day → post-meeting (Part 6) |
| `diagrams/02-universal-verification.mmd` | The green/amber lane challenge–response rule applied to every instrument (Part 0.3) |
| `diagrams/03-proxy-checks.mmd` | The proxy verification pipeline: form, currency, arrears bars, 5% cap, per-motion flags (Part 2) |
| `diagrams/04-lot-vote-precedence.mmd` | Which ballot counts for a lot: owner present > proxy > pre-vote, with the s 89B arrears gate, ballot-validity checks and duplicate handling (Parts 2.2, 3.2, 4.3) |
| `diagrams/05-election-count-sequence.mmd` | The election count start to finish: chair, participants, returning officer, scrutineers — who does what, including the runoff (Parts 4.2, 4.5) |
| `diagrams/06-meeting-day-runbook.mmd` | Meeting day: waiting-room checks → renamed identities → quorum → other business (ordinary procedure) → election count → on-camera workbook dispatch (Parts 4.1, 4.7) |

---

## Part 7 — Why this design answers the 2025 failures

| 2025 failure | 2026 control |
|---|---|
| 107 pre-votes bulk-forwarded from `proposedcommittee@gmail.com` / WeChat, 90 minutes before the meeting | Primary position: no pre-votes — directed proxies instead. Fallback: owner-channel-only submission, 2-business-day deadline, individual challenge–response (Parts 3.1–3.2) |
| ~66 lots excluded *after* the meeting as "unable to verify", with no owner contacted | Universal challenge–response to the address of record before rejection; no silent exclusion; all validity decided live with scrutineers watching (Parts 0.3, 4.4, 4.6) |
| "Unknown contact details" used as the exclusion ground | Contact-confirmation campaign 28 days out fixes the register first (Part 0.2) |
| Competing committee slates, nomination authenticity contested | Verified, published candidate list before the meeting; live eligibility check for oral nominations (Part 1) |
| Verifier (manager) had a direct interest in the contested motions | Independent returning officer + one scrutineer per side (Part 5) |
| Vote record reconstructable only from a video | Attributed, timestamped, saved chat log + live screen-shared tally + formula-only workbook annexed to the minutes (Parts 4.2–4.3, 4.8) |
| Minutes issued 2 weeks later differed from what owners saw at the meeting | Workbook emailed to every owner **on camera before the meeting closes**, endorsed by both scrutineers in chat; minutes must match the dispatched file (Part 4.7) |

---

*Prepared 28 August 2026. Statutory references: Owners Corporations Act 2006 (Vic) ss 70–90, 89A–89H, 95–97, 100–104, 113; Owners Corporations Regulations 2018 (Vic) regs 7A, 7B, 8, 8A, Sch 1.*
