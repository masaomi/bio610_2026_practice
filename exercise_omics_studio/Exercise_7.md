# Exercise 7 - OMAKASE: propose, approve, run
- Author: FGCZ
- Date: 28/10/2026 (DRAFT, not tested yet)

In Exercises 1-4 you started each app by hand, one after another: FastQC, then STAR, then
featureCounts, then the differential expression test. **OMAKASE** is a prototype that does the
first part of this for you. When a sequencing order is finished, it **proposes** a chain of
existing SUSHI apps (a **recipe**). A person reads the proposal and **approves** it. Then
OMAKASE **runs** the whole chain to the end, or stops and says why.

OMAKASE = **O**mics **M**etadata **A**utomated **K**nowledge-based **A**nalysis
**S**uggestion & **E**xecution (the name is provisional). Its rule:

> **Rules decide, AI assists, humans release.**

```
 order finished ─▶ find its dataset ─▶ recipe ─▶ a person approves ─▶ run the chain ─▶ notify
     (works)           (works)         (named      (works: nothing     (works: parallel   (not yet
                                        by a        runs before         steps, stops on    for users)
                                        person)     this)               failure)
```

The recipe in this exercise (`<RECIPE_ID>`, e.g. `rnaseq_meeting_shape`):

```
 FastQC       ┐
 FastQ Screen ┤  start together
 STAR         ┘ ──▶ featureCounts  (waits for STAR only)
```

STAR's reference genome is not typed by anyone. OMAKASE reads the **Species** column of the
dataset (Exercise 6, Question 3) and picks the reference that FGCZ keeps for that species.

### Work in groups

A proposal can be made **only once** for the same order, dataset and recipe version. That is
deliberate: it stops the same analysis being started twice by mistake. So each group gets
its own combination:

**Group** | **Order** | **Dataset** | **Recipe**
----------|-----------|-------------|-----------
A | `<ORDER_ID>` | `<DATASET_A>` | `<RECIPE_1>`
B | `<ORDER_ID>` | `<DATASET_A>` | `<RECIPE_2>`
C | `<ORDER_ID>` | `<DATASET_B>` | `<RECIPE_1>`
D | `<ORDER_ID>` | `<DATASET_B>` | `<RECIPE_2>`

Steps
1. [Open the OMAKASE panel](#1-open-the-omakase-panel)
2. [Find the order](#2-find-the-order)
3. [Try the automatic choice](#3-try-the-automatic-choice)
4. [Propose your group's recipe](#4-propose-your-groups-recipe)
5. [Read the proposal](#5-read-the-proposal)
6. [Approve](#6-approve)
7. [Run the chain](#7-run-the-chain)
8. [Watch it in Omics-Studio](#8-watch-it-in-omics-studio)
9. [Questions](#9-questions)

----

### 1. Open the OMAKASE panel

Open the link your instructor gives you (`<OMAKASE_PANEL_URL>` with your personal key). Your
browser remembers it afterwards. Do not share the link: whoever holds it is recorded as the
person who approved.

The **OMAKASE** tab shows `signed in as <you>`.

`[screenshot TODO: panel, OMAKASE tab]`

### 2. Find the order

Under **"Orders with an order record"**, find order `<ORDER_ID>`.

`[screenshot TODO: order list]`

### 3. Try the automatic choice

On the order, leave the recipe as **automatic** and press **Propose**. OMAKASE **declines**:
no recipe matches this order. Keep this in mind for Question 1.

### 4. Propose your group's recipe

Choose your group's dataset and recipe from the table above, and press **Propose**. A
proposal card appears under **"Proposals awaiting a decision"**, with a number (the
*candidate* number). Note it.

If the panel says `candidate N already exists`, another group used your combination. Tell
your instructor.

### 5. Read the proposal

Open the card. Read:

- the steps and which step waits for which;
- the parameters of each step;
- the **reference genome**, and the Species value it was chosen from.

Nothing has been submitted to the cluster yet.

`[screenshot TODO: proposal card]`

### 6. Approve

Discuss in your group: is this proposal right for this dataset? If yes, press **Approve**.
Your name is recorded as the approver.

Do **not** press **Dry run** (a known problem in the prototype: it can leave the proposal in
a wrong state).

### 7. Run the chain

Press **Run chain**. If the page asks you to confirm the dataset and the project, read them
and confirm.

The chain takes about `<RUN_MINUTES>` minutes (the recipe above took between 6.5 and 11
minutes in earlier tests on two mouse samples).

### 8. Watch it in Omics-Studio

While it runs, open Omics-Studio (Exercise 6) and the **Jobs** page of project
`<OS_PROJECT>`. Watch which jobs start first and which one waits.

When the panel shows **DONE**, open **DataSets**. The new datasets are named
`omakase_c<candidate>_s<step>_<App>`, for example `omakase_c3_s4_FeatureCountsApp`. Open
one and read its comment: it names the approver.

`[screenshot TODO: jobs page during the run; output datasets]`

### 9. Questions

- **Question 1 (step 3)**: OMAKASE declined instead of guessing a recipe. At FGCZ, choosing
  the most common chain from past orders of the same kind would have been right for only
  about one order in five (~20 %). Why is "no proposal" better than a wrong proposal?

- **Question 2 (step 5)**: Which reference genome was chosen, and from which column? What
  do you think OMAKASE does when Species is `NA` or contains two species?

- **Question 3 (step 8)**: Which jobs started at the same time? Why does featureCounts wait
  for STAR but not for FastQC?

- **Question 4 (step 6)**: Who is recorded as the approver, and where can you see it? Why
  does OMAKASE submit nothing before a person approves?

- **Question 5**: If STAR had failed, what should happen to featureCounts? (Hint: think about
  what featureCounts needs as input.)

- **Question 6**: The recipe stops at featureCounts. There is no differential expression
  step like Exercise 4. In Exercise 4, which choice did you have to make yourself? Why is
  that choice hard to automate?

- **Question 7**: Compare Exercises 1-3 (you started each app) with this exercise (a recipe
  and a recorded approval). What does each way record about **how** the result was made?

### If the panel is not available

Your instructor runs steps 2-7 on the screen. Answer the questions from what you see, and
follow the jobs in Omics-Studio (step 8) if you can sign in.
