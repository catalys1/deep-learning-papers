---


---

<h1 id="co-segmentation-paper-summaries">Co-Segmentation Paper Summaries</h1>
<h3 id="table-of-contents">Table of Contents</h3>
<ul>
<li>Deep Object Co-Segmentation
<ul>
<li><a href="deep-object-co-segmentation">[summary]</a> <a href="https://arxiv.org/abs/1804.06423">[paper]</a></li>
</ul>
</li>
<li>Co-Segmentation by Composition
<ul>
<li><a href="https://ieeexplore.ieee.org/document/6751271/">[paper]</a></li>
</ul>
</li>
<li>Object Co-Segmentation via Weakly Supervised Data Fusion
<ul>
<li><a href="https://www.sciencedirect.com/science/article/pii/S1077314216301825">[paper]</a></li>
</ul>
</li>
<li>Unsupervised Image Co-Segmentation via Guidance of Simple Images
<ul>
<li><a href="https://www.sciencedirect.com/science/article/pii/S0925231217316272">[paper]</a></li>
</ul>
</li>
<li>Object co-segmentation via salient and common regions discovery
<ul>
<li><a href="https://www.sciencedirect.com/science/article/pii/S0925231215006116">[paper]</a></li>
</ul>
</li>
<li>Complementary saliency driven co-segmentation with region searching and Hierarchical constraint
<ul>
<li><a href="https://www.sciencedirect.com/science/article/pii/S0020025516305990">[paper]</a></li>
</ul>
</li>
<li>Cosegmentation of multiple image groups
<ul>
<li><a href="https://www.sciencedirect.com/science/article/pii/S1077314216000497">[paper]</a></li>
</ul>
</li>
<li>Multi-task ranking SVM for image cosegmentation
<ul>
<li><a href="https://www.sciencedirect.com/science/article/pii/S0925231217305933">[paper]</a></li>
</ul>
</li>
<li>Noise-aware co-segmentation with local and global priors
<ul>
<li><a href="https://www.sciencedirect.com/science/article/pii/S0925231218301474">[paper]</a></li>
</ul>
</li>
</ul>
<hr>
<h2 id="deep-object-co-segmentation">Deep Object Co-Segmentation</h2>
<p>This paper introduces a fully convolutional network for cosegmentation. They use a siamese encoder-decoder structure. In the middle, at the bottleneck layer, they compute feature correlations between the feature maps of the two input images. They feed the feature correlation matrices into the decoder along with the feature maps. They train the network in a fully supervised manner, with ground truth binary segmentation masks (foreground/background).</p>
<p>To train the network, they create a new dataset of image pairs taken from Pascal VOC 2012. They find all pairs of images that have a common object between them, and then treat the masks for those objects as the foreground masks and set everything else to be background.</p>
<p>The results are pretty good. Given an image pair, the network produces segmentations containing only the objects that are semantically the same in some way. They further show that they can use their trained network on different co-segmentation datasets, <em>without any fine-tuning</em>, and get good results on those images.</p>
<p>I think the most interesting idea from this paper is the feature correlation layer, which is similar to what I want to use to do weakly-supervised co-segmentation.</p>

