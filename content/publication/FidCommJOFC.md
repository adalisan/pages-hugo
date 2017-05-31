+++
abstract = "In various data settings, it is necessary to compare observations from disparate data sources. We assume the data is in the dissimilarity representation (Pękalska and Duin, 2005) and investigate a joint embedding method (Priebe et al., 2013) that results in a commensurate representation of disparate dissimilarities. We further assume that there are “matched” observations from different conditions which can be considered to be highly similar, for the sake of inference. The joint embedding results in the joint optimization of fidelity (preservation of within-condition dissimilarities) and commensurability (preservation of between-condition dissimilarities between matched observations). We show that the tradeoff between these two criteria can be made explicit using weighted raw stress as the objective function for multidimensional scaling. In our investigations, we use a weight parameter, w, to control the tradeoff, and choose match detection as the inference task. Our results show weights that are optimal (with respect to the inference task) are different than equal weights for commensurability and fidelity and the proposed weighted embedding scheme provides significant improvements in statistical power."
authors = ["Sancar Adali", "Carey Priebe"]
date = "2016-11-10"
image_preview = "JOFC_textart.png"
math = true
publication_types = ["2"]
publication = "In Journal of Classification"
publication_short = "In *JoC*"
selected = true
title = "Fidelity-Commensurability Tradeoff in Joint Embedding of Disparate Dissimilarities"
url_code = "https://github.com/adalisan/JOFC-MatchDetect"
url_dataset = "http://www.cis.jhu.edu/~parky/Data/Wiki/"
url_pdf = "https://link.springer.com/article/10.1007/s00357-016-9214-6"
url_project = "project/JOFC"
url_slides = "#"
url_video = "#"

+++
Let's say our data does not consist of $n$ observations of $d$-dimensional vectors, but instead an $n \times n$ matrix, whose entries consist of the dissimilarities between the $n$ observations as measured by a bivariate function $\delta(.,.)$.  We refer to the computation of $n$ separate $d$-dimensional vectors/points  that is as consistent as possible with a dissimilarity matrices as "embedding" this dissimilarity matrix.

 Consider the embedding of $K$   dissimilarity(distance-like) matrices between $n$ objects (coming from $K$ different bivariate functions  $\delta_k(.,.)$ ) or observations of $n$  $K-tuples$ of similar objects. In any case the different dissimilarity matrices are related in a statistical or causal sense. We refer to this relation as "matched". Say $K=2$. A joint  embedding of these dissimilarity matrices will result in $2n$ points that consist of $n$ matched points.

To embed multiple dissimilarities  $\{\Delta_k\},k=1,2$  into a commensurate space, so that the information represented in different dissimality matrices can be used for a data exploitation task,  an omnibus dissimilarity matrix  $M \in \mathbb{R}^{nk \times nk}$  is constructed. Consider, for $K=2$,
$$
M=  \left[ \begin{array}{cc}
         \Delta_1 & L\\
        L^T  & \Delta_2
     \end{array}  \right]     \label{omnibus}
$$ where $L$ is an imputed or estimated matrix for the two dissimilarities between $n$ objects. The embedding of this matrix will result in $2n$ observations of $d$-dimensional vectors.

If we minimize a common multidimensional scaling objective function known as raw stress to embed, the objective function can be decomposed into three terms that are interpretable.
Fidelity describes how well the embedding in commensurate space preserves the original dissimilarities $\{\Delta_k\},k=1,2$. These terms would be the only ones that are minimized   if we embedded the dissimilarity matrices separately.

Commensurability is how well the embedding  in commensurate space preserves matchedness of matched observations. These terms correspond to the deviation from the real dissimilarities between matched observations and the distances between matched points in the embedding.

Separability is how well the embedding  in commensurate space preserves the disparateness of unmatched observations.
These terms correspond to the deviation from the real dissimilarities between unmatched observations and the distances between unmatched points in the embedding.

We show that a weight parameter that controls the terms' importance in the minimization of raw stress is essential for data exploitation task such as detection of new matched observations, given a set of  matched observations.
