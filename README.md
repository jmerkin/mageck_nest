# README #

This README would normally document whatever steps are necessary to get your application up and running.

### What is this repository for? ###

* Quick summary
* Version
* [Learn Markdown](https://bitbucket.org/tutorials/markdowndemo)

### Set Up ###
    Now this algorithm only supports python2. The new version for python3 will be updated soon.
    1. Open terminal and change to “YOUR CODES DIRECTORY"
    2. Type "git clone https://chenhaochen@bitbucket.org/liulab/mageck_nest.git”
    3. Change directory to “YOUR CODES DIRECTORY/mageck_nest"
    4. Type “tar -xvzf mageck_nest-1.0.tar.gz”
    5. Now the codes should be in “YOUR CODES DIRECTORY/mageck_nest/mageck_nest-1.0/mageck_nest/“
    6. Change directory to where the test file is stored.
  
### Usage ###

    usage: mageck_nest.py nest [-h] [-n OUTPUT_PREFIX]
                               [--genes-varmodeling GENES_VARMODELING]
                               [-i INCLUDE_SAMPLES] [-b BETA_LABELS]
                               [--adjust-method {fdr,holm,pounds}] [-o]
                               [--norm-method {none,median,total,control}] [-p]
                               [-e NEGATIVE_CONTROL] -k COUNT_TABLE -d
                               DESIGN_MATRIX

    optional arguments:
    -h, --help            show this help message and exit
    -n OUTPUT_PREFIX, --output-prefix OUTPUT_PREFIX
                          The prefix of the output file(s).
    --genes-varmodeling GENES_VARMODELING
                          The number of genes for mean-variance modeling.
                          Default all.
    -i INCLUDE_SAMPLES, --include-samples INCLUDE_SAMPLES
                          Specify the sample labels if the design matrix is not
                          given by file in the --design-matrix option. Sample
                          labels are separated by ",", and must match the labels
                          in the count table.
    -b BETA_LABELS, --beta-labels BETA_LABELS
                          Specify the labels of the variables (i.e., beta), if
                          the design matrix is not given by file in the
                          --design-matrix option. Should be separated by ",",
                          and the number of labels must equal to (# columns of
                          design matrix), including baseline labels. Default
                          value: "bata_0,beta_1,beta_2,...".
    --adjust-method {fdr,holm,pounds}
                          Method for sgrna-level p-value adjustment, including
                          false discovery rate (fdr), holm's method (holm), or
                          pounds's method (pounds).
    --norm-method {none,median,total,control}
                          Method for normalization, including "none"
                          (nonormalization), "median" (median normalization,
                          default), "total" (normalization by total read
                          counts), "control" (normalization by control sgRNAs
                          specified by the --control-sgrna option).
    -e NEGATIVE_CONTROL, --negative_control NEGATIVE_CONTROL
                          The gene name of negative controls. 
    -p, --PPI_prior       Specify whether you want to incorporate PPI as prior
    -o, --outliers_removal
                          Specify whether you want to remove outliers and
                          recalculate.
    -k COUNT_TABLE, --count_table COUNT_TABLE
                          Provide a tab-separated count table. Each line in the
                          table should include sgRNA name (1st column), target
                          gene (2nd column) and read counts in each sample.
    -d DESIGN_MATRIX, --design_matrix DESIGN_MATRIX
                          Provide a design matrix, either a file name or a
                          quoted string of the design matrix. For example,
                          "1,1;1,0". The row of the design matrix must match the
                          order of the samples in the count table (if --include-
                          samples is not specified), or the order of the samples
                          by the --include-samples option.

### Result interpretation ###
    1. gene_summary.txt:
 
    gene      | sgRNA                     | beta       | z       | wald-p-value            | wald-fdr
    gene_name | number of sgRNAs included | beta value | z-score | p-value using Wald test | FDR

    2. sgrna_summary.txt
    gene      | sgRNA      | eff        | mu       | K          | likelihood
    gene_name | sgRNA_name | efficiency | mu_value | read count | likelihood

    3. QQplot of wald p value: QQ plot of wald p values against uniform distribution
    4. Hist of beta value: Histogram of beta values for all genes
    5. mu_k_PPI_diagnosis.txt:
    Example:
    