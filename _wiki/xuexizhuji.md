---
layout: post
title: 学习助记本
categories: Cat
description: My Favorites and the description.
keywords: Favorites
comments: false
---

My Favorites and the description.

<br/>

## JupyterLab

### Jupyter Notebook使用parser.parse_args出现错误解决办法

在Jupyter Notebook中使用args传递参数时出现错误：
```
---------------------------------------------------------------------------
SystemExit                                Traceback (most recent call last)
<ipython-input-11-9e7fc7cabd7c> in <module>
     10 parser.add_argument('--adjoint', action='store_true')
     11 parser.add_argument('--rate', type=float, default=1e-3)
---> 12 args = parser.parse_args()
     13 args.method = 'rk4'

/opt/tljh/user/lib/python3.7/argparse.py in parse_args(self, args, namespace)
   1750         if argv:
   1751             msg = _('unrecognized arguments: %s')
-> 1752             self.error(msg % ' '.join(argv))
   1753         return args
   1754 

/opt/tljh/user/lib/python3.7/argparse.py in error(self, message)
   2499         self.print_usage(_sys.stderr)
   2500         args = {'prog': self.prog, 'message': message}
-> 2501         self.exit(2, _('%(prog)s: error: %(message)s\n') % args)

/opt/tljh/user/lib/python3.7/argparse.py in exit(self, status, message)
   2486         if message:
   2487             self._print_message(message, _sys.stderr)
-> 2488         _sys.exit(status)
   2489 
   2490     def error(self, message):

SystemExit: 2
```
将原始代码进行修改，修改后为：
args = parser.parse_args(args=[])

修改后即可使用。
()
[Jupyter Notebook使用parser.parse_args出现错误解决办法](https://blog.csdn.net/qq_34277608/article/details/97369630)

### linux下非root 用户安装pip 库

pip install --user *     (* 为安装库的名字)

([非root 用户安装pip 库](https://blog.csdn.net/yeyang911/article/details/78222158?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-1.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-1.control))

## 跨盘符切换目录，安装ta-lib

1.输入cd，可以显示当前目录的名称；

2.关于盘符，我的电脑有C、D、E盘，打开cmd窗口，默认路径是用户文档路径，是C盘下的一个路径，如果想要切换到任何一个C盘下的路径，输入cd 路径是可行的；

3.如果想要切换盘符，则要输入cd /d 路径；也可以不用cd指令，另一个方法是直接输入盘符：例如C:

[python的.whl https://www.lfd.uci.edu/~gohlke/pythonlibs/](https://www.lfd.uci.edu/~gohlke/pythonlibs/)

```
(base) C:\Users\hp>cd /d D:\
(base) D:\>cd /d E:\
(base) E:\>pip install TA_Lib-0.4.19-cp37-cp37m-win_amd64.whl
(base) E:\>C:
(base) C:\Users\hp>D:

```

我的python版本是3.4.4，这个错误的原因如下

可能的原因1：安装的不是对应python版本的库，下载的库名中cp27代表python2.7,其它同理。

可能的原因2：下载的是对应版本的库，然后仍然提示不支持当前平台，文件名格式不对

1.首先第一个错误：

我下载的是CP37，pyth版本是3.4.4，所以下载文件错误，重新下载带CP34的（opencv_python-3.1.0-cp34-cp34m-win_amd64.whl）

## nvidia-smi.exe-监控GPU状态

1.打开CMD

2.输入"C:\Program Files\NVIDIA Corporation\NVSMI\nvidia-smi.exe"


## VRNN and SRNN

[生成时间序列的VAE——VRNN与SRNN模型浅析](https://zhuanlan.zhihu.com/p/272106709)

[两个多变量高斯分布之间的KL散度](https://zhuanlan.zhihu.com/p/55778595)

## 基础数学

[2.6 随机变量的变换](https://zhuanlan.zhihu.com/p/35965931)

## pytorch GPU
[Pytorch将模型加载到GPU中训练时遇到的坑](https://blog.csdn.net/weixin_42118374/article/details/105102153)

[训练网络loss出现Nan解决办法](https://zhuanlan.zhihu.com/p/89588946)

[RuntimeError: DataLoader worker (pid(s) 9528, 8320) exited unexpectedly问题解决记录](https://blog.csdn.net/gyl1050097468/article/details/107523290)

[]()

## 三个概念：Epoch, Batch, Iteration

Epoch（时期）：

当一个完整的数据集通过了神经网络一次并且返回了一次，这个过程称为一次>epoch。（也就是说，所有训练样本在神经网络中都 进行了一次正向传播 和一次反向传播 ）

再通俗一点，一个Epoch就是将所有训练样本训练一次的过程。

然而，当一个Epoch的样本（也就是所有的训练样本）数量可能太过庞大（对于计算机而言），就需要把它分成多个小块，也就是就是分成多个Batch 来进行训练。

Batch（批 / 一批样本）：

将整个训练样本分成若干个Batch。

Batch_Size（批大小）：

每批样本的大小。

Iteration（batch_idx/一次迭代）：

训练一个Batch就是一次Iteration（这个概念跟程序语言中的迭代器相似）。

为什么要使用多于一个epoch?

在神经网络中传递完整的数据集一次是不够的，而且我们需要将完整的数据集在同样的神经网络中传递多次。但请记住，我们使用的是有限的数据集，并且我们使用一个迭代过程即梯度下降来优化学习过程。如下图所示。因此仅仅更新一次或者说使用一个epoch是不够的。

作者：0与1的邂逅

链接：https://www.jianshu.com/p/22c50ded4cf7

来源：简书

著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

训练数据集包含 60,000 个样本, 测试数据集包含 10,000 样本. 在 MNIST 数据集中的每张图片由 28 x 28 个像素点构成, 每个像素点用一个灰度值表示. 在这里, 我们将 28 x 28 的像素展开为一个一维的行向量, 这些行向量就是图片数组里的行(每行 784 个值, 或者说每行就是代表了一张图片). 

## VAE

[苏剑林 VAE1](https://spaces.ac.cn/archives/5253)


## Pytorch

[pytorch专门为研究人员快速实现用的一个库](https://pytorch-lightning-bolts.readthedocs.io/en/latest/introduction_guide.html)

## Neural ODE

[Problem when rtol and atol are iterables](https://github.com/rtqichen/torchdiffeq/issues/4)

[Tried to convert the latent_ode code to run on one dimension of the spiral. #91](https://github.com/rtqichen/torchdiffeq/issues/91)

[Add latent ode example #5](https://github.com/rtqichen/torchdiffeq/pull/5)

## HTML

[RSS 源 xmlParseEntityRef: no name 错误解决方法](https://www.it131.org/8487.html)


直接访问 XML 文件的错误提示：

    This page contains the following errors:
    error on line 1 at column 176713: xmlParseEntityRef: no name
    Below is a rendering of the page up to the first error.

果然不出所料，根据报错行，发现是因为内容中包含一个“&”符号，由于是利用 开发，所以果断的使用了 WordPress 自带的 esc_html 函数，该函数可以将 < > & ” ‘（小于号，大于号，&，双引号，单引号）编码，转成 HTML 实体，已经是实体的并不转换，最后完美解决这个问题。当然如果你不是使用的 WordPress，你可能就需要单独替换或者处理，当然也可以通过删除&符号来解决问题。

