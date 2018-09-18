Skip to content
 
Search or jump to…

Pull requests
Issues
Marketplace
Explore
 @DDDivano Sign out
1
0 2,052 DDDivano/Paddle
forked from PaddlePaddle/Paddle
 Code  Pull requests 0  Projects 0  Wiki  Insights  Settings
Paddle/ 
RELEASE.cn.md
  or cancel
    
 
1
# v0.11.0版本
2
​
3
## PaddlePaddle Fluid
4
​
5
- PaddlePaddle发布版本v0.11.0包含一个新的特性*PaddlePaddle Fluid*. Fluid 是设计用来让用户像Pytorch和Tensorflow Eager Execution一样执行程序。在这些系统中，不再有*模型*这个概念，应用也不再包含一个用于描述Operator图或者一系列层的符号描述，而是像通用程序那样描述训练或者预测的过程。而Fluid与PyTorch或Eager Execution的区别在于Fluid不依赖Python提供的控制流，例如 if-else-then或者for，而是提供了基于C++实现的控制流并暴露了对应的用with语法实现的Python接口。例如：
6
​
7
  https://github.com/PaddlePaddle/Paddle/blob/3df78ed2a98d37f7ae6725894cc7514effd5664b/python/paddle/v2/fluid/tests/test_while_op.py#L36-L44
8
​
9
- 在v0.11.0版本中，我们提供了一个C++类`Executor`用于运行一个Fluid程序。Executor类似一个解释器。在未来的版本中，我们将提升和优化Executor成为一个调试器，就像GDB。并可能提供一些编译器，这个编译器会读取一个上文所描述的应用然后编译成一个等价的
10
源代码，这个源代码可以被nvcc编译成可以使用CUDA的二进制，或者被icc编译成可以充分利用Intel CPU的二进制。
11
​
12
​
13
## 新特点
14
​
15
* 发布 `PaddlePaddle Fluid`。
16
* 增加了用于模型预测的C-API。
17
* 用Fluid API实现了一个简单的GAN的例子。
18
* 增加了关于性能调优的文档。
19
* 为`paddle.v2.dataset`下载数据集提供了重试机制.
20
* C++中使用protobuf-lite替换protobuf减少了二进制的大小。
21
* 发布了新特性 [Elastic Deep Learning (EDL)](https://github.com/PaddlePaddle/cloud/tree/develop/doc/autoscale/experiment).
22
* 基于Bazel API利用cmake实现了一个的新的构建系统函数库。
23
* 当使用编译选项`WITH_MKL=ON`时自动下载和编译Intel® [MKLML](https://github.com/01org/mkl-dnn/releases/download/v0.11/mklml_lnx_2018.0.1.20171007.tgz) 函数库.
24
* [Intel® MKL-DNN on PaddlePaddle](https://github.com/PaddlePaddle/Paddle/tree/develop/doc/design/mkldnn):
25
  - 完成了 11个 MKL-DNN 层: Convolution, Fully connectivity, Pooling, ReLU, Tanh, ELU, Softmax, BatchNorm, AddTo, Concat, LRN。
26
  - 完成了 3个 MKL-DNN 网络: VGG-19, ResNet-50, GoogleNet
27
  - 基于Intel Skylake 6148 CPU的[性能测试](https://github.com/PaddlePaddle/Paddle/blob/develop/benchmark/IntelOptimizedPaddle.md) : 相对于MKLML有2~3倍的训练加速。
28
* 增加 [softsign activation](http://www.paddlepaddle.org/docs/develop/documentation/zh/api/v2/config/activation.html#softsign)
29
* 增加 [dot product layer](http://www.paddlepaddle.org/docs/develop/documentation/zh/api/v2/config/layer.html#dot-prod)
30
* 增加 [L2 distance layer](http://www.paddlepaddle.org/docs/develop/documentation/zh/api/v2/config/layer.html#l2-distance)
31
* 增加 [sub-nested sequence layer](http://www.paddlepaddle.org/docs/develop/documentation/zh/api/v2/config/layer.html#sub-nested-seq)
32
* 增加 [kmax sequence score layer](http://www.paddlepaddle.org/docs/develop/documentation/zh/api/v2/config/layer.html#kmax-sequence-score)
33
* 增加 [sequence slice layer](http://www.paddlepaddle.org/docs/develop/documentation/zh/api/v2/config/layer.html#seq-slice)
34
* 增加 [row convolution layer](http://www.paddlepaddle.org/docs/develop/documentation/zh/api/v2/config/layer.html#row-conv)
35
* 增加移动端友好的网页
36
​
37
## 改进
38
​
39
* 使用一个Python`whl`包即可安装.
40
* [V2 API可以实现用户定制化评估](https://github.com/PaddlePaddle/models/tree/develop/ltr#训练过程中输出自定义评估指标)。
@DDDivano
Commit changes

Update RELEASE.cn.md

Add an optional extended description…
  Commit directly to the develop branch.
  Create a new branch for this commit and start a pull request. Learn more about pull requests.
 
© 2018 GitHub, Inc.
Terms
Privacy
Security
Status
Help
Contact GitHub
Pricing
API
Training
Blog
About
Press h to open a hovercard with more details.
