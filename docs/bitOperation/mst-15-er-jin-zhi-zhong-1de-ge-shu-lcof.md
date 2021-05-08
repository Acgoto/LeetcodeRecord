# 面试题15.二进制中1的个数
题目链接：[传送门](https://leetcode-cn.com/problems/er-jin-zhi-zhong-1de-ge-shu-lcof/)

## 题目描述：
请实现一个函数，输入一个整数，输出该数二进制表示中`1`的个数。例如，把`9`表示成二进制是`1001`，有`2`位是`1`。因此，如果输入`9`，则该函数输出`2`。

**示例**：

- 输入：`00000000000000000000000000001011`
- 输出：`3`
- 解释：输入的二进制串`00000000000000000000000000001011`中，共有三位为 '1'。

## 解决方案：
- 时间复杂度：$O(m)$，m为n的二进制数中1的个数。
- 空间复杂度：$O(1)$
- 思路：`n & (n - 1)`可以去掉二进制最低位的1，而`n & -n`可以得到二进制最低位1表示的10进制数。

## AC代码：
```java
class Solution {
	public int hammingWeight(int n) {
		// 只有当前二进制每位都变为0才退出
		int res = 0;
		while (n != 0) {
			++res;
			n &= n - 1;
		}
		return res;
	}
}
```