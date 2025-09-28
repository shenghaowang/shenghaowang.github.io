## Terminology

- BFS: Breadth First Search
- DFS: Depth First Search

## Recursion

- Recursion can be detected with the following patterns
	- Every output depends on the output of a few subproblems combined.
	- The problem requires expanding over a tree or a graph, node by node, such that same function can be called for every single node.

- Steps to follow for solving recursion problems
	- What is the smallest answer/step 1 in the problem that is a known fact and you don’t have to perform any calculation if you’re asked the answer to that? (For example, the first two Fibonacci numbers, or the fact that 1 factorial is 1). This will give you the **base case.**
	- How do I solve the second step using the base case?
	- How do I then solve the third step using the answer of the second step?
	- Try to find a pattern from steps 2 and 3. Now, how do you solve i-th step using the answer to (i-1)th step? Write that down.
	- Write the code. Make a function taking in input i, have an if statement for the base case, and then solve for i+1.

- Recursive vs. iterative solutions
	- Recursive algorithms can be very space inefficient. Each recursive call adds a new layer to the stack. If the algorithm recurses to a depth of n, it uses at least O(n) memory.
	- All recursive algorithms can be implemented iteratively. It's often better to do so if possible.

## Greedy Algorithms

- Greedy algorithms choose at each step what seems to be the best option. In other words, greedy problems reduce problems into smaller ones by making the locally optimal choice at each step.
- E.g. make changes with the minimum number of coins (pennies, nickels, dimes, and quarters).
- In ML, greedy approach is used in building decision trees, and feature selection of regression models.
- Keep greedy algorithms in mind for optimization problems, where there's a set of choices to select from.
- Greedy algorithms can be used for achieving the *local optimality* but not necessarily the *global optimality*, which dynamic programming achieves.

## Dynamic Programming (DP)

- DP uses recursion while storing results of subproblems and using it later (memoization). The main idea is to store answers to subproblems to avoid recalculation.
- Two criteria required for applying DP
	- **optimal substructure**: the problem can be broken into subproblems.
	- **overlapping subproblems** : the answer of subproblems can be reused across different subproblems.
 - DP can be implemented with a top-down or bottom-up approach. Take the Fibonacci problem as example.
	 - Top-down approach: fib(n) -> fib(n-1), fib(n-2) -> ...
	 - Bottom-up approach: fib(1), fib(2) -> fib(3) -> ... -> fib(n)
	 - Half-and-half approach: divide the data set in halves, solve for each and merge.


## References

- [#OneYearCodingPlan: Recursion and Dynamic Programming](https://medium.com/geekculture/oneyearcodingplan-recursion-and-dynamic-programming-ee7675f3e6ad)
- *Ace the Data Science Interview* book