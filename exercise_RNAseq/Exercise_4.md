# Exercise 4 - Differential Expression
- Author: FGCZ
- Date: 26/04/2024

Steps
1. [Execute EdgeRApp](#1-from-the-featurecounts-dataset-on-sushi-select-the-edgerapp)
2. [Open the Static Report](#2-once-edger-is-finished-open-the-static-report-of-the-results)
3. [Explore the Static Report](#3-explore-the-static-report)

----

### 1. From the FeatureCounts dataset on SUSHI, select the `EdgeRApp` 

Run the differential gene expression test as `diff` vs `undiff`, so **sampleGroup = diff** and **refGroup = undiff**. 

Leave all other options the same. This will compare differentiated vs undifferentiated cells. 

<img src="screenshots/screenshot22.png" width="50%">

<img src="screenshots/screenshot23.png" width="70%">

### 2. Once edgeR is finished, open the Static Report of the results 

<img src="screenshots/screenshot24.png" width="70%">

### 3. Explore the Static Report 

#### Results summary tab

- **Question 1**: How many genes have p-value < 0.01 and a log2 fold change of >= +/- 2? 

- **Question 2**: Look at genes with log2 fold change >= 1, what happens to the number of DEGs with decreasing p-value? 

#### Inspection of signficant genes tab

- **Question 3**: What does the volcano plot show us in terms of distribution of our DEGs between our two conditions? 

- **Question 4**: What are the top candidate genes, *i.e.*, the most significant DEGs?

#### Clustering of significant features tab 

- **Question 5**: How many DEGs are there in the heatmap? What are the DEG thresholds?

- **Question 6**: Looking at the colour of the heatmap, which condition would you say had more up-regulated genes?

#### Pathway Analysis: `ORA` and `GSEA` 

- **Question 7**: In the gene set enrichment analysis (GSEA) results, what are the most significantly-enriched GO categories in the three ontologies? 

- **Question 8**: In the over-representation analysis (ORA) results, which of the three ontologies has the most enriched GO categories? 


