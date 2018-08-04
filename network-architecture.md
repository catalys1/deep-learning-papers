---


---

<h1 id="network-architecture-paper-summaries">Network Architecture Paper Summaries</h1>
<h3 id="table-of-contents">Table of Contents</h3>
<ul>
<li><strong>(ResNeXt) Aggregated Residual Transformations for Deep Neural Networks</strong>
<ul>
<li><a href="https://arxiv.org/abs/1611.05431">[paper]</a></li>
</ul>
</li>
<li><strong>Wide Residual Networks</strong>
<ul>
<li><a href="#wide-residual-networks">[summary]</a> <a href="https://arxiv.org/abs/1605.07146">[paper]</a></li>
</ul>
</li>
<li><strong>Dilated Residual Networks</strong>
<ul>
<li><a href="#dilated-residual-networks">[summary]</a> <a href="https://arxiv.org/abs/1705.09914">[paper]</a></li>
</ul>
</li>
<li><strong>Reversible Residual Networks</strong>
<ul>
<li><a href="https://arxiv.org/abs/1707.04585">[paper]</a></li>
</ul>
</li>
<li><strong>Fractal Networks</strong>
<ul>
<li><a href="https://arxiv.org/abs/1605.07648">[paper]</a></li>
</ul>
</li>
<li><strong>Beyond Finite Layer Neural Networks</strong>
<ul>
<li><a href="https://arxiv.org/abs/1710.10121">[paper]</a></li>
</ul>
</li>
<li><strong>Feature Pyramid Networks</strong>
<ul>
<li><a href="https://arxiv.org/abs/1612.03144">[paper]</a></li>
</ul>
</li>
<li><strong>Squeeze-and-Excitation Networks</strong>
<ul>
<li><a href="#squeeze-and-excitation-nets">[summary]</a> <a href="https://arxiv.org/abs/1709.01507">[paper]</a></li>
</ul>
</li>
<li><strong>Deep Layer Aggregation</strong>
<ul>
<li><a href="#deep-layer-aggregation">[summary]</a> <a href="https://arxiv.org/abs/1707.06484">[paper]</a></li>
</ul>
</li>
<li><strong>Interleaved Group Convolutions</strong>
<ul>
<li><a href="#interleaved-group-convolutions">[summary]</a> <a href="https://arxiv.org/abs/1707.02725">[paper]</a></li>
</ul>
</li>
<li>Other:
<ul>
<li><strong>Introspective Classification with Convolutional Nets</strong>
<ul>
<li><a href="https://arxiv.org/abs/1704.07816">[paper]</a></li>
</ul>
</li>
<li><strong>Wasserstein Introspective Neural Networks</strong>
<ul>
<li><a href="https://arxiv.org/abs/1711.08875">[paper]</a></li>
</ul>
</li>
</ul>
</li>
</ul>
<h2 id="wide-residual-networks">Wide Residual Networks</h2>
<p>This paper investigates the effect of different types of residual-block networks. In particular, they are interested in the effect of “widening” the blocks – increasing the number of convolution feature channels. They do a bunch of experiments with different architectures on several datasets (CIFAR10/100, SVHN, and ImageNet). They show that by increasing the width on residual blocks, they can perform on par or better than ResNets that have roughly the same number of parameters but are significantly deeper. Furthermore, the wide networks are much faster to train, because they make better use of GPU parallelization. They get their results without using the bottleneck architecture prevalent in deep ResNets. They also experiment with adding dropout between convolutions in a block, and show that it leads to better generalization. They attribute this to helping with the overfit introduced by BatchNorm.</p>
<p><strong>Thoughts</strong><br>
This seems like it was a good idea, but it appears that the ResNeXt family of models actually perform a little better.<br>
I wonder if the use of dropout would benefit other models like ResNeXt though?</p>
<h2 id="dilated-residual-networks">Dilated Residual Networks</h2>
<p>This paper presents a modification to ResNets, which removes downsampling operations in order to keep a higher-resolution feature representation, and uses dilated convolutions in order preserve receptive field sizes. They also add several additional layers which serve to remove gridding artifacts introduced by the dilated convolutions and significantly improve results, especially in tasks that need accurate localization such as detection and segmentation. They show that their dilated networks outperform deeper vanilla resnets in classification tasks, and outperform them significantly in detection and segmentation tasks.</p>
<p>This seems like a promising architecture to use, particularly when working with segmentation.</p>
<h2 id="squeeze-and-excitation-nets">Squeeze-and-Excitation Nets</h2>
<p>This paper presents a general architectural block called the squeeze-and-excitation block that can be added to existing network architectures with minimal cost in terms of computation and parameters, but which provides significant boosts in performance across multiple types of architectures, datasets, and tasks. The idea is that functions that operate on local image regions with constrained receptive fields could benefit from knowing something about the global context. This is what motivates the squeeze-and-excitation (SE) block.</p>
<p>In more detail, the SE block consists of a per-channel global average pooling operation followed by a fully-connected layer, ReLU, another fully-connected layer, and a sigmoid. The average pooling operation is a simple way of collecting global spatial statistics across the features at that level. The fully-connected layers form a bottleneck with a non-linearity in the middle. The bottleneck reduces the feature dimensionality (by a factor of 16 in their experiments), in order to keep the number of parameters low and to assist in generalization. The output of the SE block is used to scale the original feature maps. The SE block essentially acts as a gated attention mechanism, which can learn to weight the importance of feature maps based on global information in the input.</p>
<p>The authors show that adding SE blocks to many different architectures results in impressive gains in accuracy, and this finding applies across datasets and tasks. The added complexity of the models is low, with relatively few parameters being added and only a small increase in computation time.</p>
<h2 id="deep-layer-aggregation">Deep Layer Aggregation</h2>
<p>This paper proposes a network architecture that aggregates convolutional features across layers of the network, so that information from multiple scales and depths are combined in a “deep” way: deep meaning used multiple times and in a non-linear manner. The approach extends earlier work such as skip connections and feature pyramid networks. Deep layer aggregation can be added to existing network architectures, and experiments show that it leads to improved performance in both classification and dense prediction tasks, with fewer parameters and fewer computations.</p>
<p>Not the point of the paper, but I wanted to make a note of the augmentation techniques they used in training fine-grained datasets:</p>
<ul>
<li>Scale and aspect ratio variation (as in  <a href="https://arxiv.org/abs/1409.4842">Inception</a>)</li>
<li>PCA color noise (as in  <a href="https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks">AlexNet</a>)</li>
<li>Photometric distortions (varying the brightness, contrast, and color)</li>
</ul>
<h2 id="interleaved-group-convolutions">Interleaved Group Convolutions</h2>
<p>This paper presents a network block called interleaved group convolutions. The block consists of two grouped convolution layers, with group sizes L and M respectively. The output of the first layer is permuted so that each of the M groups in the second layer contains one of the channels from the L groups of the first layer. The layers are then permuted back to their original order after going through the second layer. The authors use a 3x3 convolution for the first layer, and a 1x1 for the second layer. The authors do note that other choices could be made that might complement other designs, and improve parameter efficiency.</p>
<blockquote>
<p>Last,  our  approach  appears  to  be  complementary  to  existing  methods.  Other  spatial  convolutional  kernels,  such as  3  ×  1  and  1  ×  3,  can  also  be  used  in  our  primary  group convolution: decompose  a  3  ×  3  kernel  into  two  successive kernels,  3×1  and  1×3.  The  number  of  output  channels  of primary  group  convolution  can  also  be  decreased,  which  is like  a  bottleneck  design.  These  potentially  further  improve the  parameter  efficiency.</p>
</blockquote>
<p>The authors do analysis that shows that the interleaved convolutions are equivalent to a single, wider convolution, but with less parameters. So one of the advantages is less parameters. They also do experiments that seem to imply the parameters are more efficient, that is, they learn a better representation.</p>
<p><strong>Thoughts</strong><br>
It would be interesting to try and add this in to a ResNeXt architecture and see if it improves things.</p>

