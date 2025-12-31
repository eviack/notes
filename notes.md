---


---

<h2 id="heaps-patterns-and-problems">Heaps (Patterns and problems)</h2>
<h4 id="pattern-a-top-k-elements-the-most-common">Pattern A: Top K Elements (The Most Common)</h4>
<p>Goal: Find the top K largest items in a stream or list.</p>
<ul>
<li>
<p>Technique: Use a Min-Heap of size K.</p>
</li>
<li>
<p>Why? If you keep a Min-Heap of size K, the smallest element in that heap acts as the “gatekeeper.” If a new number is larger than the gatekeeper, it deserves to be in the Top <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>K</mi></mrow><annotation encoding="application/x-tex">K</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.07153em;">K</span></span></span></span></span>. You kick the gatekeeper out (pop min) and let the new guy in.</p>
</li>
<li>
<p>Result: The heap holds the largest <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>K</mi></mrow><annotation encoding="application/x-tex">K</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.07153em;">K</span></span></span></span></span> elements, and the root is the <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>K</mi></mrow><annotation encoding="application/x-tex">K</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.07153em;">K</span></span></span></span></span>-th largest.</p>
</li>
</ul>
<h4 id="pattern-b-merge-k-sorted-lists">Pattern B: Merge K Sorted Lists</h4>
<p>Goal: You have multiple sorted arrays, and you need to merge them into one big sorted array.</p>
<ul>
<li>
<p>Technique: Put the first element of every array into a Min-Heap.</p>
</li>
<li>
<p>Why? The smallest global element must be one of the heads of the lists. Pop the min from the heap, add it to your result, and then pull the next element from that specific list into the heap.</p>
</li>
</ul>
<h4 id="pattern-c-two-heaps-median-pattern">Pattern C: Two Heaps (Median Pattern)</h4>
<p>Goal: Find the median of a number stream.</p>
<ul>
<li>
<p>Technique: Maintain two heaps: a Max-Heap for the lower half of numbers and a Min-Heap for the upper half.</p>
</li>
<li>
<p>Why? The median is always at the “border” between the lower half and the upper half. By balancing these two heaps, you have instant access to the middle elements.</p>
</li>
</ul>
<h4 id="pattern-d-minimum-cost--greedy">Pattern D: Minimum Cost / Greedy</h4>
<p>Goal: Connect ropes, schedule tasks, or perform operations with minimum cost.</p>
<ul>
<li>Technique: Put all options in a Min-Heap. Always process the two smallest items, combine them, and push the result back.</li>
</ul>
<p>Why? To minimize total cost, you always want to perform expensive operations as late as possible (or multiply large numbers as few times as possible).</p>
<h4 id="problem-list-pattern-wise">Problem List (Pattern-Wise)</h4>
<p>Here is a curated list of problems. Solve them in this order to build mastery.</p>
<h4 id="level-1-the-basics-understand-push-and-pop">Level 1: The Basics (Understand push and pop)</h4>
<ul>
<li><strong>Last Stone Weight</strong> (Great for visualizing destroying elements).</li>
<li>Task: Smash two heaviest stones together.</li>
<li><strong>Relative Ranks</strong> (Simple mapping of heap order to rank).</li>
</ul>
<h4 id="level-2-top-k-elements-pattern-a">Level 2: Top K Elements (Pattern A)</h4>
<ul>
<li><strong>Kth Largest Element in a Stream</strong> (You just did this!).</li>
<li><strong>Kth Largest Element in an Array</strong> (Try both Heap and QuickSelect approaches).</li>
<li><strong>Top K Frequent Elements</strong> (Very popular interview question).</li>
<li>Hint: Count frequencies first, then heapify the counts.</li>
<li><strong>K Closest Points to Origin</strong> (Calculate distance, keep Top K smallest distances).</li>
</ul>
<h4 id="level-3-merge-k-sorted-pattern-b">Level 3: Merge K Sorted (Pattern B)</h4>
<ul>
<li><strong>Merge K Sorted Lists</strong> (Hard, but essential. Using a heap makes it manageable).</li>
<li><strong>Find K Pairs with Smallest Sums.</strong></li>
<li>Hint: Similar to merging lists, but the “lists” are implicit combinations.</li>
</ul>
<h4 id="level-4-two-heaps-pattern-c">Level 4: Two Heaps (Pattern C)</h4>
<ul>
<li>Find Median from Data Stream (The classic hard problem for this pattern).</li>
<li>Sliding Window Median.</li>
</ul>
<h4 id="level-5-scheduler--greedy-pattern-d">Level 5: Scheduler / Greedy (Pattern D)</h4>
<ul>
<li><strong>Task Scheduler (You just did this!).</strong></li>
<li><strong>Reorganize String</strong> (Arrange characters so no two adjacent are same).</li>
</ul>
<p><em><strong>-   Hint: Always pick the most frequent character, but you can’t pick it twice in a row. Park it in a temporary variable.</strong></em></p>
<ul>
<li><strong>Minimum Cost to Connect Sticks</strong> (Premium on LeetCode, but classic Greedy Heap).</li>
</ul>
<h2 id="dsu-cheat-sheet">DSU Cheat Sheet</h2>
<h4 id="tracking-edges-e.g.-for-cycle-detection-or-graph-validity">1. Tracking Edges (e.g., for Cycle Detection or Graph Validity)</h4>
<ul>
<li>Goal: Track how many edges exist inside each specific component.</li>
<li><code>Init: self.edge_count = [0] * n</code></li>
</ul>
<pre><code>def union(self, u, v):
    rootU, rootV = self.find(u), self.find(v)

    if rootU != rootV:
        # Merging two separate components
        self.parent[rootU] = rootV
        self.size[rootV] += self.size[rootU]
        # Add existing edges of 
        # U + existing edges of V + the NEW bridge edge (1)
        self.edge_count[rootV] += self.edge_count[rootU] + 1
    else:
        # Same component: We found a cycle or redundant edge
        self.edge_count[rootU] += 1
</code></pre>
<h4 id="counting-connected-components-e.g.-number-of-islands">2. Counting Connected Components (e.g., Number of Islands)</h4>
<ul>
<li>Goal: Know how many disjoint sets (islands) remain.</li>
<li><code>Init: self.num_sets = n</code> (Initially, everyone is their own island).</li>
</ul>
<pre><code>def union(self, u, v):
    rootU, rootV = self.find(u), self.find(v)

    if rootU != rootV:
        self.parent[rootU] = rootV
        # Successful merge means 1 less isolated component
        self.num_sets -= 1 
        return True
    return False

</code></pre>
<h4 id="finding-largest-component-by-size-e.g.-max-area-island">3. Finding Largest Component by Size (e.g., Max Area Island)</h4>
<ul>
<li>Goal: Track the size (number of nodes) of the biggest group formed so far.</li>
<li><code>Init: self.size = [1] * n and self.max_size = 1</code></li>
</ul>
<pre><code>def union(self, u, v):
    rootU, rootV = self.find(u), self.find(v)

    if rootU != rootV:
        self.parent[rootU] = rootV
        self.size[rootV] += self.size[rootU]
        # Update global max immediately
        self.max_size = max(self.max_size, self.size[rootV])
        return True
    return False

</code></pre>
<h4 id="grouping-components-into-a-map-e.g.-accounts-merge">4. Grouping Components into a Map (e.g., Accounts Merge)</h4>
<ul>
<li>Goal: Get a dictionary like <code>{ root_id: [node1, node2, node3] }.</code></li>
<li>Logic: <em>This is done <strong>OUTSIDE the DSU class</strong>, usually after you finish processing all unions.</em></li>
</ul>
<pre><code>groups = defaultdict(list)
for i in range(n):
    # CRITICAL: Always use find(i), 
    # not parent[i], to get the ultimate root
    root = dsu.find(i)
    groups[root].append(i)

</code></pre>
<h4 id="handling-abstract-nodes-e.g.-strings-large-coordinates">5. Handling Abstract Nodes (e.g., Strings, Large Coordinates)</h4>
<ul>
<li>Goal: Use DSU when nodes are not simple 0 to n-1 integers <code>(like "email@com" or coordinate 10005).</code></li>
</ul>
<p><strong>Init: Use a Dictionary instead of a List.</strong></p>
<pre><code>class DSU:
    def __init__(self):
        self.parent = {} # Empty dict

    def find(self, x):
        # Lazy Initialization: Add node only when seen
        if x not in self.parent:
            self.parent[x] = x

        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])
        return self.parent[x]
</code></pre>
<h2 id="mst-cheat-sheet-algorithms-patterns--recognition">MST Cheat Sheet: Algorithms, Patterns &amp; Recognition</h2>
<p>Core Concept: <strong>Connect all nodes in a graph with the minimum total edge weight and 0 cycles.</strong></p>

<table>
<thead>
<tr>
<th align="center"><strong>Algorithm</strong></th>
<th align="center"><strong>Logic</strong></th>
<th align="center"><strong>Complexity</strong></th>
<th align="center"><strong>Best Used For</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td align="center"><strong>Kruskal’s</strong></td>
<td align="center"><strong>"Greedy Merger"</strong> 1. Sort all Edges. 2. Pick smallest. 3. Use DSU to merge if not connected.</td>
<td align="center"><span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><mi>E</mi><mi>l</mi><mi>o</mi><mi>g</mi><mi>E</mi><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(E log E)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord mathnormal" style="margin-right: 0.01968em;">El</span><span class="mord mathnormal">o</span><span class="mord mathnormal" style="margin-right: 0.03588em;">g</span><span class="mord mathnormal" style="margin-right: 0.05764em;">E</span><span class="mclose">)</span></span></span></span></span></td>
<td align="center"><strong>Sparse Graphs</strong> (Roads, Networks). Easier to implement.</td>
</tr>
<tr>
<td align="center"><strong>Prim’s (Heap)</strong></td>
<td align="center"><strong>"Greedy Grower"</strong> 1. Priority Queue of edges from <em>visited</em> nodes. 2. Always pick cheapest edge to <em>unvisited</em>.</td>
<td align="center"><span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><mi>E</mi><mi>l</mi><mi>o</mi><mi>g</mi><mi>V</mi><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(E log V)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord mathnormal" style="margin-right: 0.01968em;">El</span><span class="mord mathnormal">o</span><span class="mord mathnormal" style="margin-right: 0.03588em;">g</span><span class="mord mathnormal" style="margin-right: 0.22222em;">V</span><span class="mclose">)</span></span></span></span></span></td>
<td align="center"><strong>Sparse Graphs</strong>. Standard library alternative to DSU.</td>
</tr>
<tr>
<td align="center"><strong>Prim’s (Array)</strong></td>
<td align="center"><strong>"Dense Scanner"</strong> 1. min_dist array. 2. Loop N times, scan array for min value.</td>
<td align="center">O(<span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>V</mi><mn>2</mn></msup></mrow><annotation encoding="application/x-tex">V^2</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.814108em; vertical-align: 0em;"></span><span class="mord"><span class="mord mathnormal" style="margin-right: 0.22222em;">V</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.814108em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span></span></span></span></span></span></span></span></span>)</td>
<td align="center"><strong>Dense Graphs</strong> (Grids, Coordinates). <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>V</mi><mn>2</mn></msup></mrow><annotation encoding="application/x-tex">V^2</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.814108em; vertical-align: 0em;"></span><span class="mord"><span class="mord mathnormal" style="margin-right: 0.22222em;">V</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.814108em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span></span></span></span></span></span></span></span></span> is better than <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>V</mi><mn>2</mn></msup><mi>l</mi><mi>o</mi><mi>g</mi><mi>V</mi></mrow><annotation encoding="application/x-tex">V^2 log V</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.00855em; vertical-align: -0.19444em;"></span><span class="mord"><span class="mord mathnormal" style="margin-right: 0.22222em;">V</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.814108em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span></span></span></span></span><span class="mord mathnormal" style="margin-right: 0.01968em;">l</span><span class="mord mathnormal">o</span><span class="mord mathnormal" style="margin-right: 0.03588em;">g</span><span class="mord mathnormal" style="margin-right: 0.22222em;">V</span></span></span></span></span>.</td>
</tr>
</tbody>
</table><hr>
<h3 id="pattern-recognition-when-to-use-mst">Pattern Recognition: When to use MST?</h3>
<p><strong>Keywords to spot:</strong></p>
<ul>
<li>“Connect all points/cities/servers…”</li>
<li>“Minimum cost/wire/lines to link…”</li>
<li>“Minimizing the maximum edge weight between two points” (Minimax).</li>
<li>“Critical connection” or “Redundant connection.”</li>
</ul>
<p><strong>The “Vibe” check:</strong></p>
<ul>
<li>If the problem asks for a path, it’s usually BFS/Dijkstra.</li>
<li>If the problem asks for global connectivity (everyone connected to everyone), it’s MST.</li>
</ul>
<hr>
<h3 id="the-4-essential-patterns">The 4 Essential Patterns</h3>
<h4 id="pattern-1-standard-mst-connect-everything">Pattern 1: Standard MST (Connect Everything)</h4>
<p>Goal: Calculate the cost to connect all nodes.<br>
Strategy: Standard Kruskal’s or Prim’s.</p>
<ul>
<li>[1584] Min Cost to Connect All Points: (Use Prim’s Array because it’s Dense).</li>
<li>[1135] Connecting Cities With Minimum Cost: (Use Kruskal’s).</li>
</ul>
<h3 id="pattern-2-the-bottleneck--minimax-path">Pattern 2: The “Bottleneck” / Minimax Path</h3>
<p>Goal: <strong>Find a path from A to B such that the maximum edge weight on that path is minimized.</strong></p>
<p>Strategy:</p>
<ol>
<li>
<p><strong>Kruskal’s Variation:</strong> Sort edges. Add them to DSU one by one. Stop the moment <code>find(A) == find(B)</code>. The last edge added is your answer.</p>
</li>
<li>
<p><strong>Modified Dijkstra:</strong> Minimize the max(curr_path, new_edge).</p>
<ul>
<li>[1631] Path With Minimum Effort: (Minimizing the max height difference).</li>
<li>[778] Swim in Rising Water: (Earliest time = lowest max height).</li>
<li>[1102] Path With Maximum Minimum Value: (The reverse: Max Spanning Tree).</li>
</ul>
</li>
</ol>
<h3 id="pattern-3-offline-queries-incremental-mst">Pattern 3: Offline Queries (Incremental MST)</h3>
<p>Goal: <strong>Answer multiple queries about connectivity with a “limit” or “threshold”.</strong></p>
<p>Strategy:<br>
<strong>1.  Sort Queries by their limit/weight.<br>
2.  Sort Edges by weight.<br>
3.  Two Pointers: Iterate through queries; add valid edges to DSU; never reset DSU.</strong></p>
<ul>
<li>[1697] Checking Existence of Edge Length Limited Paths</li>
</ul>
<h3 id="pattern-4-tree-structure--critical-edges">Pattern 4: Tree Structure &amp; Critical Edges</h3>
<p>Goal: <strong>Find which edges are necessary for the MST and which are useless (cycles).</strong><br>
Strategy:</p>
<p><strong>1.  Pseudo-Critical:</strong> Force include an edge <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>→</mo></mrow><annotation encoding="application/x-tex">\to</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.36687em; vertical-align: 0em;"></span><span class="mrel">→</span></span></span></span></span> calculate MST. Exclude an edge <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>→</mo></mrow><annotation encoding="application/x-tex">\to</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.36687em; vertical-align: 0em;"></span><span class="mrel">→</span></span></span></span></span> calculate MST. Compare with original MST cost.</p>
<ul>
<li>
<p>Write the skip function to include exclude ex: <code>def kruskal(include, exclude)</code><br>
always keep a seperate dsu, so define inside function, including the index means to explicitly <code>union(x, y)</code> that edge.</p>
</li>
<li>
<p>including part :</p>
</li>
</ul>
<pre><code>if include != -1:
       u, v, w, _  = edges[include]
       dsu.union(u, v)
       min_cost += w
       min_edges += 1
</code></pre>
<p>then excluding the edge means to not include it in union of all edges, so just skip with a check :</p>
<pre><code>for i in range(nedge):
       if i==exclude:
           continue

       u, v, w, ind = edges[i]

       if dsu.union(u, v):
           min_cost += w
           min_edges += 1
</code></pre>
<p>check if MST possible or not:</p>
<pre><code>if min_edges&lt;n-1:
       return float('inf')
</code></pre>
<p>if MST is possible we have <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>e</mi><mi>d</mi><mi>g</mi><mi>e</mi><mi>s</mi><mo>=</mo><mi>n</mi><mo>−</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">edges = n-1</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.88888em; vertical-align: -0.19444em;"></span><span class="mord mathnormal">e</span><span class="mord mathnormal">d</span><span class="mord mathnormal" style="margin-right: 0.03588em;">g</span><span class="mord mathnormal">es</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.66666em; vertical-align: -0.08333em;"></span><span class="mord mathnormal">n</span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">−</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">1</span></span></span></span></span> where <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi></mrow><annotation encoding="application/x-tex">n</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.43056em; vertical-align: 0em;"></span><span class="mord mathnormal">n</span></span></span></span></span> is no. of nodes.</p>
<p>full sample:</p>
<pre><code>def kruskal(include, exclude):
   dsu = DSU(n)
   min_edges = 0
   min_cost = 0

   if include != -1:
       u, v, w, _  = edges[include]
       dsu.union(u, v)
       min_cost += w
       min_edges += 1
       
   for i in range(nedge):
       if i==exclude:
           continue

       u, v, w, ind = edges[i]

       if dsu.union(u, v):
           min_cost += w
           min_edges += 1
       
   if min_edges&lt;n-1:
       return float('inf')
   
   return min_cost
</code></pre>
<ol start="2">
<li><strong>Cycle Detection</strong>: If <code>dsu.union(u, v) returns False</code>, that edge creates a cycle (is redundant).</li>
</ol>
<ul>
<li>[684] Redundant Connection: (Find the edge that creates a cycle).</li>
</ul>
<pre><code>redundant = []
for u, v in edges:
	if not union(u, v):
		redundant.append((u,v))
</code></pre>
<p><strong>Problem :</strong> [1489] Find Critical and Pseudo-Critical Edges in MST: (Hard, but great for understanding).<br>
<strong>This “Include/Exclude” pattern (also called Sensitivity Analysis) is a powerful technique not just for MSTs, but for analyzing the robustness of any system</strong></p>
<h4 id="similar-leetcode-problems">Similar LeetCode Problems</h4>
<p><em>These problems all require you to ask: “What happens to the system if I delete this piece?” or “What happens if I force this path?”</em></p>
<p><strong>1.  [1192] Critical Connections in a Network (Hard)</strong></p>
<ul>
<li>The Concept: This is the <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><mi>V</mi><mo>+</mo><mi>E</mi><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(V+E)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord mathnormal" style="margin-right: 0.22222em;">V</span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">+</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.05764em;">E</span><span class="mclose">)</span></span></span></span></span> version of finding “Critical Edges”. In graph theory, critical edges are called Bridges.</li>
<li>Why it’s similar: You must find all edges that, if removed, make the graph disconnected. Instead of running Kruskal’s <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>E</mi></mrow><annotation encoding="application/x-tex">E</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.05764em;">E</span></span></span></span></span> times (too slow), you use <strong>Tarjan’s Bridge-Finding Algorithm (DFS + Timestamps).</strong></li>
<li>Goal: Try this after you master DFS.</li>
</ul>
<p><strong>2. [685] Redundant Connection II (Hard)</strong></p>
<ul>
<li>The Concept: You have a directed tree where one extra edge was added. You must find it.</li>
<li>Why it’s similar: You often have to “guess” (exclude) an edge to see if the remaining graph becomes a valid tree. If excluding Edge A fixes the graph, Edge A is the culprit.</li>
</ul>
<p><strong>3. [924] Minimize Malware Spread (Hard)</strong></p>
<ul>
<li>The Concept: You can remove one node from the “infected” list. Which removal saves the most computers?</li>
<li>Why it’s similar: This uses the “Exclude” logic. For every infected node, you pretend to remove it (exclude), run the infection simulation (DSU/BFS), and measure the “cost” (total infected).</li>
</ul>
<p><strong>4. [787] Cheapest Flights Within K Stops (Medium)</strong></p>
<ul>
<li>The Concept: Find the cheapest path with a constraint.<br>
Connection: While usually solved with Bellman-Ford/Dijkstra, you can think of it as: “Force this specific path structure, does it satisfy the cost?”</li>
</ul>
<h4 id="real-world-scenarios-for-includeexclude">Real-World Scenarios for “Include/Exclude”</h4>
<p>This logic is the foundation of Resilience Engineering.</p>
<h4 id="telecommunications-single-point-of-failure-spof">1. Telecommunications: Single Point of Failure (SPOF)</h4>
<ul>
<li>Scenario: An internet service provider (ISP) has cables connecting cities.</li>
<li>Critical Edge: A cable that, if cut (Excluded), disconnects a city or forces traffic onto a much longer, slower path (increasing “MST Cost”).</li>
<li>Application: ISPs run this algorithm to find Critical Edges. Once identified, they physically build a backup cable (a pseudo-critical edge) parallel to it so the critical edge becomes non-critical.</li>
</ul>
<h4 id="supply-chain-logistics-perfect-backups">2. Supply Chain Logistics: “Perfect Backups”</h4>
<ul>
<li>Scenario: Amazon shipping goods from warehouses to customers. The “MST” is the cheapest set of shipping routes.</li>
<li>Pseudo-Critical Edge: This represents an Alternative Vendor or Route that costs exactly the same as your primary one.</li>
<li></li>
</ul>
<p><strong>Application: If your primary trucking company goes on strike (Excluded), you instantly switch to the “Pseudo-Critical” vendor without losing money. Identifying these edges gives you leverage in negotiations (“I can switch to Vendor B and it costs me the same!”).</strong></p>
<h2 id="some-important-code-templates">Some important code templates</h2>
<h3 id="dsu-class">DSU class</h3>
<pre><code>class DSU:
    def __init__(self, n):
        self.parent = list(range(n))
        self.size = [1] * n

    def find(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])
        return self.parent[x]

    def union(self, x, y):
        rootX, rootY = self.find(x), self.find(y)
        if rootX != rootY:
            if self.size[rootX] &lt; self.size[rootY]:
                rootX, rootY = rootY, rootX
            self.parent[rootY] = rootX
            self.size[rootX] += self.size[rootY]
            return True
        return False
</code></pre>
<h3 id="kruskals--algorithm-sort--dsu">Kruskal’s  Algorithm (sort + DSU)</h3>
<pre><code>edges.sort(key=lambda x: x[2]) # Sort by weight
dsu = DSU(n)
cost = 0
edges_count = 0

for u, v, w in edges:
    if dsu.union(u, v):
        cost += w
        edges_count += 1
        if edges_count == n - 1: break # Tree complete
</code></pre>
<h3 id="prims-algo-for-dense-graphscoordinate-problems">Prim’s algo for dense graphs/coordinate problems</h3>
<pre><code>min_dist = [float('inf')] * n
min_dist[0] = 0
visited = [False] * n

for _ in range(n):
    # 1. Find min unvisited node (Linear Scan)
    curr_node = -1
    curr_min = float('inf')
    for i in range(n):
        if not visited[i] and min_dist[i] &lt; curr_min:
            curr_min = min_dist[i]
            curr_node = i
            
    visited[curr_node] = True
    mst_cost += curr_min
    
    # 2. Update neighbors
    for v in range(n):
        if not visited[v]:
            weight = dist(curr_node, v) # Logic to calc distance
            if weight &lt; min_dist[v]:
                min_dist[v] = weight
</code></pre>
<hr>
<h2 id="problems-solved-and-some-good-solutions-to-read">Problems solved and some good solutions to read</h2>
<h3 id="brute-force-for-1192.-critical-connections-in-a-network">**BRUTE FORCE for 1192. Critical Connections in a Network</h3>
<p>For n&lt;1000**</p>
<blockquote>
<p>NOT PASSED</p>
</blockquote>
<blockquote>
<p>Time complexity: <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><msup><mi>E</mi><mn>2</mn></msup><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(E^2)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.06411em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord"><span class="mord mathnormal" style="margin-right: 0.05764em;">E</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.814108em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span></span></span></span></span><span class="mclose">)</span></span></span></span></span></p>
</blockquote>
<p><img src="https://assets.leetcode.com/uploads/2019/09/03/1537_ex1_2.png" alt=""></p>
<p>So i implemented a DSU class and tracking all nodes in a set and also tracking components</p>
<pre><code>class DSU:
    def __init__(self, n):
        self.parent = list(range(n))
        self.nodes = set()
        self.size = [1] * n
        self.components = n
        
    def find(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])
        return self.parent[x]

    def union(self, x, y):
        rootX, rootY = self.find(x), self.find(y)
        if rootX != rootY:           
            if self.size[rootX]&lt; self.size[rootY]:
                self.parent[rootX] = rootY
                self.size[rootY] += self.size[rootX]    
            else:
                self.parent[rootY] = rootX
                self.size[rootX] += self.size[rootY]           
            self.nodes.add(rootX)
            self.nodes.add(rootY)
            self.components -= 1
            return True
        return False
</code></pre>
<p>Then i wrote a skip logic in main function which essentially does “skip an edge and then check for the whole graph, if skipping that increases the component count and if merged DSU contains all nodes of graph”<br>
which is implemented via below line</p>
<pre><code> if len(dsu.nodes.intersection(nodes))!=n or dsu.components&gt;1:
                res.append(connections[exclude])
</code></pre>
<p>then the full function code:</p>
<pre><code>class Solution:
    def criticalConnections(self, n: int, connections: List[List[int]]) -&gt; List[List[int]]:
        nconn = len(connections)
        nodes = set(range(n))
        def skip(exclude, res):
            dsu = DSU(n)
            for i in range(nconn):
                if i==exclude:
                    continue       
                u, v = connections[i]
                dsu.union(u, v)
               
            if len(dsu.nodes.intersection(nodes))!=n or dsu.components&gt;1:
                res.append(connections[exclude])
       
        res = []
        for i in range(nconn):
            skip(i, res)
       
        return res
</code></pre>
<h3 id="bruteforce-i-implemented-for-redundant-connections-2-685"><strong>Bruteforce i implemented for Redundant connections 2 (685)</strong></h3>
<blockquote>
<p>Time complexity : <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><msup><mi>N</mi><mn>2</mn></msup><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(N^2)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.06411em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord"><span class="mord mathnormal" style="margin-right: 0.10903em;">N</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.814108em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span></span></span></span></span><span class="mclose">)</span></span></span></span></span></p>
</blockquote>
<p><img src="https://assets.leetcode.com/uploads/2020/12/20/graph2.jpg" alt=""></p>
<p>First i implemented standard DSU class with track components count logic, then i implemented the solution below</p>
<p>what we do is essentially we skip an edge in graph while taking union of all of edges and checking if rest of the graph is a valid tree.</p>
<pre><code>def skip(exclude):
   dsu = DSU(n)
   rest = []
   
   for i in range(n-1, -1, -1):
       if i==exclude:
           continue
      
       u, v = edges[i]
       rest.append([u-1, v-1])
       dsu.union(u-1, v-1)
      
   #write valid tree condition + check connectivity DSU
   if dsu.components==1 and validTree(rest):
       return True
  
   return False
</code></pre>
<p>if we form 1 single component DSU merge of whole graph and tree is valid (formed from rest of edges, ignoring the skip edge, then we return true.</p>
<pre><code>if dsu.components==1 and validTree(rest):
       return True
</code></pre>
<p>A tree is valid if :</p>
<ul>
<li>Only one node has <code>indegree=0</code> that is the root node</li>
<li>Rest all the nodes have <code>indegree=1</code> and such nodes must be <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>−</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">n-1</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.66666em; vertical-align: -0.08333em;"></span><span class="mord mathnormal">n</span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">−</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">1</span></span></span></span></span> in number</li>
</ul>
<p>see the below implementation:</p>
<pre><code>zero = 0
one = 0

for i in indeg:
    if i==0:
        zero+=1
    elif i==1:
        one+=1

if zero == 1 and one == n-1:
    return True
</code></pre>
<p>Read the full implementation below :</p>
<pre><code>class Solution:
    def findRedundantDirectedConnection(self, edges: List[List[int]]) -&gt; List[int]:
        n = len(edges)
        redundant = []

        def validTree(edges):
            indeg = [0]*(n)
            for _, v in edges:
                indeg[v-1]+=1

            zero = 0
            one = 0

            for i in indeg:
                if i==0:
                    zero+=1
                elif i==1:
                    one+=1

            if zero == 1 and one == n-1:
                return True

            return False
                   
        def skip(exclude):
            dsu = DSU(n)
            rest = []
            
            for i in range(n-1, -1, -1):
                if i==exclude:
                    continue
               
                u, v = edges[i]
                rest.append([u-1, v-1])
                dsu.union(u-1, v-1)
               
            #write valid tree condition + check connectivity DSU
            if dsu.components==1 and validTree(rest):
                return True
           
            return False
       
        for i in range(n-1, -1, -1):
            if skip(i):
                return edges[i]

        return []
</code></pre>
<p>If skipping any edge results in true (valid tree) then we just return that edge</p>
<pre><code>for i in range(n-1, -1, -1):
   if skip(i):
       return edges[i]
</code></pre>
<h3 id="binary-search-solution-on-graph--3620.-network-recovery-pathways">Binary search solution on graph : [3620. Network Recovery Pathways]</h3>
<p><img src="https://assets.leetcode.com/uploads/2025/06/06/graph-11.png" alt=""><br>
As you can see, we can reach from <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>s</mi><mi>r</mi><mi>c</mi><mo>=</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">src=0</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.43056em; vertical-align: 0em;"></span><span class="mord mathnormal">src</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">0</span></span></span></span></span> to <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>d</mi><mi>e</mi><mi>s</mi><mi>t</mi><mo>=</mo><mn>4</mn></mrow><annotation encoding="application/x-tex">dest=4</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.69444em; vertical-align: 0em;"></span><span class="mord mathnormal">d</span><span class="mord mathnormal">es</span><span class="mord mathnormal">t</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">4</span></span></span></span></span> via minedge cost <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>K</mi><mo>=</mo><mn>5</mn></mrow><annotation encoding="application/x-tex">K=5</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.07153em;">K</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">5</span></span></span></span></span> since every edge weight is <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>&gt;</mo><mo>=</mo><mi>K</mi></mrow><annotation encoding="application/x-tex">&gt;=K</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.5782em; vertical-align: -0.0391em;"></span><span class="mrel">&gt;=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.07153em;">K</span></span></span></span></span> so since we need maximum, we will greedily try reaching src to dest via taking a little higher <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>K</mi></mrow><annotation encoding="application/x-tex">K</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.07153em;">K</span></span></span></span></span> since we can already reach it with previous smaller <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>K</mi></mrow><annotation encoding="application/x-tex">K</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.07153em;">K</span></span></span></span></span>.</p>
<p>Thus <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>a</mi><mi>n</mi><mi>s</mi><mo>=</mo><mn>6</mn></mrow><annotation encoding="application/x-tex">ans=6</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.43056em; vertical-align: 0em;"></span><span class="mord mathnormal">an</span><span class="mord mathnormal">s</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">6</span></span></span></span></span>, going any more than this will make this condition fail: edgeweight <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>w</mi><mo>&gt;</mo><mo>=</mo><mi>K</mi></mrow><annotation encoding="application/x-tex">w&gt;=K</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.5782em; vertical-align: -0.0391em;"></span><span class="mord mathnormal" style="margin-right: 0.02691em;">w</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">&gt;=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.07153em;">K</span></span></span></span></span></p>
<pre><code>N = Number of nodes (len(online)).
M = Number of edges (len(edges)).
W = Number of unique edge weights (W&lt;=M).
</code></pre>
<p>Time complexity: <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><mi>M</mi><mi>l</mi><mi>o</mi><mi>g</mi><mi>M</mi><mi>l</mi><mi>o</mi><mi>g</mi><mi>N</mi><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(M logM logN)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord mathnormal" style="margin-right: 0.01968em;">Ml</span><span class="mord mathnormal">o</span><span class="mord mathnormal" style="margin-right: 0.03588em;">g</span><span class="mord mathnormal" style="margin-right: 0.01968em;">Ml</span><span class="mord mathnormal">o</span><span class="mord mathnormal" style="margin-right: 0.03588em;">g</span><span class="mord mathnormal" style="margin-right: 0.10903em;">N</span><span class="mclose">)</span></span></span></span></span></p>
<p>The core idea is, if we take all online nodes, then can we reach from <code>source</code> to <code>destination</code> via some optimal cost <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>K</mi></mrow><annotation encoding="application/x-tex">K</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.07153em;">K</span></span></span></span></span></p>
<p>now that cost <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>K</mi></mrow><annotation encoding="application/x-tex">K</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.07153em;">K</span></span></span></span></span> is special since it is maximum among all minimum cost edge we need to pick to reach to destination ex:<br>
agar hamare paas edges h : <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>E</mi><mo>=</mo><mrow><mn>7</mn><mo separator="true">,</mo><mn>5</mn><mo separator="true">,</mo><mn>6</mn><mo separator="true">,</mo><mn>6</mn></mrow></mrow><annotation encoding="application/x-tex">E = {7, 5, 6, 6}</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.05764em;">E</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.83888em; vertical-align: -0.19444em;"></span><span class="mord"><span class="mord">7</span><span class="mpunct">,</span><span class="mspace" style="margin-right: 0.166667em;"></span><span class="mord">5</span><span class="mpunct">,</span><span class="mspace" style="margin-right: 0.166667em;"></span><span class="mord">6</span><span class="mpunct">,</span><span class="mspace" style="margin-right: 0.166667em;"></span><span class="mord">6</span></span></span></span></span></span> then if we pick <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>7</mn></mrow><annotation encoding="application/x-tex">7</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">7</span></span></span></span></span> and try, we will not be able to walk on paths with edges <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>5</mn><mo separator="true">,</mo><mn>6</mn></mrow><annotation encoding="application/x-tex">5, 6</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.83888em; vertical-align: -0.19444em;"></span><span class="mord">5</span><span class="mpunct">,</span><span class="mspace" style="margin-right: 0.166667em;"></span><span class="mord">6</span></span></span></span></span> so we need to get lower, we pick <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>5</mn></mrow><annotation encoding="application/x-tex">5</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">5</span></span></span></span></span>, so if we have min edge weight <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>K</mi><mo>=</mo><mn>5</mn></mrow><annotation encoding="application/x-tex">K=5</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.07153em;">K</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">5</span></span></span></span></span> with us, then we can reach to dest while walking on <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>E</mi></mrow><annotation encoding="application/x-tex">E</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.05764em;">E</span></span></span></span></span></p>
<p>so let’s get greedy and search for a bit higher, let’s say <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>K</mi><mo>=</mo><mn>6</mn></mrow><annotation encoding="application/x-tex">K=6</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.07153em;">K</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">6</span></span></span></span></span> and WOW we can even reach to destination while walking on edges in <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>E</mi></mrow><annotation encoding="application/x-tex">E</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.05764em;">E</span></span></span></span></span> , so our answer is <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>K</mi><mo>=</mo><mn>6</mn></mrow><annotation encoding="application/x-tex">K=6</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.07153em;">K</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">6</span></span></span></span></span> since we cannot take higher than <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>6</mn></mrow><annotation encoding="application/x-tex">6</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">6</span></span></span></span></span></p>
<p>The sum of edges we take must be less than a given value <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>k</mi></mrow><annotation encoding="application/x-tex">k</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.69444em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.03148em;">k</span></span></span></span></span></p>
<p>We have to <strong>binary search</strong> the value of optimal <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>K</mi></mrow><annotation encoding="application/x-tex">K</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.07153em;">K</span></span></span></span></span></p>
<p><strong>ALGO:</strong></p>
<ul>
<li>We sorted the unique edge weights of online nodes</li>
<li>Applying binary searching for the optimal minimum value or lower bound that helps us to reach the destination <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo stretchy="false">(</mo><mi>n</mi><mo>−</mo><mn>1</mn><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">(n-1)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mopen">(</span><span class="mord mathnormal">n</span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">−</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord">1</span><span class="mclose">)</span></span></span></span></span></li>
<li>Now the <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>l</mi><mi>b</mi><mo>=</mo><mi>X</mi></mrow><annotation encoding="application/x-tex">lb = X</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.69444em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.01968em;">l</span><span class="mord mathnormal">b</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.07847em;">X</span></span></span></span></span> s.t for that <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>v</mi><mi>a</mi><mi>l</mi><mi>u</mi><mi>e</mi><mo>&gt;</mo><mo>=</mo><mi>X</mi></mrow><annotation encoding="application/x-tex">value&gt;=X</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.73354em; vertical-align: -0.0391em;"></span><span class="mord mathnormal" style="margin-right: 0.03588em;">v</span><span class="mord mathnormal">a</span><span class="mord mathnormal" style="margin-right: 0.01968em;">l</span><span class="mord mathnormal">u</span><span class="mord mathnormal">e</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">&gt;=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.07847em;">X</span></span></span></span></span> we can reach the destination and we will greedily search for maximum minimum we need to reach <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>−</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">n-1</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.66666em; vertical-align: -0.08333em;"></span><span class="mord mathnormal">n</span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">−</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">1</span></span></span></span></span></li>
<li>Then define <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>c</mi><mi>a</mi><mi>n</mi><mi>R</mi><mi>e</mi><mi>a</mi><mi>c</mi><mi>h</mi><mo stretchy="false">(</mo><mo stretchy="false">)</mo><mo>:</mo></mrow><annotation encoding="application/x-tex">canReach():</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathnormal">c</span><span class="mord mathnormal">an</span><span class="mord mathnormal" style="margin-right: 0.00773em;">R</span><span class="mord mathnormal">e</span><span class="mord mathnormal">a</span><span class="mord mathnormal">c</span><span class="mord mathnormal">h</span><span class="mopen">(</span><span class="mclose">)</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">:</span></span></span></span></span></li>
<li>It will apply dijkstra’s algo to check whether we can reach the n-1 node from 0 via minimum cost path where the mincost=X (our lower bound)</li>
</ul>
<p>Store weights and we will binary search on it:</p>
<pre><code>sweights = sorted(list(weights))
</code></pre>
<p>set <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>l</mi><mo>=</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">l=0</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.69444em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.01968em;">l</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">0</span></span></span></span></span> and <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>h</mi><mo>=</mo><mi>l</mi><mi>e</mi><mi>n</mi><mo stretchy="false">(</mo><mi>s</mi><mi>w</mi><mi>e</mi><mi>i</mi><mi>g</mi><mi>h</mi><mi>t</mi><mi>s</mi><mo>−</mo><mn>1</mn><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">h=len(sweights-1)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.69444em; vertical-align: 0em;"></span><span class="mord mathnormal">h</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.01968em;">l</span><span class="mord mathnormal">e</span><span class="mord mathnormal">n</span><span class="mopen">(</span><span class="mord mathnormal">s</span><span class="mord mathnormal" style="margin-right: 0.02691em;">w</span><span class="mord mathnormal">e</span><span class="mord mathnormal">i</span><span class="mord mathnormal" style="margin-right: 0.03588em;">g</span><span class="mord mathnormal">h</span><span class="mord mathnormal">t</span><span class="mord mathnormal">s</span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">−</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord">1</span><span class="mclose">)</span></span></span></span></span></p>
<pre><code>l = 0
r = len(sweights)-1
ans = -1

while l&lt;=r:
    mid = (l+r)//2
    val = sweights[mid]
    if canReach(val):
        ans = val
        l = mid+1
    else:
        r = mid-1
</code></pre>
<p>while we binary search in range <code>l&lt;=r</code> we find the optimal weight we atleast need to pick, to reach the destination. We check that via <code>canReach(val)</code> function.<br>
See it is just a heap dijkstra implementation from src to dest</p>
<p>If we can reach, we check if we can reach with cost within given range <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>k</mi></mrow><annotation encoding="application/x-tex">k</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.69444em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.03148em;">k</span></span></span></span></span></p>
<pre><code>if node==n-1:
	return cost&lt;=k
</code></pre>
<p>other wise if mincost that we are checking this function on, is greater than edge weights than we push them in heap (include that path)</p>
<pre><code>for v, w in graph[node]:
  if w&lt;mincost:
      continue
      
  if cost+w&lt;=k and cost + w &lt; dist[v]:
      dist[v] = cost+w
      heapq.heappush(pq, (cost+w, v))
</code></pre>
<p>Full <code>canReach()</code> function below:</p>
<pre><code>def canReach(mincost):
   pq = [(0, 0)]
   dist = [float('inf')]*n
   dist[0] = 0
   while pq:
       cost, node = heapq.heappop(pq)
       if node==n-1:
           return cost&lt;=k
     
       if cost &gt; dist[node]:
           continue
      
       for v, w in graph[node]:
           if w&lt;mincost:
               continue
               
           if cost+w&lt;=k and cost + w &lt; dist[v]:
               dist[v] = cost+w
               heapq.heappush(pq, (cost+w, v))
   return False
</code></pre>
<p>Full solution below :</p>
<pre><code>class Solution:
    def findMaxPathScore(self, edges: List[List[int]], online: List[bool], k: int) -&gt; int:
        graph = defaultdict(list)

        weights = set()
        for u, v, w in edges:           
            if online[u] and online[v]:
                weights.add(w)
                graph[u].append((v, w))

        if not weights:
            return -1
       
        sweights = sorted(list(weights))
        n = len(online)

        def canReach(mincost):
            pq = [(0, 0)]
            dist = [float('inf')]*n
            dist[0] = 0
            while pq:
                cost, node = heapq.heappop(pq)
                if node==n-1:
                    return cost&lt;=k
              
                if cost &gt; dist[node]:
                    continue
               
                for v, w in graph[node]:
                    if w&lt;mincost:
                        continue
                        
                    if cost+w&lt;=k and cost + w &lt; dist[v]:
                        dist[v] = cost+w
                        heapq.heappush(pq, (cost+w, v))
            return False
   

        l = 0
        r = len(sweights)-1
        ans = -1

        while l&lt;=r:
            mid = (l+r)//2
            val = sweights[mid]
            if canReach(val):
                ans = val
                l = mid+1
            else:
                r = mid-1
           
        return ans
</code></pre>
<h3 id="a-good-bfsdfs-problem--827.-making-a-large-island">A good bfs/dfs problem : [827. Making A Large Island]</h3>
<p><strong>Input:</strong> grid = [[1,0],[0,1]]<br>
<strong>Output:</strong> 3<br>
<strong>Explanation:</strong> Change one 0 to 1 and connect two 1s, then we get an island with area = 3</p>
<p><strong>Solution:</strong> So essentially what we have to do it is we just have to make the largest island possible by change any one zero in island to a 1.</p>
<p>So i first wrote a brute force that passed <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>72</mn><mi mathvariant="normal">/</mi><mn>75</mn></mrow><annotation encoding="application/x-tex">72/75</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord">72/75</span></span></span></span></span> on leetcode but it was horrible <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><msup><mi>N</mi><mn>4</mn></msup><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(N^4)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.06411em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord"><span class="mord mathnormal" style="margin-right: 0.10903em;">N</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.814108em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">4</span></span></span></span></span></span></span></span><span class="mclose">)</span></span></span></span></span> in which what i did was just starting bfs from each 0 treating it as 1 and counting the whole island and returning it, so bfs essentially looked like:</p>
<pre><code>def bfs(src):
	count = 1 #treating 0 as 1
	
	while queue:
		visit neighbours of that node
			count+=1
</code></pre>
<p>then call this bfs for all the 0s one by one and storing max using <code>maxarea = max(maxarea, bfs((i, j)))</code> which is just a bruteforce. Simple to come up with.</p>
<p>A better solution than this is very smart and a bit code heavy.</p>
<p>So just build a hashmap of all islands paired like <code>{islandID: size}</code>, Ex:</p>
<pre><code>{
2: 10
3: 12
4: 3
....n
}
</code></pre>
<p>So just run a bfs, paint all the 1s to id (initally 2) and increment after each bfs for each island.<br>
So island 1 will get <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>i</mi><mi>d</mi><mo>=</mo><mn>2</mn></mrow><annotation encoding="application/x-tex">id=2</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.69444em; vertical-align: 0em;"></span><span class="mord mathnormal">i</span><span class="mord mathnormal">d</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">2</span></span></span></span></span>, island 2 will get <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>i</mi><mi>d</mi><mo>=</mo><mn>3</mn></mrow><annotation encoding="application/x-tex">id=3</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.69444em; vertical-align: 0em;"></span><span class="mord mathnormal">i</span><span class="mord mathnormal">d</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">3</span></span></span></span></span> and so on…</p>
<pre><code>def bfs(source, nid):
   q = deque()
   q.append(source)
   direc = [(1, 0), (0,1), (-1, 0), (0, -1)]
   count = 1
   grid[source[0]][source[1]] = nid

   while q:
       r, c = q.popleft()
       for dr, dc in direc:
           nr = r+dr
           nc = c+dc               
           if 0&lt;=nr&lt;n and 0&lt;=nc&lt;n and grid[nr][nc]==1:
               count+=1
               grid[nr][nc] = nid
               q.append((nr, nc))                      
   return count
</code></pre>
<p>Now after painting, just store it in the map with something like this :</p>
<pre><code>nid = 2
areaid = defaultdict(int)
for i in range(n):
    for j in range(n):
        if grid[i][j] == 1:
            size = bfs((i, j),nid)
            areaid[nid] = size
            nid+=1
</code></pre>
<p>what if our matrix has no 0s ? So if islands exist, we preassign the max size of island to our maxarea variable</p>
<pre><code>mxarea = max(areaid.values()) if areaid else 0
</code></pre>
<p>Now lookup time, we have unique identification to each island using ids <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>2</mn><mo separator="true">,</mo><mn>3</mn><mo separator="true">,</mo><mn>4...</mn></mrow><annotation encoding="application/x-tex">2, 3, 4...</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.83888em; vertical-align: -0.19444em;"></span><span class="mord">2</span><span class="mpunct">,</span><span class="mspace" style="margin-right: 0.166667em;"></span><span class="mord">3</span><span class="mpunct">,</span><span class="mspace" style="margin-right: 0.166667em;"></span><span class="mord">4...</span></span></span></span></span><br>
So we need to find all <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>0</mn><mi>s</mi></mrow><annotation encoding="application/x-tex">0s</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">0</span><span class="mord mathnormal">s</span></span></span></span></span> and just check the neighbours of it, if any neighbour is an island ! (cell contains <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>2</mn><mo separator="true">,</mo><mn>3</mn><mo separator="true">,</mo><mn>4...</mn></mrow><annotation encoding="application/x-tex">2, 3, 4...</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.83888em; vertical-align: -0.19444em;"></span><span class="mord">2</span><span class="mpunct">,</span><span class="mspace" style="margin-right: 0.166667em;"></span><span class="mord">3</span><span class="mpunct">,</span><span class="mspace" style="margin-right: 0.166667em;"></span><span class="mord">4...</span></span></span></span></span> ids) Then we add the unique id values.</p>
<pre><code>directions = [(1, 0), (0, 1), (-1, 0), (0, -1)]
for i in range(n):
  for j in range(n):
      if grid[i][j]==0:
          neighbor_ids = set() 
      
          for dr, dc in directions:
              nr, nc = i + dr, j + dc       
              if 0 &lt;= nr &lt; n and 0 &lt;= nc &lt; n and grid[nr][nc] &gt; 1:
                  neighbor_ids.add(grid[nr][nc])
          
          current_total = 1
          for id in neighbor_ids:
              current_total += areaid[id]
          
          mxarea = max(mxarea, current_total)
</code></pre>
<p>We take unique neighbour ids to tackle the below case:</p>
<pre><code>2 2 2
2 0 2
2 2 2
</code></pre>
<p><strong>Up:</strong> ID 2 (Size 8)<br>
<strong>Down:</strong> ID 2 (Size 8)<br>
<strong>Left:</strong> ID 2 (Size 8)<br>
<strong>Right:</strong> ID 2 (Size 8)</p>
<p>If you blindly sum them (<code>1 + 8 + 8 + 8 + 8</code>), you get 33. <strong>WRONG.</strong> It’s all one island! You only connect to Island #2 <strong>once</strong>. The result should be <code>1 + 8 = 9</code>.<br>
Thus our <code>mxarea</code> is the answer.</p>
<h3 id="alternate-2d-dsu-approach-a-lot-better-and-dynamic">Alternate 2D-DSU approach (A lot better and dynamic)</h3>
<p>Time complexity : <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><msup><mi>N</mi><mn>2</mn></msup><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(N^2)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.06411em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord"><span class="mord mathnormal" style="margin-right: 0.10903em;">N</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.814108em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span></span></span></span></span><span class="mclose">)</span></span></span></span></span></p>
<p>So we can just take union of all 1s and form island groups, and simply check the neighbours of all 0s, which neighbour belongs to which island by checking their ultimate parent. This way we can easily implement it.</p>
<p>Since it is a matrix, we need a <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>2</mn><mi>D</mi><mover><mo stretchy="true" minsize="3.0em">undefined</mo><mpadded width="+0.6em" lspace="0.3em"><mrow></mrow></mpadded></mover><mn>1</mn><mi>D</mi></mrow><annotation encoding="application/x-tex">2D \xrightarrow{} 1D</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.69433em; vertical-align: -0.011em;"></span><span class="mord">2</span><span class="mord mathnormal" style="margin-right: 0.02778em;">D</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel x-arrow"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 0.622em;"><span class="" style="top: -3.144em;"><span class="pstrut" style="height: 2.522em;"></span><span class="sizing reset-size6 size3 mtight x-arrow-pad"><span class="mord mtight"></span></span></span><span class="svg-align" style="top: -2.511em;"><span class="pstrut" style="height: 2.522em;"></span><span class="hide-tail" style="height: 0.522em; min-width: 1.469em;"><svg width="400em" height="0.522em" viewBox="0 0 400000 522" preserveAspectRatio="xMaxYMin slice"><path d="M0 241v40h399891c-47.3 35.3-84 78-110 128
-16.7 32-27.7 63.7-33 95 0 1.3-.2 2.7-.5 4-.3 1.3-.5 2.3-.5 3 0 7.3 6.7 11 20
 11 8 0 13.2-.8 15.5-2.5 2.3-1.7 4.2-5.5 5.5-11.5 2-13.3 5.7-27 11-41 14.7-44.7
 39-84.5 73-119.5s73.7-60.2 119-75.5c6-2 9-5.7 9-11s-3-9-9-11c-45.3-15.3-85
-40.5-119-75.5s-58.3-74.8-73-119.5c-4.7-14-8.3-27.3-11-40-1.3-6.7-3.2-10.8-5.5
-12.5-2.3-1.7-7.5-2.5-15.5-2.5-14 0-21 3.7-21 11 0 2 2 10.3 6 25 20.7 83.3 67
 151.7 139 205zm0 0v40h399900v-40z"></path></svg></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 0.011em;"><span class=""></span></span></span></span></span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.68333em; vertical-align: 0em;"></span><span class="mord">1</span><span class="mord mathnormal" style="margin-right: 0.02778em;">D</span></span></span></span></span> mapping which is <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>r</mi><mo>∗</mo><mi>N</mi><mo>+</mo><mi>c</mi></mrow><annotation encoding="application/x-tex">r*N+c</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.46528em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.02778em;">r</span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">∗</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 0.76666em; vertical-align: -0.08333em;"></span><span class="mord mathnormal" style="margin-right: 0.10903em;">N</span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">+</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 0.43056em; vertical-align: 0em;"></span><span class="mord mathnormal">c</span></span></span></span></span> where <strong>N represents the number of COLUMNS</strong>.</p>
<p>So for island groups :</p>
<pre><code>n = len(grid)
dsu = DSU(n*n)
direc = [(1, 0), (0, 1), (-1, 0), (0, -1)]

for r in range(n):
  for c in range(n):
    if grid[r][c]==1:
      idx = r*n+c        
      for dr, dc in direc:
        nr = r+dr
        nc = c+dc

        if 0&lt;=nr&lt;n and 0&lt;=nc&lt;n and grid[nr][nc]==1:
          newidx = nr*n+nc
          dsu.union(idx, newidx)
</code></pre>
<p>Since we merged all islands into groups, we just need to check neighbours of all 0s and which group they belong to by checking the ultimate parent of each neighbour by <code>dsu.find(neighbourIndex)</code> and <code>neighbourindex = nr*n+nc</code></p>
<pre><code>mxarea = 0
haszero = False
for i in range(n):
    for j in range(n):
        if grid[i][j]==0:
            haszero=True
            roots = set()
            for dr, dc in direc:
                nr = i+dr
                nc = j+dc

                if 0&lt;=nr&lt;n and 0&lt;=nc&lt;n and grid[nr][nc]==1:
                    idx = nr*n+nc
                    root = dsu.find(idx)
                    roots.add(root)

            size = 1
            for r in roots:
                size += dsu.size[r]
            
            mxarea = max(mxarea, size)
</code></pre>
<p>Then we just return :</p>
<pre><code>if not haszero:
  return n*n
return mxarea if mxarea&gt;0 else 1
</code></pre>
<ul>
<li><strong>Efficiency:</strong> With path compression, DSU operations are nearly <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><mn>1</mn><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(1)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord">1</span><span class="mclose">)</span></span></span></span></span>.</li>
<li><strong>Real-world variants:</strong> If the problem was “Stream of incoming lands” (lands appearing dynamically), DSU is the <strong>only</strong> efficient solution. BFS would be too slow to re-run every time.</li>
</ul>
<p>When to use what ?</p>
<ul>
<li><strong>BFS/DFS (The Coloring Method):</strong> Generally preferred for this specific problem because it’s purely <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><msup><mi>N</mi><mn>2</mn></msup><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(N^2)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.06411em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord"><span class="mord mathnormal" style="margin-right: 0.10903em;">N</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.814108em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span></span></span></span></span><span class="mclose">)</span></span></span></span></span> and intuitive. It shows you can manipulate grids.</li>
<li><strong>DSU:</strong> Use this if you are very comfortable with it or if the interviewer asks “What if the land is added dynamically?”.</li>
</ul>
<h3 id="an-edge-reversal-problem-solved-with-a-custom-graph--1466.-reorder-routes-to-make-all-paths-lead-to-the-city-zero">An edge reversal problem solved with a custom graph : [1466. Reorder Routes to Make All Paths Lead to the City Zero]</h3>
<blockquote>
<p>Time complexity: <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><mi>N</mi><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(N)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord mathnormal" style="margin-right: 0.10903em;">N</span><span class="mclose">)</span></span></span></span></span></p>
</blockquote>
<p><img src="https://assets.leetcode.com/uploads/2020/05/13/sample_1_1819.png" alt=""><br>
We have to start from 0, and make sure all other nodes are able to reach 0, so we gotta do minimum edge reversals to achieve that.</p>
<p>What we can do is, we gotta modify the graph a bit. We will build the graph such that it remembers the original direction.<br>
Mark original edges <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>u</mi><mo>→</mo><mrow></mrow><mi>v</mi></mrow><annotation encoding="application/x-tex">u \rightarrow{}v</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.43056em; vertical-align: 0em;"></span><span class="mord mathnormal">u</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">→</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.43056em; vertical-align: 0em;"></span><span class="mord"></span><span class="mord mathnormal" style="margin-right: 0.03588em;">v</span></span></span></span></span> with weight <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>w</mi><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">w=1</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.43056em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.02691em;">w</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">1</span></span></span></span></span> and newly added reverse edge <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>v</mi><mo>→</mo><mrow></mrow><mi>u</mi></mrow><annotation encoding="application/x-tex">v \rightarrow{}u</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.43056em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.03588em;">v</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">→</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.43056em; vertical-align: 0em;"></span><span class="mord"></span><span class="mord mathnormal">u</span></span></span></span></span> to make it undirected with weight <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>w</mi><mo>=</mo><mn>0</mn></mrow><annotation encoding="application/x-tex">w=0</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.43056em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.02691em;">w</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">0</span></span></span></span></span></p>
<p>Now do a normal BFS like :</p>
<ol>
<li>Visit each neighbour <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>v</mi></mrow><annotation encoding="application/x-tex">v</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.43056em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.03588em;">v</span></span></span></span></span></li>
<li>Check if we visit via edge weight <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>w</mi><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">w=1</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.43056em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.02691em;">w</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">1</span></span></span></span></span>, if yes then count <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>c</mi><mo>+</mo><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">c+=1</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.66666em; vertical-align: -0.08333em;"></span><span class="mord mathnormal">c</span><span class="mord">+</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">1</span></span></span></span></span> as we have a corresponding <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>0</mn></mrow><annotation encoding="application/x-tex">0</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">0</span></span></span></span></span> edge with it</li>
<li>If we visit it via the reverse edge, it means the original edge was already in right direction, skip it.</li>
<li>Repeat until all nodes are visited.</li>
</ol>
<p>Make the graph:</p>
<pre><code>graph = defaultdict(list)
for u, v in connections:
    graph[u].append((v, 1))
    graph[v].append((u,0))
</code></pre>
<p>Now BFS acc to our algo:</p>
<pre><code>count = 0
start = 0

q = deque()
q.append(start)
vis = set()

while q:
    node = q.popleft()
    if node in vis:
        continue
    vis.add(node)

    for v,d in graph[node]:
        if d==1 and v not in vis:
            count+=1

        q.append(v)
</code></pre>
<h3 id="dsu-problem-on-connectivity-and-removal-of-edges-1579.-remove-max-number-of-edges-to-keep-graph-fully-traversable">DSU problem on connectivity and removal of edges [1579. Remove Max Number of Edges to Keep Graph Fully Traversable]</h3>
<blockquote>
<p>Time complexity : <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><mi>E</mi><mi>l</mi><mi>o</mi><mi>g</mi><mi>E</mi><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(ElogE)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord mathnormal" style="margin-right: 0.01968em;">El</span><span class="mord mathnormal">o</span><span class="mord mathnormal" style="margin-right: 0.03588em;">g</span><span class="mord mathnormal" style="margin-right: 0.05764em;">E</span><span class="mclose">)</span></span></span></span></span></p>
</blockquote>
<p><img src="https://assets.leetcode.com/uploads/2020/08/19/ex1.png" alt=""></p>
<p><strong>Input:</strong> n = 4, edges = [[3,1,2],[3,2,3],[1,1,3],[1,2,4],[1,1,2],[2,3,4]]<br>
<strong>Output:</strong> 2<br>
<strong>Explanation:</strong> If we remove the 2 edges [1,1,2] and [1,1,3]. The graph will still be fully traversable by Alice and Bob. Removing any additional edge will not make it so. So the maximum number of edges we can remove is 2.</p>
<p>Okay so we just need to make 2 DSUs to track connectivity by alice and bob seperately. Process all the type 3 edges first and <code>union()</code> it to both alice and bob and keep picking and adding respective edges to alice and bob. If any union fails, we need to exclude that edge since it is duplicate/extra.</p>
<p>For connectivity, if the <code>component size == num of nodes</code> it is a connected component and all nodes are reachable by each other.</p>
<p>ALGO:</p>
<ol>
<li>Sort edges in descending order by <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>t</mi><mi>y</mi><mi>p</mi><mi>e</mi><mo>=</mo><mn>3</mn></mrow><annotation encoding="application/x-tex">type=3</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.80952em; vertical-align: -0.19444em;"></span><span class="mord mathnormal">t</span><span class="mord mathnormal" style="margin-right: 0.03588em;">y</span><span class="mord mathnormal">p</span><span class="mord mathnormal">e</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">3</span></span></span></span></span></li>
<li>Traverse all edges and take union of type 1 edges with alice and type 2 edges with bob and type 3 with both.</li>
<li>If any of the union fails, then count that edge, <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>c</mi><mo>+</mo><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">c+=1</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.66666em; vertical-align: -0.08333em;"></span><span class="mord mathnormal">c</span><span class="mord">+</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">1</span></span></span></span></span></li>
<li>Find parent of alice and bob DSUs using <code>alice.find(node in alice)</code> and same for bob.</li>
<li>Check if all nodes are reachable via both alice and bob by:<br>
<code>if alice.size(root)==bob.size(root)==numnodes</code></li>
</ol>
<p>So start with making seperate DSUs</p>
<pre><code>alice = DSU(n)
bob = DSU(n)
</code></pre>
<p>Now sort the edges by type</p>
<pre><code>edges.sort(key = lambda x: x[0], reverse=True)
</code></pre>
<p>Create count, variables to store a node from alice and bob to later find their parents</p>
<pre><code>count = 0
al = 0
b = 0
</code></pre>
<p>Traverse in all edges take union of respective edges to their respective DSUs, if any union fails then <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>c</mi><mi>o</mi><mi>u</mi><mi>n</mi><mi>t</mi><mo>+</mo><mo>=</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">count+=1</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.69841em; vertical-align: -0.08333em;"></span><span class="mord mathnormal">co</span><span class="mord mathnormal">u</span><span class="mord mathnormal">n</span><span class="mord mathnormal">t</span><span class="mord">+</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">1</span></span></span></span></span></p>
<pre><code>for t, u, v in edges:
  if t==1:
    al = u-1
    if not alice.union(u-1, v-1):
        count+=1
  elif t==2:
    b = u-1
    if not bob.union(u-1, v-1):
        count+=1
  else:
    if not (bob.union(u-1, v-1) and alice.union(u-1, v-1)):
        count+=1
</code></pre>
<p>Take <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>u</mi><mo>−</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">u-1</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.66666em; vertical-align: -0.08333em;"></span><span class="mord mathnormal">u</span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">−</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">1</span></span></span></span></span> and <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>v</mi><mo>−</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">v-1</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.66666em; vertical-align: -0.08333em;"></span><span class="mord mathnormal" style="margin-right: 0.03588em;">v</span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">−</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">1</span></span></span></span></span> to convert to <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>0</mn></mrow><annotation encoding="application/x-tex">0</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">0</span></span></span></span></span>-based indexing.</p>
<p>Now find parents of alice component and bob component:</p>
<pre><code>rootal = alice.find(al)
rootb = bob.find(b)
</code></pre>
<p>where al is just some node in alice, and b is just some node in bob<br>
Now compare sizes. A fully connected component has <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>s</mi><mi>i</mi><mi>z</mi><mi>e</mi><mo>=</mo><mo>=</mo><mi>n</mi></mrow><annotation encoding="application/x-tex">size==n</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.65952em; vertical-align: 0em;"></span><span class="mord mathnormal">s</span><span class="mord mathnormal">i</span><span class="mord mathnormal">ze</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">==</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.43056em; vertical-align: 0em;"></span><span class="mord mathnormal">n</span></span></span></span></span></p>
<pre><code>if alice.size[rootal]==bob.size[rootb]==n:
    return count

return -1
</code></pre>
<h2 id="eulerian-path-problems">Eulerian path problems</h2>
<p><strong>Pattern</strong> - <strong>Eulerian path (hierholzer’s algo) (Post-Order DFS)</strong></p>
<ul>
<li>Definition: A path in a graph that visits every edge exactly once.</li>
<li>The Algorithm: <strong>Hierholzer’s Algorithm</strong> (or simply “Post-Order DFS”).</li>
</ul>
<p><strong>How to spot it:</strong></p>
<ul>
<li>“Use all tickets.”</li>
<li>“Valid arrangement of pairs.”</li>
<li>“Draw a shape without lifting your pen.”</li>
<li>“Reconstruct a sequence from fragments.”</li>
</ul>
<h3 id="the-mental-block-this-pattern-is-about-visiting-edges.">The Mental Block: This pattern is about visiting Edges.</h3>
<ul>
<li>Standard DFS: Mark visited[node] = True.</li>
<li>Eulerian DFS: Remove edge from graph (or mark visited[edge] = True).</li>
</ul>
<h3 id="hierholzers-algorithm">Hierholzer’s Algorithm</h3>
<p><strong>If a graph has an Eulerian path (i.e., it’s possible to visit every edge exactly once), Hierholzer’s algorithm is guaranteed to find it efficiently in <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><mi>E</mi><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(E)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord mathnormal" style="margin-right: 0.05764em;">E</span><span class="mclose">)</span></span></span></span></span> time.</strong></p>
<p>Imagine you are exploring a maze, but you have a rule: “Burn the bridges behind you.” Every time you cross an edge, you destroy it so you can never cross it again.</p>
<p><strong>The problem is: What if you get stuck?</strong></p>
<ul>
<li>If you take a wrong turn, you might end up at a dead-end node while there are still unvisited edges back at the start.</li>
</ul>
<p><strong>Hierholzer’s Solution:</strong> “It’s okay to get stuck. When you get stuck, it means you have finished the end of the journey. Write that node down, then step back (backtrack) to see if you missed any turns earlier.”</p>
<p><strong>The Setup (Prerequisites)</strong><br>
Before running the algorithm, the graph must actually have an Eulerian Path.</p>
<ul>
<li><strong>Start Node</strong>: The node where <code>OutDegree - InDegree = 1</code> (Or any node if it’s a closed circuit).</li>
<li><strong>End Node</strong>: The node where <code>InDegree - OutDegree = 1</code></li>
<li><strong>Other all nodes</strong>:  <code>InDegree == OutDegree</code></li>
</ul>
<h3 id="algorithm">Algorithm:</h3>
<p><strong>Step 1:</strong> Start DFS from the valid Start Node.<br>
<strong>Step 2:</strong> From the current node U, pick any neighbor V.<br>
<strong>Step 3 (Burn the Bridge):</strong>  Delete the edge U -&gt; V immediately so you don’t use it again.<br>
<strong>Step 4:</strong> Move to V and repeat Step 2 recursively.<br>
<strong>Step 5 (The Magic):</strong> If a node has no outgoing edges left (you are stuck):</p>
<ul>
<li>Add this node to your Result List.</li>
<li>Return (Backtrack) to the previous node.</li>
</ul>
<p><strong>Step 6:</strong> Finally, Reverse the Result List to get the actual path.</p>
<p><strong>Code implementation:</strong></p>
<p>Build the graph first and calculate indegrees and outdegrees incase we wanna find out the start node if it is not given to us</p>
<pre><code>def findEulerianPath(edges):
    graph = defaultdict(list)
    out_degree = defaultdict(int)
    in_degree = defaultdict(int)
    
    for u, v in edges:
        graph[u].append(v)
        out_degree[u] += 1
        in_degree[v] += 1
</code></pre>
<p>Finding the start node in the below snippet by checking if any node has <code>outdegree-indegree=1</code></p>
<pre><code>    start_node = edges[0][0] # Default to first node
    for node in out_degree:
        # If out &gt; in by 1, it MUST be the start
        if out_degree[node] - in_degree[node] == 1:
            start_node = node
            break
</code></pre>
<p>Then we have to build and store the eularian path:</p>
<pre><code>    path = []

    def dfs(u):
        # While unused edges exist...
        while graph[u]:
            # Pop removes the edge (Burns the bridge)
            v = graph[u].pop()
            dfs(v)
        
        # Only add to path when STUCK (Post-Order)
        path.append(u)

    # 3. Execute
    dfs(start_node)
</code></pre>
<p>At the end just reverse the path we built, and that would be our final answer</p>
<pre><code>    # 4. Reverse to get correct order
    return path[::-1]
</code></pre>
<h3 id="leetcode-322-reconstruct-itineary-solution-implemented-using-heirholzers-algo">Leetcode 322: Reconstruct Itineary Solution implemented using heirholzer’s algo</h3>
<blockquote>
<p>Time complexity - <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><msup><mi>E</mi><mn>2</mn></msup><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(E^2)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.06411em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord"><span class="mord mathnormal" style="margin-right: 0.05764em;">E</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.814108em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span></span></span></span></span><span class="mclose">)</span></span></span></span></span></p>
</blockquote>
<p><img src="https://assets.leetcode.com/uploads/2021/03/14/itinerary2-graph.jpg" alt=""><br>
<strong>Input:</strong> tickets = [[“JFK”,“SFO”],[“JFK”,“ATL”],[“SFO”,“ATL”],[“ATL”,“JFK”],[“ATL”,“SFO”]]<br>
<strong>Output:</strong> [“JFK”,“ATL”,“JFK”,“SFO”,“ATL”,“SFO”]<br>
<strong>Explanation:</strong> Another possible reconstruction is [“JFK”,“SFO”,“ATL”,“JFK”,“ATL”,“SFO”] but it is larger in lexical order.</p>
<pre><code>class Solution:
    def findItinerary(self, tickets: List[List[str]]) -&gt; List[str]:
        res = []
        tickets.sort()
        graph = defaultdict(list)
        for u,v in tickets:
            graph[u].append(v)
        def dfs(node):
            while graph[node]:
                neigh = graph[node].pop(0)
                dfs(neigh)
            res.append(node)
        dfs("JFK")
        return res[::-1]
</code></pre>
<h3 id="similar-eulerian-path-problems-ordering-edges">Similar eulerian path problems (Ordering Edges)</h3>
<ul>
<li>Concept: The exact pattern you just solved. Linking edges start-to-end.</li>
</ul>
<p>Practice:</p>
<p><a href="https://leetcode.com/problems/valid-arrangement-of-pairs/">2097. Valid Arrangement of Pairs</a> (Hard)</p>
<ul>
<li>Note: This is almost identical to “Reconstruct Itinerary” but with numbers. It forces you to handle the “Start Node” logic explicitly <code>(Start is where out_degree - in_degree == 1).</code></li>
</ul>
<p><a href="https://leetcode.com/problems/cracking-the-safe/">753. Cracking the Safe</a> (Hard)</p>
<ul>
<li>Note: This is a hidden Eulerian Path problem. You construct a De Bruijn sequence by finding a path that traverses every possible combination (edge).</li>
</ul>
<h3 id="valid-arrangements-of-pairs-solved-solution-">Valid arrangements of pairs solved solution :</h3>
<p>I just simply implemented heirholzer’s algo for eularian path after identifying the start node and i got the answer:</p>
<pre><code>class Solution:
    def validArrangement(self, pairs: List[List[int]]) -&gt; List[List[int]]:

        graph = defaultdict(list)
        indeg = defaultdict(int)
        outdeg = defaultdict(int)

        for u, v in pairs:
            graph[u].append(v)
            indeg[v] += 1
            outdeg[u] +=1
        
        start = pairs[0][0]

        for node in outdeg:
            if outdeg[node]-indeg[node]==1:
                start = node
                break
        
        path = []

        def dfs(node):
            while graph[node]:
                v = graph[node].pop()
                dfs(v)
            
            path.append(node)        
        dfs(start)

        p = path[::-1]
        res = []        
        for i in range(len(p)-1):
            res.append([p[i], p[i+1]])        
        return res        
</code></pre>
<h2 id="de-bruijn-sequence">De-Bruijn Sequence</h2>
<p><strong>Definition:</strong><br>
A De Bruijn sequence <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>B</mi><mo stretchy="false">(</mo><mi>k</mi><mo separator="true">,</mo><mi>n</mi><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">B(k, n)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.05017em;">B</span><span class="mopen">(</span><span class="mord mathnormal" style="margin-right: 0.03148em;">k</span><span class="mpunct">,</span><span class="mspace" style="margin-right: 0.166667em;"></span><span class="mord mathnormal">n</span><span class="mclose">)</span></span></span></span></span> is the shortest possible string that contains every possible combination of length <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi></mrow><annotation encoding="application/x-tex">n</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.43056em; vertical-align: 0em;"></span><span class="mord mathnormal">n</span></span></span></span></span> using <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>k</mi></mrow><annotation encoding="application/x-tex">k</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.69444em; vertical-align: 0em;"></span><span class="mord mathnormal" style="margin-right: 0.03148em;">k</span></span></span></span></span> different characters.</p>
<p>like the example: 01100 contains : 01, 11, 10, 00 all possible combinations of digits of length <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi></mrow><annotation encoding="application/x-tex">n</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.43056em; vertical-align: 0em;"></span><span class="mord mathnormal">n</span></span></span></span></span></p>
<p><strong>The Core Secret: Overlap</strong></p>
<p>The magic comes from “Domino Matching.” To get from the code <code>1234</code> to <code>2345</code>, you don’t need to clear the screen. You just type <code>5</code>.</p>
<ul>
<li>Old Window: <code>1 2 3 4</code></li>
<li>Type <code>5</code>: <code>_ 2 3 4 5</code></li>
<li>New Window: <code>2 3 4 5</code></li>
</ul>
<p>We recycled 3 digits (<code>234</code>). So we can match it in 1 move !</p>
<p><strong>Length of De Bruijn Sequence:</strong> <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>k</mi><mi>n</mi></msup><mo>+</mo><mo stretchy="false">(</mo><mi>n</mi><mo>−</mo><mn>1</mn><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">k^n + (n - 1)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.77777em; vertical-align: -0.08333em;"></span><span class="mord"><span class="mord mathnormal" style="margin-right: 0.03148em;">k</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.664392em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mathnormal mtight">n</span></span></span></span></span></span></span></span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">+</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mopen">(</span><span class="mord mathnormal">n</span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">−</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord">1</span><span class="mclose">)</span></span></span></span></span></p>
<ul>
<li>The first combination takes <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi></mrow><annotation encoding="application/x-tex">n</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.43056em; vertical-align: 0em;"></span><span class="mord mathnormal">n</span></span></span></span></span> characters.</li>
<li>Every subsequent combination adds exactly <strong>1</strong> character.</li>
<li>Example (<span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>2</mn><mo separator="true">,</mo><mi>k</mi><mo>=</mo><mn>2</mn></mrow><annotation encoding="application/x-tex">n=2, k=2</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.43056em; vertical-align: 0em;"></span><span class="mord mathnormal">n</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.88888em; vertical-align: -0.19444em;"></span><span class="mord">2</span><span class="mpunct">,</span><span class="mspace" style="margin-right: 0.166667em;"></span><span class="mord mathnormal" style="margin-right: 0.03148em;">k</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">2</span></span></span></span></span>): <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mn>2</mn><mn>2</mn></msup><mo>+</mo><mo stretchy="false">(</mo><mn>2</mn><mo>−</mo><mn>1</mn><mo stretchy="false">)</mo><mo>=</mo><mn>4</mn><mo>+</mo><mn>1</mn><mo>=</mo><mn>5</mn></mrow><annotation encoding="application/x-tex">2^2 + (2-1) = 4 + 1 = 5</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.897438em; vertical-align: -0.08333em;"></span><span class="mord"><span class="mord">2</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.814108em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span></span></span></span></span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">+</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mopen">(</span><span class="mord">2</span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">−</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord">1</span><span class="mclose">)</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.72777em; vertical-align: -0.08333em;"></span><span class="mord">4</span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">+</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">1</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">5</span></span></span></span></span> characters. (<code>00110</code>)</li>
</ul>
<h3 id="how-to-build-it-the-graph-method">How to Build It (The Graph Method)</h3>
<p>This is the standard way to generate these sequences. We use a <strong>Directed Graph</strong>.</p>
<h4 id="the-rules">The Rules</h4>
<ol>
<li>
<p><strong>Nodes (States):</strong> Every possible string of length <strong><span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>−</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">n-1</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.66666em; vertical-align: -0.08333em;"></span><span class="mord mathnormal">n</span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">−</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">1</span></span></span></span></span></strong>.</p>
<ul>
<li>Why <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>−</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">n-1</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.66666em; vertical-align: -0.08333em;"></span><span class="mord mathnormal">n</span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">−</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">1</span></span></span></span></span>? Because a node represents the “prefix” waiting for one final character to become a full code.</li>
</ul>
</li>
<li>
<p><strong>Edges (Transitions):</strong> Adding a new character (<span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>0</mn><mo separator="true">,</mo><mn>1</mn><mo separator="true">,</mo><mi mathvariant="normal">.</mi><mi mathvariant="normal">.</mi><mi mathvariant="normal">.</mi><mi>k</mi><mo>−</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">0, 1, ... k-1</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.88888em; vertical-align: -0.19444em;"></span><span class="mord">0</span><span class="mpunct">,</span><span class="mspace" style="margin-right: 0.166667em;"></span><span class="mord">1</span><span class="mpunct">,</span><span class="mspace" style="margin-right: 0.166667em;"></span><span class="mord">...</span><span class="mord mathnormal" style="margin-right: 0.03148em;">k</span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">−</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">1</span></span></span></span></span>).</p>
<ul>
<li>An edge represents <strong>typing one digit</strong>.</li>
<li>When you traverse an edge, you form a full code of length <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi></mrow><annotation encoding="application/x-tex">n</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.43056em; vertical-align: 0em;"></span><span class="mord mathnormal">n</span></span></span></span></span>.</li>
</ul>
</li>
<li>
<p><strong>The Goal:</strong> Find an <strong>Eulerian Path</strong> (visit every edge exactly once).</p>
</li>
</ol>
<h3 id="example-binary-length-3-n3-k2">Example Binary, Length 3 (<span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>=</mo><mn>3</mn><mo separator="true">,</mo><mi>k</mi><mo>=</mo><mn>2</mn></mrow><annotation encoding="application/x-tex">n=3, k=2</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.43056em; vertical-align: 0em;"></span><span class="mord mathnormal">n</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.88888em; vertical-align: -0.19444em;"></span><span class="mord">3</span><span class="mpunct">,</span><span class="mspace" style="margin-right: 0.166667em;"></span><span class="mord mathnormal" style="margin-right: 0.03148em;">k</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">2</span></span></span></span></span>)</h3>
<p>We want all combinations like <code>000, 001... 111</code>.</p>
<p><strong>Setup:</strong></p>
<ul>
<li><strong>Nodes (<span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>n</mi><mo>−</mo><mn>1</mn><mo>=</mo><mn>2</mn></mrow><annotation encoding="application/x-tex">n-1 = 2</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.66666em; vertical-align: -0.08333em;"></span><span class="mord mathnormal">n</span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">−</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">1</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">2</span></span></span></span></span> digits):</strong> <code>00</code>, <code>01</code>, <code>10</code>, <code>11</code>.</li>
<li><strong>Edges:</strong> Type <code>0</code> or <code>1</code>.</li>
</ul>
<p><strong>Logic for Edges:</strong></p>
<p>From Node 01:</p>
<ul>
<li>
<p>Type <code>0</code> <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>→</mo></mrow><annotation encoding="application/x-tex">\rightarrow</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.36687em; vertical-align: 0em;"></span><span class="mrel">→</span></span></span></span></span> Code <strong><code>010</code></strong>. Next Node: <strong><code>10</code></strong> (last 2 digits).</p>
</li>
<li>
<p>Type <code>1</code> <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>→</mo></mrow><annotation encoding="application/x-tex">\rightarrow</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.36687em; vertical-align: 0em;"></span><span class="mrel">→</span></span></span></span></span> Code <strong><code>011</code></strong>. Next Node: <strong><code>11</code></strong> (last 2 digits).</p>
</li>
</ul>
<p><strong>The Path (Hierholzer’s traversal):</strong></p>
<p>Let’s just trace a valid Eulerian Circuit:</p>
<p><span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>00</mn></mrow><annotation encoding="application/x-tex">00</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">00</span></span></span></span></span> <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><mo stretchy="true" minsize="3.0em">undefined</mo><mpadded width="+0.6em" lspace="0.3em"><mn>0</mn></mpadded></mover></mrow><annotation encoding="application/x-tex">\xrightarrow{0}</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.08411em; vertical-align: -0.011em;"></span><span class="mrel x-arrow"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 1.07311em;"><span class="" style="top: -3.322em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight x-arrow-pad"><span class="mord mtight"><span class="mord mtight">0</span></span></span></span><span class="svg-align" style="top: -2.689em;"><span class="pstrut" style="height: 2.7em;"></span><span class="hide-tail" style="height: 0.522em; min-width: 1.469em;"><svg width="400em" height="0.522em" viewBox="0 0 400000 522" preserveAspectRatio="xMaxYMin slice"><path d="M0 241v40h399891c-47.3 35.3-84 78-110 128
-16.7 32-27.7 63.7-33 95 0 1.3-.2 2.7-.5 4-.3 1.3-.5 2.3-.5 3 0 7.3 6.7 11 20
 11 8 0 13.2-.8 15.5-2.5 2.3-1.7 4.2-5.5 5.5-11.5 2-13.3 5.7-27 11-41 14.7-44.7
 39-84.5 73-119.5s73.7-60.2 119-75.5c6-2 9-5.7 9-11s-3-9-9-11c-45.3-15.3-85
-40.5-119-75.5s-58.3-74.8-73-119.5c-4.7-14-8.3-27.3-11-40-1.3-6.7-3.2-10.8-5.5
-12.5-2.3-1.7-7.5-2.5-15.5-2.5-14 0-21 3.7-21 11 0 2 2 10.3 6 25 20.7 83.3 67
 151.7 139 205zm0 0v40h399900v-40z"></path></svg></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 0.011em;"><span class=""></span></span></span></span></span></span></span></span></span> <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>00</mn></mrow><annotation encoding="application/x-tex">00</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">00</span></span></span></span></span> <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><mo stretchy="true" minsize="3.0em">undefined</mo><mpadded width="+0.6em" lspace="0.3em"><mn>1</mn></mpadded></mover></mrow><annotation encoding="application/x-tex">\xrightarrow{1}</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.08411em; vertical-align: -0.011em;"></span><span class="mrel x-arrow"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 1.07311em;"><span class="" style="top: -3.322em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight x-arrow-pad"><span class="mord mtight"><span class="mord mtight">1</span></span></span></span><span class="svg-align" style="top: -2.689em;"><span class="pstrut" style="height: 2.7em;"></span><span class="hide-tail" style="height: 0.522em; min-width: 1.469em;"><svg width="400em" height="0.522em" viewBox="0 0 400000 522" preserveAspectRatio="xMaxYMin slice"><path d="M0 241v40h399891c-47.3 35.3-84 78-110 128
-16.7 32-27.7 63.7-33 95 0 1.3-.2 2.7-.5 4-.3 1.3-.5 2.3-.5 3 0 7.3 6.7 11 20
 11 8 0 13.2-.8 15.5-2.5 2.3-1.7 4.2-5.5 5.5-11.5 2-13.3 5.7-27 11-41 14.7-44.7
 39-84.5 73-119.5s73.7-60.2 119-75.5c6-2 9-5.7 9-11s-3-9-9-11c-45.3-15.3-85
-40.5-119-75.5s-58.3-74.8-73-119.5c-4.7-14-8.3-27.3-11-40-1.3-6.7-3.2-10.8-5.5
-12.5-2.3-1.7-7.5-2.5-15.5-2.5-14 0-21 3.7-21 11 0 2 2 10.3 6 25 20.7 83.3 67
 151.7 139 205zm0 0v40h399900v-40z"></path></svg></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 0.011em;"><span class=""></span></span></span></span></span></span></span></span></span> <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>01</mn></mrow><annotation encoding="application/x-tex">01</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">01</span></span></span></span></span> <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><mo stretchy="true" minsize="3.0em">undefined</mo><mpadded width="+0.6em" lspace="0.3em"><mn>1</mn></mpadded></mover></mrow><annotation encoding="application/x-tex">\xrightarrow{1}</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.08411em; vertical-align: -0.011em;"></span><span class="mrel x-arrow"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 1.07311em;"><span class="" style="top: -3.322em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight x-arrow-pad"><span class="mord mtight"><span class="mord mtight">1</span></span></span></span><span class="svg-align" style="top: -2.689em;"><span class="pstrut" style="height: 2.7em;"></span><span class="hide-tail" style="height: 0.522em; min-width: 1.469em;"><svg width="400em" height="0.522em" viewBox="0 0 400000 522" preserveAspectRatio="xMaxYMin slice"><path d="M0 241v40h399891c-47.3 35.3-84 78-110 128
-16.7 32-27.7 63.7-33 95 0 1.3-.2 2.7-.5 4-.3 1.3-.5 2.3-.5 3 0 7.3 6.7 11 20
 11 8 0 13.2-.8 15.5-2.5 2.3-1.7 4.2-5.5 5.5-11.5 2-13.3 5.7-27 11-41 14.7-44.7
 39-84.5 73-119.5s73.7-60.2 119-75.5c6-2 9-5.7 9-11s-3-9-9-11c-45.3-15.3-85
-40.5-119-75.5s-58.3-74.8-73-119.5c-4.7-14-8.3-27.3-11-40-1.3-6.7-3.2-10.8-5.5
-12.5-2.3-1.7-7.5-2.5-15.5-2.5-14 0-21 3.7-21 11 0 2 2 10.3 6 25 20.7 83.3 67
 151.7 139 205zm0 0v40h399900v-40z"></path></svg></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 0.011em;"><span class=""></span></span></span></span></span></span></span></span></span> <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>11</mn></mrow><annotation encoding="application/x-tex">11</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">11</span></span></span></span></span> <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><mo stretchy="true" minsize="3.0em">undefined</mo><mpadded width="+0.6em" lspace="0.3em"><mn>1</mn></mpadded></mover></mrow><annotation encoding="application/x-tex">\xrightarrow{1}</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.08411em; vertical-align: -0.011em;"></span><span class="mrel x-arrow"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 1.07311em;"><span class="" style="top: -3.322em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight x-arrow-pad"><span class="mord mtight"><span class="mord mtight">1</span></span></span></span><span class="svg-align" style="top: -2.689em;"><span class="pstrut" style="height: 2.7em;"></span><span class="hide-tail" style="height: 0.522em; min-width: 1.469em;"><svg width="400em" height="0.522em" viewBox="0 0 400000 522" preserveAspectRatio="xMaxYMin slice"><path d="M0 241v40h399891c-47.3 35.3-84 78-110 128
-16.7 32-27.7 63.7-33 95 0 1.3-.2 2.7-.5 4-.3 1.3-.5 2.3-.5 3 0 7.3 6.7 11 20
 11 8 0 13.2-.8 15.5-2.5 2.3-1.7 4.2-5.5 5.5-11.5 2-13.3 5.7-27 11-41 14.7-44.7
 39-84.5 73-119.5s73.7-60.2 119-75.5c6-2 9-5.7 9-11s-3-9-9-11c-45.3-15.3-85
-40.5-119-75.5s-58.3-74.8-73-119.5c-4.7-14-8.3-27.3-11-40-1.3-6.7-3.2-10.8-5.5
-12.5-2.3-1.7-7.5-2.5-15.5-2.5-14 0-21 3.7-21 11 0 2 2 10.3 6 25 20.7 83.3 67
 151.7 139 205zm0 0v40h399900v-40z"></path></svg></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 0.011em;"><span class=""></span></span></span></span></span></span></span></span></span> <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>11</mn></mrow><annotation encoding="application/x-tex">11</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">11</span></span></span></span></span> <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><mo stretchy="true" minsize="3.0em">undefined</mo><mpadded width="+0.6em" lspace="0.3em"><mn>0</mn></mpadded></mover></mrow><annotation encoding="application/x-tex">\xrightarrow{0}</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.08411em; vertical-align: -0.011em;"></span><span class="mrel x-arrow"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 1.07311em;"><span class="" style="top: -3.322em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight x-arrow-pad"><span class="mord mtight"><span class="mord mtight">0</span></span></span></span><span class="svg-align" style="top: -2.689em;"><span class="pstrut" style="height: 2.7em;"></span><span class="hide-tail" style="height: 0.522em; min-width: 1.469em;"><svg width="400em" height="0.522em" viewBox="0 0 400000 522" preserveAspectRatio="xMaxYMin slice"><path d="M0 241v40h399891c-47.3 35.3-84 78-110 128
-16.7 32-27.7 63.7-33 95 0 1.3-.2 2.7-.5 4-.3 1.3-.5 2.3-.5 3 0 7.3 6.7 11 20
 11 8 0 13.2-.8 15.5-2.5 2.3-1.7 4.2-5.5 5.5-11.5 2-13.3 5.7-27 11-41 14.7-44.7
 39-84.5 73-119.5s73.7-60.2 119-75.5c6-2 9-5.7 9-11s-3-9-9-11c-45.3-15.3-85
-40.5-119-75.5s-58.3-74.8-73-119.5c-4.7-14-8.3-27.3-11-40-1.3-6.7-3.2-10.8-5.5
-12.5-2.3-1.7-7.5-2.5-15.5-2.5-14 0-21 3.7-21 11 0 2 2 10.3 6 25 20.7 83.3 67
 151.7 139 205zm0 0v40h399900v-40z"></path></svg></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 0.011em;"><span class=""></span></span></span></span></span></span></span></span></span> <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>10</mn></mrow><annotation encoding="application/x-tex">10</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">10</span></span></span></span></span> <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><mo stretchy="true" minsize="3.0em">undefined</mo><mpadded width="+0.6em" lspace="0.3em"><mn>1</mn></mpadded></mover></mrow><annotation encoding="application/x-tex">\xrightarrow{1}</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.08411em; vertical-align: -0.011em;"></span><span class="mrel x-arrow"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 1.07311em;"><span class="" style="top: -3.322em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight x-arrow-pad"><span class="mord mtight"><span class="mord mtight">1</span></span></span></span><span class="svg-align" style="top: -2.689em;"><span class="pstrut" style="height: 2.7em;"></span><span class="hide-tail" style="height: 0.522em; min-width: 1.469em;"><svg width="400em" height="0.522em" viewBox="0 0 400000 522" preserveAspectRatio="xMaxYMin slice"><path d="M0 241v40h399891c-47.3 35.3-84 78-110 128
-16.7 32-27.7 63.7-33 95 0 1.3-.2 2.7-.5 4-.3 1.3-.5 2.3-.5 3 0 7.3 6.7 11 20
 11 8 0 13.2-.8 15.5-2.5 2.3-1.7 4.2-5.5 5.5-11.5 2-13.3 5.7-27 11-41 14.7-44.7
 39-84.5 73-119.5s73.7-60.2 119-75.5c6-2 9-5.7 9-11s-3-9-9-11c-45.3-15.3-85
-40.5-119-75.5s-58.3-74.8-73-119.5c-4.7-14-8.3-27.3-11-40-1.3-6.7-3.2-10.8-5.5
-12.5-2.3-1.7-7.5-2.5-15.5-2.5-14 0-21 3.7-21 11 0 2 2 10.3 6 25 20.7 83.3 67
 151.7 139 205zm0 0v40h399900v-40z"></path></svg></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 0.011em;"><span class=""></span></span></span></span></span></span></span></span></span> <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>01</mn></mrow><annotation encoding="application/x-tex">01</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">01</span></span></span></span></span> <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><mo stretchy="true" minsize="3.0em">undefined</mo><mpadded width="+0.6em" lspace="0.3em"><mn>0</mn></mpadded></mover></mrow><annotation encoding="application/x-tex">\xrightarrow{0}</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.08411em; vertical-align: -0.011em;"></span><span class="mrel x-arrow"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 1.07311em;"><span class="" style="top: -3.322em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight x-arrow-pad"><span class="mord mtight"><span class="mord mtight">0</span></span></span></span><span class="svg-align" style="top: -2.689em;"><span class="pstrut" style="height: 2.7em;"></span><span class="hide-tail" style="height: 0.522em; min-width: 1.469em;"><svg width="400em" height="0.522em" viewBox="0 0 400000 522" preserveAspectRatio="xMaxYMin slice"><path d="M0 241v40h399891c-47.3 35.3-84 78-110 128
-16.7 32-27.7 63.7-33 95 0 1.3-.2 2.7-.5 4-.3 1.3-.5 2.3-.5 3 0 7.3 6.7 11 20
 11 8 0 13.2-.8 15.5-2.5 2.3-1.7 4.2-5.5 5.5-11.5 2-13.3 5.7-27 11-41 14.7-44.7
 39-84.5 73-119.5s73.7-60.2 119-75.5c6-2 9-5.7 9-11s-3-9-9-11c-45.3-15.3-85
-40.5-119-75.5s-58.3-74.8-73-119.5c-4.7-14-8.3-27.3-11-40-1.3-6.7-3.2-10.8-5.5
-12.5-2.3-1.7-7.5-2.5-15.5-2.5-14 0-21 3.7-21 11 0 2 2 10.3 6 25 20.7 83.3 67
 151.7 139 205zm0 0v40h399900v-40z"></path></svg></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 0.011em;"><span class=""></span></span></span></span></span></span></span></span></span> 10 <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mover><mo stretchy="true" minsize="3.0em">undefined</mo><mpadded width="+0.6em" lspace="0.3em"><mn>0</mn></mpadded></mover></mrow><annotation encoding="application/x-tex">\xrightarrow{0}</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.08411em; vertical-align: -0.011em;"></span><span class="mrel x-arrow"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 1.07311em;"><span class="" style="top: -3.322em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight x-arrow-pad"><span class="mord mtight"><span class="mord mtight">0</span></span></span></span><span class="svg-align" style="top: -2.689em;"><span class="pstrut" style="height: 2.7em;"></span><span class="hide-tail" style="height: 0.522em; min-width: 1.469em;"><svg width="400em" height="0.522em" viewBox="0 0 400000 522" preserveAspectRatio="xMaxYMin slice"><path d="M0 241v40h399891c-47.3 35.3-84 78-110 128
-16.7 32-27.7 63.7-33 95 0 1.3-.2 2.7-.5 4-.3 1.3-.5 2.3-.5 3 0 7.3 6.7 11 20
 11 8 0 13.2-.8 15.5-2.5 2.3-1.7 4.2-5.5 5.5-11.5 2-13.3 5.7-27 11-41 14.7-44.7
 39-84.5 73-119.5s73.7-60.2 119-75.5c6-2 9-5.7 9-11s-3-9-9-11c-45.3-15.3-85
-40.5-119-75.5s-58.3-74.8-73-119.5c-4.7-14-8.3-27.3-11-40-1.3-6.7-3.2-10.8-5.5
-12.5-2.3-1.7-7.5-2.5-15.5-2.5-14 0-21 3.7-21 11 0 2 2 10.3 6 25 20.7 83.3 67
 151.7 139 205zm0 0v40h399900v-40z"></path></svg></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 0.011em;"><span class=""></span></span></span></span></span></span></span></span></span> <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mn>00</mn></mrow><annotation encoding="application/x-tex">00</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">00</span></span></span></span></span></p>
<p>Sequence: <code>0001110100</code></p>
<p>Length: <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mn>2</mn><mn>3</mn></msup><mo>+</mo><mo stretchy="false">(</mo><mn>3</mn><mo>−</mo><mn>1</mn><mo stretchy="false">)</mo><mo>=</mo><mn>8</mn><mo>+</mo><mn>2</mn><mo>=</mo><mn>10</mn></mrow><annotation encoding="application/x-tex">2^3 + (3-1) = 8 + 2 = 10</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.897438em; vertical-align: -0.08333em;"></span><span class="mord"><span class="mord">2</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.814108em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">3</span></span></span></span></span></span></span></span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">+</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mopen">(</span><span class="mord">3</span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">−</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord">1</span><span class="mclose">)</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.72777em; vertical-align: -0.08333em;"></span><span class="mord">8</span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">+</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">2</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.64444em; vertical-align: 0em;"></span><span class="mord">10</span></span></span></span></span>.</p>
<h3 id="why-is-this-useful">Why is this useful?</h3>
<ol>
<li>
<p><strong>Robotic Vision:</strong> Robots use these patterns (often colored bars) on floors. By seeing just a tiny slice of the pattern (e.g., “Red-Blue-Red”), the robot knows <strong>exactly</strong> where it is on the map because that specific sequence “Red-Blue-Red” only appears once in the entire loop.</p>
</li>
<li>
<p><strong>DNA Assembly:</strong> Scientists chop up DNA into small overlapping fragments and use De Bruijn graphs to piece the full genome sequence back together.</p>
</li>
<li>
<p><strong>Hackers:</strong> As mentioned, brute-forcing PIN pads efficiently.</p>
</li>
</ol>
<pre><code>class DeBruijnGenerator:
    def crackSafe(self, n: int, k: int) -&gt; str:
        """
        Generates the De Bruijn sequence B(k, n).
        n: Length of the password/substring
        k: Size of the alphabet (e.g., 2 for binary, 10 for digits 0-9)
        """
        if n == 1:
            return "".join(str(i) for i in range(k))

        # 1. Initialize Start Node (String of n-1 zeros)
        # Why 'n-1'? Because the node represents the prefix.
        start_node = "0" * (n - 1)
        
        # 2. Track visited edges (combinations)
        visited = set()
        path = []

        # 3. Hierholzer's Algorithm (Post-Order DFS)
        def dfs(node):
            # Try every digit in the alphabet 
            #(e.g., 0 to k-1)
            for x in range(k):
                x_char = str(x)
                
                # Form the potential edge (The full n-digit code)
                edge = node + x_char
                
                if edge not in visited:
                    visited.add(edge)
                    
                    # Next Node is the suffix of the edge (last n-1 chars)
                    next_node = edge[1:]
                    
                    dfs(next_node)
                    
                    # Append digit on the way back (Post-Order)
                    path.append(x_char)

        # Start the traversal
        dfs(start_node)

        # 4. Construct Final String
        # The path is recorded in reverse.
        # Format: StartNode + Reverse(Path)
        return start_node + "".join(path[::-1])

sol = DeBruijnGenerator()
# Binary, Length 2 -&gt; "00110"
print(f"n=2, k=2: {sol.crackSafe(2, 2)}") 

# Digits 0-9, Length 2 (PIN codes) -&gt; String of length 100 + 1 = 101
print(f"n=2, k=10: {len(sol.crackSafe(2, 10))}")
</code></pre>
<h3 id="complexity-analysis">Complexity Analysis</h3>
<ul>
<li>
<p><strong>Time Complexity:</strong> <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><msup><mi>k</mi><mi>n</mi></msup><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(k^n)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord"><span class="mord mathnormal" style="margin-right: 0.03148em;">k</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.664392em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mathnormal mtight">n</span></span></span></span></span></span></span></span><span class="mclose">)</span></span></span></span></span></p>
<ul>
<li>We visit exactly <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>k</mi><mi>n</mi></msup></mrow><annotation encoding="application/x-tex">k^n</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.69444em; vertical-align: 0em;"></span><span class="mord"><span class="mord mathnormal" style="margin-right: 0.03148em;">k</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.664392em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mathnormal mtight">n</span></span></span></span></span></span></span></span></span></span></span></span> edges. Each visit is constant time <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><mn>1</mn><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(1)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord">1</span><span class="mclose">)</span></span></span></span></span> operations on average (using a Set).</li>
</ul>
</li>
<li>
<p><strong>Space Complexity:</strong> <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><msup><mi>k</mi><mi>n</mi></msup><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(k^n)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord"><span class="mord mathnormal" style="margin-right: 0.03148em;">k</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.664392em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mathnormal mtight">n</span></span></span></span></span></span></span></span><span class="mclose">)</span></span></span></span></span></p>
<ul>
<li>We store <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>k</mi><mi>n</mi></msup></mrow><annotation encoding="application/x-tex">k^n</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.69444em; vertical-align: 0em;"></span><span class="mord"><span class="mord mathnormal" style="margin-right: 0.03148em;">k</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.664392em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mathnormal mtight">n</span></span></span></span></span></span></span></span></span></span></span></span> visited strings in the Set and the recursion stack depth can go up to <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><msup><mi>k</mi><mi>n</mi></msup></mrow><annotation encoding="application/x-tex">k^n</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.69444em; vertical-align: 0em;"></span><span class="mord"><span class="mord mathnormal" style="margin-right: 0.03148em;">k</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.664392em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mathnormal mtight">n</span></span></span></span></span></span></span></span></span></span></span></span></li>
</ul>
</li>
</ul>

