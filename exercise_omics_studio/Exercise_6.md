# Exercise 6 - A tour of Omics-Studio
- Author: FGCZ
- Date: 28/10/2026 (DRAFT, not tested yet)

**Omics-Studio** is the next version of SUSHI, now in internal testing at FGCZ. It runs the
same SUSHI apps (FastQC, STAR, featureCounts, ...) on the same cluster. What is new is the
web page you see and a programming interface (an API), so that scripts and other programs
can use SUSHI too. Exercise 7 uses that interface.

```
 legacy SUSHI web page ─┐
                        ├─▶ SUSHI apps ─▶ job manager ─▶ cluster (SLURM) ─▶ result files (gStore)
 Omics-Studio web page ─┤
 OMAKASE, scripts ──────┘  (through the Omics-Studio API)
```

In this exercise you look around Omics-Studio and compare it with the SUSHI pages you used in
Exercises 1-4. You do **not** submit a job here unless your instructor asks you to.

Steps
1. [Open Omics-Studio and sign in](#1-open-omics-studio-and-sign-in)
2. [Select the project](#2-select-the-project)
3. [Open the dataset list](#3-open-the-dataset-list)
4. [Open the RNA-seq dataset](#4-open-the-rna-seq-dataset)
5. [Look at an app's parameter form](#5-look-at-an-apps-parameter-form)
6. [Open the job list, a job script and a job log](#6-open-the-job-list-a-job-script-and-a-job-log)
7. [Questions](#7-questions)

----

### 1. Open Omics-Studio and sign in

Open `<OMICS_STUDIO_URL>`. Choose one of the two ways to sign in:

- **Sign in with B-Fabric.** A short code appears. The link opens B-Fabric with the code
  already filled in, and you approve there. Your password is typed only at B-Fabric; it never
  reaches Omics-Studio.
- **User name and password** (`<LOGIN_METHOD_FOR_STUDENTS>`).

At B-Fabric there is a box **"allow job submission"**. Leave it **unticked** for this
exercise. Without it you can read everything, but a job submission is refused with
`403 insufficient_scope`. That refusal is the permission check working, not an error.

`[screenshot TODO: sign-in page]`

### 2. Select the project

Choose project `<OS_PROJECT>` from the drop-down at the top, or type its number.

`[screenshot TODO: project drop-down]`

### 3. Open the dataset list

Click **DataSets**. You should see the RNA-seq dataset `<OS_DATASET_NAME>` (mouse, 3 samples),
and also the datasets that OMAKASE produced from it. Their names start with `omakase_`
(Exercise 7 explains them).

`[screenshot TODO: dataset list]`

### 4. Open the RNA-seq dataset

Click the dataset name. You see the sample table and, below it, the apps that can run on this
dataset, grouped by category.

Find the column **Species** in the sample table and note its value. You will need it in
Exercise 7.

`[screenshot TODO: dataset page with Species column and app list]`

### 5. Look at an app's parameter form

Click **FastqcApp**. The parameter form is generated from the app itself, just as in legacy
SUSHI (Exercise 1, step 5). Read it, then go **back** without submitting.

`[screenshot TODO: FastQC parameter form]`

### 6. Open the job list, a job script and a job log

Click **Jobs** for the project. Each row is one job on the cluster: its ID, status, user,
start and end time.

Pick a job that is `COMPLETED` and open:

- its **script**: the exact command that ran on the cluster;
- its **log**: what the program printed while it ran;
- its **dataset**: the result it produced.

`[screenshot TODO: job list, script, log]`

### 7. Questions

- **Question 1**: Compare the app list in step 4 with the list you saw in legacy SUSHI
  (Exercise 1, step 4). Are the same apps offered for an RNA-seq dataset?

- **Question 2**: Open a job script (step 6). Can you find the app, the input dataset and the
  reference genome it used? Why is it useful that this script is kept after the job ends?

- **Question 3**: What is the value of **Species** for this dataset (step 4)? Guess what a
  program could do with this value before it runs STAR.

- **Question 4**: Legacy SUSHI and Omics-Studio run the same apps. What can you do with a
  programming interface (API) that is hard to do by clicking on a web page?

### Optional (only if your instructor says so)

Sign in again with **"allow job submission"** ticked, then submit FastqcApp on the RNA-seq
dataset from Omics-Studio. Compare the steps with Exercise 1.

Next: [Exercise7 OMAKASE: propose, approve, run](Exercise_7.md)
