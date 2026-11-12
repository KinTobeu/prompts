<!-- ============================================================ -->
<!-- RESPONSE: Station 6 done + Mould test reminder | 2026-11-13  -->
<!-- ============================================================ -->

**All three pass.** ✅✅✅

| Check | Result |
|---|---|
| "Customer impact" divider + `None in this release` | ✅ |
| "No customer impact" divider with 13166 and 11952 under it | ✅ |
| All 4 impact cells end with `(draft – PO to confirm)` | ✅ |
| Check line: `2 in fix version, 2 rows` | ✅ |

**Station 6 is done.** 🏁 Two small tweaks, two clean fixes, and no new bugs. That's what a well-built station looks like: you turn one bolt and only that bolt moves.

**One optional polish:** the technical descriptions run long. 13166's now lists performance testing, rollback, security assessments and more. Joane's are about 3 tight sentences. If you want them shorter, add this to the Rules:
> Keep each description under 60 words.

That's taste, not a bug, so your call.

---

**Scoreboard:** all **6 content stations work** individually. 🏭

**The one thing left before Orchestrator v2 is the mould test.** It decides how the final page gets built: fill the release team's blank page, or create a new one.

**Your task:** run this in a new chat:
> Copy the Confluence page "Release X.X" as a new page titled "Release 1.11 – MOULD TEST" under "Rovo Agent Test-v0.2".
> Keep ALL formatting, panels, layouts and headings exactly as they are.
> Then, in the "Useful Links" table only, set the Release Ticket row to BTFM-13034 as a Jira link. Change nothing else.

Then tell me:
1. Did the layout survive (blue banners, side-by-side)?
2. Was only that one cell filled?
3. Was it published directly, or a preview?

<!-- ============================================================ -->
<!-- END RESPONSE: Station 6 done + Mould test reminder           -->
<!-- ============================================================ -->


<!-- ============================================================ -->
<!-- RESPONSE: Agent 06 tweaks (grouping + draft tags) | 2026-11-13 -->
<!-- ============================================================ -->

Here are the exact edits. Copy and paste them into **Agent 06 – Release Note**.

---

**Tweak 1: Grouping (matches Joane's table)**

**Where:** under Step 3, just after the table header line.

**Add:**
> **Grouping:** split the table into two groups, using a divider row:
> 1. First, a row with **"Customer impact"** in the first cell, then every feature whose Customer Impact is NOT "None".
> 2. Then a row with **"No customer impact"** in the first cell, then every feature whose Customer Impact is "None" or "NA".
>
> If a group is empty, keep the divider row and write `None in this release` under it.

**Why:** Joane's page has that divider row. Without it, the PO has to re-sort the table by hand, which brings back the copy-paste work you're trying to remove.

---

**Tweak 2: The draft tag on every impact cell**

**Where:** in Rules, replace the existing Customer / Colleague Impact line.

**Replace:**
> - **Customer / Colleague Impact:** your best draft + `(draft – PO to confirm)`

**With:**
> - **Customer / Colleague Impact:** your best draft, **always** ending with `(draft – PO to confirm)`. This applies to EVERY impact cell, including ones that say "None".
>   - ✅ `None expected; ensures operational stability (draft – PO to confirm)`
>   - ❌ `None expected; ensures operational stability`

**Why:** in your run, 13166's colleague impact looked like it was missing the tag. An untagged guess looks like a fact, like a used car with no "estimated" sticker on the mileage. The ✅/❌ example stops Rovo skipping it.

---

**Then re-run:**
> Execute "Agent 06 – Release Note" with PROJECT = BTFM, VERSION = 1.11

**What you should see:**
- A **"Customer impact"** divider with `None in this release` under it. (Both features are "None" now that PO Box was pulled.)
- A **"No customer impact"** divider with 11952 and 13166 under it.
- **All 4 impact cells** ending with `(draft – PO to confirm)`

**Your task:** Tell me ✅/❌ for those three.

<!-- ============================================================ -->
<!-- END RESPONSE: Agent 06 tweaks                                -->
<!-- ============================================================ -->


<!-- ============================================================ -->
<!-- RESPONSE: Station 6 – Release Note | 2026-11-12              -->
<!-- ============================================================ -->

**Jackpot.** 🎯 The release holds exactly **2 work items, BTFM-11952 and BTFM-13166**, which are *exactly* the 2 features on Joane's 1.11 Release Note. So:
- ✅ **Fix Version sits on the Features.** That's the link we were missing.
- ✅ The count is a perfect answer key: 2 in Jira = 2 rows on Joane's page.

**Station 6 is unblocked.** It's also the first station where Rovo **writes** instead of copying. That's the *generative* part of Generative AI: turning a messy Feature description into a clean release note, like a mechanic turning scribbled job notes into a proper service report. 🧾

---

**Station 6: Release Note**

**Create `Agent 06 – Release Note`:**

> ⚠️ **ROVO:** Instruction set. Execute, don't summarise.
>
> 🔴 **MODES**
> **A: missing PROJECT or VERSION** → ask as bullets and stop.
> **B: both given** → reply with ONLY the table and the check line.
>
> **Step 1: Find the release.** In PROJECT, find the fix version whose name contains `SR<VERSION>` followed by a space (`SR1.1` must NOT match `SR1.11`). **Copy the name exactly from Jira, never retype it.** None or several → reply `FIX_VERSION: NOT_FOUND` or `MULTIPLE: …` and stop.
>
> **Step 2: Get the features.** JQL: `project = PROJECT AND fixVersion = "<exact name>"`
>
> **Step 3: One row per feature:**
> | Change (Feature) | Team | Business Description | Technical Description | Customer Impact | Colleague Impact | Changes Live? | Status |
>
> **Rules:**
> - **Change:** `<KEY>: <Summary>` as a Jira link
> - **Team:** the WorkTeam field, copied exactly
> - **Business Description:** start with `<KEY> delivers…`, then 2–4 plain-English sentences on the **benefit**, based on the feature description. **Skip anything marked as pulled, removed or struck through.**
> - **Technical Description:** start with `<KEY> implements…`, then 2–4 sentences summarising the **child items**.
> - **Customer / Colleague Impact:** your best draft + `(draft – PO to confirm)`
> - **Changes Live?:** `TBC – PO`
> - **Status:** Jira status
> - **Never invent** systems, numbers or dates that aren't in Jira.
>
> **Check line:** `Features: N in fix version, N rows in table` (they must match).

**Run it:**
> Execute "Agent 06 – Release Note" with PROJECT = BTFM, VERSION = 1.11

**Compare with Joane's page:**
1. 2 rows, 11952 and 13166? ✅/❌
2. Does 13166 **skip the PO Box item** (it was struck through, "pulled from this release")?
3. ⚠️ **Team trap:** Joane's page says *"Annuities Team 4"*, but Jira's WorkTeam says *"Annuity Quote and Apply 1"*. Which does Rovo show? That's a **naming mismatch to ask the PO about**, not a Rovo bug.

**Your task:** Answer 1–3, and tell me how close the descriptions read to Joane's.

<!-- ============================================================ -->
<!-- END RESPONSE: Station 6 – Release Note                       -->
<!-- ============================================================ -->


<!-- ============================================================ -->
<!-- RESPONSE: Edit test result (B) + Relay design + Mould test | 2026-11-12 -->
<!-- ============================================================ -->

It's **B.** 🔍 Rovo *can* edit an existing page, but only as a **preview**. A human has to accept it and publish.

That's a handbrake built into the car, not a broken engine. 🅿️ For a release doc it's actually healthy: nothing changes without a person signing it off.

**Two findings from this:**
1. **Fixes after the page exists need a human click.** So the QC inspector should run **before** the page is built, not after. Inspect the parts before the car leaves the factory.
2. **Edited values come in as plain text, not Jira links.** Any fix instruction has to say "as a Jira link".

**The v2 design is now clear: a relay race, not one tired driver.** 🏃‍♂️➡️🏃‍♀️
- **Run 1:** stations 1–5, then QC on their outputs, giving one verified block of data.
- **Run 2:** build the page from that verified block, using Joane's template as the mould.

I've added these findings to the tracker.

---

**Next step: the mould test** (still needed, because Run 2 depends on it)

In a new chat:
> Copy the Confluence page "Release X.X" as a new page titled "Release 1.11 – MOULD TEST" under "Rovo Agent Test-v0.2".
> Keep ALL formatting, panels, layouts and headings exactly as they are.
> Then, in the "Useful Links" table only, set the Release Ticket row to BTFM-13034 as a Jira link. Change nothing else.

**Your task:** Tell me:
1. Did the copy keep Joane's layout (blue banners, side-by-side)?
2. Was only that one cell filled?
3. Did it publish directly, or come back as a preview?

<!-- ============================================================ -->
<!-- END RESPONSE: Edit test result (B) + Relay design + Mould test -->
<!-- ============================================================ -->


<!-- ============================================================ -->
<!-- RESPONSE: QC didn't edit page + One-cell edit test | 2026-11-12 -->
<!-- ============================================================ -->

Confirmed: **the inspector only wrote a report. The page wasn't touched.** EoTR and IRR still say NOT FOUND, and the progress line is still duplicated. 📋

That raises a bigger question than the inspector itself: **can Rovo edit an existing page at all?** So far it has *created* pages every time, but never *changed* one. The "Insert into page" button suggests editing may need a human click.

That one answer changes the factory design:
- **If Rovo can edit:** keep the QC inspector at the end and have it fix the page in place.
- **If Rovo can't edit:** move the inspector **before** the paint shop. QC checks the station outputs first, and only then is the page created. You can't repaint a car once it's left the factory, so inspect it before it goes out the door. 🏭➡️🚗

---

**Step: the one-cell edit test**

In a new chat, on the draft page:
> Edit the Confluence page "Release 1.11 – DRAFT (Rovo)". In the Useful Links table, change the EoTR / Test Plan value from "NOT FOUND – please check" to "BTFM-13054". Change nothing else. Save the page.

**Your task:** Tell me which happened:
- **A)** The page actually changed by itself.
- **B)** It gave you text or an "Insert into page" button, and you had to click.
- **C)** It refused, or said it can't edit.

<!-- ============================================================ -->
<!-- END RESPONSE: QC didn't edit page + One-cell edit test       -->
<!-- ============================================================ -->


<!-- ============================================================ -->
<!-- RESPONSE: Alignment issues + Mould test | 2026-11-12         -->
<!-- ============================================================ -->

Good eye. 👀 Yes, the bodywork doesn't match Joane's car:

| Joane's doc | Rovo's draft |
|---|---|
| Headings in **blue banner panels** with ℹ️ and underline | Plain headings |
| Exact names, e.g. *"List of Components being changed (Version Control):"* | Shortened to *"Components"* |
| **Side by side:** progress pie on the left, Useful Links on the right | Stacked vertically |
| All tables the same width | Route to Live table is **wider and shifted left** |
| Progress shown as a pie chart | A text panel and a line |

**Why:** we told Rovo *what* to put in, but never *what it should look like*. So it designed its own layout, like a factory with no body mould where every car comes out a slightly different shape.

**The fix: use a mould, not a description.** 🏭 Your space already has a template page (I saw **"Release X.X"** in your sidebar). Instead of Rovo building a page from scratch, have it **copy the template and fill in the blanks**. The layout, banners, side-by-side columns and headings then come for free.

---

**Step: test the mould (one small test first)**

Don't change the orchestrator yet. First check whether Rovo can do this at all:

> Copy the Confluence page "Release X.X" as a new page titled "Release 1.11 – MOULD TEST" under "Rovo Agent Test-v0.2".
> Keep ALL formatting, panels, layouts and headings exactly as they are.
> Then, in the "Useful Links" table only, fill the Release Ticket row with BTFM-13034. Change nothing else.

**Your task:** Tell me:
1. Did it create a copy with Joane's layout intact (banners, side-by-side)?
2. Did it edit **only** that one cell?

If yes, the orchestrator becomes "copy mould → fill each section". If no, plan B is to spell out the exact headings and panel styles. I'll also add an **alignment check** to the QC inspector either way.

<!-- ============================================================ -->
<!-- END RESPONSE: Alignment issues + Mould test                  -->
<!-- ============================================================ -->


<!-- ============================================================ -->
<!-- RESPONSE: Orchestrator results + Station 7 QC Inspector | 2026-11-12 -->
<!-- ============================================================ -->

🎉 **Huge milestone: the orchestrator built a full release doc in one go.** Page created, all 9 sections, in the right order. That's the whole factory working without Rovo Studio.

Now the inspection. Compare it with the stations' solo runs:

| Section | Solo run | In the orchestrator | |
|---|---|---|---|
| Useful Links: EoTR | BTFM-13054 | **NOT FOUND** | ❌ Regression |
| Useful Links: IRR | BTFM-13040 | **NOT FOUND** | ❌ Regression |
| Route to Live: Planned Start | Blank | **2026-11-03** on every row | ❌ Suspicious |
| Progress | One line | Shown **twice** | 🟡 Cosmetic |
| Everything else | | Matches | ✅ |

**What happened: the tired driver.** 🚗💤 Solo, each station gets Rovo's full attention. In one long run, Rovo does five jobs in a row, and quality drops: it skips the subtask check (Links) and fills empty columns with the nearest date it saw. **3 Nov is the "Updated" date**, not a planned start. That's an invented value, exactly what the rules forbade.

**This is why the QC loop exists.** A long assembly line *will* drop bolts. You need an inspector at the end.

---

**Next step: Station 7, the QC inspector** 🔍

**Create `Agent 07 – QC Inspector`:**

> ⚠️ **ROVO:** Instruction set. Execute, don't summarise.
>
> 🔴 **MODES**
> **A: no PAGE or RELEASE_TICKET** → ask for both as bullets and stop.
> **B: both given** → run the checks and reply with ONLY the QC report.
>
> **Checks (re-read Jira for each one; never trust the page):**
> 1. **Useful Links:** for every `NOT FOUND` row, search the subtasks of RELEASE_TICKET again by summary (EoTR, IRR, SOE, MVD). If found → **FIX**.
> 2. **Dates:** for each Route-to-Live row, compare Planned Start/End with the Jira fields. If the Jira field is empty but the page has a date → **FIX** (blank it).
> 3. **Count:** table rows = `parent = RELEASE_TICKET` count = "Total N"? If not → **FAIL**.
> 4. **No invented data:** Components must still say "TBC – EL to provide".
> 5. **Duplicates:** the progress line appears only once.
>
> **Then:** apply all FIXes to PAGE.
>
> **Reply format:**
> `QC: ✅ PASS` or `QC: ⚠️ FIXED <n>` or `QC: ❌ FAIL`
> Then one line per check: `1 ✅ / 🔧 fixed: … / ❌ …`

**Run it on your draft:**
> Execute "Agent 07 – QC Inspector" with PAGE = "Release 1.11 – DRAFT (Rovo)", RELEASE_TICKET = BTFM-13034

**Your task:** Does it catch and fix all 3 problems (EoTR/IRR, the fake dates, the duplicate progress line)? Also, what did the orchestrator's **run log** say? Did it admit anything?

<!-- ============================================================ -->
<!-- END RESPONSE: Orchestrator results + Station 7 QC Inspector  -->
<!-- ============================================================ -->


<!-- ============================================================ -->
<!-- RESPONSE: Orchestrator v1 | 2026-11-12                       -->
<!-- ============================================================ -->

**All 4 sections came out right.** ✅ Section 2 stayed empty, with no invented hashes, and the "PO to confirm" lines are honest. Station 5 is done. I've updated the tracker.

**Five stations are built.** 🏭 Station 6 (Features) is blocked until you find out how features link to a release. So rather than wait, let's do the exciting part now.

---

**Step: Orchestrator v1, the factory manager** 🧑‍🏭

The manager doesn't build anything. It **calls each station in order and passes the key along**, like a pit crew chief shouting "tyres, fuel, go!"

This is also the **biggest limit test yet**: can Rovo chain five instruction pages in one run?

**Create `Release Doc Orchestrator`:**

> ⚠️ **ROVO:** Instruction set. Execute, don't summarise.
>
> 🔴 **MODES**
> **A: missing PROJECT, VERSION or PARENT_PAGE** → ask for them as a bulleted list and stop.
> **B: all given** → run the steps below.
>
> **Steps:**
> 1. Execute page "Agent 01 – Release Ticket Finder" with PROJECT, VERSION and LABEL.
>    If the result is NOT_FOUND, MULTIPLE or PROJECT_NOT_FOUND → **stop** and show that line.
> 2. Using the RELEASE_TICKET from step 1, execute these pages in order:
>    - "Agent 02 – Useful Links"
>    - "Agent 03 – Route to Live Tasks"
>    - "Agent 04 – Post Live Support"
>    - "Agent 05 – Placeholders"
> 3. Create a Confluence page titled `Release VERSION – DRAFT (Rovo)` under PARENT_PAGE, with sections in this order:
>    1 Release Note → write `Coming soon – Station 6`
>    2 Components · 3 Dependencies · 4 Route to Live Tasks · 5 Progress · 6 Useful Links · 7 Risks · 8 Incidents · 9 Post-live Support
> 4. Reply with **only**:
>    - The page link
>    - A run log: `Agent 01 ✅/❌ · 02 ✅/❌ · 03 ✅/❌ · 04 ✅/❌ · 05 ✅/❌`

**Why the run log?** It's the dashboard warning lights. 🚨 If a station fails silently, you'll see which one.

**Run it:**
> Execute "Release Doc Orchestrator" with PROJECT = BTFM, VERSION = 1.11, LABEL = RetirementReleaseTicket, PARENT_PAGE = "Rovo Agent Test-v0.2"

**Your task:** Tell me:
1. Did it create the page?
2. What does the run log show?
3. Did all 9 sections land in the right order?

<!-- ============================================================ -->
<!-- END RESPONSE: Orchestrator v1                                -->
<!-- ============================================================ -->


<!-- ============================================================ -->
<!-- RESPONSE: Station 5 – Placeholders | 2026-11-12              -->
<!-- ============================================================ -->

**4 out of 4, first try.** 🏁 That's the skeleton paying off: you're no longer fixing format bugs, just checking results.

---

**Station 5: The leftovers (sections 2, 3, 7, 8)**

**Lesson first: not everything needs a brain.** 🧠 A car's chassis comes off a mould; it doesn't need a robot to *think*. Two of these sections are just empty tables for humans. Only two need a quick Jira check.

| Section | Smart or fixed? |
|---|---|
| 2 Components / versions | 🔩 Fixed: blank table, "TBC – EL to provide" |
| 3 Key dependencies | 🧠 Check the release ticket's **linked issues** (blocks / depends on) |
| 7 Risks | 🧠 Check linked issues of type **Risk** |
| 8 Incidents | 🔩 Fixed: blank table, "Post-live – fill after go-live" |

**Create `Agent 05 – Placeholders`:**

> ⚠️ **ROVO:** Instruction set. Execute, don't summarise.
>
> 🔴 **MODES**
> **A: no RELEASE_TICKET** → "I need: • RELEASE_TICKET (e.g. BTFM-13034)"
> **B: given** → reply with ONLY the 4 sections below.
>
> **Section 2: Components:** table `Component | Team | Repository | New Version | Previous Version | Comments` with one row: `TBC – EL to provide` in every cell. **Never fill in version numbers or hashes.**
>
> **Section 3: Dependencies:** check RELEASE_TICKET's linked issues with link types "blocks", "is blocked by" or "depends on".
> - Found → table `Ref | Description | Team | Status`
> - None → `No key dependencies identified – PO to confirm`
>
> **Section 7: Risks:** check linked issues of type "Risk".
> - Found → table `Risk Ref | Summary | Severity | Status`
> - None → `No risks raised – PO to confirm`
>
> **Section 8: Incidents:** table `Incident No. | Priority | Summary | Owner | Status` with one row: `Post-live – complete after go-live`

**Answer key (1.11):** sections 2, 3, 7 and 8 should all come out as "TBC / none / post-live", since Joane's were empty or manual.

> Execute "Agent 05 – Placeholders" with RELEASE_TICKET = BTFM-13034

**Your task:** Did all 4 sections come out, and did section 2 stay **empty**, with no invented hashes?

<!-- ============================================================ -->
<!-- END RESPONSE: Station 5                                      -->
<!-- ============================================================ -->


<!-- ============================================================ -->
<!-- RESPONSE: Station 4 – Post Live Support | 2026-11-12         -->
<!-- ============================================================ -->

Done. Rejected tasks **stay in for now**. I've started a tracker doc in your **Mater AI** project (`release-agent-tracker.md`) with the station status, this PO question, and the 3 other open checks, so nothing gets lost.

---

**Station 4: Post-live support** 🛠️

A short one: four fields, mostly inferred.

**Create `Agent 04 – Post Live Support`:**

> ⚠️ **ROVO:** Instruction set. Execute, don't summarise.
>
> 🔴 **MODES**
> **A: no RELEASE_TICKET** → reply: "I need: • RELEASE_TICKET (e.g. BTFM-13034)"
> **B: RELEASE_TICKET given** → reply with ONLY this table:
>
> | Field | Value |
> |---|---|
> | Live support required | |
> | Duration | |
> | Resource engagement | |
> | Status | |
>
> **Rules:**
> 1. Look for a subtask of RELEASE_TICKET whose summary contains "Post-Live" or "Early Life Support".
> 2. **Live support required:** found → `YES (<KEY>)`; not found → `NO`
> 3. **Duration:** if the ticket or subtask states one, copy it. Otherwise `2 WEEKS (default)`
> 4. **Resource engagement:** always `TBC – RM to confirm`
> 5. **Status:** the status of the subtask from rule 1, or blank if none.

**Why the "(default)" tag?** It tells the PO this value is a factory setting, not something Rovo actually found. It's like a car showing "est. range" instead of a real fuel reading.

**Answer key (1.11):** YES · 2 WEEKS · (blank) · (blank).
Expected from your agent: `YES (BTFM-13063)` · `2 WEEKS (default)` · `TBC – RM to confirm` · `In Progress`

> Execute "Agent 04 – Post Live Support" with RELEASE_TICKET = BTFM-13034

**Your task:** Does it find BTFM-13063, and does it tag the duration as default?

<!-- ============================================================ -->
<!-- END RESPONSE: Station 4                                      -->
<!-- ============================================================ -->


**TBC ✅. Station 2 is done.** 🏁

You now have two working parts that bolt together:
- **Station 1:** VERSION → `BTFM-13034`
- **Station 2:** `BTFM-13034` → the Useful Links table

---

**Station 3: Tasks + Progress** 📋

You built a rough version of this on day one. Now rebuild it with the proper skeleton.

**Create `Agent 03 – Route to Live Tasks`:**

> ⚠️ **ROVO:** Instruction set. Execute, don't summarise.
>
> 🔴 **MODES**
> **A: no RELEASE_TICKET** → reply: "I need: • RELEASE_TICKET (e.g. BTFM-13034)"
> **B: RELEASE_TICKET given** → reply with ONLY the two parts below.
>
> **Steps:**
> 1. Run JQL: `parent = RELEASE_TICKET ORDER BY key DESC`
> 2. Include **ALL** results. Do not skip, sample or shorten.
>
> **Part 1: table**
> | Key | Summary | Assignee | Status | Planned Start | Planned End |
> Empty field → leave blank. Never invent dates.
>
> **Part 2: progress line, one line only:**
> `Progress: X Done, Y In Progress, Z Other (Total N)`
>
> **Self-check:** Total N must equal the number of rows in the table. If not, write `⚠️ COUNT MISMATCH` instead.

**The self-check is your first mini quality-control loop.** 🔁 Day one's bug was that Rovo only showed 8 of about 30 subtasks. Now it has to count its own work, like a mechanic counting the bolts back into the tray.

**Answer key:** Joane's 1.11 pie showed **Done = 25, In Progress = 1** (as of 3 Nov, so it may have moved since).

> Execute "Agent 03 – Route to Live Tasks" with RELEASE_TICKET = BTFM-13034

**Your task:** Is the Total about 26? Is any key skipped? Does it match the Jira count for `parent = BTFM-13034`?







**6 out of 8 exact, and zero made-up values.** 🎯 That second part matters most.

| Item | Expected | Got | |
|---|---|---|---|
| Release Ticket | 13034 | 13034 | ✅ |
| MVD | N/A | NOT FOUND | 🟡 |
| EoTR | 13054 | 13054 | ✅ |
| Solution Record | N/A | NOT FOUND | 🟡 |
| IRR | 13040 | 13040 (Governance + IRR subtask) | ✅ |
| SOE | 13044 | 13044 | ✅ |
| Change Record | CHG2971779 | CHG2971779 | ✅ |
| SI Record | N/A | N/A | ✅ |

**The two 🟡s are safe misses, not errors.** Rovo said "I don't know" instead of guessing. A mechanic saying "I can't see the part number" is far better than one who makes one up.

- **MVD:** it isn't on the ticket anywhere, so NOT FOUND is honest. Joane filled it in by hand. ✔️ Leave as is.
- **Solution Record:** remember Station 1's output? The ticket says **"TBC"**. Rovo saw TBC and called it NOT FOUND, which loses information.

**Small fix: add to Value rules:**
> - If the ticket gives its own value (e.g. "TBC", "Not Required"), **copy it exactly**.

**Your task:** Re-run it. The Solution Record should now say **TBC**.

Once that passes, Station 2 is done and you've got **two parts that bolt together**: Station 1 gives you the key, Station 2 uses it. 🔩










Station 1 is done. 🏁 The engine block is in.

**What you learned building it** (these carry over to every station):
1. **Banner:** "execute, don't summarise"
2. **Modes:** each output rule says *when* it applies
3. **Examples:** show a ✅ and a ❌
4. **No guessing:** exact inputs only, with clear "not found" answers

Use these four as the **skeleton for every agent page** from now on.

---

**Station 2: Links agent** 🔗

**Input:** a release ticket key, which is Station 1's output. That's the first link in your assembly line.
**Output:** the 8-row Useful Links table.

**Create `Agent 02 – Useful Links` and add:**

> ⚠️ **ROVO:** Instruction set. Execute, don't summarise.
>
> 🔴 **MODES**
> **A: no RELEASE_TICKET given** → reply: "I need: • RELEASE_TICKET (e.g. BTFM-13034)"
> **B: RELEASE_TICKET given** → reply with ONLY the table below.
>
> **Steps:**
> 1. Open RELEASE_TICKET. Read its **description links**.
> 2. Read its **subtasks**, and match items by summary (e.g. "SOE", "IRR", "EoTR").
> 3. Fill this table, keeping exactly these 8 rows in this order:
>
> | Item | Link |
> |---|---|
> | Release Ticket | |
> | MVD | |
> | EoTR / Test Plan | |
> | Solution Record | |
> | IRR | |
> | SOE | |
> | Change Record | |
> | SI Record | |
>
> **Value rules:**
> - Found → the key or link
> - Ticket says "Not Required" → `N/A`
> - Can't find it → `NOT FOUND – please check`
> - Never invent a key or number.

**Why separate N/A from NOT FOUND?** N/A means "this car has no sunroof." NOT FOUND means "I couldn't see whether it has one." The QC station needs to tell those apart.

**Test against your answer key:**
> Execute "Agent 02 – Useful Links" with RELEASE_TICKET = BTFM-13034

Compare the result with Joane's 1.11 page: 13034, N/A, 13054, N/A, 13040, 13044, CHG2971779, N/A.

**Your task:** How many of the 8 rows match? ✅/❌ per row.





















add to Step 1:
Use PROJECT exactly as the user typed it. Never correct or guess a project key.
If the project does not exist, reply: RELEASE_TICKET: PROJECT_NOT




**Station 1: Release Ticket Finder** 🔧

Give each station **its own page** so you can test and fix it alone, like a part on a workbench before it goes in the car.

**1. Create a page called `Agent 01 – Release Ticket Finder` and paste this:**

> **Purpose:** Find the release ticket for a given VERSION.
>
> **When asked "find release ticket for VERSION":**
> 1. Run this JQL, replacing VERSION:
>    `project = BTFM AND labels = RetirementReleaseTicket AND summary ~ "\"Release VERSION\""`
> 2. Check each result's title. Keep it **only** if it contains "Release VERSION" followed by a space or the end of the title. "Release 1.1" must NOT match "Release 1.11".
> 3. Reply with **exactly one line**, nothing else:
>    - one match → `RELEASE_TICKET: <KEY>`
>    - no match → `RELEASE_TICKET: NOT_FOUND`
>    - more than one → `RELEASE_TICKET: MULTIPLE: <KEY1>, <KEY2>`

**Why the strict one-line output?** Later the orchestrator will read this answer and pass it to the next station. It's like a standard bolt size: every station has to fit the next one.

**2. Run these 4 test drives** (start a new Rovo chat for each):
> Read "Agent 01 – Release Ticket Finder" and find release ticket for **X**

| Test | X | Expected |
|---|---|---|
| A | 1.11 | `BTFM-13034` (from the answer key) |
| B | 1.2 | `BTFM-11420` |
| C | 9.99 | `NOT_FOUND` |
| D | 1.1 | Must **not** say 13034. This is the trap. |

**Your task:** Send me a ✅ or ❌ for each test. If A fails, check whether BTFM-13034 actually has the `RetirementReleaseTicket` label.


___________________updated________________________




Yes, good thinking. 💡 Right now the seat is fixed for one driver (BTFM). Let's make it **adjustable for any driver**.

**Update `Agent 01` to this:**

> **Purpose:** Find the release ticket for any team.
>
> **Inputs needed:**
> - PROJECT: Jira project key (e.g. BTFM)
> - VERSION: release version (e.g. 1.11)
> - LABEL: release ticket label (optional, e.g. RetirementReleaseTicket)
>
> **Step 0:** If PROJECT or VERSION is missing, **ask the user for it** and stop. Do not guess.
>
> **Step 1:** Run this JQL:
> `project = PROJECT AND summary ~ "\"Release VERSION\""`
> If LABEL is given, add: `AND labels = LABEL`
>
> **Step 2:** Keep only titles containing "Release VERSION" followed by a space or the end of the title ("1.1" must NOT match "1.11").
>
> **Step 3:** Reply with exactly one line:
> - `RELEASE_TICKET: <KEY>`
> - `RELEASE_TICKET: NOT_FOUND`
> - `RELEASE_TICKET: MULTIPLE: <KEY1>, <KEY2>`

**Test drives:**

| Test | Ask Rovo | Expected |
|---|---|---|
| A | "…find release ticket for project BTFM, version 1.11, label RetirementReleaseTicket" | `BTFM-13034` |
| B | "…find release ticket for project BTFM, version 1.2" (no label) | `BTFM-11420` |
| C | "…find release ticket for version 1.11" (**no project**) | It should **ask you** for the project |
| D | "…project BTFM, version 1.1" | Must **not** return 13034 |

Test C is the new one. It checks whether Rovo asks or guesses. A good agent stops and asks for the address instead of driving somewhere random.

**Your task:** Send me ✅ or ❌ for A–D.










@@@@

One line ✅. Station 1 is basically working.

What you've spotted is a classic problem: **rule bleed**. 🩸 You wrote "no bullet points" for the *answer*, but Rovo applied it to *everything*, including the "please give me the project" question.

It's like telling a driver "no honking", and he stops using the indicators too. Rules apply to the whole page unless you say **when** they apply.

**Fix: give it two modes, each with its own rule**

Replace the OUTPUT RULE at the top with:

> 🔴 **OUTPUT RULES: pick ONE mode:**
>
> **MODE A: inputs missing** (no PROJECT or no VERSION)
> Ask for them using this exact format:
> > I need these inputs:
> > • PROJECT – Jira project key (e.g. BTFM)
> > • VERSION – release version (e.g. 1.11)
> > • LABEL – optional (e.g. RetirementReleaseTicket)
>
> **MODE B: all inputs given**
> Your ENTIRE reply must be ONE line, e.g. `RELEASE_TICKET: BTFM-13034`

Keep the ✅/❌ examples at the bottom. They belong to Mode B.

**Your task:** Run two tests, each in a new chat:
1. **Test C** (no inputs) → should show the **bulleted question**
2. **Test A** (all inputs) → should give **one line**

Send me ✅ or ❌ for both. If they pass, run **B** and **D** too and Station 1 is done. 🏁

<!-- ============================================================ -->
<!-- RESPONSE: Station 3 – Route to Live Tasks | 2026-11-12       -->
<!-- ============================================================ -->

**TBC ✅. Station 2 is done.** 🏁

You now have two working parts that bolt together:
- **Station 1:** VERSION → `BTFM-13034`
- **Station 2:** `BTFM-13034` → the Useful Links table

---

**Station 3: Tasks + Progress** 📋

You built a rough version of this on day one. Now rebuild it with the proper skeleton.

**Create `Agent 03 – Route to Live Tasks`:**

> ⚠️ **ROVO:** Instruction set. Execute, don't summarise.
>
> 🔴 **MODES**
> **A: no RELEASE_TICKET** → reply: "I need: • RELEASE_TICKET (e.g. BTFM-13034)"
> **B: RELEASE_TICKET given** → reply with ONLY the two parts below.
>
> **Steps:**
> 1. Run JQL: `parent = RELEASE_TICKET ORDER BY key DESC`
> 2. Include **ALL** results. Do not skip, sample or shorten.
>
> **Part 1: table**
> | Key | Summary | Assignee | Status | Planned Start | Planned End |
> Empty field → leave blank. Never invent dates.
>
> **Part 2: progress line, one line only:**
> `Progress: X Done, Y In Progress, Z Other (Total N)`
>
> **Self-check:** Total N must equal the number of rows in the table. If not, write `⚠️ COUNT MISMATCH` instead.

**The self-check is your first mini quality-control loop.** 🔁 Day one's bug was that Rovo only showed 8 of about 30 subtasks. Now it has to count its own work, like a mechanic counting the bolts back into the tray.

**Answer key:** Joane's 1.11 pie showed **Done = 25, In Progress = 1** (as of 3 Nov, so it may have moved since).

> Execute "Agent 03 – Route to Live Tasks" with RELEASE_TICKET = BTFM-13034

**Your task:** Is the Total about 26? Is any key skipped? Does it match the Jira count for `parent = BTFM-13034`?
