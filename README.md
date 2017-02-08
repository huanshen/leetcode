#LeetCode JavaScript版本

##1. Two Sum
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:
```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

###solution 1
```
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    var arr=[0,1], flag=0;
    for(var i=0; i<nums.length-1; i++){
        for(var j=i+1; j<nums.length; j++){
            if(nums[i] + nums[j] == target){
                arr[0] = i;
                arr[1] = j;
                flag = 1;
                break;
            }
        }
        if(flag) break;
    }
    
    return arr;
};
```

###solution 2
```
var twoSum = function(nums, target) {
    const map = {};
    let compliment;
    for (let idx = 0; idx < nums.length; idx++) {
        compliment = target - nums[idx];
        if (compliment in map) return [map[compliment], idx];
        map[nums[idx]] = idx;
    }
};
```
##2 Add Two Numbers
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8

###solution
```
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var addTwoNumbers = function(l1, l2) {
    var List = new ListNode(0);
    var head = List;
    var sum = 0;
    var carry = 0;

    while(l1!==null||l2!==null||sum>0){

        if(l1!==null){
            sum = sum + l1.val;
            l1 = l1.next;
        }
        if(l2!==null){
            sum = sum + l2.val;
            l2 = l2.next;
        }
        if(sum>=10){
            carry = 1;
            sum = sum - 10;
        }

        head.next = new ListNode(sum);
        head = head.next;

        sum = carry;
        carry = 0;

    }

    return List.next;
};
```

##111 Minimum Depth of Binary Tree
Given a binary tree, find its minimum depth.
The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.


###solution
```
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */

 var minDepth = function(root) {  
     if (!root) return 0  
     var L = minDepth(root.left), R = minDepth(root.right)  
     return 1 + (Math.min(L, R) || Math.max(L, R))  
 };  
```
