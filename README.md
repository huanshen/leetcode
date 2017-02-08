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
