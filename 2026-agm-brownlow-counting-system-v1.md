# The Brownlow Medal Counting System — Proposal for the 2026 AGM, Owners Corporation PS640556E

### The Register

One row per lot, columns:

- Lot number · Owner name(s) (per title/OC register) · **Registered email** (address of record) · Phone · Lot entitlement · Lot liability · Arrears amount and as-at date · Arrears-cleared date (for the s 89B four-business-day rule) · Contact-verified flag · Notes.

### The verification rule

For **every** instrument received (nomination, proxy, pre-vote if permitted, registration):
- **Accepted:** sent from the lot's registered email → logged and acknowledged by reply.
- **Declined:** sent from any other address.

---

## Part 1 — Verifying Committee Nominations (s 103)

### 1.1 Procedure

1. **Written nominations** open with the AGM notice and close **5:00pm, 3 business days before the AGM**
2. **Eligibility check** per nominee, recorded in Excel (sheet `Nominations`): identity verified (sent from the registered email, per the verification rule) · lot ownership or verified proxy confirmed against `LotRegister` · arrears check as at the meeting date (s 103(7))  
3. **Publication:** the verified candidate list (name, lot, owner/proxy basis) is emailed to all owners **2 business days before the AGM**, with any rejected nominations listed by lot and reason code. Objections may be emailed before the meeting and are put to the chair at the meeting.
4. **Oral nominations at the AGM**: the nominee or nominating owner states name and lot in the meeting (voice or Zoom chat); the chair checks `LotRegister` and arrears **live** and the nominee is admitted to the ballot or refused with the reason stated on the record, before voting opens.


### 1.2 Excel: sheet `Nominations`

Nominee · Lot · Basis (owner / proxy for lot) · Received datetime · Sender address · Verified? · Arrears OK? · One-per-lot OK? · **Eligible?** (formula over the three checks) · Reason given if not.

## Part 2 — Verifying Proxies (ss 89C–89F)

### 2.1 Procedure

1. **Deadline for emailed proxies: 5:00pm, 2 business days before the AGM**, to allow verification and the cap checks to complete. (The Act allows delivery up to the meeting; therefore proxies **may still be delivered at the meeting**, but a late proxy is only *counted* once verified — see step 5.)
2. Each proxy form received is checked into Excel (sheet `Proxies`) and verified under the verification rule: operative only if sent from the **grantor's** registered email — including any proxy submitted by the *holder*.
3. **Automated checks in Excel:** prescribed-form fields present · dated and within 12 months · names an individual · grantor signature field completed · grantor arrears status (flag: barred on ordinary resolutions per s 89B) · **holder arrears** status (s 89C(10): holder barred entirely) · holder is/isn't a lot owner (drives the s 89C(7) flag on manager-related motions) · **running count per holder** against the 5% cap with family/multi-lot exceptions recorded.
4. **Cap overflow rule (proposed):** where a holder exceeds the cap, proxies are counted in order of *verified receipt* up to the cap; excess proxies are ineligible to be voted but the grantors are notified before the meeting so they can attend, appoint someone else, or grant a directed proxy to an eligible holder.
5. **Proxies delivered at the meeting** are announced by the chair (holder, grantor lot) and checked live against `LotRegister`; the proxy counts only if it was sent from the grantor's registered email, or an email from that address confirming it arrives before the relevant vote closes. Otherwise the vote for that lot is recorded as **provisional** (Part 4.5) rather than silently included or excluded.
6. **Admittance of proxies** is a listed agenda item, the full proxy register — holder, grantor lot, directed/undirected, verified status, cap position — is displayed by screen-share **before any vote is taken**, so every participant sees exactly who is voting for whom before it matters, not in the minutes two weeks later.

### 2.3 Excel: sheet `Proxies`

Grantor lot · Grantor name · Holder name · Holder lot (if any) · Dated · Expiry · Directed? (with per-motion directions transcribed) · Received datetime · Sender address · Verified? · Grantor arrears flag (s 89B) · Holder arrears bar (s 89C(10)) · s 89C(7) flag · Holder running count / cap position · **Operative?** · Reason code.

## Part 4 — Verifying Votes at the AGM (Zoom + Chat + Excel)

### 4.1 Registration and admission

1. Zoom registration (name + lot number + email) closes 30 minutes before the meeting. The registration list is reconciled against `LotRegister` **before** the meeting.
2. **Waiting room** admission: a registrant whose email matches the lot's registered address is admitted directly. Any mismatch is admitted as an **observer** (renamed accordingly), who can be upgraded mid-meeting if an email from the lot's registered address confirms their identity.
3. On admission each participant is **renamed** by the host to a standard label, which is the participant's voting identity for the chat log:
   - `Lot 304 – A. Carson (Owner)`
   - `Lots C9,C37,602 – J. Chin (Proxy)`
   - `Observer – S. Saint-John (Above OCM)`
4. The `Attendance` sheet records: label, lot(s), capacity (owner / proxy / attorney / observer), admission time, verification status. Quorum (s 77) is computed live: count of lots represented ÷ total lots; if below 50%, entitlement fallback; the chair announces quorum status on the record (interim-resolution consequences under s 78 stated if applicable).

### 4.2 The election ballot, by Zoom chat

The election vote is a **typed message in the Zoom chat, visible to everyone** — one ballot per lot, listing **up to 7 candidates** by name (and candidate lot, to disambiguate):

```
Lot 304: CARSON (507), CHIN (C9), XU (206), PETTIT (C27), JOHNSTON (C67)
Lots C9, C37, 602: CARSON (507), LEE (314)     ← a proxy casts each lot's ballot explicitly
Lot 1106: ABSTAIN
```

The count runs once:

1. Chair reads the **verified candidate list** (Part 1) — name, lot, owner/proxy basis — plus any candidates validly added by oral nomination at the meeting, and opens a **timed voting window** (5 minutes, announced; longer than a Yes/No vote because ballots take longer to type).
2. Participants type ballots. Owners with operative directed proxies/pre-votes do not vote (their instrument already votes); if they do, their live ballot **supersedes** the instrument (s 89E logic) and the tally sheet swaps it automatically.
3. **Live correction, not silent rejection:** the chair prompts in chat the moment a ballot has a defect — more than 7 candidates, an unrecognised name, a duplicate — and the voter may resubmit within the window (last message counts). A ballot still defective at close is invalid with a reason code; a duplicate candidate on an otherwise valid ballot is simply counted once.
4. Window closes; a **reconciliation pause** (~2 minutes) while the chair and scrutineers confirm the sheet matches the chat; the chair then announces the count for **every candidate** (not just the winners), the 7 elected, and any flagged/provisional ballots (4.5).

**Who does what during a vote — no ballot is read out by the chair except the voice fallback below:**

| Role | During the voting window |
|---|---|
| **Participants** | Type the ballot in chat. The chat message *is* the public declaration of the vote — visible to all, attributed, timestamped. No oral repetition is needed or evidentially useful. |
| **Chair** | Reads the candidate list and opens/closes the window; keys each ballot into the lot's row in `VoteTally` as the messages arrive, on the live shared screen, prompting in chat for correctable defects; states flagged or provisional ballots with reasons; announces the count. Each voter watches their own ballot land in the grid seconds after typing it. |
| **Scrutineers** | Cross-check chat against sheet in real time; object in chat (`Point of order: Lot 610's ballot entered without CARSON, chat includes CARSON`) the moment an entry is wrong or missed. |

In 2025 the chairing, the counting, and the commercial interest in the outcome sat with the same organisation. Here one Tribunal-appointed independent chair (Part 5) both conducts and counts — but with no interest in the outcome, every entry made on a screen the whole meeting is watching, and the interested parties themselves checking each one as scrutineers.

**Voice fallback:** a participant who joined by telephone or cannot type states their ballot aloud ("Lot 105: Carson, Chin, Xu"); the chair repeats it back for the recording and enters it flagged `voice vote` in the log. This is the only case in which a ballot is read aloud.

**Time budget — approximately 25 minutes for the whole election count:**

| Step | Time |
|---|---|
| Chair reads the verified candidate list (incl. any oral nominations checked live) | ~5 min |
| Ballot window (chat ballots of up to 7 candidates typed, chair keys them live) | 5 min |
| Reconciliation pause (chair + scrutineers confirm sheet = chat, defects resolved) | ~5 min |
| Chair announces every candidate's count, the 7 elected, any flagged ballots | ~5 min |
| Buffer for provisional-ballot rulings (4.5) | ~5 min |

### 4.3 The tally engine (Excel: sheet `VoteTally`)

One row per lot; **7 candidate columns** (Choice 1–7) plus validity columns; one results block with a row per candidate. For each lot's ballot the sheet validates against the other sheets, all by lookup on lot number:

- Lot is represented (in `Attendance`, or has operative proxy/pre-vote) — else no ballot.
- Voter matches the lot's operative channel (owner present > later instrument > earlier instrument).
- **s 87:** one ballot per lot — duplicate chat entries for a lot are flagged; the *last* message within the window from the operative voter counts, and any conflict between different persons for the same lot is a provisional ballot (4.5).
- **Ballot validity:** at most 7 candidates; every name matches the verified candidate list (data-validation dropdowns in the choice columns make an unrecognised name impossible to key); a candidate appearing twice on one ballot is counted once.
- **s 89B:** arrears lots blocked (auto-lifted where `LotRegister` shows payment in full ≥ 4 business days prior, or cash).
- **s 89C(10), 89D:** proxy bars — an arrears proxy holder cannot cast ballots for others; ballots beyond a holder's 5% cap are not counted.
- **Candidate totals:** one `COUNTIF` per candidate across the choice columns of valid ballots; the 7 highest totals are elected. Poll mode (s 89(3)): a toggle switches each `COUNTIF` to a `SUMIF` of lot entitlements, so a demanded poll re-ranks by entitlement instantly. The chat message *is* the written vote required by s 89(4).

Formulas are ordinary `COUNTIF`/`SUMIF`/`XLOOKUP` — no macros, so the workbook is inspectable by any party.

### 4.4 Provisional votes

Any ballot failing live verification (identity unresolved, conflicting instruments, cap dispute) is recorded as **provisional with a reason code**, announced in the running tally as such, and resolved by confirmation from the lot's registered email during or immediately after the meeting **only where the provisional ballots could change which candidates are elected**. If they cannot change the result, the election stands and the provisional list is simply published. If they can, the chair states on the record which seats await resolution of the named provisional lots by a stated deadline (48 hours), after which the final tally is published showing exactly how each provisional ballot resolved. No ballot moves from counted to excluded, or vice versa, without a published reason.

### 4.5 Live dispatch of the completed workbook (before the meeting closes)

The final integrity step happens **on camera, while the screen share is still running**:

1. After the last motion is decided, the chair saves the workbook with the date-time in the filename (`AGM-2026-Tally-FINAL.xlsx`).
2. Still sharing the screen, the chair composes the email in view of the meeting — the file attached, addressed to the dedicated AGM address, **BCC to every registered email in `LotRegister`**, CC to both scrutineers and any administrator — and **clicks send while everyone watches**. The sent item, timestamped inside the meeting, is captured in the recording.
3. The chair states on the record that the workbook as dispatched is the voting record of the meeting, and each scrutineer confirms in the Zoom chat (`Scrutineer [name]: workbook as sent reflects the tally displayed`).
4. Only then is the meeting closed and the chat log saved.

The effect: the recording shows the tally being built, the same file being sent, and both scrutineers endorsing it — so any later document that differs from what landed in every owner's inbox during the meeting is provably not the record. Provisional votes (4.
Part 5 — Who runs this: the Independent Chair and the Returning Officer
Given the history, neither the person chairing the meeting nor the person operating the register and tally should have a financial interest in any motion (Above OCM has an interest in the management-contract motion; s 89C(7) reflects the same concern). The meeting is run by two independent officers with separated functions:

The Tribunal appoints an independent chairperson to chair the meeting. The chair conducts the meeting under these procedures: opens and closes voting windows, rules on points of order and objections, states flagged/provisional votes with reasons on the record, announces results, and conducts any on-camera tie-break (4.5). The chair does not operate the workbook and does not decide vote validity alone — validity outcomes are produced by the verification rule and the tally sheet, in view of the scrutineers.
The Tribunal designates (or the parties agree) a returning officer — an independent person (e.g. the administrator if one is appointed, an independent OC manager engaged for the meeting only, or a person nominated by the Tribunal) — who runs Parts 0–4. The returning officer and the chair should be different people, so that conducting and counting remain in different hands.
Each side of the proceeding nominates one scrutineer with the real-time rights in 4.4.
The returning officer's inbox for the AGM is a single dedicated address stated in the notice; all instruments go there; the Inbox log is complete and producible.5) are the one open item; their resolution is published as a **supplementary email within 48 hours** that changes only the flagged lots and references the dispatched workbook, never a reissued one.

### 4.8 After the meeting

Within 14 days (s 81, and s 78(2) if quorum failed): minutes including, as attachments or annexures — the saved Zoom chat log, the `Attendance`, `Proxies`, `PreVotes` (if any), `VoteTally`, and `Flags` sheets, and the per-motion results. Every excluded or provisional vote appears with its lot, reason code, and resolution. The meeting recording is retained by the OC.

---

## Additional Safeguards

- **One dedicated inbox for correspondance** — a single dedicated AGM address stated in the notice that is used only for the 2026 AGM. All emails are forwarded automatically to all parties; for example `2026thevicagm@aboveocm.com.au`
