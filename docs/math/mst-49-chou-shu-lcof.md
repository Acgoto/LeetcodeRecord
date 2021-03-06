# 面试题49.丑数
题目链接：[传送门](https://leetcode-cn.com/problems/chou-shu-lcof/)

## 题目描述：
我们把只包含质因子`2`、`3`和`5`的数称作丑数（`Ugly Number`）。求按从小到大的顺序的第`n`个丑数。

**说明**：`1`是丑数。`n`不超过`1690`。

**示例**:

- 输入：`n = 10`
- 输出：`12`
- 解释：`1, 2, 3, 4, 5, 6, 8, 9, 10, 12`是前`10`个丑数。

## 解决方案：
- 时间复杂度：$O(n)$
- 空间复杂度：$O(n)$
- 思路：数学。实际上，`uglyNum` $ = 2^x \times 3^y \times 5^z$，对于每个丑数，肯定是x个2、y个3、z个5的乘积得来的。于是我们每次尝试着将x、y、z都加1后取最小值，并且判断这个最小值是哪个因子相乘后得到的，是则将那个因子的个数加1，一直这样递推下去，即可求出第n个丑数！
- 备注：微保笔试题。

## AC代码：
```java
class Solution {
	public int nthUglyNumber(int n) {
		int[] dp = new int[n];
		// 1 是丑数
		dp[0] = 1;
		// 每个因子实际的个数减去1
		int p2 = 0, p3 = 0, p5 = 0;
		for (int i = 1; i < n; i++) {
			// 尝试取每个因子加1后得到的最小值
			dp[i] = Math.min(dp[p2] * 2, Math.min(dp[p3] * 3, dp[p5] * 5));
			// 若是2，则个数加1，以下同理
			if (dp[p2] * 2 == dp[i])
				p2++;
			if (dp[p3] * 3 == dp[i])
				p3++;
			if (dp[p5] * 5 == dp[i])
				p5++;
		}
		return dp[n - 1];
	}
}
```