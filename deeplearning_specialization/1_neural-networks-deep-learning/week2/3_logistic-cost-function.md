---
categories: 深度学习工程师

tags: 
  - AI
  - 深度学习工程师
  - 学习笔记
  - 二分分类
  - Logistic
  - sigmoid函数


title: 神经网络和深度学习-第二周神经网络基础-第三节：Logistic 回归损失函数

date: 2017-12-26
---

本系列博客是吴恩达(Andrew Ng)[深度学习工程师](http://mooc.study.163.com/smartSpec/detail/1001319001.htm) 课程笔记。全部课程请查看[吴恩达(Andrew Ng)深度学习工程师课程目录](http://blog.geekidentity.com/deeplearning_specialization/catalogues/)

在上一节中，讲解的是logistic回归模型。为了训练回归模型参数w和b，我们需要定义一个成本函数（cost function）。这是上一节中的函数：
$$
\begin{equation}
\hat{y} = \theta (w^T x + b), \quad where \, \theta (z) = \frac{1} {1+e^{-z}}   
\quad \label{eq:Sample}
\end{equation}
$$
为了让模型通过学习调整参数，需要一个大小为m的训练集：
$$
\{ (x^{(1)}, y^{(1)}) , \, ... \,  (x^{(m)}, y^{(m)}) \}
$$
通过训练集，找到参数w和b，最终使得$\hat{y}^{(i)} \approx y^{(i)}$。

> 符号说明：这里的$\hat{y}$是对一个训练样本x来说的，对于每个训练样本，使用带有圆括号的上标进行引用说明和区分样本。这样，训练样本$x^{(i)}$的预测值是$\hat{y}^{(i)}$，$\hat{y^{(i)}}$是用训练样本$x^{(i)}$通过sigmoid函数作用到$w^T x +b$得到的。

你也可以将$z^{(i)}$定义成$z^{(i)}=w^T x^{(i )} + b$，在这门课里，我们将使用这个符号约定：上标(i)来指明第i个数据样本。

现在我们看看损失函数（或叫作误差函数），它们可以用来衡量算法的运行情况（即衡量你的预测输出值$\hat{y}​$和$y​$的实际值有多近），你可以定义损失为$(\hat{y}-y)^2​$或$\frac {(\hat{y}-y)^2} {2}​$。结果表明你可以这样做，但通常在logistic回归中大家都不这么做，因为你在学习这些参数的时候，你会发现之后讨论的优化问题会变成非凸的，最后会得到很多个局部最优解，梯度下降法可能找不到全局最优值（后面课程会对此做详细讲解）。

误差平方在梯度下降法中不太好用，所以在logistic回归中损失函数如下：
$$
l (\hat{y}, y) = - (y \log \hat{y} + (1-y) \log (1-\hat{y}))
$$
我们直观地看一下这个损失函数为何能起作用，之前我们说误差平方越小越好，同样对于这个logistic回归损失函数，我们也希望它尽可能地小。下面举两个例子。当$y=1$时损失函数为$-\log \hat{y}$此时若让损失函数尽可能小让$\hat{y}$尽可能大（但永远不会大于1）。另一种情况，当$y=0$时损失函数为$- \log (1-\hat{y})$，此时若想要损失函数尽可能小，$\hat{y}$尽可能小即可（$y=0$）。

最后说一下，损失函数是在单个训练样本中定义的，它衡量了在单个训练样本上的表现。下面我们定义一个成本函数，它衡量的是在全体训练样本上的表现，即所有训练样本的损失函数和：
$$
J(w,b)=\frac{1}{m} \sum_{i=1}^m l(\hat{y}^{(i)},y^{(i)}) = -[\frac{1}{m} \sum_{i=1}^m  (y^{(i)} \log \hat{y}^{(i)} + (1-y^{(i)}) \log (1-\hat{y}^{(i)}))]
$$
所以损失函数只适用于单个训练样本，成本函数基于参数的总成本，所以，在训练logistic回归模型时，我们要找到合适的参数w和b，让成本函数$J$尽可能地小。

这里logsitic回归可以被看作一个非常小的神经网络，下节会更直观地去理解神经网络能做什么。