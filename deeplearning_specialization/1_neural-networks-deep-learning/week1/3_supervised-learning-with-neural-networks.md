---
categories: 深度学习工程师

tags: 
  - AI
  - 深度学习工程师
  - 学习笔记
  - 监督学习
  - 神经网络和深度学习

title: 神经网络和深度学习-第一周深度学习概论-第三节：用神经网络进行监督学习

date: 2017-12-14
---

本系列博客是吴恩达(Andrew Ng)[深度学习工程师](http://mooc.study.163.com/smartSpec/detail/1001319001.htm) 课程笔记。全部课程请查看[吴恩达(Andrew Ng)深度学习工程师课程目录](http://blog.geekidentity.com/deeplearning_specialization/catalogues/)

神经网络有时被媒体炒作得很厉害，考虑到它们的使用效果，有些说法还是靠谱的。事实上，到目前为止，几乎所有由神经网络创造的经济价值都基于其中一种机器学习--我们称之为“监督学习”，我们来看一些例子。
![image](http://blog.geekidentity.com/images/deeplearning_specialization/neural-networks-deep-learning/week1/3_supervised-learning-with-neural-networks/supervised_learning.PNG)

在监督学习中输入x，学习到一个函数，映射到输出y，比如我们之前看到的应用于房价预测的例子：输入房屋的一些特征就能输出价格y。下面是一些其他例子，这些例子中神经网络效果非常好。很可能今天通过深度学习获利最大的就是在线广告，给网站输入广告信息（有时还需要输入一些用户信息），网站会考虑是否给你看这个广告。神经网络在预测你是否会点击这个广告方面已经表现的很好了。

过去几年里，计算机视觉也有很大进步，这要感谢深度学习。你输入一个图像，然后想输出一个指数，可以是从1到1000来表明这张照片是1000个不同的图像中的某一个，可以用来给照片打标签。

深度学习最近在语音识别方面的进展也是令人兴奋的，你可以将音频片段输入神经网络，它可以输出文本。

机器翻译也有很大的进步，这得感谢深度学习让你有一个神经网络能实现，输入英文句子，它直接输出一个中文句子。

在无人驾驶技术中，你输入一副图像（汽车前方的一个快照），还有一些雷达信息，基于这个训练过的神经网络，能告诉你路上其他汽车的位置，这是无人驾驶系统的关键组件。

神经网络创造这么多价值的案例中，你要机智的选择x和y才能解决特定问题，然后把这个监督学习过的组件嵌入到更大型的系统中，比如无人驾驶。

可以看出稍微不同的神经网络应用到不同的地方，也都先之有效。比如说，应用到房地产上，我们上节课看到了我们用了通用标准的神经网络架构，对于房地产和在线广告用的都是相对标准的神经网络。正如我们之前见到的，图像领域里我们经常应用的是CNN（卷积神经网络）；对于序列数组，例如音频中含有时间成分（音频是随时间播放的，所以音频很自然地被表示为一维时间序列），对于序列数据你经常使用RNN（循环神经网络）。语言，英语和汉语字母或单词都是逐个出现的，所以语言最自然的表示方式也是序列数据，列复杂的RNN经常用于这些应用。

对于更复杂的应用，比如无人驾驶，你有一张图片可能需要CNN架构去处理。雷达信息会更不一样，你需要一些更复杂的混合的神经网络结构。所以，为了更具体地说明标准的CNN和RNN结构是什么。在论文文献中你可能见过这样的图片，这是一个标准的神经网络：
![image](http://blog.geekidentity.com/images/deeplearning_specialization/neural-networks-deep-learning/week1/3_supervised-learning-with-neural-networks/standard_nn.png)

你可能见过这样的图片，这是一个卷积神经网络，在后续的课程我们会了解这幅图的含义和如何实现它，卷积网络通常用于图像处理。
![image](http://blog.geekidentity.com/images/deeplearning_specialization/neural-networks-deep-learning/week1/3_supervised-learning-with-neural-networks/convolutional_nn.png)

你可能也会看到这样的图片后续的课程也会实现它，循环神经网络，非常适合处理一维序列数据，其中包含时间成分。
![image](http://blog.geekidentity.com/images/deeplearning_specialization/neural-networks-deep-learning/week1/3_supervised-learning-with-neural-networks/recurrent_nn.png)

你可能也听说过机器学习被应用于结构化数据（Structured Data）和非结构化数据（Unstructrured Data），下面是这些术语的含义。结构化数据是数据的数据库。例如在房价预测中，你可能有一个数据库或者数据列告诉你房间的大小和卧室数量，这就是结构化数据。在预测用户是否会点击广告的例子中，你可能会有用户信息，比如年龄，还有广告信息，还有你要预测的标签y，这就是结构化数据意味着每个特征比如说房屋大小，卧室数量，用户的年龄，都有着清晰的定义。
![image](http://blog.geekidentity.com/images/deeplearning_specialization/neural-networks-deep-learning/week1/3_supervised-learning-with-neural-networks/structured_data.png)

相反，非结构化数据比如音频、视频、图像，你想要识别图像或文本中的内容。这里的特征可能是图像中的像素值。或者文本中的单个单词。
![image](http://blog.geekidentity.com/images/deeplearning_specialization/neural-networks-deep-learning/week1/3_supervised-learning-with-neural-networks/unstructured_data.png)

从历史角度看，非结构化数据与结构化数据比较，让计算机理解起来更难。但人类进化到现在，委擅长理解音频信号和图像。文本是一个更近代的发明，但人类更擅长解读非结构化数据。神经网络的兴起过程中最令人兴奋的事情之一就是，深度学习使计算机更好的解释非结构化数据。这给我们创造了很多令人兴奋的应用机会，语言识别，图像识别、自然语言处理，现在能做的事情比两三年前要丰富多了。

我个人认识因为人类生来就有能力理解非结构化数据，你可能知道，神经网络在非结构化数据上的成功尤其是媒体。当神经网络识别了一只猫时，那直的很酷。神经网络在很多短期经济价值的创造是基于结构化数据的，比如更好的广告系统，更好的获利建议，有更好的能力去处理很多公司拥有的海量数据库，并用这些数据准确预测未来趋势。在这门课中，我们会学到很多技巧，可以应用到结构化数据也可以应用到非结构化数据。为了更清楚地解释算原理，我们会多用非结构化数据的例子，但当你自己的团队评估了各种神经网络的应用之后希望你的算法能够同时学习结构化和非结构化数据。

神经网络彻底改变了监督学习，正创造着巨大的经济价值。其实，基本的神经网络背后的技术概念大部分都不是新概念，有些甚至有几十年历史了，那么为什么它们现在才流行，才行之有效呢。下一集视频中，我们将讨论为什么是最近神经网络才成为你可以使用的强大工具。
