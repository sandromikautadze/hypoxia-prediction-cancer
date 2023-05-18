# Hypoxia Prediction from scRNA-seq Data

The project was conducted by **Group 3**: Beatrice Citterio, Irene Colombo, Giovanni De Muri, Mattia Martino, and Sandro Mikautadze

### Table of Contents
* [Introduction](#introduction)
  * [Motivation](#motivation)
  * [The Research Question](#the-research-question)
  * [Materials](#materials)
* [How To Read the Project (!)](#how-to-read-the-project)
  * [Why Such a Structure?](#why-such-a-structure)

## Introduction

### Motivation
Cancer is a very complex and **heterogeneous** disease. What this means is that different cells can show different profiles, ranging from cellular morphology deformations to varying gene expression patterns. Although treatments are available for different types of mutations, there is still a need to improve our understanding of cancer cells' environment, which can significantly influence the behavior and response to treatment. In particular, what plays a crucial role is **oxygen availability** in the cell's environment, as the exposure of cancer cells to different levels of oxygen can lead to changes in gene expression patterns. For example, cells exposed to low oxygen levels, namely *hypoxic* cells, can exhibit altered gene expression patterns, which can contribute to tumor progression and treatment resistance. This is because they are in a stressed environment, and therefore the cells activate some genes that might help them survive and become unresponsive to treatment.

Therefore, this environmental condition further complicates the diagnosis and treatment of the disease, as it can result in different treatment outcomes for the same type of cancer. In this context, having the possibility to analyze the genetic sequence of cancer cells to gain information about their environment can hugely help in identifying the most aggressive and resistant cells. Hence, developing methods to identify and characterize cancer cells' environment accurately is **critical** to improving cancer diagnosis and treatment.

### The Research Question
The research question we aim to address is the following: **can we determine from the genetic sequence whether a cell was exposed to an environment with low or high oxygen levels?**

In particular, our goal is to predict hypoxia or normoxia status from single-cancer-cell RNA-seq data.

### Materials
In order to answer this question, we will work in a simplified environment. In particular, we have at our disposal single-cancer-cell RNA-sequencing (scRNA-seq) data coming from breast cancer. The cells that we are going to analyze were derived originally from tumors of female patients, and then they were grown in two cultures: MCF7 and HCC1806. The culture corresponding to the cell line MCF7 was given estrogen, while the one corresponding to HCC1806 was given other growth factors. We are assuming that the cell lines that we obtain are a good representation of the tumor cells.

The samples in the cell line correspond to cells and the features of sequenced genes. We will be working with two given types of sequencing techniques: SmartSeq and DropSeq. For each technique and for each cell we have the following data:
- SmartSeq for MCF7 and HCC1806:
  - Metadata, with information about the samples
  - Unfiltered data, so the actual sequencing data, with no filter nor normalization.
  - Filtered and normalized data, so the preprocessed data ready for training
- DropSeq for MCF7 and HCC1806:
  - Filtered and normalized data

In addition, there's also a test set, for each colture and for each technique, that will be used for evaluation.

## How To Read the Project
Here we are going to summarize the order in which the files must be read in order to understand our choices, thus **read this section carefully**. What follows is the exact file name order, with a brief explanation of the content:

- ```00-SmartSeq``` folder:

  1. ```HCC1806_unfiltered.ipynb```: it contains the exploratory data analysis, data preprocessing, and unsupervised learning of the unfiltered data of the HCC1806 cell line.

  2. ```HCC1806_train.ipynb```: it contains a brief EDA and unsupervised learning section, supervised learning for classification, and analysis of the results for the HCC1806 cell line.

  3. ```MCF7_unfiltered.ipynb```: same as (i), but for the MCF7 cell line.

  4. ```MCF7_train.ipynb```: same as (ii), but for the MCF7 cell line.

All the techniques and choices are carefully motivated and explained in (i) and (ii). Therefore, for the MCF7 cell line, we kept our comments much more compact, without explaining once again our decisions.

- ```01-DropSeq``` folder:

  5. ```HCC1806_dropseq_train.ipynb```: EDA and training for the HCC1806 cell line.
  6. ```MCF7_dropseq_train.ipynb```: same as (v), but MCF7 cell line.

We stress once again the importance of reading the files in the order presented above. Not doing so will very likely result in a big confusion for the reader.

### Why Such a Structure?
On the one hand, we understand that structuring the project with this format might slow down the process of reading, understanding, and grading all at once. On the other, we believe that it's the setup that gives the most credit to our work, as we have put a lot of effort into doing the best work we could, despite the time and domain-knowledge constraints, while keeping the comments short enough as to be both well descriptive and not excessively long.

In addition, notice that we decided not to perform the training on the processed data from the unfiltered files, but the only learning that we did was on the given training set. This was made to avoid lengthening the project and to keep the results consistent for both sequencing techniques.
