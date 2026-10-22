# Exercise 1 - ReadQC
- Author: FGCZ
- Date: 26/04/2024

Steps
1. [Navigate to SUSHI Course Server](#1-navigate-to-sushi-course-server-httpsfgcz-course1bfabricorg)
2. [Select your project ID](#2-enter-your-project-id-in-the-field-or-select-your-project-id-in-the-selection-box-eg-1001-1002--etc)
3. [Select DataSets](#3-select-datasets-to-see-the-list-of-existing-datasets-under-this-sushi-project)
4. [Check DataSet](#4-click-on-the-name-of-the-dataset-to-be-taken-to-that-dataset-page-on-sushi)
5. [Confirm parameters](#5-keep-the-default-options-click-next)
6. [Submit the job](#6-submit-the-job)
7. [Return to the dataset main page](#7-return-to-the-dataset-main-page)
8. [Navigate to the FastQC dataset](#8-navigate-to-the-fastqc-dataset)
9. [Explore the FastQC and MultiQC reports](#9-explore-the-fastqc-and-multiqc-reports)
10. [Questions](#10-questions)

----

### 1. Navigate to SUSHI Course Server: https://fgcz-course1.bfabric.org

### 2. Enter your project ID in the field, or select your project ID in the selection box, *e.g.*, 1001, 1002 ..., *etc*.

<img src="screenshots/screenshot1.png" width="70%">

### 3. Select "DataSets" to see the list of existing datasets under this SUSHI project 

There should be two datasets, one for bulk RNA and another for variant calling

<img src="screenshots/screenshot2.png" width="70%">

### 4. Click on the name of the dataset to be taken to that dataset page on SUSHI 

See the list of apps available for this dataset, select `FastqcApp`

<img src="screenshots/screenshot3.png" width="70%">

### 5. Keep the default options, click "Next" 

<img src="screenshots/screenshot4.png" width="50%">

### 6. Submit the job 

<img src="screenshots/screenshot5.png" width="70%">

### 7. Return to the dataset main page

Wait... Or maybe take a peek at the `jobs` screen? 

### 8. Navigate to the FastQC dataset 

<img src="screenshots/screenshot6.png" width="70%">

### 9. Explore the FastQC and MultiQC reports 

<img src="screenshots/screenshot7.png" width="70%">

### 10. Questions 

### 10. Questions

#### Quantity

- **Question 1**: Which, if any, samples are overrepresented?

<img src="screenshots/total_reads.png" width="70%">

#### Quality

- **Question 2**: Are there differences in base quality scores across or within the samples?

- **Question 3**: Is there any adapter contamination in any of the samples? What might be the cause of this?

- **Question 4**: What would be a good preprocessing strategy for this data?


Next: [Exercise2 Read Mapping and IGV](Exercise_2.md)
