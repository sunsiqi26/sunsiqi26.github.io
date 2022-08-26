---
weight: 4
title: "Paper Reading-OSS"
date: 2022-07-03T21:57:40+08:00
lastmod: 2022-07-04T16:45:40+08:00
draft: false
author: "siqi"
description: "开源软件项目安全与信任的定性研究"
images: []

tags: ["oss", "security"]
categories: ["Paper"]

lightgallery: true

toc:
  auto: true
---
开源软件项目安全与信任的定性研究
<!--more-->


> *原文标题：Committed to Trust: A Qualitative Study on Security & Trust in Open Source Software Projects
>
> *原文作者：Wermke D, Wöhler N, Klemmer J H, et al.*
>
> *原文链接：https://ieeexplore.ieee.org/document/9833686*
>
> *发表期刊：S&P'22*

### 前期工作
- You get where you're looking for: The impact of information sources on code security - S&P 2016
- Security Developer Studies with {GitHub} Users: Exploring a Convenience Sample - SOUPS 2017
  
### 简介
论文通过调查以下3个问题研究OSS中的安全措施和信任过程，讨论了其对开源软件生态系统的影响，以及研究社区如何以信任和安全考虑更好地支持开源项目。
- RQ1：开源项目再安全和信任背景下是如何互动和决策的
- RQ2：开源项目是否提供了哪些指导和安全策略？
- RQ3：开源项目如何应对信任问题

### 访谈及发现
访谈人员：基于先前工作的数据集，筛选其中活跃用户，将受欢迎程度和活动指标合并排名，最终选出27名访谈用户。
- 安全挑战：许多参与者熟悉可疑或低质量的提交项目以及依赖项引入的潜在漏洞，只有少量项目遇到直接的安全问题。
- 指导和安全政策：参与者对（书面的）指导的帮助性有不同的意见。对于安全策略，较大的项目提到了专门的安全团队，而较小的项目提到了安全问题联系通道。
- 项目构建：参与者充分利用了现代的构建系统，只有少数项目显式地使用已签名的提交。
- 发布和更新：参与者大多基于直接的社区输入和反馈来发布项目的发布和更新。
- 角色和责任：大多数项目都没有配备专门用于该项目安全的团队，有些项目要么依赖于组织的资源，要么利用其他团队的成员。
- 信任：大多数参与者在他们的项目中从未经历过信任问题，也没有建立具体的信任策略。
- 问题和改进：建议的改进大致分类为：需要更多的人员贡献（15），需要更多钱（9），或需要基础设施（9）。

### 总结
参与者的项目在部署的安全措施和信任过程及其潜在动机方面都具有高度多样化。随着项目范围和贡献者的增长，它们对安全性和信任流程的需求也在增长。作者主张不要将开源开发人员单独视为数据源，并审查流程黑盒，而是将它们视为为作为一个整体的OSS和软件生态系统带来安全性和信任的宝贵合作伙伴。总的来说，我们主张以更好地考虑其个人优势和局限性的方式来支持开源项目，特别是在贡献者数量较低和资源访问量有限的较小项目中。