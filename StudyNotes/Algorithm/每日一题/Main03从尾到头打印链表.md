> 题目：输入链表的头结点，从尾到头反过来打印出每个结点的值。

##### 解题思路：

- 方法一：使用栈的方式输出

1. 根据给出的头结点，从头结点开始依次入栈；
2. 将栈内的数据依次输出。

- 方法二：使用递归的方式输出

1. 构建函数输出当前结点的值；
2. 判断当前结点是否为空；
3. 若当前结点不为空，则在输出当前结点值之前，调用自身，参数为下一个结点。

```java
public class Main03 {
	/**
	 * 定义结点对象
	 */
	public static class ListNode {
		// 结点值
		int val;
		// 下一个结点
		ListNode next;
	}

	/**
	 * 方法一：使用栈的方式进行输出
	 * @param head 链表头结点
	 */
	private static void printListInverselyUsingIteration(ListNode head) {
		Stack<ListNode> stack = new Stack<>();
		while (head != null) {
			stack.push(head);
			head = head.next;
		}
		while (!stack.isEmpty()) {
			System.out.print(stack.pop().val + " ");
		}
	}

	/**
	 * 方法二：使用递归的方式输出
	 * @param head 链表头结点
	 */
	private static void printListInverselyUsingRecursion(ListNode head) {
		if (head != null) {
			printListInverselyUsingRecursion(head.next);
			System.out.print(head.val + " ");
		}
	}

	public static void main(String[] args) {
		ListNode head = new ListNode();
		head.val = 1;
		head.next = new ListNode();
		head.next.val = 2;
		head.next.next = new ListNode();
		head.next.next.val = 3;
		head.next.next.next = new ListNode();
		head.next.next.next.val = 4;
		head.next.next.next.next = new ListNode();
		head.next.next.next.next.val = 5;

		// 方法一：使用递归的方式
		printListInverselyUsingIteration(head);

		System.out.println();

		//方法二：使用栈的方式
		printListInverselyUsingRecursion(head);
	}
}
```

##### 运行结果：

![1566312239143](C:%5CUsers%5Ceasysir%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5C1566312239143.png)