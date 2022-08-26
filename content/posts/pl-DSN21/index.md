---
weight: 4
title: "DSN'21 paper list"
date: 2021-12-03T21:57:40+08:00
lastmod: 2021-12-03T16:45:40+08:00
draft: false
author: "siqi"
description: "DSN'21相关论文记录"
images: []

tags: ["paper list"]
categories: ["Paper"]

lightgallery: true

toc:
  auto: true
---
DSN'21相关论文记录
<!--more-->


## Statically Detecting JavaScript Obfuscation and Minification Techniques in the Wild
对JavaScript文件执行静态分析，以构建它们的抽象语法树(AST)，使用控制流和数据流对AST进行扩展。定义了两个分类器，基于AST特征检测转换样本以及特定的转换技术。除了恶意样本，我们发现在Node.js库和客户端JavaScript上代码转换越来越常见，例如，90%的Alexa Top 10k网站包含转换后的脚本。这样，代码转换就不是恶意的指示器。最后，我们展示了良性代码转换技术及其频率都不同于流行的恶意代码转换技术。

## Hiding in the Particles: When Return-Oriented Programming Meets Program Obfuscation
面向返回的程序设计（ROP）
将程序功能转换为与周围软件堆栈无缝共存的ROP链。我们展示了如何构建能够承受流行的静态和动态去模糊方法的链，评估了设计的健壮性和开销。结果表明，为了实现秘密发现和代码覆盖的目标，进行去模糊攻击需要大量的计算资源。

## PDGraph: A Large-Scale Empirical Study on Project Dependency of Security Vulnerabilities
论文提出了第一个关于安全漏洞的项目依赖性的大规模实证研究，

## PatchDB: A Large-Scale Security Patch Dataset
从github中收集安全补丁，并开发了一种新的最近链接搜索方法来帮助找到最有希望的安全补丁候选。提供了一个合成数据集，它使用一种新的过采样方法，通过丰富原始补丁的控制流变体，在源代码级别合成补丁。

## When Program Analysis Meets Bytecode Search: Targeted and Efficient Inter-procedural Analysis of Modern Android Apps in BackDroid
动态字节码搜索，提出一种有针对性的过程间分析范式，它可以跳过不相关的代码，只关注安全敏感的sink APIs流。