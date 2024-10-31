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











