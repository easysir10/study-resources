> 题目：请实现一个函数，把字符串中的每个空格替换成"%20"，例如“We are happy.“，则输出”We%20are%20happy.“。

##### 解题思路：

1. 统计字符数组中的空白字符数；
2. 计算出转换后的字符串长度；
3. 若空白字符数为0，则直接返回-1；
4. 若空白字符数不为0，则从字符串最后一位开始检查；
5. 若检查为空白字符，则进行替换并前移；
6. 若检查为非空白字符，则直接进行赋值并前移一位。

```java
public class Main02 {
	/**
	 * @param  string     要转换的字符数组
	 * @param  strLength  字符数组中已经使用的长度
	 * @return 转换后的字符长度，-1表示处理失败
	 */
	private static int replaceBlank(char[] string, int strLength) {

		// 校验输入是否合法，不合法则返回-1
		if (string == null || string.length < strLength) {
			return -1;
		}

		// 统计字符数组中的空白字符数
		int blankCount = 0;
		for (int i = 0; i < strLength; i++) {
			if (string[i] == ' ') {
				blankCount++;
			}
		}

		// 计算转换后的字符长度是多少
		int targetLength = blankCount * 2 + strLength;
		int tmp = targetLength;
		if (targetLength > string.length) {
			return -1;
		}

		// 如果没有空白字符就不用处理
		if (blankCount == 0) {
			return strLength;
		}

		strLength--; // 从后向前，第一个开始处理的字符
		targetLength--; // 处理后的字符放置的位置

		// 字符中有空白字符，一直处理到所有的空白字符处理完
		while (strLength >= 0 && strLength < targetLength) {
			// 如是当前字符是空白字符，进行"%20"替换
			if (string[strLength] == ' ') {
				string[targetLength--] = '0';
				string[targetLength--] = '2';
				string[targetLength--] = '%';
			} else { 
				string[targetLength--] = string[strLength];
			}
			strLength--;
		}
		return tmp;
	}

	public static void main(String[] args) {
		char[] string = new char[100];
		string[0] = ' ';
		string[1] = 's';
		string[2] = ' ';
		string[3] = 't';
		string[4] = ' ';
		string[5] = ' ';
		string[6] = 'u';
		string[7] = ' ';
		string[8] = 'd';
		string[9] = ' ';
		string[10] = 'y';
		string[11] = ' ';

		int length = replaceBlank(string, 12);
		System.out.println(new String(string, 0, length));
	}
}
```

##### 运行结果：

![1566228244769](C:%5CUsers%5Ceasysir%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5C1566228244769.png)