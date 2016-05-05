---
title: Dont Repeat Yourself - Dynamic Programming
excerpt: "My impressions of the concept dynamic programming using small examples."
image: 
  feature: Those-who-cannot-remember-the__quotes-by-George-Santayana.png
  teaser: P1510382_teaser.jpg
  credit: QuotesCover.com
  creditlink: http://www.quotescover.com/those-who-cannot/app/high-resolution-image
tags: [design, programming, dynamic]
comments: true
featured: true
---

I will introduce you with basics of dynamic programming.

{% include toc.html %}

As a programmer you love to solve problems, requirement analysis and implementation. In the field of mathematics, computer science and management science many times you have to deal with complex problems in time O(n[^2]) or O(n[^3]). Those types of problems are hard to resolve with naive approach. Here comes the Dynamic programming ( *DP* for short ) to rescue. You can solve important parts of given problem with it.

I presume that you have basic hands-on with [PHP](http://php.net/ "PHP") programming, recursion functions and [cyclomatic complexity](https://en.wikipedia.org/wiki/Cyclomatic_complexity "Cyclomatic complexity").

## What is a dynamic programming?

It is a design technique which uses algorithms and is usually based on a repeated formula and few intermediate states for storage.

In this approach you divide a problem into smaller sub problems, solve each of them and combine their results to solve the bigger problem. A sub-solution of the problem is constructed from previously found solution.

This breaking up of the main problem into sub problems can be several levels deep. *DP* is mainly used when solutions of same sub problems are needed again and again. The key in *DP* is remembering. In short *DP* uses past knowledge to make solving a future problem faster.

### Dynamic programming is not recursion

In recursion, sometimes there are cases when same sub-problems are resolved many times. Take an example of calculating xth Fibonacci number.

~~~
1. fib(x) = fib(x-1) + fib(x-2)
2. fib(x-1) = fib(x-2) + fib(x-3)
3. fib(x-2) = fib(x-3) + fib(x-4)
.................................
................................
................................
x. fib(2) = fib(1) + fib(0)
~~~

You can clearly see here that in the first three steps, fib(x-3) is calculated twice. So if you have very large sequence and deeper recursion, you can find repeating the same sub-problems again and again.

In short DP is a memorization / remembering method and it uses a table to store results of sub-problem. This way if same sub-problem is encountered again in future, it could directly return the result instead of calculating it again.

So DP is not much useful in cases where you don't need have any common / overlapping sub problems. This is because there is no point storing / memorizing / remembering solutions if they are not needed again in future. We should go for recession in such cases

## Example

It will be much easier to explain with examples, because a raw theory is very hard to understand.

### Problem statement

Given a cost matrix matrix[][] and a position (m, n) in matrix[][], write a function that returns cost of minimum cost path to reach (m, n) from (0, 0). You can only traverse down, right and diagonally lower cells from a given cell, i.e., from a given cell (i, j), cells (i+1, j), (i, j+1) and (i+1, j+1) can be traversed. You may assume that all costs are positive integers. You may assume that all costs are positive integers.

what is the minimum cost path to (2, 2)?

![Alt](https://akasralikar.files.wordpress.com/2016/04/matrix_1.png "Matrix 1")

The path with minimum cost is highlighted in the following image. The path is (0, 0) –&gt; (1, 1) –&gt; (2, 2). The cost of the path is 15 (1 + 5 + 9).

![Alt](https://akasralikar.files.wordpress.com/2016/04/matrix_2.png "Matrix 1")

### Solution with recursion approach
{% highlight php %}
<?php
/**
 * Given a cost matrix cost[][] and a position (m, n) in cost[][], it returns cost of minimum cost path to reach (m, n)
 * from (0, 0).
 */
class CMinCostPath {
	/**
	 * @param array $arrintMatrix
	 * @param integer $intDesiredRowDimension
	 * @param integer $intDesiredColumnDimension
	 * @return mixed
	 */
	public function minCost( array $arrintMatrix, $intDesiredRowDimension, $intDesiredColumnDimension ) {
		if( 0 > $intDesiredColumnDimension || 0 > $intDesiredRowDimension ) {
			return PHP_INT_MAX;
		} else if( 0 === $intDesiredRowDimension && 0 === $intDesiredColumnDimension ) {
			return $arrintMatrix[$intDesiredRowDimension][$intDesiredColumnDimension];
		} else {
			return $arrintMatrix[$intDesiredRowDimension][$intDesiredColumnDimension] + min( $this->minCost( $arrintMatrix, $intDesiredRowDimension - 1, $intDesiredColumnDimension - 1 ),
				$this->minCost( $arrintMatrix, $intDesiredRowDimension - 1, $intDesiredColumnDimension ),
				$this->minCost( $arrintMatrix, $intDesiredRowDimension, $intDesiredColumnDimension - 1 ) );
		}
	}
}

$objCostPath = new CMinCostPath();
$arrintCosts = [ [ 1, 2, 3 ], [ 4, 5, 6 ], [ 7, 8, 9 ] ];
echo $intResult = $objCostPath->minCost( $arrintCosts, 2, 2 );
?>
{% endhighlight %}

We can clearly see that this function calculates same sub problem multiple times, so there are many recursive function call which appear more than once.

### Solution with dynamic programming approach

{% highlight php %}
<?php
/**
 * Given a cost matrix cost[][] and a position (m, n) in cost[][], it returns cost of minimum cost path to reach (m, n)
 * from (0, 0).
 */
class CMinCostPath {
	/**
	 * @param array $arrintMatrix
	 * @param integer $intDesiredRowDimension
	 * @param integer $intDesiredColumnDimension
	 * @return mixed
	 */
	public function minCost( array $arrintMatrix, $intDesiredRowDimension, $intDesiredColumnDimension ) {
		$arrintCosts = [ ];

		$intTempPlaceHolder = 0;
		for( $intCounter = 0; $intCounter <= $intDesiredColumnDimension; $intCounter++ ) {
			$arrintCosts[0][$intCounter] = $intTempPlaceHolder + $arrintMatrix[0][$intCounter];
			$intTempPlaceHolder = $arrintCosts[0][$intCounter];
		}

		$intTempPlaceHolder = 0;
		for( $intCounter = 0; $intCounter <= $intDesiredRowDimension; $intCounter++ ) {
			$arrintCosts[$intCounter][0] = $intTempPlaceHolder + $arrintMatrix[$intCounter][0];
			$intTempPlaceHolder = $arrintCosts[$intCounter][0];
		}

		for( $intRowCounter = 1; $intRowCounter <= $intDesiredRowDimension; $intRowCounter++ ) {
			for( $intColumnCounter = 1; $intColumnCounter <= $intDesiredColumnDimension; $intColumnCounter++ ) {
				$arrintCosts[$intRowCounter][$intColumnCounter] = $arrintMatrix[$intRowCounter][$intColumnCounter] + min( $arrintCosts[$intRowCounter - 1][$intColumnCounter - 1], $arrintCosts[$intRowCounter - 1][$intColumnCounter], $arrintCosts[$intRowCounter][$intColumnCounter - 1] );
			}
		}

		return $arrintCosts[$intDesiredRowDimension][$intDesiredColumnDimension];
	}
}

$objCostPath = new CMinCostPath();
$arrintCosts = [ [ 1, 2, 3 ], [ 4, 5, 6 ], [ 7, 8, 9 ] ];
echo $intResult = $objCostPath->minCost( $arrintCosts, 2, 2 );
?>
{% endhighlight %}

Time Complexity of this implementation is O(mn) which is way better than Naive Recursive implementation.

## Common Popular Problems

Some of the well known common problems which could be solved using *DP* approach is as below. I will plan to write about each of this use case with examples and sample code implementations. You can find more info about these at [here]( http://www.geeksforgeeks.org/tag/dynamic-programming/ "dynamic-programming")

- 0/1 Knapsack Problem
- Longest Common Subsequence
- Matrix Chain Multiplication
- Coin Changing Minimum Number of Coins
- Subset Sum Problem
- Longest Increasing Subsequence
- Optimal Binary Search Tree
- Minimum Edit Distance
- Longest Palindromic Sub sequence
- Coin Changing Number of ways to get total
- Egg Dropping
- Cutting Rod
- Weighted Job Scheduling
- Longest Common Substring
- Maximum Sum Rectangular Sub matrix in Matrix /2D kadane
- Box Stacking
- 0/1 Knapsack Problem Top Down
- Text Justification
- Maximum Size Rectangle of All 1's
- Coin Change Top down
- Word Break Problem
- Palindrome Partition
- Maximum Sum Increasing Subsequence
- Minimum jump to reach end
- Minimum Cost Path
- Longest Bitonic Subsequence
- Maximum Sub Square Matrix
- Optimal Strategy Game Pick from Ends of array
- String Interleaving
- Maximum Sum Subsequence Non-Adjacent
- Coin Changing Minimum Coins
- Staircase Problem Fibonacci Series
- Numbers WIthout Consecutive 1s in binary representation
- Buy/Sell Stock With K transactions To Maximize Profit
- Total Ways in Matrix
- Maximum Sub square With Sides as X
- Count Number of Binary Search Tree Possible given n keys
- Count Number of Binary Tree Possible given Preorder Sequence length
- Wild card Matching

Please write comments below if you find anything incorrect, missing, or you want to share more information about the topic discussed above.
