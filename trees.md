---


---

<h1 id="trees">Trees</h1>
<p>Some important <strong>patterns</strong> along with problems :</p>
<h3 id="passing-info-down-top-down--pre-order">1. Passing Info Down (Top-Down / Pre-order)</h3>
<p>The Analogy: The “Gift Bag”<br>
Imagine you are at the top floor (Root). You have a bag. As you go down to your children, you put something in their bags (like a running sum or the path you took).</p>
<ul>
<li>
<p><strong>Direction:</strong> Root <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>→</mo></mrow><annotation encoding="application/x-tex">\rightarrow</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.36687em; vertical-align: 0em;"></span><span class="mrel">→</span></span></span></span></span> Leaf.</p>
</li>
<li>
<p><strong>The Action:</strong> The parent tells the child: <em>“Hey, here is the total sum of everyone above you. Add yourself to it and tell your kids.”</em></p>
</li>
<li>
<p><strong>Example:</strong> <strong>Path Sum</strong>.</p>
<ul>
<li>Root (Value 5) says to Left Child: “The sum so far is 5.”</li>
<li>Left Child (Value 3) says to its kids: “The sum so far is 8 (5 + 3).”</li>
</ul>
</li>
<li>
<p><strong>Code looks like this:</strong></p>
<pre><code>def dfs(node, current_sum):
    if not node: return
    new_sum = current_sum + node.val # Parent does work
    dfs(node.left, new_sum)          # Passes info DOWN
    dfs(node.right, new_sum)         # Passes info DOWN
</code></pre>
</li>
</ul>
<h3 id="combining-info-up-bottom-up--post-order">2. Combining Info Up (Bottom-Up / Post-order)</h3>
<p>The Analogy: The “Tax Collector”<br>
Imagine you are the Root. You have no idea what the answer is. You ask your children: “Go find out the height of your subtrees and tell me.” You can’t calculate your own height until they come back with their numbers.</p>
<ul>
<li>
<p><strong>Direction:</strong> Leaf <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>→</mo></mrow><annotation encoding="application/x-tex">\rightarrow</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.36687em; vertical-align: 0em;"></span><span class="mrel">→</span></span></span></span></span> Root.</p>
</li>
<li>
<p><strong>The Action:</strong> The parent waits for the children to finish and says: <em>“Okay, Left said 3 and Right said 5. I’ll take the bigger one, add 1 for myself, and tell my boss.”</em></p>
</li>
<li>
<p><strong>Example:</strong> <strong>Tree Height</strong>.</p>
<ul>
<li>Leaf nodes return 0.</li>
<li>Parent of leaves receives (0, 0), calculates <code>1 + max(0, 0) = 1</code>, and returns 1.</li>
<li>The Root eventually receives (3, 5), calculates <code>1 + max(3, 5) = 6</code>, and that’s the final answer.</li>
</ul>
</li>
<li>
<p><strong>Code looks like this:</strong></p>
<pre><code>def dfs(node):
    if not node: return 0
    left_h = dfs(node.left)    # Wait for Left to finish
    right_h = dfs(node.right)  # Wait for Right to finish
    return max(left_h, right_h) + 1 # Combine and pass UP
</code></pre>
</li>
</ul>
<h2 id="some-problems-worth-reading">Some problems worth reading</h2>
<h3 id="balanced-binary-tree">Balanced Binary Tree</h3>
<p><img src="https://assets.leetcode.com/uploads/2020/10/06/balance_2.jpg" alt=""></p>
<p>As you can see the above tree is not balanced. A tree is balanced if the <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi mathvariant="normal">∣</mi><msub><mi>h</mi><mrow><mi>l</mi><mi>e</mi><mi>f</mi><mi>t</mi></mrow></msub><mo>−</mo><msub><mi>h</mi><mrow><mi>r</mi><mi>i</mi><mi>g</mi><mi>h</mi><mi>t</mi></mrow></msub><mi mathvariant="normal">∣</mi></mrow><annotation encoding="application/x-tex">|h_{left} - h_{right}|</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.03611em; vertical-align: -0.286108em;"></span><span class="mord">∣</span><span class="mord"><span class="mord mathnormal">h</span><span class="msupsub"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 0.336108em;"><span class="" style="top: -2.55em; margin-left: 0em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight"><span class="mord mathnormal mtight" style="margin-right: 0.01968em;">l</span><span class="mord mathnormal mtight">e</span><span class="mord mathnormal mtight" style="margin-right: 0.10764em;">f</span><span class="mord mathnormal mtight">t</span></span></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 0.286108em;"><span class=""></span></span></span></span></span></span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">−</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 1.03611em; vertical-align: -0.286108em;"></span><span class="mord"><span class="mord mathnormal">h</span><span class="msupsub"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 0.336108em;"><span class="" style="top: -2.55em; margin-left: 0em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight"><span class="mord mathnormal mtight" style="margin-right: 0.02778em;">r</span><span class="mord mathnormal mtight">i</span><span class="mord mathnormal mtight" style="margin-right: 0.03588em;">g</span><span class="mord mathnormal mtight">h</span><span class="mord mathnormal mtight">t</span></span></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 0.286108em;"><span class=""></span></span></span></span></span></span><span class="mord">∣</span></span></span></span></span>&lt;=1 if greater it is not balanced so we can just return <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>−</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">-1</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.72777em; vertical-align: -0.08333em;"></span><span class="mord">−</span><span class="mord">1</span></span></span></span></span> also if any of left subtree and right subtree gives -1 to parent that means parent is unbalanced !</p>
<p><img src="https://static.takeuforward.org/content/-2l9zrptW" alt=""><br>
<img src="https://static.takeuforward.org/content/-3TKcmFIC" alt=""></p>
<p>Mental image:</p>
<ol>
<li>Think of smallest tree which is just of one node, the parent and ask what can I get from my children? Their respective heights. Then i can just calculate <code>abs(left-right)</code> and check if <code>abs(left-right) &gt; 1</code> if yes then i must return <code>-1</code></li>
<li>I must check, did any of my children gave me <code>-1</code> ? That would mean they themselves are imbalanced ! If that’s the case, how can me as a parent be balanced !? So parent returns <code>-1</code> himself.</li>
<li>If everything goes right, we will keep calculating the height, and ultimately will return the maximum height from leaf to root node.</li>
<li>Check if answer returned by the dfs <code>ans = dfs(root)</code> is actually <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>&gt;</mo><mo>=</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">&gt;=0</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.5782em; vertical-align: -0.0391em;"></span><span class="mrel">&gt;=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">0</span></span></span></span></span> if yes that means we do have some height, so return <code>True</code> else we have a negative value <code>-1</code> which says nothing was balanced, so return <code>False</code></li>
</ol>
<p>Main logic is :</p>
<pre><code>if left==-1 or right==-1: return -1
if abs(left-right)&gt;1: return -1
</code></pre>
<p>These 2 conditions, we check while calculating the height of tree, check full code below:</p>
<pre><code>def isBalanced(self, root: Optional[TreeNode]) -&gt; bool:
    def dfs(root):
        if not root: return 0
        
        left = dfs(root.left)
        right = dfs(root.right)
        
        if left==-1 or right==-1:
            return -1
        if abs(left-right)&gt;1: return -1
        return 1+max(left, right)
   
    d = dfs(root)
    return True if d&gt;=0 else False
</code></pre>
<h3 id="is-tree-same">Is tree same?</h3>
<p><img src="https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/e78fc10c-4692-471f-5261-61e9be4f3a00/public" alt=""></p>
<p><strong>Step 1: The Base Cases (The “Empty” Scenarios)</strong><br>
Before looking at values, look at “existence.” There are three tiny scenarios:</p>
<ol>
<li><strong>Both are missing:</strong> If <code>P</code> is None and <code>Q</code> is None, they are identical. <strong>Return <code>True</code></strong>.</li>
<li><strong>One is missing, one isn’t:</strong> If one is None but the other isn’t, they are different. <strong>Return <code>False</code></strong>.</li>
</ol>
<p><strong>Step 2: The “Smallest Unit” Work (The Value Check)</strong><br>
Now, assume both nodes exist. Look at their “faces” (their values).</p>
<ul>
<li><strong>Are the values different?</strong> If <code>P.val != Q.val</code>, the trees are officially not the same. <strong>Return <code>False</code></strong>.</li>
</ul>
<p><strong>Step 3: The Recursive Leap of Faith (The Delegation)</strong><br>
If the current nodes are identical, you now need to check their children. This is where you delegate the work.</p>
<ul>
<li>You ask your assistant: “Is the <strong>left</strong> side of P the same as the <strong>left</strong> side of Q?”</li>
<li>You ask again: “Is the <strong>right</strong> side of P the same as the <strong>right</strong> side of Q?”</li>
</ul>
<p><strong>Algorithm:</strong></p>
<ol>
<li>Start at the root node of both trees (node1 and node2).</li>
<li>Check if the values of the current nodes in both trees are equal. If not, return  <code>false</code>.</li>
<li>Recursively check the left subtree and then the right subtree of both trees.</li>
<li>If all recursive checks return  <code>true</code>, the trees are identical; otherwise, they are not.<br>
<img src="https://static.takeuforward.org/content/s1.png-rXFgoNo2" alt="Image 1"><br>
<img src="https://static.takeuforward.org/content/s3.png-o9HGyqio" alt="Image 3"><br>
<img src="https://static.takeuforward.org/content/s4.png-Fdef0e6V" alt="Image 4"><br>
<img src="https://static.takeuforward.org/content/s5.png-QJ-rwoVp" alt="Image 5"></li>
</ol>
<p>How to do it on code ?</p>
<pre><code>def isSameTree(self, p: Optional[TreeNode], q: Optional[TreeNode]) -&gt; bool:
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
</code></pre>
<h3 id="subtree-of-another-tree-using-small-helper-functions-to-solve-big-problems">Subtree of another tree (using small helper functions to solve big problems)</h3>
<p><img src="https://assets.leetcode.com/uploads/2021/04/28/subtree1-tree.jpg" alt=""><br>
Now as we can see in the figure, we found subroot inside our main tree, so why not just search the whole tree ? Just assume we go at each node in the main tree, and <strong>compare subRoot tree with the tree below root.</strong></p>
<p>Each node in main tree will act as a parent of a subtree inside it and then we will check if we find the subtree we are searching for in left part of main tree <code>dfs(root.left, subRoot)</code> or in right part <code>dfs(root.right, subRoot)</code> and combine the result</p>

