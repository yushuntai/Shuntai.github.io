---
layout: post
title:  " GEO database"
tags: 实验方法与科研小技巧
date:   2024-10-31
categories: Front-end JavaScript
excerpt: 实验方法与科研小技巧
---

**目录：**

* content
{:toc}

# GEO database

随着基因芯片技术的广泛应用，产生了海量的数据，迫切需要一个统一管理的平台。基因表达数据库(Gene Expression Omnibus，GEO):隶属于NCBI，是当今最大、最全面的公共基因表达数据资源。
Platform：表示数据用什么芯片检测的，平台的检索号为GPL。
Series：每个实验的相关样本集中成的数据集合，检索号是GSE开头。
Sample：表示样本，检索号为GSM。

Dataset:存储经过多种手段处理和不同方法分析的高通量实验数据。GEO数据集组能提供关于一个实验的相关梗概，以此作为下游数据挖掘和数据显示的工具。数据集组的检索号为GDS****，
Profiles:表达谱数据存储了来自与DataSets基因表达谱信息。每一个表达谱都表现为一个能反映一个数据集组中所有样本的基因表达量的统计图。

[GEO数据库官网](https://www.ncbi.nlm.nih.gov/geo/)


GEO数据处理7个步骤：<br>
1、下载GEO矩阵数据 <br>
2、数据进行标准化，并通过箱线图对比标准化前后结果 <br>
3、下载平台注释文件进行ID转换：将探针ID数据匹配到Symbol上 <br>
4、数据清洗：保留在所有样本里面表达最大的那个探针 <br>
5、limma包筛选出差异基因 <br>
6、差异基因可视化：热图、火山图 <br>
7、KEGG通路分析、GO分析、GSEA分析 <br>




# 数据查询与下载+读取

[GEO数据库挖掘](https://mp.weixin.qq.com/s/XynaAMHKjuejixXxxVB7Vw)

```R
#  gset <- getGEO("GSE735566", GSEMatrix=TRUE, AnnotGPL=TRUE, destdir=".")
setwd("D:/data")
Rawdata=read.table('GSE182373_series_matrix.txt.gz', sep = '\t', quote ="", fill = T, comment.char = "!", header = T);head(Rawdata)
#读进来发现第一列的字符串带有引号，写循环太麻烦，用quote=F手动给去掉一下
write.table(Rawdata, file = "test.csv",sep=",", row.names = F,quote = F)
Raw2=read.table('test.csv',sep=",",header=T);head(Raw2)
rownames(Raw2)=Raw2[,1];head(Raw2)   #将第1列命名给行
Raw2=Raw2[,-1];head(Raw2)   # 将命名后的文件第1列删除。
```

# 下载注释文件+基因symbol ID

现在得到的data.frame列名是样本名，行名是探针ID，我们要得到 行名是 gene symbol 的表达矩阵。将探针ID转成gene symbol的方法
方法一：如果很幸运的话，文章里用到的芯片是比较常用的芯片，在各个平台都可以搜到注释包，例如GPL15396的注释包就为hthgu133b.db，然后直接library这个包就可以了.
方法二：点击GEO数据库下载页面的 GPL，如果有上传注释包的话就可以直接下载，下载完之后，直接到 下文1.4 步骤接着往下做

![image](https://github.com/user-attachments/assets/cbe20ef0-5892-40fe-a6d6-1a01cb252855)


```R




```








