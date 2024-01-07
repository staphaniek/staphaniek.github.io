---
layout: post
title: "Brief Note about Time Complexity Notations"
tags: "[Algorithm]"
comments: true
---

When denoting an algorithm's time complexity, we typically use Big-Oh (O) notation. For instance, the well-known time complexity of the bubble-sort algorithm is O($$n^2$$), and that of binary search is O(log n).

Even though we commonly use the Big-Oh notation as the tightest upper-bound time complexity of an algorithm, the formal definition of Big-O notation is slightly different from the widespread usage, especially when there is no given implementation of the algorithm. This definition often confuses us when dealing with the time complexity in theoretical computer science.

Since I was confused when I tried to utilize this definition in my Algorithms course, I want to share how I understood this concept to help others who might have similar issues with this notion.

Although I tried my best to understand and contain all the knowledge regarding the topic, this post might have some wrong information or errors. Please feel free to contact me if you have any doubts about the content. I will do my best to resolve them.

# Definition of time complexity notation

The definition of Big-Oh notation (O) is as follows:

> Let our algorithm's time complexity function be f(n).
For all $$n' \geq n_0$$, if there exists c>0 that $$f(n') \leq c * g(n')$$,
then f(n) = O(g(n)).

To simplify, if g(n)'s highest degree of the input size (here, n) is larger than or equal to the highest degree of the input size of f(n), we can say that f(n) = O(g(n)).
The time complexity function can be interpreted as how many logical steps are needed to solve the problem when the input size is n. If we need $$1 \over 2$$$$n^2 + n + 100$$ steps, our f(n) in this case would be $$1 \over 2$$$$n^2 + n + 100$$.

For instance, if our algorithm's time complexity f(n) is $$1 \over 2$$$$n^2 + n + 100$$ and g(n) is $$n^2$$, we can find $$n_0$$ and c that satisfy the condition. ($$n_0 = 16, c = 1$$) 

Therefore, f(n) = $$1 \over{2}$$$$n^2 + n + 100$$ = O($$n^2$$) = O(g(n)).

Similarly, the definition of Big-Omega (Ω) and Big-Theta (Θ) would be:

Big-Omega (Ω)

> Let our algorithm's time complexity function be f(n).
For all $$n' \geq n_0$$, if there exists c>0 that $$f(n') \geq c * g(n')$$,
then f(n) = Ω(g(n)).

Big-Theta (Θ)

> Let our algorithm's time complexity function be f(n).
For all $$n' \geq n_0$$, if there exists $$c_1, c_2 > 0$$ that $$c_1 * g(n') \leq f(n') \leq c_2 * g(n')$$,
then f(n) = Θ(g(n)).


# Uncommon usage of the time complexity notations

When we analyze an algorithm, we are usually asked to answer with the tightest upper-bound time complexity(Big-O), as mentioned in the former section.

However, we **can** use the Big-Oh notation with the functions that are not the tightest upper bound. In other words, if f(n) = O(log n), f(n) can be O(n), O($$n^2$$), or even O($$2^n$$). It is not a widely used way, but there would be no harm for us to know that it is not wrong to analyze an algorithm with non-tightest bounded functions. This notion indicates that **when we denote f(n) = O(g(n)), g(n) might not be the tightest upper bound of f(n)**.

Similarly, we can apply this notion to Big-Omega (Ω) notation. If f(n) = Ω($$n^3$$), f(n) can be $$Ω(n^2)$$, Ω(log n), or even Ω(1). **When we say f(n) = Ω(g(n)), g(n) might not be the tightest lower-bound of f(n)**.

This is the main takeaway from this post. However, it is quite challenging to get this idea since it conflicts with our common sense when analyzing the algorithm's time complexity.

# Comprehending the definition of time complexity notations

How can we utilize the notion of time complexity notations?

I interpreted these notions as a form of **solution ranges of the inequality equations**. 

When we deal with Big-Oh (O) notation, we first find the simplest and the tightest upper-bound expression g'(n) of our algorithm. To be specific, we utilize our typical process to get the Big-Oh notation of the algorithm and call this function g'(n). Now, we can say that all forms of functions $$g(n) \geq g'(n)$$ (when $$n \rightarrow \infty$$) can be denoted as f(n) = O(g(n)). We call this situation that g(n) grows asymptotically faster than g'(n), and g'(n) grows asymptotically slower than g(n).

In other words, if f(n) = O(g(n)), all forms of functions $$f'(n) \leq g(n)$$ (when $$n \rightarrow \infty$$) can be the exact time complexity function f(n).

We can also apply it to the Big-Omega (Ω) notation. We derive our algorithm's most straightforward and tightest lower-bound expression, g'(n). We can say that all forms of functions $$g(n) \leq g'(n)$$ (when $$n \rightarrow \infty$$) can be used as f(n) = Ω(g(n)).

In other words, if f(n) = Ω(g(n)), all forms of functions $$f'(n) \geq g(n)$$ (when $$n \rightarrow \infty$$) can be the exact time complexity function f(n).

# Simple check-up

Let's practice this notion with a simple true/false question to check our understanding.

> If f(n) = Ω(n) and g(n) = O($$n^2$$), then f(n)=O(g(n)) [True / False]

By definition, f(n) can be any form of function that grows asymptotically faster than n $$(f(n) \geq n)$$, and g(n) can be any form of function that grows asymptotically slower than $$n^2$$ $$(g(n) \leq n^2)$$. We want to know whether f(n) grows asymptotically slower than g(n) $$(f(n) \leq g(n))$$. 

We can roughly convert this problem to the following question: Does the range of function g(n) cover all the range of function f(n)? The answer would be **False** because g(n) cannot be the upper bound of f(n) in all cases. Our function f(n) can be $$n^2 , n^3 , \cdots , 2^n$$, and g(n) can be $$n$$ and even a constant function(which is just 1).

# Conclusion

In summary, while analyzing the existing implementation of an algorithm would be quite solid, the original definitions, in general, allow the functions to be boundary-tolerated when using time complexity notations like Big-Oh and Big-Omega. We can think of applying the notations' definition as the solution boundary of the inequality equations with function classes (constant, logarithm, linear, polynomial, or exponential). We also utilized this approach to solve the simple true/false question regarding the time complexity notations.
