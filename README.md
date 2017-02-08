#LeetCode JavaScript版本

##111 Minimum Depth of Binary Tree
Given a binary tree, find its minimum depth.
The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

<code>
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

</code>
