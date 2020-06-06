# Invert Binary Tree

## 문제 개요
June LeetCoding Challenge 2일차 문제.  

Write a function to delete a node (except the tail) in a singly linked list, given only access to that node.

Given linked list -- head = [4,5,1,9], which looks like following:   
![Given linked list](/assets/leetcode-june-challenge-day2-content.PNG)

> node에 대한 access만 주어진 singly linked list에서 node를(tail이 아닌) 삭제하는 함수를 구현.

**Note**:
- The linked list will have at least two elements.   
주어지는 linked list는 최소 두 개의 elements를 가진다.
- All of the nodes' values will be unique.   
모든 node들의 value는 유일한 값이다.
- The given node will not be the tail and it will always be a valid node of the linked list.   
주어진 node는 tail이 아니며 항상 유효한 node이다.
- Do not return anything from your function.   
작성한 함수에서 어떤것도 return하면 안된다.

### Test Case
- Example 1:
```
Input: head = [4,5,1,9], node = 5
Output: [4,1,9]
Explanation: You are given the second node with value 5, the linked list should become 4 -> 1 -> 9 after calling your function.
```
- Example 2:
```
Input: head = [4,5,1,9], node = 1
Output: [4,5,9]
Explanation: You are given the third node with value 1, the linked list should become 4 -> 5 -> 9 after calling your function.
```

### Default Code Definition
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public void deleteNode(ListNode node) {
        
    }
}
```

### 내 코드
```java
class Solution {
    public void deleteNode(ListNode node) {
        node.val = node.next.val;
        node.next = node.next.next;
    }
}
```

- 사용한 알고리즘
    - 없다....

- 막힌 부분 / 실수한 부분
    - 없다...

### Solution
LeetCode에서 제공한 코드
```java
public void deleteNode(ListNode node) {
    node.val = node.next.val;
    node.next = node.next.next;
}
```
- 확인해보니 solution에서 제공하는 코드와 같았다.
- 어제 binary tree를 반전하는거에 비하면 너무 쉬웠다.
