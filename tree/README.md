# Tree

## Tree Traversals 

### Iterative


### Recursive


### How to check if a tree is a binary tree

``` python
class Solution(object):
    def isValidBST(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        return self.checkBST(root, float('-inf'), float('inf'))
    
    def checkBST(self, root, low, high):
        if root is None:
            return True
        
        left = self.checkBST(root.left, low, root.val)
        right = self.checkBST(root.right, root.val, high)
        return root.val > low and root.val < high and left and right
```