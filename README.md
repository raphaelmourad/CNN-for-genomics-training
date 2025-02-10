# Deep Learning for Genomics Training (Raphael Mourad, Biostatistics platform, INRAe)

%![plot](https://github.com/benoitballester/inserm-ML-workshop-266/blob/main/header_googlesites.png?raw=true)


<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-workshop">About The Workshop</a>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#day1">Day 1</a></li>
    <li><a href="#day2">Day 2</a></li>
  </ol>
</details>

<!-- ABOUT THE WORKSHOP -->
## About The Workshop

The aim of this practical session is to learn machine and deep learning models for regulatory genomics using R. Deep learning models will be programmed with the Keras R interface of Tensorflow. Most models we will use can be used for many different problems in biology and in science in general. 
We will focus on the prediction of genomic experimental output such as transcription factor ChIP-seq or DNase-seq, using the DNA sequence as input. Once the model is built and trained, we will see how to extract and interpret the model features as DNA motifs. Lastly, we will use our model for predicting the effect of single nucleotide polymorphisms (SNPs) that were previously identified from genetic studies (GWAS, eQTL). 

<!-- GETTING STARTED -->
## Getting Started

### Prerequisites

If you have an Nvidia GPU, then you must install CUDA and cuDNN libraries. See:
https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html
https://developer.nvidia.com/cudnn
Be aware that you should check the compatibility between your graphic card and the versions of CUDA and cuDNN you want to install. This is a bit tricky and time consuming!

If you don't have an Nvidia GPU, you can use the CPU, which will be slower for deep learning computations. 

You need to install tensorflow and keras R packages. See the following link for explanations:
https://tensorflow.rstudio.com/installation/gpu/local_gpu/
Ideally, you should install libraries for GPUs if you have an Nvidia GPU. If not, you can also install tensorflow and keras for CPU. 

The following R libraries must be installed (using install.packages() function):
- pROC, reticulate, tensorflow, keras, reticulate, glmnet, doParallel, ranger, e1071, gkmSVM, data.table, ggplot2, gplots, knitr, markdown, rmarkdown, tinytex, ggseqlogo

The following R libraries must be installed (using bioconductor):
- BSgenome.Hsapiens.UCSC.hg19, BSgenome.Hsapiens.UCSC.hg19.masked, GenomicRanges, Biostrings, TFBSTools, JASPAR2020, motifStack, universalmotif, motifmatchr, kebabs

<!-- ARTICLES YOU CAN READ -->
## Articles to read

In the folder articles, many deep learning models applied in genomics are saved. We advice you to read at least some of these articles to better understand the deep learning models, the genomic data and the aims of these models. 

<!-- DAY 1 -->
## Day 1

During the morning, we will first preprocess ChIP-seq/DNase-seq (positive) peaks obtained from different experiments: CTCF, POL2, H3K4me3 and DNase-seq. From the peaks, we will generate random control (negative) peaks with similar length, GC content and repeat distribution. From the peaks, we will extract DNA sequences. Then, we will split the sequences in a train and a test sets for machine/deep learning model training and prediction evaluation. From the sequences, we will build features using k-mer counts and known DNA binding protein motif counts. These features will be used for building machine learning models such as logistic lasso regression, random forests and support vector machines. The model predictions will be evaluated using receiver operating characteristic curves. In the morning, we will use the following R markdown / HTML scripts (scriptR directory):
- script_preprocess_data.Rmd / script_preprocess_data.html
- script_machine_learning.Rmd / script_machine_learning.html

During the afternoon, we will first encode the DNA sequences as tensors using one-hot encoding. Then, we will build different deep learning architectures by adding different layers (convolution, dense, dropout, LSTM, ...). We will build a simple convolutional model, a model with parallel convolutional layers, a model with multiple convolutional layers, and a model including an LSTM layer. We will train the model and play with different hyperparameters. We will compare the accuracy on the training and the validation sets. We will then extract the features from the convolutional layer of the simple convolutional model, and convert them to Position Frequency Matrices (PFMs) that are commonly used for DNA motif analysis. We will trim and cluster the motifs and compare them to JASPAR database. We will assess the importance of each motif as predictor. In the afternoon, we will use the following R markdown / HTML scripts:
- script_deep_learning.Rmd / script_deep_learning.html
- script_feature_extraction_interpretation.Rmd / script_feature_extraction_interpretation.html

<!-- DAY 2 -->
## Day 2

We will use a deep learning model trained during the previous day to predict the impact of known non-coding single nucleotide polymorphisms (SNPs) on the binding of a particular transcription factor, histone mark activity or chromatin accessibility. The aim of the predictions will be to better understand the underlying biological mechanism of a non-coding SNP that is known to be associated to a particular common genetic disease (GWAS), and/or to be associated with gene expression deregulation. Moreover, we will compute mutation maps to evalute the impact of SNPs on a whole DNA region. During the last day, we will use the following R script: 
- script_SNP_analysis.Rmd / script_SNP_analysis.html

## If the R code does not work for tensorflow and keras, use this Google Colab (which works on python):
https://colab.research.google.com/drive/1MJocDZ5fC9qfbaGpXFFzGH-jGRywWN6L#scrollTo=OxW_pnHVv3Aa
