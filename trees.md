# Trees

Some important **patterns** along with problems :

### 1. Passing Info Down (Top-Down / Pre-order)

The Analogy: The "Gift Bag"
Imagine you are at the top floor (Root). You have a bag. As you go down to your children, you put something in their bags (like a running sum or the path you took).
-   **Direction:** Root $\rightarrow$ Leaf.
-   **The Action:** The parent tells the child: _"Hey, here is the total sum of everyone above you. Add yourself to it and tell your kids."_   
-   **Example:** **Path Sum**.
    
    -   Root (Value 5) says to Left Child: "The sum so far is 5."       
    -   Left Child (Value 3) says to its kids: "The sum so far is 8 (5 + 3)."
        
-   **Code looks like this:**
    ```
    def dfs(node, current_sum):
        if not node: return
        new_sum = current_sum + node.val # Parent does work
        dfs(node.left, new_sum)          # Passes info DOWN
        dfs(node.right, new_sum)         # Passes info DOWN
    ```
### 2. Combining Info Up (Bottom-Up / Post-order)

The Analogy: The "Tax Collector"
Imagine you are the Root. You have no idea what the answer is. You ask your children: "Go find out the height of your subtrees and tell me." You can't calculate your own height until they come back with their numbers.

-   **Direction:** Leaf $\rightarrow$ Root.    
-   **The Action:** The parent waits for the children to finish and says: _"Okay, Left said 3 and Right said 5. I'll take the bigger one, add 1 for myself, and tell my boss."_
    
-   **Example:** **Tree Height**.    
    -   Leaf nodes return 0.        
    -   Parent of leaves receives (0, 0), calculates `1 + max(0, 0) = 1`, and returns 1.
    -   The Root eventually receives (3, 5), calculates `1 + max(3, 5) = 6`, and that's the final answer.
        
-   **Code looks like this:**  
    ```
    def dfs(node):
        if not node: return 0
        left_h = dfs(node.left)    # Wait for Left to finish
        right_h = dfs(node.right)  # Wait for Right to finish
        return max(left_h, right_h) + 1 # Combine and pass UP
    ```

## Some problems worth reading

### Balanced Binary Tree
![](https://assets.leetcode.com/uploads/2020/10/06/balance_2.jpg)

As you can see the above tree is not balanced. A tree is balanced if the $|h_{left} - h_{right}|$<=1 if greater it is not balanced so we can just return $-1$ also if any of left subtree and right subtree gives -1 to parent that means parent is unbalanced !

![](https://static.takeuforward.org/content/-2l9zrptW)
![](https://static.takeuforward.org/content/-3TKcmFIC)

Mental image:
1. Think of smallest tree which is just of one node, the parent and ask what can I get from my children? Their respective heights. Then i can just calculate `abs(left-right)` and check if `abs(left-right) > 1` if yes then i must return `-1`
2. I must check, did any of my children gave me `-1` ? That would mean they themselves are imbalanced ! If that's the case, how can me as a parent be balanced !? So parent returns `-1` himself.
3. If everything goes right, we will keep calculating the height, and ultimately will return the maximum height from leaf to root node.
4. Check if answer returned by the dfs `ans = dfs(root)` is actually $>=0$ if yes that means we do have some height, so return `True` else we have a negative value `-1` which says nothing was balanced, so return `False`

Main logic is :
```
if left==-1 or right==-1: return -1
if abs(left-right)>1: return -1
```
These 2 conditions, we check while calculating the height of tree, check full code below:
```
def isBalanced(self, root: Optional[TreeNode]) -> bool:
    def dfs(root):
        if not root: return 0
        
        left = dfs(root.left)
        right = dfs(root.right)
        
        if left==-1 or right==-1:
            return -1
        if abs(left-right)>1: return -1
        return 1+max(left, right)
   
    d = dfs(root)
    return True if d>=0 else False
``` 

### Is tree same?
![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/e78fc10c-4692-471f-5261-61e9be4f3a00/public)

 **Step 1: The Base Cases (The "Empty" Scenarios)**
Before looking at values, look at "existence." There are three tiny scenarios:

1.  **Both are missing:** If `P` is None and `Q` is None, they are identical. **Return `True`**.    
2.  **One is missing, one isn't:** If one is None but the other isn't, they are different. **Return `False`**.

**Step 2: The "Smallest Unit" Work (The Value Check)**
Now, assume both nodes exist. Look at their "faces" (their values).
-   **Are the values different?** If `P.val != Q.val`, the trees are officially not the same. **Return `False`**.

**Step 3: The Recursive Leap of Faith (The Delegation)**
If the current nodes are identical, you now need to check their children. This is where you delegate the work.
-   You ask your assistant: "Is the **left** side of P the same as the **left** side of Q?"
-   You ask again: "Is the **right** side of P the same as the **right** side of Q?"

**Algorithm:**

1.  Start at the root node of both trees (node1 and node2).
2.  Check if the values of the current nodes in both trees are equal. If not, return  `false`.
3.  Recursively check the left subtree and then the right subtree of both trees.
4.  If all recursive checks return  `true`, the trees are identical; otherwise, they are not.
![Image 1](https://static.takeuforward.org/content/s1.png-rXFgoNo2)
![Image 3](https://static.takeuforward.org/content/s3.png-o9HGyqio)
![Image 4](https://static.takeuforward.org/content/s4.png-Fdef0e6V)
![Image 5](https://static.takeuforward.org/content/s5.png-QJ-rwoVp)

How to do it on code ?

```
def isSameTree(self, p: Optional[TreeNode], q: Optional[TreeNode]) -> bool:
 # 1. BASE CASE: Both are empty? Perfect match.
 if not p and not q:
     return True
 
 # 2. BASE CASE: 
 #One is empty or values don't match? No match.
 if not p or not q or p.val != q.val:
     return False
 
 # 3. RECURSIVE STEP: "Delegate" the children
 # "I've checked the root, 
 # now you check the subtrees."
 left_is_same = self.isSameTree(p.left, q.left)
 right_is_same = self.isSameTree(p.right, q.right)
 
 # 4. COMBINE: Both sides must be True 
 # for the whole tree to be Same
 return left_is_same and right_is_same
```
### Subtree of another tree (using small helper functions to solve big problems)

![](https://assets.leetcode.com/uploads/2021/04/28/subtree1-tree.jpg)
Now as we can see in the fi
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjQ4MjMyNzYzLC0zODIzMjAxMjhdfQ==
-->