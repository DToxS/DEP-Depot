# Calculating Differentially Expressed Proteins

This R program calculates the differentially expressed proteins (DEPs) by comparing the label-free quantification (LFQ) intensities of the protein samples at each drug-treated condition with those control samples from the same cell line and cultured in the same experiment. This program reads in two input data files, the experiment design table and the LFQ intensity table, and generates the DEP comparison results for each drug treatment within each experiment of each cell line and combine the DEP results from multiple experiments to a single ranked DEP list for each drug treatment and each cell line.

## Inputs

The input data files for this R program include:

- `Experiment-Design-Table.tsv`: the experiment design table of the protein samples at drug-treated and control conditions for each cell line.
- `Protein-Gene-Sample-LFQ-Intensity-Norm.tsv`: the LFQ intensity table of reference proteins for all samples.


## Outputs

The output data files from this R program include:

- `Protein-LFQ-DEP-Calc.[Durg Treatment]-[Cell Line]-[Experiment Number].tsv`: the data file containing the raw LFQ intensities, normalized LFQ intensities, and differential comparison results from a drug treatment for a cell line and a cell-culture experiment.
- `Protein-LFQ-DEP-Combined.[Drug Treatment]-[Cell Line].tsv`: the data file containing the combined differential comparison results from a drug treatment for a cell line.
- `Protein-LFQ-DEP-Summary.tsv`: the data file containing a summary table of DEPs from each drug treatment for each cell line and each cell-culture experiment.
- `Protein-LFQ-DEP-Combined-Summary.tsv`: the data file containing a combined summary table of DEPs from each drug treatment for each cell line.

## Requirements

This R program needs the following R packages to be installed before launching:

- *utils*
- *stats*
- *matrixStats*
- *vsn*
- *limma*
- *metap*

## Launch

Set the `input_data_dir` and `output_data_dir` variables in the R program to the directories containing input and output data files. For example, the following R lines set the input and output data directories to `${HOME}/DToxS-DEP-Depot/Input-Data` and `${HOME}/DToxS-DEP-Depot/Output-Data`:

```R
input_data_dir <- file.path(home_dir, "DToxS-DEP-Depot", "Input-Data")
output_data_dir <- file.path(home_dir, "DToxS-DEP-Depot", "Output-Data")
```

And then launch this R program using the following command line:

```bash
Rscript "${R_PROG_PATH}/Calc-Protein-LFQ-Intensity-DEP.R"
```

After finishing, all the output data files can be found at the output data directory.
