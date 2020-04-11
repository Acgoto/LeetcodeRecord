# 371.两整数之和
题目链接：[传送门](https://leetcode-cn.com/problems/sum-of-two-integers/)

## 题目描述：
**不使用**运算符`+`和`-`​​​​​​​，计算两整数`​​​​​​​a`、`b`​​​​​​之和。

## 解决方案：
- 时间复杂度：$O(n)$
- 空间复杂度：$O(1)$
- 思路：位运算。两数相加，某二进制位上同1则进位1，用`&`运算来实现；进位取模2或没有进位的情况用`^`运算来实现。按照这样一直循环下去，直到进位为0，变量`a`即为答案。

## AC代码：
```java
class Solution {
	public int add(int a, int b) {
		int tmp;
		while (b != 0) { // 循环直到进位为0
			tmp = a ^ b; // 先计算出两个数相加不进位的数
			b = (a & b) << 1;
			// 则进位的数为 (a & b) << 1，同1则1，否则为0，左移得到进位数，需要和不进位相加，当每个位都错位时异或的结果就是相加的结果
			a = tmp; // 重新赋值给a
		}
		return a; 
	}
}
```