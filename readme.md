# Statistical Analysis for Identification of Invasive Carp Eggs Manuscript

This folder contains all of the files relating to the statistical analysis in the manuscript "Evaluation of a Random Forest Model to Identify Invasive Carp Eggs Based on Morphometric Features". This document contains helpful information about the files in this folder including descriptions of the files, the way the folders need to be structured in order to run the code, and instructions for running the code. 

## Folder and File Descriptions

Below are descriptions of the four sub-folders and their contents (arranged alphabetically).

**`code`**

Contains all of the R code associated with the manuscript

- `analysis.Rmd` (and `analysis.pdf`) contains the R code used to produce results for the manuscript including cleaning of the data, fitting of the models, validation of the models, and computation of performance metrics
- `figures.Rmd` (and `figures.pdf`) contains the R code used to generate figures for the manuscript
- `rf-example-predictions.Rmd` (and `rf-example-predictions.pdf`) contains the example code for applying one of the trained random forests to a new dataset to obtain predictions

**`data`** 

Contains the raw data used with the manuscript

- `eggdata_cleaned.csv` is a cleaned version of the data that is used to create the subset versions of the data used for model training and validation
- `eggdata1415.csv` is a cleaned version of the data with only observations from 2014-2015 and used to train the original models
- `eggdata141516.csv` is a cleaned version of the data with only observations from 2014-2016 and used to train the augmented model
- `eggdata16.csv` is a cleaned version of the data with only observations from 2016 and used for validation of the original models
 (`eggdata1415.csv`, `eggdata141516.csv`, and `eggdata16.csv`)
- `eggdata141516_raw.csv` is the original (raw) data file that contains the fish egg data
- `site-groups.csv` is a dataset with a list of the river and site locations in the study

**figures**

Contains the figures generated by the file `code/figures.Rmd` and included in the manuscript (figure03 to figure09)

**results**

Contains the saved versions of output from the code such as the cleaned data and random forest models

- `ice1415.csv` contains the individual conditional expectation curves produce for the original model with reduced variables for predicting species with invasive carp as one group
- `ice141516.csv` contains the individual conditional expectation curves produce for the augmented model with reduced variables for predicting species with invasive carp as one group
- `perf_metrics1415.csv` contains the performance metric results from the original models
- `perf_metrics141516.csv` contains the performance metric results from the augmented models
- `pred2016.csv` contains the predictions from the original models on the validation (2016) data
- `rfs1415.rds` contains the saved versions of the original random forest models
- `rfs141516.rds` contains the saved versions of the augmented random forest models
- `val_metrics.csv` contains the performance metrics computed on the predictions of the original models on the validation (2016) data
- `val_metrics.csv` contains the performance metrics computed on the predictions of the original models on the validation (2016) data when the observations were first separated into locations only sampled in 2016 and locations sampled previously to 2016


## Folder Structure

In order for the R code to work properly, the files (such as data and R code) must be stored using the following file structure.

Main folder contains (required):

- sub-folder called `code` with the files:
  - `analysis.Rmd`
  - `figures.Rmd`
  - `rf-example-predictions.Rmd`
  
- sub-folder called `data` with the files:
  - `eggdata141516_raw.csv`
  - `site-groups.csv`
  
Main folder contains (optional):

- sub-folder called `results` with the files:
  - `eggdata1415.csv`
  - `eggdata141516.csv`
  - `eggdata16.csv`
  - `eggdata_cleaned.csv`
  - `ice1415.csv`
  - `ice141516.csv`
  - `perf_metrics1415.csv`
  - `perf_metrics141516.csv`
  - `pred2016.csv`
  - `rfs1415.rds`
  - `rfs141516.rds`
  - `val_metrics.csv`
  - `val_metrics_separate.csv`

- sub-folder called `figures` with the files:
  - `confusion-matrices.png`
  - `cor_heatmap.png`
  - `pd_plot.png`
  - `perf_metric_plot.png`
  - `val_metric_compare_plot.png`
  - `val_metric_plot.png`
  - `vi_plot.png`
  
## Running the Code

In order to run the R code, the working directory should be set to the main folder containing the sub-folders of `data` and `code` (as described above). Then run the code in the following order.

1. Run the code in the file `analysis.Rmd`. This will generate the `results` folder with the files listed above (if not already contained in the main folder).
2. Run the code in the file `figures.Rmd`. The code in this document depends on the files in the `results` folder. It will also generate a folder called `figures` where the figures will be saved to as .png files.
3. The file `rf-example-predictions.Rmd` contains a description and examples showing how to use the trained augmented models to make predictions for a new set of fish egg morphometric variables.
