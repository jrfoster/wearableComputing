Wearable Computing
==
Overview
--
This repository contains the deliverables related to the course project for the Coursera "Getting and Cleaning Data" class.  The purpose of this project is to demonstrate our ability to collect, work with, and clean a data set. The goal is to prepare tidy data that can be used for later analysis.

The data for this project come from the [Human Activity Recognition Study](https://www.elen.ucl.ac.be/Proceedings/esann/esannpdf/es2013-84.pdf).

This [paper](http://vita.had.co.nz/papers/tidy-data.pdf) contains more information on what constitutes a "tidy" dataset.

Artifacts
--
In this repository you will find the following artifacts:

| Name | Description |
| --- | --- |
| README.md | This file |
| CodeBook.md | The code book describing the tidy data |
| run_analysis.R | The driver program to produce the tidy data |

Requirements
--
To be able to execute the driver program to produce the tidy data, you must have the following:
 1. A local copy of this repository. 
 2. An environment in which to source and execute the R program, such as RStudio, or the R Console, available from [CRAN](https://cran.r-project.org/).
 2. The public dataset from the [Human Activity Recognition Study](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones)

Producing the Tidy DataSet
--
To create the dataset, perform the following steps:

 1. Download the [UCI HAR Dataset](https://d396qusza40orc.cloudfront.net/getdata/projectfiles/UCI%20HAR%20Dataset.zip) to your computer.
 2. Unzip the dataset into your R working directory, preserving the zip file's directory structure.
 3. Copy run_analysis.R into your R working directory.
 4. In the R console, source the driver program `source(run_analysis.R)`
 5. Execute the driver program, optionally specifying the data directory and whether or not to produce the raw data `run_analysis()`
 6. Verify that the file finalTidyData.txt is created in the working directory.

Function Documentation
--
Generally speaking, the driver program is self-contained, and requires the base R packages plus the [data.table R package](https://cran.r-project.org/web/packages/data.table/index.html).  The program itself will install this package if it is not already present in your R environment.

To run the driver program, simply execute the function run_analysis() in the R console. 

    run_analysis(datadir = "UCI HAR Dataset", outputraw = FALSE)

| Argument | Description |
| --- | --- |
| datadir | The top-level directory of the UCI HAR Dataset, assumed to be in the working directory. Default value is "UCI HAR Dataset" | 
| outputraw | A flag to indicate if you also wish to write the raw data in addition to the aggregated dataset.  This can be useful for testing purposes. Default value is FALSE. | 

Details
The function requires data.table, and will install it, plus its dependencies, if not present in the environment.  If unable to install or load this package, the function will halt.

The function requires the HAR dataset, and will make a small attempt to verify that its actually there by checking for datadir within the current working directory, along with datadir/test and datadir/train.  If any of those directories are not present, the function will halt.

The program combines the test and training datasets for observations, activities and subjects into single datasets using read.table and rbind.  The activities are loaded as factors to facilitate labeling with appropriate text.  As data is loaded and combined, the source data structures are removed from memory to conserve resources.

Feature extraction was performed using a simple regular expression for identifying all features that are either a mean or a standard deviation, according to the study documentation.  The regex used is `.*-mean[(]|.*-std[(]` which essentially extracts all columns with "mean(" or "std(" in the name.  These columns were chosen based on the study documentation's description of each of the "functions" in the feature names, as shown in the following table.

| Function | Description |
| --- | --- |
| mean | Mean value |
| std | Standard deviation |
| mad | Median absolute value |
| max | Largest values in array |
| min | Smallest value in array |
| sma | Signal magnitude area |
| energy | Average sum of the squares |
| iqr | Interquartile range |
| entropy | Signal Entropy |
| arCoeff | Autorregresion coefficients |
| correlation | Correlation coefficient |
| maxFreqInd | Largest frequency component |
| meanFreq | Frequency signal weighted average |
| skewness | Frequency signal Skewness |
| kurtosis | Frequency signal Kurtosis |
| energyBand | Energy of a frequency interval |
| angle | Angle between two vectors |

For more information, please see the CodeBook.

The aggregation was performed using the data.table package, largely for performance reasons.  I did investigate the reshape2 package and the melt/cast functionality, and while it was functional, it didn't perform as well as the data.table aggregations and it felt inefficient to have to transpose the data to another format just for the purposes of aggregation.

> Written with [StackEdit](https://stackedit.io/).