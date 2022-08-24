## 南大程序分析课件
https://tai-e.pascal-lab.net/lectures.html
### Static

- IR中间表示
  [![](../pic/IR.png)]()
  AST不含控制流信息  
  IR包含控制流信息，是静态分析基础
- Three-Address Code (3AC)
- 控制流图CFG
- 数据流分析
  - 变量分析：变量不应在使用前被重新定义
  - 表达式分析
  - 