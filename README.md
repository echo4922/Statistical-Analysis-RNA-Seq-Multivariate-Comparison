# Statistical-Analysis-RNA-Seq-Multivariate-Comparison

Two different analytic approaches have been utilized for my Master's thesis: standard "counts" approach and compositinal data approach. Pioneered by a statistician, John Aitchison, CoDA emerged as a compositional data approach (CoDA) analysis framework based on log ratios to examine constrained data represented by proportions. Commonly used in the geology field to investigate compositions of rocks, CoDA is also used for the analysis of metagenomic sequencing data (Source: original paper by Erb et al). Recognizing the nature of sequencing data is what makes CoDA robust. In sequencing data, DNA fragments are incorporated into a library and a small proportion of the particular library is sequenced on a sequencing machine (Source: original paper by Fernandes et al). Because the “proportions” are sequenced, the sequencing data could be considered as compositions instead of absolute count data. As such, the CoDA analysis takes account of the compositions and transforms data accordingly. 	It has been pointed out that sequencing data may be poorly fitted by the NB distribution model. According to Hawinkel et al. (2020), the overdispersion in the model is related to the frequency of zeros in count data. In addition, a statistical model for sequencing data needs fine-tuning such that it does not yield false positives too much at the same time it does not yield enough true positives (Source: original paper by Hawinkel et al). As a result, the statistical method of sequencing data based on the NB distribution model may lead to a poor false discovery rate resulting in too many false positive findings though precise reasons are unclear. The nonparametric methods, often incorporated in the CoDA approach, do not rely on statistical assumptions of distributions and may be able to control the false discovery rate more effectively.

The figure below indicates a workflow for multivarite statistical analysis:

![Stat Analysis](https://github.com/echo4922/Statistical-Analysis-RNA-Seq-Multivariate-Comparison/assets/112420424/81020a46-8cf2-4b09-8035-377e78b05f1b)


In statistics, the multivariate comparison is used when multiple dependent variables exist. perMANOVA (permutational multivariate Analysis of Variance) is a non-parametric alternative to MANOVA (multivariate ANOVA). The MANOVA assumes the model to be parametric similar to ANOVA. In other words, it assumes a normal distribution. Sequencing data is not normally distributed thus conventional parametric statistical methods cannot be applied. The perMANOVA is based on permutations of distance matrices and it helps to statistically determine the significance of groups with centroids and the dispersion of the groups. A centroid is “the central location or vector of mean parameters for all variables” (Source: original paper by Anderson & Walsh). The purpose behind perMANOVA is to statistically determine “whether the sum of squared differences between points and their centroids are equal to the sum of squared interpoint distances divided by the number of points” (Source: Applied Multivariate Statistics in R tutorial by University by Washington). The R programming package, vegan, was used to perform a perMANOVA multivariate comparison.

The perMANOVA is a five-step process. First, the distance matrix is created from an original count matrix with a distance measure. Second, the distance matrix is squared. Third, three different sums of squares are calculated: the total sum of squares, the sum of squares for within groups, and the sum of squares for between groups. Fourth, statistical significance is calculated with a permutation and then a p-value is obtained. Lastly, R^2 is calculated (Source: Applied Multivariate Statistics in R tutorial by University by Washington). For calculating the statistical significance, Jonathan D. Bakker (2023) in Applied Multivariate Statistics in R explains how the statistical significance is obtained with a permutation test in an easy way; once the number of permutations is defined, the pseudo F-test statistic is calculated until the number of permutations is satisfied. In the end, the permutations “produce a distribution of pseudo F values against which the actual pseudo F-test statistic value is compared” (Bakker, 2023). Lastly, a final p-value is obtained when “the proportion of permutations that yielded a pseudo F-value equal or greater than the actual data” (Source: Applied Multivariate Statistics in R tutorial by University by Washington). The null hypothesis for the perMANOVA is determined with centroids. It is specified by Marti J. Anderson who pioneered perMANOVA analysis in ecology and the only assumption is “the exchangeability of the sample units among the groups” (Source: Applied Multivariate Statistics in R tutorial by University by Washington).

The following is the null hypothesis(H0) and the alternativ hypothesis (H1) for perMANOVA specified by Marti J. Anderson:

H0=The centroids of the groups are equivalent for all groups. <br />
H1=The centroids of the groups are NOT equivalent for all groups. <br />

In other words, the observations are replaceable. The null hypothesis states that if the centroids of all groups are equal, then there are no statistical differences for all groups. 




References: <br />
Paper by Erb et al: https://doi.org/10.1093/nargab/lqaa103 <br />
Paper by Fernandes et al: https://doi.org/10.1186/2049-2618-2-15 <br />
Paper by  Hawinkel et al: https://doi.org/10.1371/journal.pone.0224909  <br />
Paper by Anderson & Walsh: https://doi.org/10.1890/12-2010.1 <br />
Applied Multivariate Statistics in R tutorial by University by Washington: https://uw.pressbooks.pub/appliedmultivariatestatistics/chapter/permanova/ <br />
