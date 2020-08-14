# 项目背景

* 情感分析是指用自然语言处理、文本挖掘以及计算机语言学等方法来识别和提取原素材中的主观信息。
* 基于LSTM对酒店评论的情感分析。
* 语言：Python、TensorFlow。

# 数据集

## 数据集介绍

项目训练数据使用的是谭松波老师的酒店评论语料：

* 训练样本放置在两个文件夹内：pos和neg；
* 每个文件夹内有2000个txt文件，每个文件是一段评语，共有4000个训练样本；
* 也可以选择其他样本量：2000，4000，6000，10000。

## 数据集预处理

### 1.读取原始文本

* 依次将pos和neg文件夹中的每一个文件读入一个列表，得到一个长度为4000的字符串train_texts_orig（list）。

### 2.分词与索引化

* jieba分词；

* 预训练词向量使用北京师范大学中文信息处理研究所与中国人民大学 DBIIR 实验室的研究者开源的"chinese-word-vectors"，github链接为：https://github.com/Embedding/Chinese-Word-Vectors。得到存放所有博文分词索引的train_tokens(list of list)；
* 索引长度标准化：长度统一为$np.mean(num_tokens) + 2 * np.std(num_tokens)$，得到train_pad。

### 3.准备Embedding矩阵

## 模型搭建与训练

* 划分测试集与训练集；
* 搭建网络结构：
  * Embedding：使用预训练词向量，参数不可训练；
  * 双向LSTM，参数64；
  * 单向LSTM，参数16；
  * 全连接层。

* 训练模型；
* 测试集评价效果：accuracy=88.25%。