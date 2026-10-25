# Exercise 2 - Read Mapping and IGV
- Author: FGCZ
- Date: 26/04/2024, steps rewritten for Omics-Studio 25/10/2026

Steps
1. [Go back to the RNA-seq dataset and select STARApp](#1-go-back-to-the-rna-seq-dataset-and-select-starapp)
2. [Select parameters](#2-select-some-required-parameters-and-preprocessing-options)
3. [Submit the job](#3-submit-the-job)
4. [Download and install IGV](#4-download-and-install-igv-on-your-computer)
5. [Open IGV](#5-open-igv)
6. [Load the BAM files into IGV](#6-load-the-bam-files-into-igv)
7. [Questions](#7-questions)

----

### 1. Go back to the RNA-seq dataset and select STARApp

Open the RNA-seq dataset again (`NextSeq500_20190507_NS278_o5638_subSampled`, the parent), not the FastQC
result: the FastQC result holds reports, not reads, so it has no apps to run.
In **Runnable Applications**, select `STARApp` in the **Map** row.

<img src="screenshots/omics_studio/os12_star_app.png" width="70%">

### 2. Select some required parameters and preprocessing options

You will need a `refBuild` reference genome at the very least. We will use **Homo_sapiens/GENCODE/GRCh38.p13/Annotation/Release_37-2021-05-04**

Ensure the other options such as `paired` and `strandMode` are correct (they are filled in from the dataset but still require double-checking!)

Take a look at the `fastp` preprocessing parameters. Do we want to trim some of the front bases off? Maybe we can change `trim_front1` to 4.

<img src="screenshots/omics_studio/os13_star_form.png" width="70%">

### 3. Submit the job

Click **Next →** through the pages and **Continue to Review →**, check your chosen parameters again, then
**Confirm & Submit Job**. STAR takes longer than FastQC: follow it under **Jobs** and continue with IGV meanwhile.

### 4. Download and install IGV on your computer

URL: https://software.broadinstitute.org/software/igv/download

Should include Java as required.

<img src="screenshots/screenshot11.png" width="70%">

### 5. Open IGV

Download the correct reference, which in our case, is **Human (hg38)**. If you can't see it on the list, click "More".

<img src="screenshots/screenshot12.png" width="50%">

### 6. Load the BAM files into IGV

In IGV, **File → Load from URL**, paste the link of a BAM file and the link of its index (`.bai`).
Load samples `S1_undiff` and `S4_diff`, so we have one from each condition.

Where to get the links: open your STAR result dataset; in the sample table, right-click the file in the
`BAM` column and the one in the `BAI` column and copy the link. The **Data Folder** lists the same files.

Do not use the link in the `IGV` column: it opens a page that asks for an FGCZ sign-in and does not hold course data.

<img src="screenshots/omics_studio/os14_star_files.png" width="70%">

#### **BUT!**

Your BAM files come from only 100 000 reads a sample, so a single gene has few reads on it. It is probably best
to load full BAM files, to see how a real big dataset might look. Use the links below instead!
(They come from all reads of the same samples, mapped to a newer GENCODE release; viewed on hg38 in IGV this
makes no difference.)

S1_undiff:

* https://fgcz-course1.bfabric.org/projects/p6000/STAR_2026-09-29--15-58-50/S1_undiff.bam

* https://fgcz-course1.bfabric.org/projects/p6000/STAR_2026-09-29--15-58-50/S1_undiff.bam.bai

S4_diff

* https://fgcz-course1.bfabric.org/projects/p6000/STAR_2026-09-29--15-58-50/S4_diff.bam

* https://fgcz-course1.bfabric.org/projects/p6000/STAR_2026-09-29--15-58-50/S4_diff.bam.bai

<img src="screenshots/screenshot15.png" width="70%">

<img src="screenshots/screenshot16.png" width="70%">

### 7. Questions

- **Question 1**: What is the gene model? Do our reads map to the right part of the gene? (Hint: Take a look at the annotation track at the bottom, You can search *FST* gene at the box left side to the "Go" button)

<img src="screenshots/FST_mapping.png" width="70%">

- **Question 2**: Is the gene expressed in samples from both conditions?

- **Question 3**: Is there a difference in the read coverage between samples from both conditions? (Hint: Take a look at the number of reads in the coverage track)

- **Question 4**: How many isoforms are identified? (Hint: You can open **Sashimi plot** by right click menu)

<img src="screenshots/sashimi_plot1.png" width="70%">

- **Question 5**: Look at the splice junctions, which isoforms are present almost exclusively in one sample? Which sample?

Next: [Exercise3 Feature Counts](Exercise_3.md)
