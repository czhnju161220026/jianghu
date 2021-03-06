# 2019大数据综合实验-金庸的江湖

## 任务描述

### 任务1 数据预处理 

数据输入：1.全本的金庸武侠小说文集（未分词）；2. 金庸武侠小说人名列表。
数据输出：分词后，仅保留人名的金庸武侠小说全集。 

### 任务2 特征抽取：人物同现统计 

如果两个人在原文的同一段落中出现，则认为两个人发生了一次同现关系。  

输入：任务 1 的输出；
输出：在金庸的所有武侠小说中，人物之间的同现次数。 

### 任务 3 特征处理：人物关系图构建与特征归一化 

将共现次数转换为共现概率。

**示例**
输入：

```
<狄云，戚芳> 1
<狄云，戚长发> 1
<狄云，卜垣> 1
<戚芳，狄云 > 1
<戚芳，戚长发 > 1
<戚芳，卜垣 > 2
<戚长发，狄云 > 1
<戚长发，戚芳 > 1
<戚长发，卜垣 > 1
<卜垣，狄云> 1
<卜垣，戚芳> 2
<卜垣，戚长发> 1
```

输出：

```
狄云 [戚芳,0.33333|戚长发，0.333333|卜垣 0.333333]
戚芳 [狄云,0.25 |戚长发，0.25|卜垣 0.5]
戚长发 [狄云,0.33333|戚芳，0.333333|卜垣 0.333333]
卜垣 [狄云 0.25|戚芳,0.5|戚长发，0.25] 
```

### 任务4 数据分析：基于人物关系图的PageRank计算 

输入：任务3的输出
输出：人物的PageRank值 

### 任务5 数据分析：在人物关系图上的标签传播（选做）

标签传播

### 任务6 分析结果整理（选做）  

排序与整理

## 打包 及 运行方法
### 打包
mvn package -Dhttps.protocols=TLSv1.2

### 运行
hadoop jar *.jar cn.nju.st13.Main arg0 arg1 arg2 
+ arg0:小说路径
+ arg1:人名文件
+ arg2:输出路径


