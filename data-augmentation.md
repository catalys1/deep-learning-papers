---


---

<h1 id="data-augmentation-paper-summaries">Data Augmentation Paper Summaries</h1>
<h3 id="table-of-contents">Table of Contents</h3>
<ul>
<li>Data Augmentation by Pairing Classes for Image Classification
<ul>
<li><a href="#data-augmentation-by-pairing-classes-for-image-classification">[summary]</a> <a href="https://arxiv.org/abs/1801.02929">[paper]</a></li>
</ul>
</li>
<li>Smart Augmentation - Learning an Optimal Augmentation Strateg
<ul>
<li><a href="https://arxiv.org/abs/1703.08383">[paper]</a></li>
</ul>
</li>
<li>Shake-Shake Regularizatio
<ul>
<li><a href="https://arxiv.org/abs/1705.07485">[paper]</a></li>
</ul>
</li>
<li>ShakeDrop Regularization
<ul>
<li><a href="https://arxiv.org/abs/1802.02375">[paper]</a></li>
</ul>
</li>
<li>Random Erasing Data Augmentation
<ul>
<li><a href="https://arxiv.org/abs/1708.04896">[paper]</a></li>
</ul>
</li>
<li>Parallel Grid Pooling for Data Augmentation
<ul>
<li><a href="https://arxiv.org/abs/1803.11370">[paper]</a></li>
</ul>
</li>
</ul>
<hr>
<h2 id="data-augmentation-by-pairing-classes-for-image-classification">Data Augmentation by Pairing Classes for Image Classification</h2>
<p>This paper presents a data augmentation technique that is quite simple but surprisingly effective: simply blend two images together. During training, two random images are paired together. Standard image augmentation can (and probably should) be applied to each. Then a new image is produced by a simple pixel-wise averaging of the two images. The new image is fed through the network, with the <em>label</em> being the label of the first image – no label averaging is done. They follow a periodic training regimen, training with the paired images for a while, and then training using single images for a while. They train longer on the paired images, exact details are in the paper. They finish training by fine-tuning using the single images.</p>
<p>The results they give in the paper show that the method provides superior results across multiple datasets. They also experiment with different factors. For instance, they do an experiment where they show that randomly choosing the images to be blended was more effective then other sampling strategies.</p>
<p>This method provides strong regularization which leads to reduced overfit and better generalization. There are two intuitions here. The first is that by pairing images, you are in effect squaring the number of images in the dataset, hence providing a lot of new data for the network to work with. Second, since the images are averaged together there is essentially an equal “amount” of each class represented in them: however, they are trained with a single class label. This introduces confusion and regularization into the training process, making it more difficult for the network to overfit to particular features of the training set. As they mention in the paper, it’s actually impossible for the network to predict the correct class, since both classes are equally valid. Somehow this forces the network to learn better features.</p>
<p>The method is super simple to implement: there’s nothing complicated here. I think the trickiest part is probably setting up the training schedule, but that really shouldn’t be too hard to do.</p>

