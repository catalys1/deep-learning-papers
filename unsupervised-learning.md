---


---

<h1 id="unsupervised-learning-paper-summaries">Unsupervised Learning Paper Summaries</h1>
<h3 id="table-of-contents">Table of Contents</h3>
<ul>
<li><strong>Learning Visual Groups from Co-Occurrences in Space and Time</strong>
<ul>
<li><a href="https://arxiv.org/abs/1511.06811">[paper]</a></li>
</ul>
</li>
<li><strong>Split-Brain Autoencoders: Unsupervised Learning by Cross-Channel Prediction</strong>
<ul>
<li><a href="#split-brain-autoencoders-unsupervised-learning-by-cross-channel-prediction">[summary]</a> <a href="http://openaccess.thecvf.com/content_cvpr_2017/html/Zhang_Split-Brain_Autoencoders_Unsupervised_CVPR_2017_paper.html">[paper]</a></li>
</ul>
</li>
<li><strong>Colorization as a Proxy Task for Visual Understanding</strong>
<ul>
<li><a href="http://openaccess.thecvf.com/content_cvpr_2017/html/Larsson_Colorization_as_a_CVPR_2017_paper.html">[paper]</a></li>
</ul>
</li>
<li><strong>Unsupervised Learning by Predicting Noise</strong>
<ul>
<li><a href="#unsupervised-learning-by-predicting-noise">[summary]</a> <a href="http://proceedings.mlr.press/v70/bojanowski17a.html">[paper]</a></li>
</ul>
</li>
</ul>
<hr>
<h2 id="unsupervised-learning-by-predicting-noise">Unsupervised Learning by Predicting Noise</h2>
<p><strong>Main Idea</strong><br>
Train the features of a convolutional neural net in a completely unsupervised way by mapping the input features to a set of noise vectors. That is, instead of using ground truth targets such as class labels, the targets are randomly sampled noise. The network tries to minimize the l2 distance from its output to the noise vectors. The authors show that they can train on large datasets like imagenet in a completely unsupervised way, and then use the learned features for classification tasks with only a small drop in accuracy.</p>
<p><strong>Details</strong><br>
Every image in the dataset gets a unique target vector. The target vectors are drawn uniformly from the  <em>d</em>-dimensional unit sphere, where  <em>d</em> is the dimensionality of the feature vectors. We start with  <em>n</em> fixed target vectors, where  <em>n</em> is the number of instances in the dataset. This prevents mode collapse (inputs mapping to the same target) while allowing for an efficient algorithm to optimize the network (having more than  <em>n</em> targets would make the algorithm slower, see the paper). The algorithm is to take mini-batches of  <em>b</em>  images, put them through the network, and then run a Hungarian algorithm to map them to the best target vector. The only targets available are the  <em>b</em> targets previously assigned to those images (this makes the algorithm efficient, aka it scales linearly in the size of the dataset).</p>
<h2 id="split-brain-autoencoders-unsupervised-learning-by-cross-channel-prediction">Split-Brain Autoencoders: Unsupervised Learning by Cross-Channel Prediction</h2>
<p>This paper proposes a novel autoencoder formulation. The network is split into two disjoint networks, each of which are trained to solve a complementary self-supervised task, e.g., one network predicts the color channels from the intensity channel, and the other predicts the intensity channel from the color channels (they use <em>Lab</em>  color space). The networks are then concatenated to form the representations. This task has the advantage over reconstruction autoencoders in that it does not need a compressive representation nor does it need to drop or corrupt the input data.</p>
<p>They show that training the network with a classification-style loss function leads to image representations that provide state of the art results on all tested unsupervised learning transfer tasks.</p>
<p><strong>Questions</strong></p>
<ul>
<li>I wasn’t quite clear on how they were able to turn the problem into a classification task – I need to look closer at the details</li>
<li>I’m not sure exactly how the networks are concatenated. The intermediate representations would have to stay on their separate paths, because the weights only connect them along the path of the sub-network. I guess it’s only the final representation that is unified.</li>
</ul>

