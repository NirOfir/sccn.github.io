---
layout: default
title: A10 MI-clust
permalink: /docs/A10_MI-clust
parent: Docs
---

{ {Backward_Forward|A09:_Using custom MRI from individual
subjects|A09: Using custom MRI from individual
subjects|A11:_BESA_(outdated)|A11: BESA} }

## The MI-clust Plug-in: Clustering independent components using mutual information

The infomax ICA algorithm tries to minimize mutual information between
components and is greatly successful at this task. Since the activities
of cortical and other EEG sources are not perfectly independent, after
performing ICA a low level of dependence still exists between the
returned maximally independent components( ICs). This residual mutual
information can be used to infer relations between different ICs. Figure
below shows the scalp maps 30 ICs returned for a sample dataset.

<center>

[750px](/Image:_exp44_30_comps.png "wikilink")

</center>

We can use the { {File|mi_pairs.m} } function to calculate the mutual
information between the activities (or activations) of these first 30
ICs:

> \>\> mutual_info = mi_pairs(EEG.icaact(1:30,:));


To visualize the resulting matrix, it is better to first remove the
diagonal values (indicating the mutual information between each
component and itself), which are quite higher than off-diagonal inter-IC
pair values

> \>\> mutual_info = mutual_info – diag(diag(mutual_info));


Now we can use a simple Matlab call to visualize this matrix:

> \>\> figure; imagesc(mutual_info);


giving

<center>

[750px](/Image:_exp44_mutual_info.png "wikilink")

</center>


As we can see, there is some residual dependency between some of the
component activities. For example, ICs 1-4 have a higher dependency on
each other than on other components. The scalp maps of these ICs (below)
show that they are all related to artifacts generated by subject eye
movements, specifically eye blinks.

<center>

[Image: exp44_comps1_4.png](/Image:_exp44_comps1_4.png "wikilink")

</center>


The *MI_clust* plug-in takes advantage of such residual mutual
information to find subsets of maximally independent components whose
activities are in some way related to each other. This makes it easier
to differentiate various sources of the recorded EEG signal separated by
ICA. To use this plug-in, we first need to perform ICA on our dataset.
Then select <font color=brown>Plot \> Cluster dataset ICs</font>

<center>

[Image: miclust_menu.png](/Image:_miclust_menu.png "wikilink")

</center>


A pop-up dialog window will appear:

<center>

[Image: miclust_dialog.png](/Image:_miclust_dialog.png "wikilink")

</center>


Here we need to input three values:
\*Components to cluster: These are the indices of the ICs to cluster.

  - Number of clusters: Number of different groups into which ICs are to
    be clustered. For example, we might want to keep at least one
    cluster per every type of EEG signal source (eye movements, noise
    subspace, cortical activities,...).
  - Clustering method: Currently one can choose either "linkage" (which
    uses the Matlab *linkage()* function, using the 'ward' method) or
    "kmeans" (based on the Matlab *kmeans()* function) for clustering.
    "Linkage" seems to produce better results. An additional dendrogram
    of IC distance relationships is plotted if the "linkage" option is
    selected.


After receiving these inputs, the plug-in calculates mutual information
between ICs using the { {File|mi_pairs.m} } function (this may take
some time...). The function produces 2-D and 3-D IC "locations" whose
distances from each other best represent the degree of dependence
between each IC pair (closer ICs exhibiting more dependence). This uses
the Matlab *mdscale()* function. These locations are clustered by the
specified clustering function ("linkage" or "kmeans"). Several figures
are plotted :


1.  Component Cluster Plots:
    Each IC cluster is plotted in a separate figure. Figure below shows
    a cluster of vertical eye movement components:

    <center>
    [625px](/Image:_eye_comp_cluster.png "wikilink")
    </center>

    Another cluster, plotted below, consists of likely brain sources:
    <center>
    [625px](/Image:_brain1_comp_cluster.png "wikilink")
    </center>

    The brightness of the background in these plots indicates the
    confidence level (returned by the Matlab *silhouette()* function)
    that each IC belongs to this cluster. The figure below shows an
    example in which three ICs on the top-right corner have a dark
    background, meaning they are not a strong part of this cluster.
    (Notice that their scalp maps are quite different as well). In such
    cases, increasing the number of clusters is recommended. The
    plotting function interpolates the *silhouette()* values to show a
    smooth background transition between components.

    <center>
    [675px](/Image:_background_example_comp_cluster.png "wikilink")
    </center>


2.  The Silhouette Plot:
    *Silhouette()* measures the degree of confidence that a certain IC
    belongs to the indicated cluster versus other clusters. It is
    measured by a value between -1 and +1. The plug-in plots
    *silhouette()* values for all the ICs that belong to the given
    cluster. From the figure below we can see that the high confidence
    (positive silhouette value) ICs in cluster 5 (eye component cluster)
    and low confidence (negative silhouette) for ICs in cluster 2 (above
    figure). This suggests increasing the number of clusters to provide
    additional groups for ICs with low silhouette.

    <center>
    [425px](/Image:_miclust_silh.png "wikilink")
    </center>

3.  The 3-D Plot:
    <center>
    [750px](/Image:_3d_comp_cluster.png "wikilink")
    </center>

    This plot shows a 3-D representation in which closer ICs have higher
    mutual information or activity dependence. Components are colored
    according to their respective cluster.

4.  The Dendrogram Plot:
    If the "linkage" clustering method is selected, an IC dendrogram is
    plotted:

    <center>
    [Image:
    miclust_dendogram.png](/Image:_miclust_dendogram.png "wikilink")
    </center>

    In this plot, IC are hierarchically joined together (in a binary
    manner) to form groups with high interdependency. For example, in
    the above figure, ICs 3 and 4 joint together to form a group that
    joins the group of ICs 1 and 2 at a higher level to form an \\'eye
    component\\' group. The height of the tree at each level is
    proportional to the distance (independence) between joined group at
    that level.

[Category:IV. Appendix](/Category:IV._Appendix "wikilink") {
{Backward_Forward|A09:_Using custom MRI from individual
subjects|A09:Using custom MRI from individual
subjects|A11:_BESA_(outdated)|A11: BESA} }