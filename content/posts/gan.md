---
title: "Generative Adversarial Networks: AI Breakthroughs and Image Wizardry"
date: 2020-08-22T16:00:00+05:30
url: "/posts/gan-ai-breakthrough-image-wizardry"
# categories:
# - Deep Learning
# - Image Processing
tags: 
- Deep Learning
- Neural Networks
- GAN
- Image Processing
toc: true
draft: false
---

## Introduction

Deepfakes — you may have heard this term thrown around in the field of machine learning. You may have also seen the [almost realistic video](https://www.youtube.com/watch?v=cQ54GDm1eL0) of Barack Obama saying things you'd never expect him to say in public and wondered, “what kind of wizardry is this?”. Let's take a look behind the curtain at the technology that enables this — Generative Adversarial Networks — what it is, how and when it came into being, the impact it is having on the world, and what may lie in a future in which this technology is prevalent.

## In the Beginning

To truly grasp why this technology is revolutionary, let's take a brief look at how deep learning has progressed since its emergence. Almost sixty years ago, the single artificial neuron in the McCulloch-Pitts Model was invented. It could work only with booleans. The perceptron followed, overcoming this drawback by accepting non-boolean inputs. Since then, a multitude of advancements have been made in neural network technology. These advancements have made possible feats previously thought impossible or unachievable in our lifetime. 

The multi-layer perceptron and feedforward networks added layers to the training algorithm allowing in-depth computations and are still used widely in supervised learning; the backpropagation algorithm was revolutionary as it helped tune the weights better, improve accuracy, reduce errors, thereby dramatically improving the learning; recurrent neural networks were used to process sequential and time-based information such as sentiment analysis, text synthesis, speech recognition and other natural language processing applications; convolutional neural networks opened a wide array of possibilities with image processing and computer vision; etc.

While we have been able to transform, classify or predict data with great sophistication, we hadn't really explored the idea of truly generating completely new data until recently. For this reason, generative models have generally been in the back seat.

## Enter GANs

Ian Goodfellow and fellow researchers introduced the Generative Adversarial Network in a [2014 paper](https://arxiv.org/abs/1406.2661). A revolution in deep learning technology, GANs were picked up quickly by other researchers and developers, and have made a lot of noise in and out of the machine learning industry since their arrival. Yann LeCun called GANs the most interesting idea in the past 10 years in machine learning.

GANs are a type of **Deep Generative Models**, i.e., a generative model created with deep neural networks. These models didn't have much of an impact until GANs were invented, due to difficulties such as computing probabilities in the maximum likelihood estimation method that these models follow. GANs were created in a way that they overcame these difficulties and they did it with a very innovative approach.

## How GANs Work

Instead of being a large and complex but single network, the Generative Adversarial Network is in fact made up of **two neural networks**. The first, called the **generator**, generates data; and the second, called the **discriminator**, decides whether the data given to it is from the generator or the actual real-world dataset. Both networks are trained using backpropagation, with the end goal being that the generator achieves a level of sophistication such that the discriminator is no longer able to discriminate between the data from the generator and the actual dataset. This point, when the generator and the discriminator come to an equilibrium, is called the **convergence**. In an ideal case, the discriminator will have only 50% accuracy in distinguishing between real and generated data. Training beyond the convergence can lead to a drop in the quality of data generated. The two networks individually have similar architectures to networks we've seen so far, and are generally multi-layer perceptrons or convolutional networks.

{{< image
src="/images/gan/gan_diagram.svg"
alt="GAN diagram"
height=300
title="Working of a GAN to create images. Image Source: https://developers.google.com/machine-learning/gan/gan_structure - licensed under CC BY 4.0">}}

The aforementioned paper uses an analogy which compares a GAN to a game between counterfeiters and police, where the counterfeiters (generator) try create counterfeit currency (data) and the police (discriminator) have to detect the counterfeits while both of them continuously improve their methods. This ends when the discriminator can no longer distinguish between real data and generated data.

### The Turing Test Analogy

The working of a GAN can also be seen — to an extent — analogous to a Turing Test. The Turing Test was proposed by Alan Turing, to determine whether machines could 'think'. It consists of three players — A, B and C. A and B are machine and human respectively. C plays the role of an interrogator, and is given the task of determining which is which. The machine is said to have passed the Turing Test if C cannot decisively tell the machine from the human. Coming back to a GAN, the discriminator sits in the interrogator's chair, with the task of deciding whether the data came from a real-world source (human) or the generator network (machine).

{{< image
src="/images/gan/turing_test_diagram.png"
alt="Turing Test"
height=300
title="Turing Test. Image Source: https://en.wikipedia.org/wiki/Turing_test - licensed under CC BY 2.5">}}


The Turing Test has stayed relevant to this date as a benchmark for intelligent machines, but never before had a machine played the interrogator. This was a very new concept and the biggest difference. Also, in this case, the interrogator learned along with the machine. Around the same time, a more generalized research was being done — independently of GANs — on allowing machines to learn in a fully automatic competitive manner. This research was later termed '**Turing Learning**'. One might call the idea of computers learning purely by observation pioneering and — given the title of this article — revolutionary, in the field of unsupervised and semi-supervised learning.

## GANs and Image Processing

GANs have taken the world of machine learning by storm. Things have been made possible that previously seemed out of reach — at least for a few more years. The most notable advances have been in the field of Image Processing. This can be attributed to the **continuous nature of image data**, which is the kind of data that GANs produce.

### Deepfakes

The most well-known application might be the deepfakes mentioned at the beginning of this article. Deepfakes are a combination of generated photorealistic images and audio style transfer, using which a person's voice could be made to sound like another person's — as was the case with the Obama deepfake.

### Generating Faces and Altering Styles

GANs can be trained using a dataset of faces in order to **generate completely artificial yet photo-realistic faces**. The generator starts by generating random noise and as training progresses, gradually begins to generate images that look indistinguishable from real people. [This Person Does Not Exist](https://thispersondoesnotexist.com) shows you a different face every time you refresh the page, each belonging to a person that does not exist. GANs can also be trained in a specialized manner to change the styles of objects in images. The [StyleGAN](https://github.com/NVlabs/stylegan) — an architecture designed by researchers at NVIDIA — can differentiate between different aspects of the faces, and then combine them to produce entirely new faces.

### Super-Resolution

GANs — due to their ability to generate data — are also capable of **upscaling low-resolution images into high-resolution ones**. It is the real-world counterpart of the 'zoom-and-enhance' feature from detective television shows. Super Resolution GANs, or [SRGAN](https://arxiv.org/abs/1609.04802), were proposed in 2016. According to the paper that introduced them, they are capable of inferring photo-realistic natural images with a 4 times upscaling factor. This is done by adding the most probable data in-between the pixels of the low-resolution image. There has been further research in this area and a lot of subsequent papers, such as the Enhanced SRGAN ([ESRGAN](https://arxiv.org/abs/1809.00219)), have built on it and proposed more advanced methods of upscaling images.

{{< image
src="/images/gan/ESRGAN-side-by-side.png"
alt="ESRGAN-side-by-side"
height=300
title="Left: Low-Resolution Image. Right: Result of ESRGAN. Image Source: https://github.com/xinntao/ESRGAN - licensed under Apache License 2.0">}}

### Creating Images Out Of Thin Air

Object Detection and Image Captioning have been fundamental problems in the field of Computer Vision for a long time. Identifying individual objects, discerning the context they exist in and then formulating a natural sentence that describes them aptly is no easy task. There has been continuous research on this in recent history.

On the other hand, GANs enabled the reverse of this — **text-to-image synthesis**. A 2017 paper introduced a GAN based architecture called [StackGAN](https://github.com/hanzhanggit/StackGAN), which generates photo-realistic 256x256 images based on semantic descriptions. This research was a significant leap forward in text-to-image synthesis as it was the first architecture to generate relatively higher quality images compared to other approaches — such as the ones which used VAE.

{{< image
src="/images/gan/stackgan-flower.jpg"
alt="stackgan-flower"
title="Image created by a StackGAN in two stages. Image Source: https://github.com/hanzhanggit/StackGAN - licensed under MIT license">}}

A StackGAN creates the images much akin to the way an artist making a sketch. Just like the way an artist creates a rough sketch before adding the nuances, it starts out with a basic low-resolution less detailed version of the image, then adds more details at a later stage. There has been further research in this area since, and various proposals have been made. Hierarchical approaches have been suggested which promise even higher resolutions and preserve semantic details. The technology is still in its infancy and will take some time to mature, but it's both exciting and slightly scary to think about the possibilities once it does in a few years' time.

## Some More Applications of GANs

### Medical Imaging, Informatics and Bioinformatics

This too may come within the territory of Image Processing, but I mention it here due to its specialized nature.

GANs — and deep learning in general — have been used in myriad ways in the field of medicine. To list some of them, they've been used to create high resolution MRI scans, generate 3D high-resolution MRI scans, denoise CT scans, generate embryo cell images, etc. The one I find most impressive is the use of CycleGAN to **synthesize a CT image from an MRI image and vice versa**. Creating accurate and reliable scans of one kind from another without spending the time and money to do both of them can be a huge help in accelerating diagnosis and treatments and reducing healthcare expenditure. 

GANs have also been used in Medical Informatics — [medGAN](https://arxiv.org/abs/1703.06490), a GAN architecture specially designed to **create synthetic health record of patients** to be used for training purposes; and in Bioinformatics to **generate molecular sequences** and data samples which can be used for advancing research in the specific field.

There are a lot more applications of GANs in medicine, but sadly not all of them can be mentioned here.

### Creating New Chemical Compounds and Drugs

GANs can be used to create and test new chemical compounds without synthesizing them in the real world. [CrystalGAN](https://arxiv.org/abs/1810.11203) introduced a new and dedicated architecture which can be used to **generate crystallographic structures** with high order complexity and stability.

[LatentGAN](https://jcheminf.biomedcentral.com/articles/10.1186/s13321-019-0397-9) is a new molecule design method used to **create drug-like compounds**. If it and deep learning solutions like it are successful in drug discovery, the potential benefits to healthcare would be incalculable.

### GANs in Cybersecurity

In 2019, a paper titled '[Efficient GAN-based method for cyber-intrusion detection](https://arxiv.org/abs/1904.02426)' proposed to use GANs to learn the distribution of the 'normal' status in order to **detect abnormalities** (anomalies and possible attacks on the systems). This makes use of the fact that generative networks learn the distribution of the data itself, as compared to a discriminative model learning the probability of a label. The paper also introduced a special loss function in order to tackle the problem of discrete data — which an ordinary GAN is not equipped to handle.

[SSGAN](https://arxiv.org/abs/1707.01613), which stands for Secure Steganography based on GAN — analysis the image to evaluate it for steganography potential. It can be used for both **creating and detecting steganographic images**.

### Games and GANs

Earlier this year, NVIDIA introduced the [GameGAN](https://nv-tlabs.github.io/gameGAN/). This network is capable of learning a video game by observing a user interact with it. It only needs to observe, and does not need to have a peek at the game's engine or logic. It can then **simulate the game** and allow the user to play with the GAN, while giving the user the feel of playing the actual game. It does so with the help of a memory, a dynamic engine and a rendering engine.

The memory allows it to build a map of the environment which the user to seamlessly go back to previously visited spots and maintain visual consistency by not having the rendering engine render the environment again. The Dynamics Engine is the component that learns the 'logic' of the game. Game rules such as interacting with the environment, shooting enemies, not being able to walk through walls, etc. are learned by it. The Rendering Engine takes care of rendering the frames that is to be shown to the user. Owing to the way GameGAN works, it can seamlessly work cross-platform and could run on any OS that supports running the model without having to make OS specific adjustments.

There have also been attempts to **generate game levels** for games such as [Super Mario](https://arxiv.org/abs/1805.00728), [Doom](https://www.technologyreview.com/2018/05/07/143016/ai-generates-new-doom-levels-for-humans-to-play/) and [Zelda](https://medium.com/syncedreview/using-conditional-gans-to-build-zelda-game-levels-6004b30bb753) using GANs. ESRGANs and SRGANs can also be used to **improve the texture of older games**.

## Wrapping Up

This post turned out longer than I expected, but fun and exciting nevertheless. The invention of GANs was one of the most impressive advances in deep learning. Researchers and enthusiasts were quick to adapt and develop on it. As a result, we have seen some extremely innovative ideas and applications.

There have been questions about ethics, after seeing what this technology is capable of and the possible misuses of it. But that's an article for another day. For now, let's think of all the things GANs have helped us accomplish and get excited thinking of what they may help us accomplish in the near future as research continues. 
GANs are — without doubt — a very promising set of tools that have many more milestones to achieve as we progress in the realm of Artificial Intelligence.

*All images licensed under Creative Commons [CC BY 2.5](https://creativecommons.org/licenses/by/2.5), [CC BY 4](https://creativecommons.org/licenses/by/4.0/), [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0) or [MIT License](https://mit-license.org/) and are copyrights of their respective owners.*
