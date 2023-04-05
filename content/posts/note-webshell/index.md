---
weight: 4
title: "Note-WebShell"
date: 2022-11-01T14:57:40+08:00
lastmod: 2022-11-01T14:45:40+08:00
draft: false
author: "siqi"
description: "webshell检测"
images: []

tags: ["webshell"]
categories: ["Skills"]

lightgallery: true

toc:
  auto: true
---
WebShell学习记录
<!--more-->

### AST
- Zend AST 节点类型
  - 特殊节点
    - ZVAL 特殊类型，php使用zend_ast_zval专门保存类型
  - 声明节点
  - list节点
    - STMT_LIST：statement_list 表达式类型
    - IF 条件分支
  - 0-4 child nodes
    - 1 child
      - VAL 变量类型 
    - 2 child
      - ASSIGN 赋值类型 
      - BINARY_OP 二元操作符+-*/等
      - IF_ELEM 
      - CALL 函数调用
      - 
    

- 节点说明
  - 翻译单元：package申明、枚举定义、语句列表(statement_list)、block语句
  - 语句：if_then、switch、while、do_while、for、foreach、break、continue、yield、return、throw、assert、synchronized、try、catch、exception、class、interface、函数声明、函数定义、函数头、数组文本
  - 赋值操作符：NODE_TYPE_ASSIGN_*
  - 计算操作符：NODE_TYPE_OPERATOR_*
  - 基本变量
  - 基本说明符
  - 表达式类型：获取属性GET_ATTRIBUTE
  - 描述符相关：static public等
  - 变量声明相关

### webshell特点
Webshell主要分为大马、小马、一句话木马，这三类类型说实话文件特征其实都不太一样，所以想要用一个模型去兼容三类文件的检测，其实不是一件容易的事。

### 恶意样本总结
- getcwd(val/zval) cwd cmd shell_exec
- execute
- chmoD 修改文件权限
- 编码/加解密
  - base64_decode md5
  - urlencode
- login_password
- file / dir
  - dirhandle opendir readdir workingdiR open_basedir CDIR extdir?
  - fread realpath fileRealPath FileInputStream
  - uploaddir(val/zval)
  - download
  - _FILES .php fopen phpcode
- 网络
  - wget curl
  - ftpchecK pop3checK fsockopen fcgi?
  - setsockopt Socket
  - _SERVER servlet
- 数据库
  - mysql_query SELECT语句 mysql_fetch_array
  - updatedb
- pdomain
- log
  - logfilE
- 错误
  - error_reporting display_errors
- 正则
  - preg_match_all ereg reg
- var特殊操作？&
- foo print?
- 敏感信息
  - phpinfo
  - config
    - ServletConfig getServletConfig



### 特征提取

- 混淆特征
  - 字符串函数
  - 编码函数
  - 特殊字符
  - 最长字符串长度
  - 超过特定长度的字符串数量
- API特征
  - 发送敏感信息
  - 查询环境变量
  - 修改文件权限
  - 网络相关
  - 识别os
  - 执行脚本文件
  - 修改标准输入输出

### php知识
- 魔术常量 MAGIC_CONST(__FILE__): 指向当前执行的PHP脚本，__FILE__ 获取当前执行的PHP脚本
- preg_match正则匹配
- PHP_SELF页内跳转
- 

### 模拟执行
当函数名是“不确定性值”，参数是污点时，就能识别出恶意代码。

### 污点分析
一切外部可控的输入都是有害的，通过跟踪有害变量，检查其是否被传入了某些敏感函数。
做动态污点跟踪关键点是设定好污染源、污染传播策略和沉降点。
- 污染源标记
  - 在PHP解释器中，全局变量都保存在一个HashTable类型的符号表symbol_table中，包括预定义变量GLOBALS、$_COOKIE、_GET、$_POST等。利用变量结构体中的flag中未被使用的一位来标识这个变量是否被污染。在初始化过程中首先将𝐺𝐸𝑇、_POST、$_SERVER...等数组中的值标记为污染。
- 沉降点
  - 当被污染的变量作为参数被传入关键函数时，触发关键函数的安全检查代码
- 污染传播策略
  - 显式数据流传播：包括变量的复制、赋值、大部分的字符串处理、隐式函数回调、数组操作。
  - 隐式数据流传播：控制流追踪（if-else、foreach、...）

<!-- 
### 混淆还原

### 技术贴收集 -->

