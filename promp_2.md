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
