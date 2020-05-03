### 数字类型约定

参考 [EMCA-262 Numeric Literals](https://www.ecma-international.org/ecma-262/5.1/#sec-7.8.3) 

*NumericLiteral* **::**

* *DecimalLiteral*

* *HexIntegerLiteral*

*DecimalLiteral* **::**

* *DecimalIntegerLiteral* `.` *DecimalDigits*opt *ExponentPart*opt

* `.` *DecimalDigits* *ExponentPart*opt

* *DecimalIntegerLiteral* *ExponentPart*opt

*DecimalIntegerLiteral* **::**

* 0

* *NonZeroDigit* *DecimalDigits*opt

*DecimalDigits* **::**

* *DecimalDigit*

* *DecimalDigits* *DecimalDigit*

*DecimalDigit* **::** **one of**

​	0 1 2 3  4 5  6 7 8 9

*NonZeroDigit* **::** **one of**

​	1 2 3  4 5  6 7 8 9

*ExponentPart* **::**

* *ExponentIndicator* *SignedInteger*

*ExponentIndicator* **::** **one of**

​	e E

*SignedInteger* **::**

* *DecimalDigits*

* `+` *DecimalDigits*

* `-` *DecimalDigits*

*HexIntegerLiteral* **::**

* `0x` *HexDigit*

* `0X` *HexDigit*

*HexIntegerLiteral* *HexDigit*

*HexDigit* **::** **one of**

0 1 2 3 4 5 6 7 8 9 a b c d e f A B C D E F



### 正则

* 十进制数

  ```
  /^(0\.?|0?\.\d+|[1-9]\d*\.?\d*?)([eE][-\+]?\d+)?$/
  ```

* 二进制数

  ```
  /^0[bB][01]+$/
  ```

* 八进制数

  ```
  /^0[oO][0-7]+$/
  ```

* 十六进制数

  ```
  /^0[xX][0-9a-fA-F]+$/
  ```

  

综上，对于数字的正则表达式为：

```
/^(0\.?|0?\.\d+|[1-9]\d*\.?\d*?)([eE][-\+]?\d+)?$|^0[bB][01]+$|^0[oO][0-7]+$|^0[xX][0-9a-fA-F]+$/
```



