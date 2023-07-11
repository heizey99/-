# - 代码结构
1、导入各种要用到的库

2、结合train.txt，导入有标签的数据，构建起【编号、情感标签、文本、图片张量】的数组，即训练验证数据

3、结合test_without_label，导入无标签数据，构建起【编号、NULL标签、文本、图片张量】的数组，即测试数据

4、将训练验证集和测试集中的文本同时进行TF-IDF向量化，用向量替换文字

5、使用train_test_split随机划分训练集和验证集

6、构建文本流模型txt_stream，图像流模型img_stream，文本+图像的双流模型TwoStream

7、设置模型参数，并根据不同模型的输入需要，准备不同类型的训练集和验证集

8、分别定义文本流/图像流模型、双流模型的训练函数

9、使用one_model_train(txt_model,txt_train_batch,txt_val_batch)对文本流模型进行训练，并考察其在验证集上的表现情况，存储在验证集上表现最好的模型

10、使用one_model_train(img_model,img_train_batch,img_val_batch)对图像流模型进行训练，并考察其在验证集上的表现情况，存储在验证集上表现最好的模型

11、使用two_model_train(two_model,two_train_batch,two_val_batch)对双流模型进行训练，并考察其在验证集上的表现情况，存储在验证集上表现最好的模型

12、利用所存储的最佳双流融合模型来对测试集进行预测，并将数字情感分类标签替换为文字标签写入文件

# - 执行流程
总的来说，因为代码都集中在一个文件内，点击全部运行即可。

如果想分别查看多模态融合模型和消融实验结果模型的情况，可以这样操作：

单独运行one_model_train(txt_model,txt_train_batch,txt_val_batch)：训练单文本流模型

单独运行one_model_train(img_model,img_train_batch,img_val_batch)：训练单图像流模型

单独运行two_model_train(two_model,two_train_batch,two_val_batch)：训练融合模型

# - 调用的主要库
torch、torchvision、sklearn
