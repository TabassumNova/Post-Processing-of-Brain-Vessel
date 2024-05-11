# Post-Processing of Cerebrovascular Models after DTF-skeletonization
Computed tomography angiography (CTA) is a popular modality of choice for detecting strokes. As it can generate highly resolved images with enhanced vessel visibility. But sometimes it is difficult to locate the exact location of a stroke because of the surrounding vessels and bones. A graph of the complete vessel tree can give the physicians an overview of the patient’s vessel structure. With this motivation in mind, Thamm et al. [[1]](https://arxiv.org/abs/2204.12333) proposed a visualization pipeline that can produce a skeletonized image from a CTA image. However, the skeletonized images sometimes do not follow the actual anatomical structure of the vessels. In this project, I have analyzed the geometrical and structural shapes of  skeletonized graph models of brain vessels and proposed solutions to reconstruct them according to the actual structure of the vessel tree.
 
<img src="/images/overview.png"  width=80% height=80%>
<!-- <img src="/images/img2.png"  width=50% height=50%> -->

# Data analysis and Visualization 
<img src="/images/full.gif"  width=60% height=60%>

# Artifacts
The main idea of [skeletonization](https://www.sciencedirect.com/topics/computer-science/skeletonization) is to reduce the dimension of an object under consideration, so that this representation carries all information about the original shape of the object and, at the same time, facilitates an algorithmic geometrical and structural shape analysis. Skeletonization has been widely used in different medical imaging applications. Because of the structure of the blood vessels, it has become a very useful tool to simplify the vessel tree.

Thamm et al. [1] applied skeletonization as a part of their proposed fully automated image processing and visualization pipeline, which provides a full segmentation and modeling of the cerebral arterial tree for CTA data. Their algorithm can automatically label the cerebral arteries (Middle Cerebral Artery left and right, Anterior Cerebral Artery short, Posterior Cerebral Artery left and right) and detect occlusions or interruptions in these vessels due to stroke. To detect the actual structure of vessel trees, it is important to compute a proper skeletonization. But in some regions, this computation may be difficult because a large number of neighboring vessels make loop structures in the skeletons. To avoid this, post-processing of the skeletonized images is needed.

<img src="/images/loops.png"  width=80% height=80%>

# Feature extraction and Classification
Type of loops: 
* **Type-00**: These loops have exactly two nodes and two edges
* **Type-01**: These loops have higher average node density and smaller total loop length.
* **Type-02**: These loops have lower average node density and larger total loop length

In order to eliminate these two types of loops, two different types of actions are needed to take. I designed a classifier to differentiate between these two groups. For this, I took two features:
* **Average loop density**: Average density of the nodes within a loop by using kernel density estimator where kernel bandwidth = 10.
* **Total loop length**: Total length of the edges within a loop.
For classification, I used k-means clustering.
<img src="/images/Classification006.png"  width=60% height=60%>

# Solution to eliminate Type-01 loops
As Type-01 loops are created from large vessels, here the main target was to merge all the loops and create edges that are aligned to the main direction of the vessel and have an enlarged radius.

<img src="/images/g1.gif"  width=30% height=30%><img src="/images/g2.gif"  width=30% height=30%>

# References
- F. Thamm, M. Jürgens, H. Ditt and A. Maier:  VirtualDSA++: Automated Segmentation, Vessel Labeling, Occlusion Detection and Graph Search on CT-Angiography Data. 
