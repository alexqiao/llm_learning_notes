# llm_learning_notes

## 大模型路线图
<img width="406" alt="截屏2024-03-30 07 35 47" src="https://github.com/alexqiao/llm_learning_notes/assets/17316456/6347750b-6304-4143-b7ad-fe834484d277">

### 机器学习路线图
<img width="565" alt="image" src="https://github.com/alexqiao/llm_learning_notes/assets/17316456/526a70a1-c3ed-4158-af49-2feb5671b090">

### 深度学习路线图
<img width="557" alt="image" src="https://github.com/alexqiao/llm_learning_notes/assets/17316456/343ea410-c948-491a-867b-4ef62747c67a">


## 技术相关
Sora和runaway技术上的区别

Transformer各种变体的区别
transformer 
## 模型微调
lora微调

ptuning




## 大模型应用开发


## 面试题
1. 请具体介绍一下L1、L2正则化。
2. 过拟合怎么解决
3. Dropout 有什么作用？训练和推理时怎么用？
4. 常见的激活函数及其优缺点
5. 数据不平衡问题如何解决
6. 有哪些学习率调整策略
7. Warm up一般是在什么情况下使用的
8. 模型压缩有哪些方法，介绍一下
9. 模型陷入局部极小了怎么办
10. 当资源很少时怎么做数据增强
11. Adam如何设置参数使学习率衰减
12. 为什么出现梯度爆炸，梯度爆炸怎么解决
13. 神经网络权重全 0 初始化会有什么问题？应该怎样初始化？讲讲 Xavier 初始化
14. 现在有哪些归一化方法
15.  学会了哪些网络训练调参技巧

> RAG技术体系的总体思路

数据预处理->分块（这一步骤很关键，有时候也决定了模型的效果）->文本向量化->query向量化->向量检索->重排->query+检索内容输入LLM->输出

> 使用外挂知识库主要为了解决什么问题
克服遗忘问题
提升回答的准确性、权威性、时效性
解决通用模型针对一些小众领域没有涉猎的问题
提高可控性和可解释性，提高模型的可信度和安全性
> 如何评价RAG项目效果的好坏
> 大模型的幻觉问题、复读机问题是什么
> 针对幻觉问题，有没有什么解决办法
> 有哪几种SFT方法
> 什么是lora微调
> RAG的检索阶段，常见的向量检索模型有哪些？
> 针对通用的RAG，你觉得还有哪些改进点？
> 什么是LangChain
>  大模型训练经常出现一些OOM问题，在现有硬件基础下，有什么性能提升trick
>  LLaMA模型输入句子理论上可以无限长吗？
受限于计算资源
训练阶段长句子会导致梯度消失或者梯度爆炸（因为它依赖前面的词进行最大似然估计作为损失函数，这个最大似然估计化简一下就是连乘的形式，容易造成梯度消失或者梯度爆炸）
推理阶段会增加预测错误率
> 如何让大模型处理更长的文本？
> 大模型推理时，显存中有那几部分数据？
> 介绍下ChatGLM
首先要说起它的基座 GLM， GLM 既可以做 Encoder 也可以做 Decoder。
主要通过 两种mask方式来实现：
[mask]： bert形式，随机mask文本中的短span
[gmask]： gpt 形式，mask末尾的长span
在chatglm里面做生成任务时，是用 [gmask]。chaglm2中完全采用 gmask来进行预训练。
在ChatGLM 的内部结构中的变换，从下到上依次是：
位置编码： 从BERT的训练式位置编码转变为旋转位置编码
激活函数：从BERT中的 GeLU 转变为 GLU， 在ChatGLM2 中又变成了SwiGLU
LayerNormalization：采用的是DeepNorm，是对post-Normalization 的改进，即在残差之后做Normalization。在ChatGLM中，把 layer-normalization 改为 RMSNormalization。
> 详细说说Deepspeed的机制
> 什么是混合精度训练
> 什么是prefix LLM和casual LLM
> 为什么现在的LLM都是Decoder only的架构？
