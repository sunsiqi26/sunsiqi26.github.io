---
title: "My First Post"
date: 2022-05-24T20:04:02+08:00
---

## Paper list
- Towards measuring supply chain attacks on package managers for interpreted languages. NDSS (2021)
- Towards using source code repositories to identify software supply chain attacks. In: Proceedings of the 2020 ACM SIGSAC Conference on Computer and Communications Security, (2020)
- Small world with high risks: a study of security threats in the npm ecosystem. In: 28th USENIX 2019
  <!-- - 方法定义：npm依赖图、包维护器、package reach、maintainer reach、 -->
- Containing malicious package updates in NPM with a lightweight permission system[C]//2021 IEEE/ACM 43rd International Conference on Software Engineering (ICSE). IEEE, 2021: 1334-1346.
  - 轻量级权限系统
- An Empirical Study of Dependency Downgrades in the npm Ecosystem. TSE 2019
- Detecting Suspicious Package Updates. ICSE-NIER 2019
- Synode: Understanding and Automatically Preventing Injection Attacks on Node.js. NDSS 2018
- On the impact of security vulnerabilities in the npm package dependency network[C]//Proceedings of the 15th international conference on mining software repositories. 2018
- The case of the poisoned event handler: Weaknesses in the Node. js event-driven architecture[C]//Proceedings of the 10th European Workshop on Systems Security. 2017
- Containing malicious package updates in npm with a lightweight permission system-21 ICSE
  - 轻量级权限系统，包权限向下层传递
  - 权限集：网络连接权限、文件系统权限、进程创建权限、元编程权限
  - 不足：不支持设置细粒度权限；全面正确设置权限集困难大；
- 研究npm许可证兼容  

- There’s no such thing as a free lunch: Lessons learned from exploring the overhead introduced by the Greenkeeper dependency bot in npm - 22 TOSEM
- Deprecation of Packages and Releases in Software Ecosystems: A Case Study on NPM - 21 TSE


1. 定性评估安全性框架
   1. 元数据分析、静态分析、动态分析
   2. 发现229个恶意包
2. mininode静态代码分析，依赖图、减少攻击面
3. AMALFI的轻量级恶意NPM包检测方法。该方法包含3个部分：一个在恶意包和正常包样本上训练的分类器、一个用于从源代码构建包的重构器、一个用于查找已知恶意包的检测器

权限系统
5沙箱、7RWX权限、10latch行为清单