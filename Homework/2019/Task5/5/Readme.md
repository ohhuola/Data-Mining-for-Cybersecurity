## 基于深度学习，机器学习与Word2Vec的SQL语句检测
### 简介：

​	本项目分别采用机器学习以及卷积神经网络算法训练SQL注入检测模型，主要包括文本处理、提取文本向量和训练检测模型三个部分，实验过程中的数据集主要分为三组训练集(用于训练检测模型的数据)、验证集(训练过程中验证模型的准确率)、测试集(测试训练完成后模型的准确率)。
​	
​	机器学习我们采用了多种算法，包括贝叶斯、SVM、决策树、逻辑斯蒂回归、KNN、随机森林以及adaboost、GBDT,采用了sql注入常用词个数、注释符的个数等特征，可能由于老师提供的数据集中测试集比较少，所以准确率比较高的问题，个别模型的准确率居然达到了100%，召回率在95%左右。
​	
​	卷积神经网络由三个卷积层、三个池化层组成，最后连接全连接层。在基于深度学习的sql注入检测中，我们找了其他现有的基于CNN的sql注入检测中模型的准确率最终可达99.63%。该模型的网络结构图如下图所示：
​	
    ![](https://github.com/scusec/Data-Mining-for-Cybersecurity/blob/master/Homework/2019/Task5/5/Screen/SQL_CNN.png)


### 文件目录
    |-- code
        |-- CNN //CNN检测sql注入的代码实现   
            |-- cnn.py //模型训练的代码
            |-- word.py //数据预处理
            |-- utils.py 
            |-- test_one.py //测试代码
            |--log //训练时的日志文件
        |-- ML //机器学习检测sql注入    
            |--adaboost.py
            |--sqlbys.py
            |--sqltree.py
            |-- sqlsvm.py
            |--sqllogistic.py
            |-- sqlkNN.py
            |-- sqlforestrandom.py
            |--featurepossess.py //特征处理
            |-- test.py //测试代码
    |--model
        |--Adaboost.model
        |--bys.model
        |--forestrandom.model
        |--GBDT.model
        |--knn.model
        |--lg.model
        |--svm.model
        |--tree.model
    |--Screen //相关截图
    
### **环境配置**：
```
    python == 3.6
​    tensorflow==2.0
​    gensim
```

### **文本特征**：

机器学习：

- 语句长度
- 语句特殊字符大小
- 数字字符的频率
- 大写字母的频率
- 空格百分比
- 特殊字符百分比
- 注释符的个数
- sql注入常用词的个数

### 系统流程图

- 机器学习

![](https://github.com/scusec/Data-Mining-for-Cybersecurity/blob/master/Homework/2019/Task5/5/Screen/Frame_ML.jpg)

- 深度学习
![](https://github.com/scusec/Data-Mining-for-Cybersecurity/blob/master/Homework/2019/Task5/5/Screen/Freame_CNN.png)

### 运行
#### 深度学习模型
运行test_one.py即可进行预测，由于该模型没有进行良好的优化，所以模型比较大有84M,由于github单个文件的大小不能超过25M，所以如果要测试请使用我们在百度网盘链接提供的模型(注意一下路径的更改)

如果要自己训练，请使用我们在百度网盘提供的数据集

百度网盘的链接如下:

链接:https://pan.baidu.com/s/1s4WdUx4Mhi4fFD6B1t4IhQ  密码:m6ok

如果要自己运行，请将百度网盘中的数据集下载到本地，然后首先运行word.py来对训练集进行word2vec预处理，之后使用cnn.py来训练模型，最后使用test_one.py进行测试。

#### 机器学习模型
运行/model文件夹中的`test.py`输入payload和要选择的机器学习模型即可进行测试

模型的测试结果已经放到了Screen文件下

            



