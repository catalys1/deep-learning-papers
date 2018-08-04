---


---

<h1 id="fine-grained-recognition-paper-summaries">Fine Grained Recognition Paper Summaries</h1>
<h3 id="table-of-contents">Table of Contents</h3>
<ul>
<li><strong>Large Scale Fine-Grained Categorization and Domain-Specific Transfer Learning</strong>
<ul>
<li><a href="#large-scale-fine-grained-categorization-and-domain-specific-transfer-learning">[summary]</a> <a href="http://openaccess.thecvf.com/content_cvpr_2018/html/Cui_Large_Scale_Fine-Grained_CVPR_2018_paper.html">[paper]</a></li>
</ul>
</li>
</ul>
<h2 id="large-scale-fine-grained-categorization-and-domain-specific-transfer-learning">Large Scale Fine-Grained Categorization and Domain-Specific Transfer Learning</h2>
<p>This paper studies the effect of transfer learning on fine-grained classification datasets. They do a couple of interesting things:</p>
<ul>
<li>They do an experiment where they show that using larger input-image sizes has a significant impact on performance. On the iNaturalist dataset, they improved 4.5% and 2% on top-1 and top-5 classification accuracy by scaling up the network inputs from 299 to 560 square.</li>
<li>They experiment with pre-training networks using ImageNet, iNaturalist, or a combination of the two, and then fine-tuning the network for a specific, smaller-scale fine-grained dataset. They find that pre-training on a dataset that is more similar in its content to the target domain provides increased performance.</li>
<li>They construct a method for creating a pre-training dataset from existing large-scale datasets by selecting a subset that is most similar to the target domain, using the Earth Movers distance.</li>
</ul>

