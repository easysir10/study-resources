> 题目：在一个二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序
>
> 排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

##### 解题思路：

1. 从数组右上角开始查找；
2. 若找到目标值，跳出循环；
3. 若当前值大于目标值，当前值向*左移一位*；
4. 若当前值小于目标值，当前值向*下移一位*。

```java
public class Main01 {
    
	private static boolean find(int[][] numArray, int number) {

		// 校验数组的合法性
		if (numArray == null || numArray.length < 1 || numArray[0].length < 1) {
			return false;
		}

		// 数组的行数
		int rows = numArray.length;
		// 数组的列数
		int cols = numArray[0].length;
		// 数组初始行号
		int row = 0;
		// 数组初始列号
		int col = cols - 1;

		while (row >= 0 && row < rows && col >= 0 && col < cols) {
			// 找到该数返回true
			if (numArray[row][col] == number) {
				return true;
			}
			// 当前值大于目标值，列向左移
			else if (numArray[row][col] > number) {
				col--;
			}
			// 当前值小于目标值，行向下移
			else {
				row++;
			}
		}

		return false;
	}

	public static void main(String[] args) {
		int[][] matrix = {
				{0, 3, 6, 10},
				{2, 5, 9, 12},
				{4, 7, 10, 13},
				{6, 9, 11, 18}
		};
		System.out.println(find(matrix, 7));
		System.out.println(find(matrix, 5));
		System.out.println(find(matrix, 1));
		System.out.println(find(matrix, 15));
		System.out.println(find(matrix, 0));
		System.out.println(find(matrix, 16));
	}
}
```

##### 运行结果：

![1565937422390](C:%5CUsers%5Ceasysir%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5C1565937422390.png)