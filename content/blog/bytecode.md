---
title: "bytecode"
date: 2022-05-26T20:04:02+08:00
draft: true
---

## V8 bytecode

### 环境
win10 + vs2017  
下载链接：https://my.visualstudio.com/Downloads?q=visual%20studio%202017&wt.mc_id=o~msft~vscom~older-downloads  
企业版：NJVYC-BMHX2-G77MM-4XJMR-6Q8QF   
专业版：KBJFW-NXHK6-W4WJM-CRMQB-G3CDH
```
git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git
fetch v8
git checkout -b 7.3 -t branch-heads/7.3

set DEPOT_TOOLS_WIN_TOOLCHAIN=0
set GYP_MSVS_OVERRIDE_PATH=F:\Microsoft Visual Studio\2017
set WINDOWSSDKDIR=D:\Windows Kits\10

gclient sync
python3 tools\dev\v8gen.py x64.debug 
```

### 指令
- StackCheck：固定出现，检查stack有没有overflow 
- Ld*属于加载到累加器的指令集
- Star寄存器操作指令
- src/interpreter/interpreter-generator.cc

### 功能
1. 变量赋值，寄存器变化，抛出错误
2. 判断式，对于 if (true) 这种case，V8 Ignition 会做优化。在程式码中同一个字串是可以被重复利用的，都是指向同一个constant pool 的元素
3. loop，
4. 函数


### bytecode序列能否应用于为静态分析兜底分析代码意图