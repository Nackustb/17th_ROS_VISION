# 17th_ROS

#### 双系统安装

```
指定版本:ubuntu20.04版本
参考网站：
https://zhuanlan.zhihu.com/p/135953477
https://blog.csdn.net/qq_41565526/article/details/88900171
https://www.bilibili.com/video/BV1554y1n7zv/
或可在B站、百度、csdn等网站查找相关教程
```



#### ROS安装

```
指定版本： ROS Noetic
参考网站：
http://wiki.ros.org/    				 
http://wiki.ros.org/cn
古月居ROS入门21讲:
https://www.bilibili.com/video/BV1zt411G7Vn
可在B站、百度、csdn等网站查找教程
```





## 非负责图像的参赛队员无需进行以下步骤



#### CUDA安装

```
根据自己的显卡驱动，选择适配的CUDA

相关教程：
https://blog.csdn.net/qq_43665602/article/details/125752433
https://blog.csdn.net/qq_41295081/article/details/125240142
		
搜索关键词：ubuntu cuda安装
```



#### OPENCV安装

```
推荐版本：3.4.15
相关教程：https://blog.csdn.net/weixin_45525272/article/details/122154145
```





#### 安装darknet

##### step0 你需要具有的环境

```
1.一个ubuntu20.04的双系统而不是虚拟机，建议分配空间>50GB。
2.一台带有Nvidia显卡的电脑
3.确保在你的双系统中已经配置好cuda、opencv等环境。
```

##### step1 安装git

```
在终端中输入 sudo apt install git
```

##### step2 克隆工程

```
在终端中输入 git clone https://github.com/Nackustb/17th_ROS_VISION.git
```

##### step3 编译darknet

```
打开终端，cd 进darknet所在的目录
输入make 指令，等待编译
如果没有报错，恭喜你成功编译～
完成后在终端输入./darknet detect cfg/yolov4.cfg yolov4.weights data/person.jpg
成功执行后，即可以看到该模型对示例图片的识别结果。
```

![](https://nack-1316646329.cos.ap-nanjing.myqcloud.com/predictions.jpg)

##### step4 开始尝试训练自己的数据集。

```
（1）在scripts文件夹下按如下目录创建VOCdevkit 文件夹，放自己的训练数据。
VOCdevkit
--VOC2007
----Annotations  #（XML标签文件）
----ImageSets
------Main
----JPEGImages   # (原始图片)
（2）划分训练集、测试集等文件
（3）生成图片的labels标签文件
（4）修改data/voc.names
（5）修改cfg/voc.data
（6）修改cfg  训练参数修改：包括batch、max_batches ,其中max_batches=classes*2000,;修改filters个数：（classes + 5）;修改类别数classes  
（7）在终端中执行./darknet detector train cfg/voc.data cfg/yolov4-tiny.cfg yolov4-tiny.weights -map 
```

在本仓库中，对于step4，你只需修改voc.data下的路径即可开始训练。

想要获得更好的结果吗？ 尝试了解yolov4-tiny.cfg中的超参数并修改他们后进行训练

##### step5 检验模型

```
将你需要检测照片保存至data目录下,我们暂时命名为val.jpg
cd至darknet路径下并在终端中执行./darknet detector test cfg/voc.data cfg/yolov4-tiny.cfg backup/yolov4-tiny_best.weights ./data/val.jpg
```



推荐相关网站：

```
https://www.bilibili.com/
https://www.csdn.net/
https://github.com/    
https://gitee.com/
https://www.guyuehome.com/
```

