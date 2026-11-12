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