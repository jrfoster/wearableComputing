Tidy Data CodeBook
===
Overview
---
This document contains information about the source data from which the tidy data are produced and information about the final data produced.  Information in this document borrows heavily from the [UCI HAR study documentation](https://www.elen.ucl.ac.be/Proceedings/esann/esannpdf/es2013-84.pdf).

The data have been extracted from the Human Activity Recognition (HAR) dataset.  The Human Activity Recognition dataset was built from the recordings of 30 subjects performing activities of daily living (ADL) while carrying a waist-mounted smartphone with embedded inertial sensors.  The data are a public domain dataset, but its use requires an acknowledgement [1].

The original experiments were conducted with a group of 30 volunteers between the ages of 19-48 years. Each person performed six activities (WALKING, WALKING\_UPSTAIRS, WALKING\_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist.  The original dataset was randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data.  The partitioning is an important assumption because it directly implies that the two datasets are mutually exclusive and can be combined simply by appending the rows of the training set to the rows of the test set.

The data are given in a comma-separated format, with quoted strings.  It also contains a single header row.

Data Type Definitions
---
The following data type definitions are utilized in this dictionary

| Code | Term | Definition |
| --- | --- | -- |
| s | string | Character-based (string) data |
| c | classification | A coded classification, such M for Male, or F for Female |
| d | decimal | Numeric data containing a decimal point with varying precision and scale |

Data Elements
---
Each observation (row) in the data set consists of the following variables (columns):

Subject (c)
A numeric string identifying the volunteer who performed the activity and whose data are recorded in the observation



[1] Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012



> Written with [StackEdit](https://stackedit.io/).