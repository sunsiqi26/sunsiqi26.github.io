# Paper Reading-TPL

基于程序模块化和语义匹配的二进制级别三方库检测
<!--more-->


> *原文标题：ModX: Binary Level Partially Imported Third-Party Library Detection via Program Modularization and Semantic Matching*
>
> *原文作者：Yang C, Xu Z, Chen H, et al.*
>
> *原文链接：https://dl.acm.org/doi/pdf/10.1145/3510003.3510627*
>
> *发表会议：ICSE'22*


## 简介
随着软件的快速增长，使用第三方库(TPL)变得越来越流行。多数现有的方法依赖于句法特征，当这些特征被敌对双方改变或故意隐藏时，这些方法并不健壮。此外，这些方法通常将每个导入的库作为一个整体建模，因此，不能应用于主机软件仅部分使用库代码段的情况。
论文提出了ModX，利用程序模块化技术将程序分解成细粒度的基于功能的模块的框架。通过提取句法和语义特征，测量模块之间的距离来检测程序中相似的库模块重用。
第一个挑战是将给定的程序划分为有意义的和实用的模块。
本工作的第二个挑战是通过提取合适的特征来准确地度量模块之间的语义级相似性。

对模块进行语义匹配以检测完全或部分导入的TPL
首先，modx定义了模块质量评分来评估函数聚类的一致性。对于给定库，将单个函数分组形成模块，最大化整体模块的质量分数。然后从模块间和模块内级别中提取语法和语义特征，度量模块间相似性。


## 方法
- 二进制模块化阶段
  - 基于社区检测算法的模块度量方法，Girvan–Newman Algorithm，节点连通度
  - 函数大小(核心功能倾向于更长的代码)，提出了函数体积权值传播算法，将权值调整添加到度量中。完整模块和相关模块倾向更高的得分。根据其体积和连通性为每个函数分配不同的权重。对于具有层次结构的程序，该传播算法保证了顶级函数比低级函数得到更多的关注。
- TPL检测阶段
  - 提取句法特征（TF-IDF为特殊的字符串常数分配更多权重）、
  - 拓扑特征（图相似性，通过propagation graph kernel算法度量图结构相似性，通过RouAlign算法衡量边相似性。
  - 函数特征，利用二进制函数匹配工具Gemini来产生两个给定函数之间的相似性得分。

USENIX 21
- Saphire: Sandboxing PHP Applications with Tailored System Call Allowlists
  - 缺乏特权分离违反了最小特权原则(PoLP)
  - 计算每个脚本依赖关系的传递闭包，将内置函数替换为相应的系统调用，输出是每个脚本的系统调用配置文件（即允许列表）
  - 

ASPLOS 21
- Enclosure: language-based restriction of untrusted libraries
  - 页表映射、对元包访问权限编码


流式系统调用分段，窗口分隔
用strace工具提取系统调用。系统调用的每次调用都被映射到一个基于频率的特征向量
n-gram
流量到许可+意向





