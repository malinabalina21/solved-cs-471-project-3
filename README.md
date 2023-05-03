Download Link: https://assignmentchef.com/product/solved-cs-471-project-3
<br>
<h1>1.1         Project Speci cation</h1>

Update your github repository with a directory submit/prj3-sol which contains a le prj3-sol.pro which contains implementations of the Prolog procedures documented in the skeleton le prj3-sol.pro.

<h1>1.2       Provided Files</h1>

The &lt;./prj3-sol&gt; directory contains the following:

prj3-sol.pro A skeleton le containing the speci cations of the Prolog procedures you need to implement.

README A template README; replace the XXX with your name, B-number and email. You may add any other information you believe is relevant to your project submission.

<h1>1.3     Hints</h1>

You may choose to follow the following hints (they are not by any means required).

<ul>

 <li>First work on your solutions using Prolog’s declarative semantics. Write facts and rules for a problem which states something about the problem domain.</li>

</ul>

Then think about the procedural semantics. It may be a good idea to include facts/rules corresponding to base cases before facts/rules corresponding to recursive cases (this should not a ect correctness, but may result in di erent orders of solutions or a solution versus an in nite loop).

<ul>

 <li>Review the Prolog Programming Heuristics given in the course</li>

</ul>

Hints for the individual exercise follow:

<ol>

 <li>Write out a fact for the sum of a leaf(V). Then write out a rule for sum of a tree(L, V, R): recursively compute the sum of L and R and then compute the overall sum in terms of those results and V using is/2.</li>

 <li>Write out a fact for the naive atten of a leaf(V). Then write out a rule for the naive atten of tree(L, V, R): recursively atten the trees L and R and then compute the overall atten in terms of those results and V using append/3.</li>

 <li>De ne an auxiliary Prolog procedure which accumulates the atten of the tree in reverse order. Call the auxiliary procedure with this accumulator empty and reverse the result of the auxiliary procedure to get the overall attened list.</li>

 <li>Proceed as follows:

  <ul>

   <li>Review the material on DCGs from the</li>

   <li>The provided grammar is left recursive; transform it to replace the left recursion with the Kleene closure operator.</li>

   <li>When using an imperative programming paradigm, the Kleene closure operator was implemented using loops. That will need to be implemented in Prolog using recursion.</li>

  </ul></li>

</ol>

Introduce new non-terminals in your grammar, say exprLoop and termLoop. Write out right-recursive rules for each of these, using a separate rule for each operator. So you will have 3 rules for exprLoop: one for ’+’, one for ’-’ and one for the base-case recognizing empty; similarly for termLoop.

<ul>

 <li>Translate the transformed grammar from the previous step to DCG notation. For now, ignore constructing the AST.</li>

 <li>Connect your DCG rules to the required parse_arith/2, leaving the AST variable uninstantiated.</li>

 <li>Test until your parse_arith/2 works as a recognizer, correctly accepting or rejecting di erent token lists.</li>

 <li>Add an AST argument to your DCG. Note that the AST in the head of a rule will be constructed using the AST’s constructed in the body; it may be a good idea to review the solution to the previous project.</li>

 <li>Iterate until you build the correct AST.</li>

</ul>

<ol start="5">

 <li>This problem is extremely straight-forward and illustrates the power of Prolog (my solution consists of 5 lines of code). The solution will depend on the backtracking behavior of member/2. To see how that would work, run the following goal:</li>

</ol>

member(s – 1 – S, [x – 0 – y, x – 1 – y,

s – 0 – x, s – 1 -x, s – 1 -t]).

Once you understand how member/2 can be used to drive the simulation, simply write out your nfa_sim/2, recursing on the list of input symbols. You will need one rule for the base case, succeeding if the input is empty and the current state is a nal state, and one rule for the recursive case when the input is non-empty.