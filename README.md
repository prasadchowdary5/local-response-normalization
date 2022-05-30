Convolutional Neural Networks (CNNs) have been doing wonders in the field of image recognition in recent times. CNN is a type of deep neural network in which the layers are connected using spatially organized patterns. This is in line with how the human visual cortex processes image data. Researchers have been working on coming up with better architectures over the last few years. In this blog post, we will discuss a particular type of layer that has been used consistently across many famous architectures. This layer is called Local Response Normalization layer and it plays an important role. What does it do? What’s the advantage of having this in our network?  

Why do we need normalization layers in the first place?

A typical CNN consists of the following layers: convolution, pooling, rectified linear unit (ReLU), fully connected, and loss. If the previous sentence didn’t make sense, you may want to go through a quick CNN tutorial before proceeding further. Anyway, the reason we may want to have normalization layers in our CNN is that we want to have some kind of inhibition scheme.

In neurobiology, there is a concept called “lateral inhibition”. Now what does that mean? This refers to the capacity of an excited neuron to subdue its neighbors. We basically want a significant peak so that we have a form of local maxima. This tends to create a contrast in that area, hence increasing the sensory perception. Increasing the sensory perception is a good thing! We want to have the same thing in our CNNs.

What exactly is Local Response Normalization?

Local Response Normalization (LRN) layer implements the lateral inhibition we were talking about in the previous section. This layer is useful when we are dealing with ReLU neurons. Why is that? Because ReLU neurons have unbounded activations and we need LRN to normalize that. We want to detect high frequency features with a large response. If we normalize around the local neighborhood of the excited neuron, it becomes even more sensitive as compared to its neighbors.

At the same time, it will dampen the responses that are uniformly large in any given local neighborhood. If all the values are large, then normalizing those values will diminish all of them. So basically we want to encourage some kind of inhibition and boost the neurons with relatively larger activations. This has been discussed nicely in Section 3.3 of the original paper by Krizhevsky et al.

How is it done in practice?

There are two types of normalizations available in Caffe. You can either normalize within the same channel or you can normalize across channels. Both these methods tend to amplify the excited neuron while dampening the surrounding neurons. When you are normalizing within the same channel, it’s just like considering a 2D neighborhood of dimension N x N, where N is the size of the normalization window. You normalize this window using the values in this neighborhood. If you are normalizing across channels, you will consider a neighborhood along the third dimension but at a single location. You need to consider an area of shape N x 1 x 1. Here 1 x 1 refers to a single value in a 2D matrix and N refers to the normalization size.
