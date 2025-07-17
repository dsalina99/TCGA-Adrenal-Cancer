Biclustering package used: https://github.com/nikitasigal/biclustlib

## Characterizing Adrenal Cancer Patients Using Gene Patterns Biclustering Methods
Abstract
For this data mining research project, our goal was to determine if there were any distinct
biological and survival markers that distinguish adrenal cancer patients based on their gene
expression patterns. To complete this task, a biclustering algorithm known as Iterative Signature
Algorithm (ISA) was employed to cluster these patients together based on their most common
gene expressions. From here, we were able to complete survival analysis on these groups, as well
as gene enrichment analysis of the different biclusters. To look into key prognostic genes in
Adrenal Cancer, we used Permutation Feature Importance in a Random Survival Forest. The top
important genes are mostly consistent with previous cancer literature related to other
malignancies, additionally we found two genes BIRC5 and NURF2 which have been identified
as being prognostic genes specifically for Adrenal Cancers.
Introduction
There are two adrenal glands in the human body, and each one located on top of each
kidney. Each adrenal gland is composed of two primary sections: the adrenal cortex and the
adrenal medulla. The adrenal cortex is separated into three distinct parts, the zonal fasciculata,
the zona glomerulosa, and the zona reticularis. Each one is responsible for producing various
hormones, including cortisol, aldosterone, and more, including hormones that determine male or
female characteristics [1]. The adrenal medulla is encapsulated by the adrenal cortex, and is
responsible for producing stress hormones, such as adrenaline. Both sections lie within a
protective sheath known as an adipose capsule [2].
There were two histological subtypes of cancer in the adrenal gland in our dataset.
Adrenal cortex cancer (adrenocortical cancer / ACC), which can be functioning (causes higher
production or hormones) or non-functioning (no effect on hormone production) type of
cancer[1]. The other histological type is known as pheochromocytoma. It is a tumor that grows
from chromaffin cells (located inside the adrenal cortex) and most of these tumors are formed
within the adrenal medulla. These tumors may cause an overproduction of hormones such as
adrenaline, resulting in symptoms that include irregular heartbeats and high blood pressure [3].
Clustering algorithms work by partitioning data into unique subsets of data sharing global
patterns, known as clusters. Data objects within each cluster share some sort of similarity among
one another, and display dissimilarities with data objects in other clusters [4]. Originally
introduced by John A. Hartigan in 1972 [5], and later employed by Y. Cheng and G. Church in
gene expression analysis [6], in contrast to clustering, biclustering is a technique that clusters
rows and columns simultaneously for a data set contained in a matrix-like formation. Data
objects within these biclusters can be shared among others [7]. These algorithms typically are
applied to two-dimensional numerical data sets, where the data values can be binary or
non-binary [8].
Gene expression data is an ideal application for this [9], especially in combination with
the comparison of multiple patients’ genes for various testing cases. Regular clustering methods
only allow data objects to be grouped into one cluster at a time. Since genes are typically shared
among multiple gene patterns, biclusters provide an ideal medium from which subsets can be
formed as well. Furthermore, this also allows the overlap of patient groups that share gene
patterns. A biclustering algorithm therefore able to pinpoint gene patterns that are specific to
certain adrenal cancer groups but not others. In these gene expression matrices, rows typically
represent the different genes, and in the case of this report, columns represent each individual
patient within the dataset. Each element is a numerical value of the gene’s expression level for a
given patient [10]. By running this type of data through a biclustering algorithm, subclusters of
conditions (i.e., patients, metrics of interests, etc.) can be formed with specific patterns of genes
of similar expression levels. Biclusters (B) can be represented in matrix form with i rows of
genes and j columns of conditions, each row a gene, each column a patient, and therefore
creating an i x j matrix of gene expression data and patients.
For our research, we chose a data set from the Cancer Genome Atlas Program (TCGA)
[11]. The website offers a free to use database of genome sequenced patients with various
cancers, including adrenal cancer from which we acquired data of. In order to determine the best
algorithm of choice, we referred to a research paper by Padhila et al.(2018) on biclustering
methods and algorithms for biological data [12]. For our dataset, we looked at four algorithms:
Iterative Signature Algorithm (ISA), Cheng and Church’s Algorithm (CCA), Large Average
Submatrices (LAS), and Spectral. Spectral biclustering tries to find checkerboard-like patterns of
conditions and genes by using singular value decomposition. LAS uses a multiple comparison
test (similar to Bonferroni) to search for submatrices. CCA removes and adds columns and rows
within a matrix dataset to reduce mean squared residue measure. CCA, LAS, and ISA are greedy
algorithms, which perform local operations to then move onto a broader level [12].
We performed a benchmark test, average Spearman’s rank correlation coefficient, to
determine the most appropriate algorithm for our dataset. This test ranks the gene expression
values within the data matrix. If a correlation value of one is obtained, then the two genes being
compared have the highest correlation possible between them. If a value of zero is obtained, they
have an inverse relationship [13]. We found ISA to have the highest average correlation values,
and when doing a timed evaluation comparison of all the algorithms, ISA was also the fastest.
Thus, we decided to employ the ISA algorithm on our dataset.
After finding the biclusters of gene expressions and patients, we explored some of the
possibilities of what can be done to gain further insight and understanding of our results. To
finalize the study of genes in the prognosis of adrenal cancer we also explored survival analysis,
in specific Random Survival Forests. Random Forest, in general, has been an attractive tool for
Gene expression data due to its ability to solve large p, low n problems and also take into
accounts correlations between features which is a common theme in gene data since biological
system networks are interconnected
