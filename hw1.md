<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({ tex2jax: {inlineMath: [['$', '$']]}, messageStyle: "none" });
</script>

HW1\
Student ID: 112054320\
Name: 黃章昱\
Department: 隨班附讀\
Date: 2023/10/16

1\
(a)\
It can be done by using Newton's method. Newton's method approximate square root of n through compute a guess repeatedly. The equation of the guess is: `new_guess = (old_guess + n / oldguess) / 2`, and the first guess is `n / 2.` We can repeat the guess untill `old_guess - new_guess < 0.1`, which means that the integer part is correct. To get the integer part, use a loop to subtract `new_guess` untill it becomes zero.

(b)
~~~
Algorithm roof_of_square_root(n):
    old_guess <- n / 2
    do:
        new_guess <- (old_guess + n / oldguess) / 2
    while old_guess - new_guess > 0.1

    result <- 0
    while new_guess >= 1:
        result <- result + 1
        new_guess <- new_guess - 1

    return result
~~~

2\
(a)
~~~
Algorithm gcd(a,b):

    if a < b:
        swap(a,b)

    while b != 0:
        while a > b:
            a <- a - b
        swap(a,b)

    return a
~~~

(b)\
Through Euclid's algorithm, we know that the smallest number this game can get is the greatest common divisor of a and b, gcd(a,b).

Assume that a > b. Then the greatest number in this game is a. Say that a = r * gcd(a,b). All numbers in the set `S = {a - i * gcd(a,b)| i from 0 to r - 1} - {a,b}` are an answer to the game. Hence, if |S| is odd, which means that r is odd, the first player will win; if |S| is even, the second player will win.

3

Proof of $(1+\frac{1}{n})^n < n$
1. $(1+\frac{1}{n})^n = (\frac{n+1}{n})^n = \frac{(n+1)^n}{n^n}$
2. Proving $(1+\frac{1}{n})^n < n$ equals to prove $(n+1)^n < n^{n+1}$
3. $(n+1)^n = n^n+C^n_1*n^{n-1}+...+C^n_{n-1}*n+1$
4. $n^{n+1} = n^n + n*n^{n-1}+...+n^{n-1}*n $
5. The first n - 1 terms of step 4 are bigger than those in step 3. The last term in step 4: $n^n$, is absolutely bigger than the sum of nth and (n+1)th terms in step 3. In other words, $C^n_{n-1}*n+1 = n^2+1 < n^n$ for $n\geq3$.

Proof of that sequence $\lbrace n^{\frac{1}{n}}\rbrace ^\infty_{n=3}$ is decreasing.
1. The statement equivalences to $ \frac{1}{n} * \log{n} $ is decreasing, which equivalences to $ \frac{1}{n+1} * \log{(n+1)} < \frac{1}{n} * \log{n} \equiv \log_n{n+1} < \frac{n+1}{n} $
2. Assume that $\log_n{n+1}\geq\frac{n+1}{n}$:
3. $\equiv \log_n{(n+1)} - 1 = \log_n{\frac{n+1}{n}} \geq \frac{1}{n}$
4. $\equiv n*\log_n{\frac{n+1}{n}} = \log_n{(\frac{n+1}{n})^n \geq 1}$
5. But in the previos proof, $\frac{(n+1)^n}{n^n} < n$. We can get $\log_n{(\frac{n+1}{n})^n} < \log_n{n} = 1$
6. In conclusion, the assumption in step 2 is wrong. Statement 1 is true.

4

Proof:
1. Basis step:\
When n = 1, $1 = f_1$
2. Induction step:\
Assume that for all $n\leq k$, n can be written as $n = f_a + f_b + f_c+...$, which a, b, c... is not consecutive and $f_a > f_b>f_c>...$.\
When $n=k+1$, $k+1=f_a+(f_b+f_c+...+1)$. Because $(f_b+f_c+...+1) < k$, it can also be written as sum of nonconsecutive Fibonacci numbers, that say $f_b+f_c+...+1 = f_{b'}+f_{c'}+...$ and $f_{b'} > f_{c'}...$\
If $f_a$ and $f_{b'}$ is consecutive, then we can use $f_{a+1}$ to exchange them.
