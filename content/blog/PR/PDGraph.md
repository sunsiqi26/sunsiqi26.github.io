---
title: "PDGraph"
date: 2022-05-24T20:04:02+08:00
draft: false
---

tags: 
  - web
  - hexo

## PR-PDGraph: A Large-Scale Empirical Study on Project Dependency of Security Vulnerabilities

### 简介
代码重用可能带来潜在的安全问题，不同的软件项目可能同时由相互依赖的重用组件引入漏洞。论文通过构建一个新的项目依赖关系图PDGraph，对项目依赖关系与安全漏洞进行了首次大规模实证研究。

### 挑战
- 项目的构建文件只提供分离的依赖关系，需要遍历项目重用库中的构建文件才能获得完整的依赖关系。
  - 解决：将依赖关系分为 Full/Whole Dataset (Maven) 和 Partial Dataset (GitHub) 两类
- 如何整合不同来源数据集(NVD、Maven、GitHub)的信息来判断项目是否存在漏洞。
  - 解决：对漏洞信息和项目依赖间的一致性进行了量化

### 方法
1. 检测依赖关系  
   a) Maven：解析pom.xml建立有向边  
   b) GitHub：针对Java、Ruby、Python、.NET、JavaScript五种语言不同的依赖声明文件，借助API爬取依赖声明文件。将GitHub数据集分为三类：A类(涉及漏洞的项目)、B类(直接使用A类项目库的项目)、C类(间接使用A类项目库的项目)
2. 识别漏洞  
   a) 相似度匹配：统计文本特征提取相关词，使用Levenshtein距离计算Maven、GitHub项目描述和CPE间相似度。  
   b) URL：比较NVD漏洞报告中的url与Maven、GitHub项目的url。  
   c) 第三方数据：Advisory database、CVE、 manually-curated dataset
3. 构建项目依赖图  
   a) 定义四项指标评估依赖风险：依赖项目数量、依赖该项目的项目数量、依赖路径长度、循环依赖。  
   b) 生成依赖图  
   c) 检测不安全的边：正则匹配依赖关系边缘中的需求版本和漏洞版本。 

### 实验
数据集：190,874 个 maven 项目（节点）和 814,331 个依赖关系（边）； 146,541 个GitHub项目和 571,007 个依赖关系

发现：总共从 B 类的 15,455 个 Github 项目中发现了 24,079 个不安全边缘，从 26,986 个 Maven 项目中发现了 43,502 个不安全边缘。换句话说，对于 Maven 数据集，近 76.3% 的跨边不安全，对于 GitHub 数据集，52.3% 的跨边不安全。

### 总结
论文构建了第一个针对漏洞的项目依赖图，发现了大量由于项目依赖性传播而引入的不安全边，可以为代码审计、防御代码重用攻击等提供帮助。但仍存在一些不足：PDGraph基于项目构建文件创建，可能存在人为错误；PDGraph目前不支持构建C和C++项目依赖；并非所有漏洞都是可传递的，现有的不安全边可能存在误报；定义的四项依赖风险评估指标有待完善。