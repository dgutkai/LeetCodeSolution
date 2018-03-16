# LeetCodeSolution
## 1. Two Sum
Given an array of integers, return indices of the two numbers such that they add up to a specific target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.

**Example:**
~~~html
Given nums = [2, 7, 11, 15], target = 9,
Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
~~~
**源码：**
~~~java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length-1; i++){
            for (int j = i+1; j < nums.length; j++){
                if (nums[i] + nums[j] == target){
                    return new int[]{i, j};
                }
            }
        }
        return null;
    }
}
~~~
## 2. Add Two Numbers
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.
You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Example:**
~~~html
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
~~~
**源码：**
~~~java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode headNode = null;
        ListNode tailNode = null;
        int numAdd = l1.val + l2.val;
        headNode = new ListNode(numAdd%10);
        ListNode l_temp1 = l1.next;
        ListNode l_temp2 = l2.next;
        tailNode = headNode;
        while(l_temp1 != null || l_temp2 != null){
            int num1;
            int num2;
            if (l_temp1 == null){
                num1 = 0;
            }else{
                num1 = l_temp1.val;
                l_temp1 = l_temp1.next;
            }
            if (l_temp2 == null){
                num2 = 0;
            }else{
                num2 = l_temp2.val;
                l_temp2 = l_temp2.next;
            }
            if (numAdd >= 10){
                numAdd = num1 + num2 + 1;
            }else {
                numAdd = num1 + num2;
            }
            tailNode.next = new ListNode(numAdd%10);
            tailNode = tailNode.next;
        }
        if (numAdd >= 10){
            tailNode.next = new ListNode(1);
        }
        return headNode;
    }
}
~~~