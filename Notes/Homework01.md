Important theorem

For any two functions \(f(n)\) and \(g(n)\), we have \(f(n) = \Theta(g(n))\) if and only if

\[
f(n) = O(g(n)) \quad \text{and} \quad f(n) = \Omega(g(n)).
\]

To prove that for any two functions \( f(n) \) and \( g(n) \), we have \( f(n) = \Theta(g(n)) \) if and only if \( f(n) = O(g(n)) \) and \( f(n) = \Omega(g(n)) \), we need to approach the proof in two directions:

1. Prove \( f(n) = \Theta(g(n)) \Rightarrow f(n) = O(g(n)) \) and \( f(n) = \Omega(g(n)) \)
The definition of \( \Theta(g(n)) \) states that:

\[
c_1 g(n) \leq f(n) \leq c_2 g(n) \quad \text{for all } n \geq n_0,
\]

where \( c_1 \), \( c_2 \), and \( n_0 \) are constants. This means that \( f(n) \) is bounded both above and below by a constant multiple of \( g(n) \).

- **To show \( f(n) = O(g(n)) \)**:  
  From the inequality \( f(n) \leq c_2 g(n) \), we can conclude that there exists a constant \( c_2 \) such that \( f(n) \) is asymptotically upper-bounded by \( g(n) \). Therefore, \( f(n) = O(g(n)) \).

- **To show \( f(n) = \Omega(g(n)) \)**:  
  Similarly, from the inequality \( f(n) \geq c_1 g(n) \), we can conclude that there exists a constant \( c_1 \) such that \( f(n) \) is asymptotically lower-bounded by \( g(n) \). Therefore, \( f(n) = \Omega(g(n)) \).

Thus, if \( f(n) = \Theta(g(n)) \), then \( f(n) = O(g(n)) \) and \( f(n) = \Omega(g(n)) \).

2. Prove \( f(n) = O(g(n)) \) and \( f(n) = \Omega(g(n)) \Rightarrow f(n) = \Theta(g(n)) \)
We are given that:

\[
f(n) = O(g(n)) \quad \text{and} \quad f(n) = \Omega(g(n)).
\]

By the definition of \( O(g(n)) \), there exists a constant \( c_2 > 0 \) and \( n_0 \) such that:

\[
f(n) \leq c_2 g(n) \quad \text{for all } n \geq n_0.
\]

By the definition of \( \Omega(g(n)) \), there exists a constant \( c_1 > 0 \) and \( n_0 \) such that:

\[
f(n) \geq c_1 g(n) \quad \text{for all } n \geq n_0.
\]

Combining these two inequalities, we get:

\[
c_1 g(n) \leq f(n) \leq c_2 g(n) \quad \text{for all } n \geq n_0,
\]

which is precisely the definition of \( f(n) = \Theta(g(n)) \).

3.2-1

Let \( f(n) \) and \( g(n) \) be asymptotically nonnegative functions. Using the basic definition of \(\Theta\)-notation, prove that

**Proof:**

\[
\max\{f(n), g(n)\} = \Theta(f(n) + g(n)).
\]

By the definition of \(\Theta\)-notation, we need to show that there exist constants \(c_1\), \(c_2\), and \(n_0\) such that for all \(n \geq n_0\):

\[
c_1(f(n) + g(n)) \leq \max\{f(n), g(n)\} \leq c_2(f(n) + g(n)).
\]

To prove this, we can choose \(c_1 = \frac{1}{2}\) and \(c_2 = 1\), and proceed as follows:

1. **Upper bound**:  
   Since \(\max\{f(n), g(n)\} \leq f(n) + g(n)\), we can choose \(c_2 = 1\) to satisfy:

   \[
   \max\{f(n), g(n)\} \leq c_2(f(n) + g(n)) = f(n) + g(n).
   \]

2. **Lower bound**:  
   Notice that \(\max\{f(n), g(n)\} \geq \frac{1}{2}(f(n) + g(n))\), because at least one of \(f(n)\) or \(g(n)\) must be at least half of the sum \(f(n) + g(n)\). Therefore, choosing \(c_1 = \frac{1}{2}\) satisfies:

   \[
   \max\{f(n), g(n)\} \geq \frac{1}{2}(f(n) + g(n)).
   \]

Thus, with \(c_1 = \frac{1}{2}\), \(c_2 = 1\), and for sufficiently large \(n\), the inequality holds. Hence, we have proven that:

\[
\max\{f(n), g(n)\} = \Theta(f(n) + g(n)).
\]

3.2-2 

Explain why the statement, "The running time of algorithm \(A\) is at least \(O(n^2)\),” is meaningless".

\(O\)-notation represents an **upper bound** on the growth of a function, not a lower bound. 

- \(O\)-notation describes the worst-case growth rate, meaning the algorithm's running time will not exceed \(O(n^2)\) for large \(n\).
- The phrase "at least" implies a **lower bound**, which should be expressed using **\(\Omega\)-notation** instead of **\(O\)-notation**.

To describe a lower bound, the correct statement would be: "The running time of algorithm \(A\) is at least \(\Omega(n^2)\)."

4.4-1

For each of the following recurrences, sketch its recursion tree, and guess a good asymptotic upper bound on its solution. Then use the substitution method to verify your answer.

1. \( T(n) = T(n/2) + n^3 \)
2. \( T(n) = 4T(n/3) + n \)

**Solution:**

\(Q_{1}\):

```plaintext
c1n^3
  |
c1(n/2)^3
  |
c1(n/4)^3
  |
c1(n/8)^3
  |
 ...
  |
 c2
```

1. **Guess the form of the solution**:
  We hypothesize that \( T(n) = O(n^3) \), meaning our inductive hypothesis is:
\[
T(n) \leq c n^3 
\]
for all \(n \geq n_{0}\) where \( c \) and \( n_{0} \) are constants.

2. **Inductive Hypothesis**:
Assume that for all values smaller than \( n \), the recurrence satisfies the following:
\[
T(n/2) \leq c \left(\frac{n}{2}\right)^3 = \frac{c n^3}{8}
\]

3. **Substitute into the recurrence**:
Choose \(n_{0} = 1\). For all \(n \geq 2n_{0}\), substitute this inductive hypothesis into the given recurrence:
\[
T(n) = T(n/2) + n^3
\]
By substituting \( T(n/2) \leq \frac{c n^3}{8} \), we get:
\[
T(n) \leq \frac{c n^3}{8} + n^3
\]
\[
T(n) \leq \left(\frac{c}{8} + 1\right) n^3
\]

4. **Choosing constants \( c \) and \(n_{0}\)**:
To ensure that this inequality holds, we need to choose \( c \) such that:
\[
\left(\frac{c}{8} + 1\right) n^3 \leq c n^3
\]
Dividing both sides by \( n^3 \) (which is positive), we get:
\[
\frac{c}{8} + 1 \leq c
\]
\[
c \geq \frac{8}{7}
\]
Thus, choosing \( c = 2 \) satisfies this condition.

5. **Base case verification**:
For the base case, when \( n_{0} \leq n \lt 2n_{0}\), we need to verify that \( T(1) \leq c \cdot 1^3 = c \). Since \( T(1) \) is a constant, we can choose \( c \) to be the maximum of \( 2 \) and \( T(1) \), i.e., \( c = \max(2, T(1)) \), to ensure that the base case is valid.

This completes the proof.

\(Q_{2}\):

```plaintext
         c1n -> c1n
      /  |  |  \
   c1n/3  c1n/3 c1n/3 c1n/3 -> 4/3c1n
   /|\    /|\    /|\    /|\
c1n/9 c1n/9 c1n/9 c1n/9 ... c1n/9 -> (4/3)^{2}c1n
            ...
|   |  | ... |
c2 c2 c2 ... c2 -> c2(4^{log_{3} n})=c2(n^{log_{3} 4})
```

Introduction to algorithms: \
A trick of the trade: subtracting a low-order term 

1. **Guess the form of the solution**:
We hypothesize:
\[
T(n) \leq c n^{\log_3 4}
\]

2. **Inductive Hypothesis**:
Assume that for all values smaller than \( n \), the recurrence satisfies the following inequality:
\[
T(n) \leq c n^{\log_3 4} - k n
\]
where \( c \) and \( k \) are constants.

3. **Substitute into the recurrence**:
Choose \(n_{0} = 1\). For all \(n \geq 3n_{0}\), substitute this inductive hypothesis into the given recurrence:
\[
T(n/3) \leq c \left(\frac{n}{3}\right)^{\log_3 4} - k \cdot \frac{n}{3}
\]
Note that \( \left(\frac{n}{3}\right)^{\log_3 4} = \frac{n^{\log_3 4}}{4} \), so:
\[
T(n/3) \leq \frac{c n^{\log_3 4}}{4} - \frac{k n}{3}
\]
\[
T(n) \leq 4 \left(\frac{c n^{\log_3 4}}{4} - \frac{k n}{3}\right) + n
\]
Simplifying:
\[
T(n) \leq c n^{\log_3 4} - n\left(\frac{4k}{3} - 1\right)
\]

4. **Choosing the constant \( k \)**:
To make sure that this inequality holds, choose \( k \) such that \( \frac{4k}{3} - 1 \geq 0 \). This simplifies to:
\[
\frac{4k}{3} \geq 1 \quad \Longrightarrow \quad k \geq \frac{3}{4}
\]
Thus, we can choose \( k = 1 \), which satisfies this condition.
Finally, the recurrence becomes:
\[
T(n) \leq c n^{\log_3 4}
\]

5. **Verify the base case**:
For the base case, when \( n_{0} \leq n \lt 3n_{0}\), \( n = 1 \), assume \( T(1)\) and \(T(2)\) are constants. We can choose \( c = \max(T(1), T(2)) \) to ensure that the base case satisfies the inductive hypothesis.

This completes the proof.

4.5-1

Use the master method to give tight asymptotic bounds for the following recurrences.

1. \(T(n)=2T(\frac{n}{4})+1\)
2. \(T(n)=2T(\frac{n}{4})+\sqrt n\)
3. \(T(n)=2T(\frac{n}{4})+n^{2}\)

**Solution:**

\(Q_{1}\):

\(a=2\), \(b=4\), \(f(n)=1\)

There exists a constant \(\epsilon\) such that \( f(n) = 1 = O(n^{\log_4 2 - \epsilon}) \), this falls into **Case I** of the master method. Thus, the tight asymptotic bound for the recurrence \( T(n) = 2T\left(\frac{n}{4}\right) + 1 \) is:

\[
T(n) = \Theta(n^{\frac{1}{2}})
\]

\(Q_{2}\):

\(a=2\), \(b=4\), \(f(n)=\sqrt n\)

There exists a constant \(K = 0\) such that \( f(n) = \sqrt n = O(n^{\log_4 2}(log n)^{K}) \), this falls into **Case II** of the master method. Thus, the tight asymptotic bound for the recurrence \( T(n) = 2T\left(\frac{n}{4}\right) + \sqrt n \) is:

\[
T(n) = \Theta(n^{\frac{1}{2}}logn)
\]

\(Q_{3}\):

\(a=2\), \(b=4\), \(f(n)=n^{2}\)

There exists a constant \(\epsilon \) such that \( f(n) = n^{2} = \Omega(n^{\log_4 2+\epsilon}) \). And \( f(n) = n^{2}\) is additionally satisfies the regularity condition \(2f(\frac{n}{4})=\frac{n^{2}}{8} \leq cf(n)=cn^{2} \) for some constant \(c \lt 1\) and all sufficient \(n\). This falls into **Case III** of the master method. Thus, the tight asymptotic bound for the recurrence \( T(n) = 2T\left(\frac{n}{4}\right) + n^{2} \) is:

\[
T(n) = \Theta(n^{2})
\]