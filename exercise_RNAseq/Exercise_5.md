# Bulk RNA Sequencing Course - Live Report

Once the differential expression (DE) test job has completed running on SUSHI, both the static and live reports will be available to view. The underlying data in these reports are identical, the only difference being that the static report is a single HTML file that cannot be edited, while the live report allows for the generation and customisation of a range of figures.

The live report is an application built in R Shiny, and allows for interactivity with the data. While the results of the DE test are specific to any given link, some of the figures are not specific to the DE results and reflect the feature expression from the wider dataset (*i.e.*, including samples from the dataset that were not part of the DE test.) This can be useful in enabling the user to view expression of DE features across the wider dataset. For example, the PCA plot is nothing to do with the DE test and is present merely for convenience. Others figures, like the heatmaps and boxplots, allow users to generate figures based on any feature, but are initially based on the top DE features. Volcano plots and pathway plots are specific to that test and exclude any other samples.

The app is intended to aid users in exploring their DE results and generate bespoke and (hopefully, at least close to) publication-ready figures. Users can search for specific features and pathways, and easily plot them. Most of the plots have buttons to download data for import into other programs like GraphPad Prism for alternative figure making.

* [Interactive report Link](https://fgcz-shiny.uzh.ch/exploreDE/?data=p6000/DESeq2_diff--over--undiff_2024-03-20--16-06-16/diff--over--undiff) for this exercise

## 1. Initial Overview of DE Features

The first tab the app opens in is just a landing page, but does have two useful features. You can download full count tables in various (or no) transformations, *e.g.*, the raw counts, the TMPs. From here, you can also change the colours of each group in the dataset. Every unique level from all the `[Factor]` columns in the SUSHI dataset will be represented here. You can choose custom colours, or select from palettes.

Moving on to the `DE Table` tab, is our first look at the results of the DE test.

#### Q1A

-   Using the table in the "Results Summary" box, how many differentially expressed features are there when p \< 0.01 and fold change is \> 2?

-   What is the FDR at these thresholds? Is this an acceptable FDR?

-   Using the slider in "DE Calculator" box, how many features are up-regulated when FDR \< 0.05 and log2 fold change = 1?

**Please note**: The Results Summary box displays fold change in linear, while elsewhere, including the DE calculator box, fold change is always in log2.

#### Q1B

-   What are the 5 features that are most significantly differentially expressed? (Rank by FDR)

-   What are the 5 features with the highest positive log2 fold change? (Rank by Log2 Ratio)

-   What is the log2 fold change and FDR for TOP2A gene?

Let's move on the `Volcano Plots` tab. The plot is interactive, you can click and drag over the plot to highlight specific features. You can also search for specific features to highlight in the "Select features to annotate" selection box.

#### Q1C

-   What is the name of the gene with the lowest p-value on the volcano plot? (Remember, volcano plots show the *negative* log10 of the p-value...)

-   Select MKI67 to highlight. Where is it on the volcano plot?

### The Feature Bucket

This would be a good place to introduce the feature bucket within the app. The feature bucket allows the user to select features from various tabs, and have them automatically displayed in other tabs. The tabs that allow for the selection of specific features that work with this bucket are: DE Table, Volcano, Heatmap, and Boxplots. For example, when you click to highlight features on the volcano plot, they will be added to the bucket, and will be automatically plotted in the Custom Heatmap and Boxplot tabs. If you click rows on the DE table, these will be added to the feature bucket. If you paste in a long list of genes in the custom heatmap tab, they will all be added to the feature bucket, and therefore, highlighted on the the volcano and plotted in the boxplots tab. Features in the bucket can excluded, by clicking and dragging them into the exclude bucket. They can be reordered too, *e.g.*, to determine the order of the boxplots.

## 2. General Expression of DE Features and Clustering

Now we go to the `Heatmaps` tab. By default, the expression of the top 50 DE features (in order of FDR) are displayed across all samples. We can see the samples cluster by "Condition".

Change the number of top DE features to 2'500.

#### Q2.

-   A. Does the clustering of the samples change? Do the 'outliers' become visible?

-   B. Trying to view the names of 2'500 features on a plot doesn't look good! Turn the feature names off (Figure Settings.)

You can also create heatmaps of any feature you wish, independent of the DE test. Change to the "Custom Heatmap" tab in the settings, and select any feature you want to plot (you need at least three). Then change to the "Custom Features" tab in the "Heatmaps" box to see your custom heatmap.

Taking a look at the `PCA Plots` tab, this is independent of the DE test, but is included for convenience. Like the volcano plot, this is interactive, allowing the user to click and drag to view specific samples.

-   C. What happens when you change to plot PC1 and PC3? Is there an option to help fix the plot? (Hint, think about the axes and their proportions.)

## 3. Expression of Target DE Features

Moving swiftly onto the `Boxplots` tab. If you have put features into your feature bucket, *e.g.*, when selecting features on the volcano plot, they will already be plotted here. Let's make some nice custom plots of expression!

If they aren't already in the feature bucket, select MKI67, TOP2A, COL1A2, and CXCL5 to plot. If some of them are, you can reorder them by dragging to reorder in the feature bucket.

#### Q3.

-   A. What are the ranges of the TPM counts of TOP2A versus MKI67? (Change count method, observe y-axes).

-   B. What do the standard deviation error bars look like in the barplots of these two features?

-   C. Add MCL1 and TP53, are these features DE? You can add the p-values to find out... (Figure Settings.)

## 4. Pathway Analysis Exploration

The last tabs we will look at today are the results from the pathway analysis. Both the ORA and GSEA results are represented, and are split into the three ontologies (in addition to the different feature directions in the ORA results.) Here, you can click different pathways of interest and they will be automatically added to the various figures available.

You can use boxes at the top of each column in the results table to search for key pathway terms (Label box) and key DE features (geneName box).

We'll start in ORA \> BP \> upGenes.

#### Q4.

-   A. What are some of the features that are common between <GO:0070098> and <GO:0006952>?

-   B. Is COL1A1 in any of the pathways?

-   C. Moving to ORA \> BP \> downGenes, make a plot of pathways that feature either TOP2A or MKI67. (Use the search feature and click the pathways)

-   D. Moving to GSEA \> BP, what are the enrichment scores of the pathways containing TOP2A or MKI67? What do these scores tell us about the pathways?

### Finally...

The app is a constant work-in-progress, and we are very keen to hear your feedback and feature requests, no matter how big or small! Do please email us at sequencing\@fgcz.ethz.ch and we will do our best to implement whatever you need.
