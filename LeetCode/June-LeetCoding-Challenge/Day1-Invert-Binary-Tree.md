# Invert Binary Tree

## 문제 개요
June LeetCoding Challenge 1일차 문제.  

Invert a binary tree.   
입력으로 주어진 binary tree의 모든 노드를 좌, 우 반전시켜야 된다.

### Test Case
- Input 1:   
![input1](../../assets/leetcode-june-challenge-day1-input1.png)
- Output 1:   
![output1](../../assets/leetcode-june-challenge-day1-output1.png)

### Default Code Definition
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public TreeNode invertTree(TreeNode root) {
        
    }
}
```

### 내 코드
```java
class Solution {
    public TreeNode invertTree(TreeNode root) {
        if(!TreeNode.class.isInstance(root)) {
            return root;
        }
        if(!TreeNode.class.isInstance(root.left) && 
                !TreeNode.class.isInstance(root.right)) {
            return root;
        }
        if(TreeNode.class.isInstance(root.left)) {
            invertTree(root.left);
        }
        if(TreeNode.class.isInstance(root.right)) {
            invertTree(root.right);
        }
        TreeNode temp = root.left;
        root.left = root.right;
        root.right = temp;
        
        return root;
    }
}
```

- 사용한 알고리즘
    - recursive function

- 막힌 부분 / 실수한 부분
    - 재귀함수 사용법을 정확히 몰라서 조건문 없이 사용할 수 있는걸 조건문으로 분기해서 재귀호출했다. 반쪽자리만도 못한  재귀함수가...
    - 입력으로 빈(null) 값이 들어오는 걸 예상하지 못해 NullPointerException이 일어났다.

### Solution
LeetCode에서 제공한 코드
```java
public TreeNode invertTree(TreeNode root) {
    if (root == null) {
        return null;
    }
    TreeNode right = invertTree(root.right);
    TreeNode left = invertTree(root.left);
    root.left = right;
    root.right = left;
    return root;
}
```
- 쓸데없이 isInstance 메서드로 instance여부를 따지지 않고 null일 경우 null return.
- 재귀호출도 쓸데없는 비교연산 없이 우측 최하위 노드부터 형제노드와 반전시키면서 진행.
- 재귀함수에 대해 더 이해할 수 있었고 조건문의 비교식을 작성함에도 반성하게됐다...
