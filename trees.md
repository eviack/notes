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
Think of a binary tree like a **corporate office** or a **relay race**. The difference between "passing down" and "combining up" is all about **who has the information** and **where the final answer is calculated.**

### 1. Passing Info Down (Top-Down / Pre-order)

The Analogy: The "Gift Bag"

Imagine you are at the top floor (Root). You have a bag. As you go down to your children, you put something in their bags (like a running sum or the path you took).

-   **Direction:** Root $\rightarrow$ Leaf.
    
-   **The Action:** The parent tells the child: _"Hey, here is the total sum of everyone above you. Add yourself to it and tell your kids."_
    
-   **Example:** **Path Sum**.
    
    -   Root (Value 5) says to Left Child: "The sum so far is 5."
        
    -   Left Child (Value 3) says to its kids: "The sum so far is 8 (5 + 3)."
        
-   **Code looks like this:**
    
    Python
    
    ```
    def dfs(node, current_sum):
        if not node: return
        new_sum = current_sum + node.val # Parent does work
        dfs(node.left, new_sum)          # Passes info DOWN
        dfs(node.right, new_sum)         # Passes info DOWN
    
    ```
    

----------

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
    
    Python
    
    ```
    def dfs(node):
        if not node: return 0
        left_h = dfs(node.left)    # Wait for Left to finish
        right_h = dfs(node.right)  # Wait for Right to finish
        return max(left_h, right_h) + 1 # Combine and pass UP
    
    ```
    

----------

### The Simple "Cheat" to tell them apart:

**Feature**

**Top-Down (Pass Down)**

**Bottom-Up (Combine Up)**

**Question**

"What is the path from the root to me?"

"What is happening in the subtrees below me?"

**Work Order**

Work happens **before** recursion.

Work happens **after** recursion.

**Return Value**

Usually returns `None` (updates a global) or a boolean.

Returns a calculated value (int, bool, list) to the parent.

**Key Keyword**

"Path", "Root-to-leaf".

"Height", "Maximum", "Total Sum", "Diameter".

**Does the "Gift Bag" (info going down) vs. "Tax Collector" (results coming up) analogy**
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzA3ODA0MDgsMTU1NTE4MTAxMF19
-->