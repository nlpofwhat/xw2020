# xw-bank-2020

con2d model部分参考 https://github.com/ycd2016/xw2020_cnn_baseline
cnn1d model部分参考 https://github.com/blueloveTH/xwbank2020_baseline_keras

# cnn2d从开始的线上0.708到0.775

# 主要环境
python 3.5
tensorflow 1.12.0
keras 2.2.4
cuda 9.0
cudnn 7.4


# trick and failure

1 全局标准化用这个上分挺多的，把训练集和测试集放在一起做标准化<br>
2 label smoothing<br>
3 这个任务很奇怪小batch_size会有更好的效果<br>
4 优化方法也尝试了很多发现还是Adam比较好，其他的也可能太难调<br>
5 本来觉得姿态角是个很强的特征，结果发现不怎么好用<br>
6 resample重采样这个是为了等间隔采样<br>
7 cnn2d收敛很快，cnn1d收敛很慢不知道为什么，前者参数量15M,后者参数量6M,后面训练速度真实很慢，前者5折交叉的val acc大概0.77-0.80左右，
  后者的val acc基本都是0.82-0.83从损失函数和来讲后者的效果应该好很多<br>
8 这个比赛也尝试了一些resnet，convlstm，transformer，lstm-attention但效果都不太好<br>
9 数据增强尝试加高斯白噪声，mixup好像都没什么效果，奇怪的是加了mixup后，训练集acc0.9的时候就差不多收敛了效果并没有更好<br>
10 基于半监督的伪标签算法也可以尝试下这个大致就是使用训练的模型对测试集进行预测，然后结合训练集和测试集的数据一起进行训练，不过在计算损失的时候在伪标签数据上加上一个惩罚系数<br>
