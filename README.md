# Post-Processing of Cerebrovascular Models after DTF-skeletonization
Computed tomography angiography (CTA) is a popular modality of choice for detecting strokes. As it can generate highly resolved images with enhanced vessel visibility. But sometimes it is difficult to locate the exact location of a stroke because of the surrounding vessels and bones. A graph of the complete vessel tree can give the physicians an overview of the patient’s vessel structure. With this motivation in mind, Thamm et al. [[1]](https://arxiv.org/abs/2204.12333) proposed a visualization pipeline that can produce a skeletonized image from a CTA image. However, the skeletonized images sometimes do not follow the actual anatomical structure of the vessels. In this project, I have analyzed the geometrical and structural shapes of  skeletonized graph models of brain vessels and proposed solutions to reconstruct them according to the actual structure of the vessel tree.
 
<img src="/images/img1.png"  width=50% height=50%>
<img src="/images/img2.png"  width=50% height=50%>

# Complete graph image using plotly
<img src="/images/full.gif"  width=60% height=60%>

# Solution to reconstruct the vessels
<img src="/images/g1.gif"  width=30% height=30%><img src="/images/g2.gif"  width=30% height=30%>

# References
- F. Thamm, M. Jürgens, H. Ditt and A. Maier:  VirtualDSA++: Automated Segmentation, Vessel Labeling, Occlusion Detection and Graph Search on CT-Angiography Data. 
