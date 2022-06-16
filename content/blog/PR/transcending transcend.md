---
title: "PR2"
draft: false
---

tags: 
  - web
  - hexo

##  Transcending TRANSCEND: Revisiting Malware Classification in the Presence of Concept Drift

### 简介
由于恶意软件作者调整他们的技术以逃避检测，基于机器学习的恶意软件分类在实际部署时会出现性能下降问题。针对恶意软件的概念漂移问题，作者提出了一个Transcend拒绝框架，基于conformal prediction理论。对一个跨越5年的恶意软件数据集进行评估，性能优于最先进方法。

### 背景
- 概念漂移：概念漂移是分布Py∈(y|x∈x)的变化。当groud truth定义改变时，这种情况经常发生。在安全社区中，通常将所有类型的漂移统称为概念漂移。
- rejection：Transcend框架评估一个新的测试示例是否相对于训练数据发生了漂移，如果一个分类器的预测似乎受到漂移的影响，则该预测将被拒绝。

### 方法
