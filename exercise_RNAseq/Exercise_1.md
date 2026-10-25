# Exercise 1 - ReadQC
- Author: FGCZ
- Date: 26/04/2024, steps rewritten for Omics-Studio 25/10/2026

Steps
1. [Open the course Omics-Studio](#1-open-the-course-omics-studio)
2. [Select your project](#2-select-your-project)
3. [Select DataSets](#3-select-datasets)
4. [Check the dataset](#4-check-the-dataset)
5. [Select FastqcApp](#5-select-fastqcapp)
6. [Keep the default parameters](#6-keep-the-default-parameters)
7. [Submit the job](#7-submit-the-job)
8. [Check the job status](#8-check-the-job-status)
9. [Open the FastQC dataset](#9-open-the-fastqc-dataset)
10. [Questions](#10-questions)

----

### 1. Open the course Omics-Studio

https://fgcz-course2.bfabric.org

No sign-in: the course copy is open to everybody in the course. The header says **Course**.

<img src="screenshots/omics_studio/os01_open.png" width="70%">

### 2. Select your project

Open **Projects** in the header and pick your project, or type its number into the **Project #...** box.
Your project number is in the table on the [course page](../README.md#hands-on-projects) (p1101, p1102, ...).
Each participant has a project of their own: work only in yours.

### 3. Select DataSets

Click **DataSets** in the header. Your project holds one dataset, `NextSeq500_20190507_NS278_o5638_subSampled`:
RNA-seq of human cells, 6 samples, cut down to 100 000 reads a sample so that the jobs finish during the course.

<img src="screenshots/omics_studio/os02_datasets.png" width="70%">

### 4. Check the dataset

Click the name of the dataset. **Dataset Information** describes it; the sample table lists the 6 samples.
The column `Condition [Factor]` gives the groups: 3 `undiff` and 3 `diff`.

<img src="screenshots/omics_studio/os03_samples.png" width="70%">

### 5. Select FastqcApp

**Runnable Applications** lists the apps that can read this dataset, grouped by category.
Select `FastqcApp` in the **QC** row.

<img src="screenshots/omics_studio/os04_apps.png" width="70%">

### 6. Keep the default parameters

The parameters come in a few pages. Keep the defaults, click **Next →** to the last page, then
**Continue to Review →**.

<img src="screenshots/omics_studio/os05_fastqc_form.png" width="50%">

### 7. Submit the job

**Confirm Job Submission** shows the name of the result dataset and the parameters. Click **Confirm & Submit Job**.

<img src="screenshots/omics_studio/os06_fastqc_confirm.png" width="70%">

### 8. Check the job status

Click **Jobs** in the header. The status moves from `SUBMITTED` / `PENDING` (waiting for a free node) to
`RUNNING` and `COMPLETED`. The page asks again every 15 seconds by itself; please do not submit the same job twice.
If it says `FAILED`, open the job and read its log.

<img src="screenshots/omics_studio/os07_jobs.png" width="70%">

Open a job to see the script that ran (**Script Content**) and what it printed (**Execution Log**).
Both are kept after the job has finished.

<img src="screenshots/omics_studio/os08_job_script.png" width="45%"> <img src="screenshots/omics_studio/os09_job_log.png" width="45%">

### 9. Open the FastQC dataset

Back in **DataSets**, a new dataset `Fastqc` has appeared under your RNA-seq dataset: the input is the parent,
the result is the child. Open it. **MultiQC Report** shows all samples together; the per-sample FastQC reports
and every other file are in **Data Folder**.

<img src="screenshots/omics_studio/os10_fastqc_result.png" width="70%">

<img src="screenshots/omics_studio/os11_gstore.png" width="70%">

### 10. Questions

#### Quantity

- **Question 1**: Which, if any, samples are overrepresented?

<img src="screenshots/total_reads.png" width="70%">

#### Quality

- **Question 2**: Are there differences in base quality scores across or within the samples?

- **Question 3**: Is there any adapter contamination in any of the samples? What might be the cause of this?

- **Question 4**: What would be a good preprocessing strategy for this data?


Next: [Exercise2 Read Mapping and IGV](Exercise_2.md)
