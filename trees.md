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

Mental image:
1. Think of smallest tree which is just of one node, the parent and ask what can I get from my children? Their respective heights. Then i can just calculate `abs(left-right)` and check if `abs(left-right) > 1` if yes then i must return `-1`
2. I must check, did any of my children gave me `-1` ? That would mean they themselves are imbalanced ! If that's the case, how can me as a parent be balanced !? So parent returns `-1` himself.
3. If everything goes right, we will keep calculating the height, and ultima 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY5MzkyMTg3MCwxODU4OTc0MDE2LDE1NT
UxODEwMTBdfQ==
-->