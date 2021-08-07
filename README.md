# simple-interpreter

这是一个简单的数学运算解释器(interpreter)

## 如何运行

利用项目目录下的venv环境直接运行parser.py文件即可，或者使用您自己的Python环境运行。

推荐使用Python 3.x 版本，低于Python3 版本的需要在main函数中修改输入函数。

## 支持的运算式

1. 支持单个数字输入，例如：
   ```
   1
   -1
   (1)
   -(1)
   ```
2. 支持的二元运算符: + - * /    例如：
   ```
   1 + 1
   ```
3. 支持多位数字运算，例如：
   ```
   10 + 10
   ```
4. 支持带有括号的运算式，例如：
   ```
   1 + (1 + 1)
   ```
5. 支持的一元运算符: + -    例如：
   ```
   1 + - 1 = 1 - 1 = 0
   1 - - 1 = 1 + 1 = 2
   ```
6. 支持消除运算式中的空白字符，例如
   ```
   1   +    1
   ```

## 原理分析

1. 程序结构
2. 语法分析
   ```
   expr : term ((PLUS | MINUS) term)*
   term : factor ((MUL | DIV) factor)*
   factor : INTEGER | LPAREN expr RPAREN | (MUL | DIV) factor
   ```
   注意：文法中的括号并不是终结符，只有LPAREN和RPAREN才表示为终结符中的括号

    非终结符：
    - expr 运算式
    - term 项
    - factor 因子

    终结符：
    - PLUS 加 +
    - MINUS 减 -
    - MUL 乘 *
    - DIV 除 /
    - LPAREN 左括号 (
    - RPAREN 右括号 )
3. 详细设计