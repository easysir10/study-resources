> 题目：输入某二叉树的先序遍历和中序遍历的结果，请重建出该二叉树。假设输入的先序遍历和中序遍历的结果中都不含重复的数字。例如：前序遍历序列｛ 1, 2, 4, 7, 3, 5, 6, 8｝和中序遍历序列｛4, 7, 2, 1, 5, 3, 8，6}，重建出下图所示的二叉树并输出它的头结点。

![二叉树](C:%5CUsers%5Ceasysir%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5C1566391144866.png)

##### 解题思路：

```java
public class Main04 {
	/**
	 * 二叉树节点类
	 */
	public static class BinaryTreeNode {
		int val;
		BinaryTreeNode left;
		BinaryTreeNode right;
	}

	/**
	 *
	 * @param preOrder   先序遍历
	 * @param postOrder  中序遍历
	 * @return 二叉树的根结点
	 */
	private static BinaryTreeNode construct(int[] preOrder, int[] postOrder) {
		// 校验输入的合法性，两个数组都不能为空，并且都有数据，而且数据的数目相同
		if (preOrder == null || postOrder == null || preOrder.length != postOrder.length || postOrder.length < 1) {
			return null;
		}
		return construct(preOrder, 0, preOrder.length - 1, postOrder, 0, postOrder.length - 1);
	}

	/**
	 *
	 * @param preOrder   先序遍历
	 * @param preStart   先序遍历的开始位置
	 * @param preEnd     先序遍历的结束位置
	 * @param postOrder  中序遍历
	 * @param postStart  中序遍历的开始位置
	 * @param postEnd    中序遍历的结束位置
	 * @return 树的根结点
	 */
	private static BinaryTreeNode construct(int[] preOrder, int preStart, int preEnd, int[] postOrder, int postStart, int postEnd) {

		// 开始位置大于结束位置说明已经没有需要处理的元素了
		if (preStart > preEnd) {
			return null;
		}
		// 取先序遍历的第一个数字，就是当前的根结点
		int val = preOrder[preStart];
		int index = postStart;
		// 在中序遍历的数组中找根结点的位置
		while (index <= postEnd && postOrder[index] != val) {
			index++;
		}

		// 如果在整个中序遍历的数组中没有找到，说明输入的参数是不合法的，抛出异常
		if (index > postEnd) {
			throw new RuntimeException("Invalid input");
		}

		// 创建当前的根结点，并且为结点赋值
		BinaryTreeNode node = new BinaryTreeNode();
		node.val = val;

		// 递归构建当前根结点的左子树，左子树的元素个数：index-postStart个
		// 左子树对应的先序遍历的位置在[preStart+1, preStart+index-postStart]
		// 左子树对应的中序遍历的位置在[postStart, index-1]
		node.left = construct(preOrder, preStart + 1, preStart + index - postStart, postOrder, postStart, index - 1);
		// 递归构建当前根结点的右子树，右子树的元素个数：postEnd-index个
		// 右子树对应的前序遍历的位置在[preStart+index-postStart+1, preEnd]
		// 右子树对应的中序遍历的位置在[index+1, postEnd]
		node.right = construct(preOrder, preStart + index - postStart + 1, preEnd, postOrder, index + 1, postEnd);

		// 返回创建的根结点
		return node;
	}

	/**
	 *
	 * 中序遍历二叉树
	 * @param root 根结点
	 */
	private static void printTree(BinaryTreeNode root) {
		if (root != null) {
			printTree(root.left);
			System.out.print(root.val + " ");
			printTree(root.right);
		}

	}

	/**
	 *  普通二叉树
	 *  		1
	 * 	     /     \
	 * 	    2       3
	 * 	   /       / \
	 * 	  4       5   6
	 * 	   \         /
	 * 	    7       8
	 */
	private static void test1() {
		int[] preOrder = {1, 2, 4, 7, 3, 5, 6, 8};
		int[] postOrder = {4, 7, 2, 1, 5, 3, 8, 6};
		BinaryTreeNode root = construct(preOrder, postOrder);
		printTree(root);
	}

	/**
	 *  所有的结点都没有右子树
	 *  		  1
	 *  		 /
	 *  		2
	 *  	   /
	 *  	  3
	 *  	 /
	 *  	4
	 *     /
	 *    5
	 */
	private static void test2() {
		int[] preOrder = {1, 2, 3, 4, 5};
		int[] postOrder = {5, 4, 3, 2, 1};
		BinaryTreeNode root = construct(preOrder, postOrder);
		printTree(root);
	}

	/**
	 * 所有的结点都没有左子树
	 *				1
	 *				 \
	 *				  2
	 *				   \
	 *				    3
	 *				     \
	 *				      4
	 *				       \
	 *				        5
	 */
	private static void test3() {
		int[] preOrder = {1, 2, 3, 4, 5};
		int[] postOrder = {1, 2, 3, 4, 5};
		BinaryTreeNode root = construct(preOrder, postOrder);
		printTree(root);
	}

	/**
	 *
	 * 树中只有一个结点
	 */
	private static void test4() {
		int[] preOrder = {1};
		int[] postOrder = {1};
		BinaryTreeNode root = construct(preOrder, postOrder);
		printTree(root);
	}

	/**
	 * 完全二叉树
	 *		    1
	 * 	     /     \
	 * 	    2       3
	 * 	   / \     / \
	 * 	  4   5   6   7
	 */
	private static void test5() {
		int[] preOrder = {1, 2, 4, 5, 3, 6, 7};
		int[] postOrder = {4, 2, 5, 1, 6, 3, 7};
		BinaryTreeNode root = construct(preOrder, postOrder);
		printTree(root);
	}

	/**
	 *
	 * 输入空指针
	 */
	private static void test6() {
		construct(null, null);
	}

	/**
	 *
	 * 输入的两个序列不匹配
	 */
	private static void test7() {
		int[] preOrder = {1, 2, 4, 5, 3, 6, 7};
		int[] postOrder = {4, 2, 8, 1, 6, 3, 7};
		BinaryTreeNode root = construct(preOrder, postOrder);
		printTree(root);
	}

	public static void main(String[] args) {

		// 普通二叉树
		test1();
		System.out.println();

		// 所有结点都没有右子结点
		test2();
		System.out.println();

		// 所有结点都没有左子结点
		test3();
		System.out.println();

		// 树中只有一个结点
		test4();
		System.out.println();

		// 完全二叉树
		test5();
		System.out.println();

		// 输入空指针
		test6();
		System.out.println();

		// 输入的两个序列不匹配
		test7();
	}
}
```

##### 运行结果：

![1566400344990](C:%5CUsers%5Ceasysir%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5C1566400344990.png)