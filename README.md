Download Link: https://assignmentchef.com/product/solved-cs577-homework1
<br>
<h1></h1>

<ol>

 <li>In a tree <em>T</em>, the distance between two vertices is the number of edges on the unique simple path between them. The <em>depth </em>of a nonempty rooted tree <em>T </em>is the largest distance between any vertex and the root, and the <em>diameter </em>of <em>T </em>is the largest distance between any pair of vertices.</li>

</ol>

The algorithm below purports to compute the diameter of a given nonempty rooted tree. Argue that FindDiameterAndDepth and FindDiameter

(a) correctly implement their specifications and (b) run in linear time.

<h2>Algorithm 1</h2>

<strong>Input: </strong><em>T</em>, where <em>T </em>is a nonempty rooted tree

<strong>Output: </strong>the diameter of <em>T</em>

1: <strong>procedure </strong>FindDiameter(<em>T</em>)

2:                    (<em>D,d</em>) ← FindDiameterAndDepth(<em>T</em>)

<h2>3:             return <em>D</em></h2>

<strong>Input: </strong><em>T</em>, where <em>T </em>is a nonempty rooted tree

<strong>Output: </strong>(<em>D,d</em>) where <em>D </em>is the diameter of <em>T </em>and <em>d </em>is the depth of <em>T</em>

4: <strong>procedure </strong>FindDiameterAndDepth(<em>T</em>)

5:              <strong>if </strong><em>T</em>’s root has no children <strong>then</strong>

6:          <strong>return </strong>(0<em>,</em>0) 7:  <strong>else</strong>

8:                           <em>T</em><sub>1</sub><em>,…,T<sub>k </sub></em>← the subtrees of <em>T </em>rooted at the children of the root of <em>T</em>

<h2>9:                      for <em>i </em>= 1 to <em>k </em>do</h2>

10:                                 (<em>D<sub>i</sub>,d<sub>i</sub></em>) ← FindDiameterAndDepth(<em>T<sub>i</sub></em>)

11:                   <em>d </em>← 1+ largest <em>d<sub>i</sub></em>

12:                       <strong>if </strong><em>k </em>= 1 <strong>then </strong><em>d</em><sup>0 </sup>← 0 <strong>else </strong><em>d</em><sup>0 </sup>← 1+ second largest <em>d<sub>i </sub></em>including repetitions

13:                       <em>D </em>← max(<em>D</em><sub>1</sub><em>,…,D<sub>k</sub>,d </em>+ <em>d</em><sup>0</sup>)

<h2>14:                   return (<em>D,d</em>)</h2>

<ol start="2">

 <li>Consider the problem of powering an integer:</li>

</ol>

<strong>Input: </strong>(<em>a,b</em>) with <em>a,b </em>∈ Z and <em>b </em>≥ 1

<strong>Output: </strong><em>a<sup>b</sup></em>, which we define as, where “·” denotes multiplication.

<em>b </em>times

Design an algorithm for this problem that uses at most <em>O</em>(log<em>b</em>) multiplications. Hint: First consider the case where <em>b </em>is a power of 2.

<h1>Regular problems</h1>

<ol start="3">

 <li>

  <ul>

   <li>You are given a perfect binary tree <em>T </em>with <em>n </em>= 2<em><sup>d </sup></em>leaves, where each leaf contains an integer value. Reading the leaf values from left to right yields a sequence of integers. The question is how small we can make the number of inversions in that sequence by applying any number of operations of the following type: Select an internal vertex and swap the two child subtrees. Data associated to a vertex in a subtree follow the vertex in the swap.</li>

  </ul></li>

</ol>

For example, if the sequence of leaf values is (4<em>,</em>2<em>,</em>1<em>,</em>3), then a swap at the root followed by a swap at the right child of the root turns the sequence into (1<em>,</em>3<em>,</em>2<em>,</em>4), which has only one inversion. See Figure 1. It is impossible to do better, so the answer for this particular example is 1.

Figure 1: Example for Problem 3(a)

Design an <em>O</em>(<em>n</em>log<em>n</em>) algorithm for this problem.

<ul>

 <li>Consider the following generalization of part (a). You are given a perfect binary tree <em>T </em>with <em>n </em>= 2<em><sup>d </sup></em>leaves, where each leaf <em>and each internal vertex </em>contains an integer value (positive or negative). As before, reading the leaf values (and the leaf values only) from left to right yields a sequence of <em>n </em> The values stored at the internal vertices factor into determining the <em>undesirability </em>of inversions in this sequence. Given an inversion (<em>i,j</em>), its undesirability is defined to be the value stored at the lowest-level common ancestor of the <em>i</em>-th and <em>j</em>-th leaves of <em>T</em>. The question is how small can we make the sum of the undesirabilities of all inversions in the sequence by applying any sequence of the same type of operations as in part (a).</li>

</ul>

Continuing the example above, suppose the root stores an undesirability value of 4, the root’s left child stores −17, and the root’s right child stores 6. The same sequence of swaps as before can be depicted as shown in Figure 2. The selected sequence of swaps no longer minimizes the total undesirability. The minimum turns out to be −13, as coincidentally attained by the second tree in the figure (swapping at the root only).

Explain how to adapt your solution to part (a) to handle part (b). Your algorithm should continue to run in <em>O</em>(<em>n</em>log<em>n</em>) time. Note that part (a) corresponds to the special case of part (b) in which all undesirabilities are 1.

Figure 2: Example for Problem 3(b).

4                                                             4                                                            4

In the first tree, the inversion between the first two leaves has undesirability −17 since their lowest-level common ancestor is the left-child of the root. The inversions between the first and third leaves, the first and fourth leaves, and the second and third leaves all have undesirability 4, since each of those pairs of leaves has the root as their lowest-level common ancestor. There are no other inversions. The total undesirability of the first tree is therefore −17 + 4 + 4 + 4 = −5. The total undesirability of the second tree is −17 + 4 = −13, and of the third tree is 4.

<ol start="4">

 <li>Consider the following computational problem:</li>

</ol>

<strong>Input: </strong>Array <em>A</em>[1<em>,…,n</em>] of positive integers.

<strong>Output: </strong>Array <em>C</em>[1<em>,…,n</em>] where <em>C</em>[<em>i</em>] is the number of <em>j </em>∈ {1<em>,…,i </em>− 1} with <em>A</em>[<em>j</em>] ≥ <em>A</em>[<em>i</em>].

For example, if <em>A </em>= [8<em>,</em>12<em>,</em>10<em>,</em>9<em>,</em>10<em>,</em>12<em>,</em>7] then <em>C </em>= [0<em>,</em>0<em>,</em>1<em>,</em>2<em>,</em>2<em>,</em>1<em>,</em>6].

Design an <em>O</em>(<em>n</em>log<em>n</em>) algorithm for this problem.

<h1>Challenge problem</h1>

<ol start="5">

 <li>Show that every comparison-based algorithm for problem 3(a) requires Ω(<em>n</em>log<em>n</em>) comparisons. You may first want to prove the same lower bound for problem 3(b).</li>

</ol>

<h1>Programming problem</h1>

<ol start="6">

 <li>SPOJ problem <a href="https://www.spoj.com/problems/CODESPTB">Insertion Sort</a> (problem code CODESPTB).</li>

</ol>