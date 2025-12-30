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
<h3 id="problems-solved-and-some-good-solutions-to-read">Problems solved and some good solutions to read</h3>
<p><strong>BRUTE FORCE for 1192. Critical Connections in a Network<br>
For n&lt;1000</strong></p>
<blockquote>
<p>NOT PASSED</p>
</blockquote>
<p>Time complexity: <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><msup><mi>E</mi><mn>2</mn></msup><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(E^2)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.06411em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord"><span class="mord mathnormal" style="margin-right: 0.05764em;">E</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.814108em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span></span></span></span></span><span class="mclose">)</span></span></span></span></span></p>
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
<p>Time complexity : <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><msup><mi>N</mi><mn>2</mn></msup><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(N^2)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.06411em; vertical-align: -0.25em;"></span><span class="mord mathnormal" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord"><span class="mord mathnormal" style="margin-right: 0.10903em;">N</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.814108em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span></span></span></span></span><span class="mclose">)</span></span></span></span></span></p>
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
<h2 id="eulerian-path-problems">Eulerian path problems</h2>

