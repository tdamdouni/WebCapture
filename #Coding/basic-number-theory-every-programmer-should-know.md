# Basic Number Theory Every Programmer Should Know...

_Captured: 2017-09-05 at 20:55 from [www.codechef.com](https://www.codechef.com/wiki/tutorial-number-theory/)_

This writeup discusses few most important concepts in number theory that every programmer should ideally know. It is neither an introductory tutorial, nor any specific algorithms are discussed here. Rather, this writeup is intended to act as a reference. External references (mostly from Wikipedia and Wolfram) have been provided at many places for further details.

### 0\. The Peano axioms

The entire formalization of arithmetic is based on five fundamental axioms, called **Peano axioms**, which define properties of natural numbers. These axioms are -

(i) 0 is a natural number  
(ii) Every natural number has a successor, which is also a natural number  
(iii) 0 is not the successor of any natural number  
(iv) Different natural numbers have different successors  
(v) If a set contains the number 0 and it also contains the successor of every number in S, then S contains every natural number.

The fifth axiom is also popularly known as "principal of mathematical induction"

Being extremely basic, we would rarely need them directly, unless we want to prove every theorem in arithmetic from the first principles. But being the building blocks of arithmetic, these axioms are worth knowing.

### 1\. Fundamental Theorem of Arithmetic and the Division Algorithm

As the name rightly says, this theorem lies at the heart of all the concepts in number theory. The fundamental theorem of arithmetic states that any integer greater than 1 can be written as a product of prime numbers in a unique way (up to the ordering of prime factors in the product). For example, 18 = 2 X 32, 1755 = 33 X 5 X 13. This theorem plays very important role in almost every number theoretic algorithm, like [finding prime factors](http://www.thelearningpoint.net/home/mathematics/prime-factors), finding GCD, finding sum of divisors of a number etc to mention a few. Proving this theorem is easy - in fact, it emerges out as a corollary to the Euclid's first theorem (discussed below).

The division algorithm states that given two integers a,b (b != 0) there exist two unique integers q and r such that

a = bq + r, 0 <= r < b

q is typically called quotient, whereas r is called remainder. If r = 0, we say that b divides a, and denote it as b|a.

### 2\. Euclid's Theorems

The two important theorems, called "Euclid's first theorem (Or Euclid's lemma)" and "Euclid's second theorem (usually simply referred as "Euclid's theorem") are as follows:

First theorem: p | ab => p|a or p | b. A direct consequence of this is the fundamental theorem of arithmetic.   
Second theorem : There are infinitely many primes. There are many simple proofs for this.

While it is true that there are infinitely many primes, it should also be remembered that there are arbitarily large gap between prime numbers. In other words, it is always possible to get a sequence of n consecutive composite numbers, given n.

### 3\. GCD, LCM, Bezout's identity

The most common algorithm for finding the greatest common divisor of two numbers is the **Euclid's algorithm.** This is an extremely efficient algorithm, as the number of steps required in this algorithm is at most 5 times the number of digits of the smaller number. GCD is typically denoted using round brackets - (a,b) denotes the gcd of a and b. Similarly LCM is denoted using square brackets - [a,b] denotes the lcm of a and b.

The numbers a and b are called coprimes iff (a,b) = 1 , i.e. iff [a,b] = ab.

If gcd(a,b) = d then (a/d, b/d) = 1.

GCD and LCM are related by a very simple equation: (a,b) * [a,b] = ab. This gives a very fast way to calculate LCM of two numbers.

The bezout's identity states that if d = (a,b) then there always exist integers x and y such that ax+by = d. (Of course, the theory of linear diophantine equations assures existance of infinitely many solutions, if one exists). It is also worth noting that k=d is the smallest positive integer for which ax+by = k has a solution with integral x and y.

Given a,b, Finding x and y, such that ax+by = d is done by extended Euclid's algorithm, which can be implemented in recursive as well as iterative styles.

### 4\. Integer Factorization

The most commonly used algorithm for the integer factorization is the **Sieve of Eratosthenes**. It is sufficient to scan primes upto sqrt(N) while factorizing N. Also, if we need to factorize all numbers between 1 to N, this task can be done using a single run of this algorithm - For every integer k between 1 to N, we can maintain a single pair - the smallest prime that divides k, and its highest power , say (p,a). The remaining prime factors of k are then same as that of k/(pa).

### 5\. Linear Congruence Equations

The equations of the form ax ≡b (mod n) where (x is an unknown integer ) are called **linear congruences**. Such a congruence will have a solution if and only if there exists an integer x such that n | (ax-b), i.e. ax -b = ny for some integer y, or in other words ax + n(-y) = b. We already know from Bezout's identity that a linear diophantine equation like this will have a solution only if gcd of (a,n), say d, divides b. In such a case, let b = dd', a = da', n = dn', so we have:  
da'x + dn'(-y) = dd' where gcd(a',n') = 1  
Cancelling d throughout,   
a'x + n'(-y) = d'.  
since gcd of (a', n') = 1, now we can use Extended Euclid's algorithm to find the solution for a'x + n'(-y) = 1. and then multiply this solution by d' to get a solution for a'x + n'(-y) = d'.

Note that if ax ≡b (mod n) has a solution, then there is a unique solution mod (n/d). If this solution is denoted by x0, then there are exactly d solutions mod n, given by x0\+ kn/d where 0 <= k < d. The [tutorial on quadratic equations](https://www.codechef.com/wiki/tutorial-quadratic-equations) discusses this in details.

### 6\. Chinese Remainder Theorem

Typical problems of the form "Find a number which when divided by 2 leaves remainder 1, when divided by 3 leaves remainder 2, when divided by 7 leaves remainder 5" etc can be reformulated into a system of linear congruences and then can be solved using Chinese Remainder theorem. For example, the above problem can be expressed as a system of three linear congruences: "x ≡1 (mod 2), x ≡2 mod(3), x ≡5 mod (7)".

In general, a system of linear congruences:  
x ≡a1 (mod n1)  
x ≡a2 (mod n2)  
x ≡a3 (mod n3)  
....  
x ≡ak (mod nk)

where (ni,nj) = 1 for every ni != nj has a unique solution modulo n where n = n1n2n3...nk.

Let ci= n/ni for every i. Let di be the solution for the congruence cix = 1 (mod ni) such that 0 <= di < ni. (This solution can be found out using Extended Euclid's algorithm). Then the common solution to the above system of linear equations is given by   
c = a1c1d1 \+ a2c2d2 \+ ... + akckdk

A direct corollary of the Chinese Remainder theorem is as follows: Let n = p1a1 * p2a2 * .... * pkak be the prime factorization of n. Then, for any integers a and b, we have a = b (mod n) iff a = b (mod piai ) for each i.

The generalization of the Chinese Remainder Theorem, which discusses the case when the ni's are not necessarily pairwise coprime is as follows - The system of linear congruences

x ≡a1 (mod n1)  
x ≡a2 (mod n2)  
x ≡a3 (mod n3)  
....  
x ≡ak (mod nk)

has a solution iff gcd(ni,nj) divides (ai-aj) for every i != j. In such a case, there is a unique solution mod n, where n is the least common multiple of n1,n2...nk

### 7\. Quadratic Congruences

Given q and n, if the quation x2 ≡q (mod n) has a solution, then q is called **quadratic residue** modulo n. If this equation doesnot have a solution, then q is called "quadratic non residue" modulo n. For example, x2 ≡9 (mod 15) has a solution x = 12, hence 9 is a quadratic residue modulo 15. On the other hand, the equation x2 ≡11 (mod 15) has no solution, hence 11 is a quadratic non-residue modulo 15. In simpler terms, an integer q is a quadratic residue modulo n if a square can take the form (nk+q) for some positive integer n.

Finding whether a quadratic congruence having prime number modulus has a solution or not is somewhat easy: x2 ≡a (mod p) has a solution only if a(p-1)/2 = 1 (mod p). In such a case, the Shank-Tonelli algorithm can be used to get the solution.

### 8\. Euler Phi Function, divisor function, sum of divisors, Mobius function

Euler's** Phi function** (also known as totient function, denoted by φ) is a function on natural numbers that gives the count of positive integers coprime with the corresponding natural number. Thus, φ(8) = 4, φ(9) = 6 etc. Following properties are worth noting about this function:

a) If p is prime then φ(pk) = (p-1)pk-1   
b) φ function is multiplicative, i.e. if (a,b) = 1 then φ(ab) = φ(a)φ(b).   
c) The value φ(n) can be obtained by Euler's formula : Let n = p1a1 * p2a2 * .... * pkak be the prime factorization of n. Then

φ(n) = n * (1- 1/p1)) * (1- 1/p2)) * ... * (1- 1/pk))

d) Programmatically, if we want to find φ for 1 to n, then we can very well use the sieve algorithm along with the multiplicative property of φ. The central idea is this: if n is a prime, then φ(n) = n-1. Otherwise, if n is a power of a prime, say n= pk, then φ(n) = (p-1)pk-1. Otherwise, let n=pk*q for some prime p. Using multiplicative property, we have φ(n) = φ(pk)φ(q)

Two important properties of φ(n):

i. aφ(n) ≡1 (mod n) whenever (a,n) = 1. Specifically, for a prime p, if p doesnot divide a then ap-1 ≡1 (mod p). This specialization is also known as Fermat's little theorem.  
ii. Let d1, d2, ...dk be all divisors of n (including n). Then φ(d1) + φ(d2) + ... + φ(dk) = n  
For example: the divisors of 18 are 1,2,3,6,9 and 18. Observe that φ(1) + φ(2) + φ(3) + φ(6) + φ(9) + φ(18) = 1 + 1 + 2 + 2 + 6 + 6 = 18

The **divisior function**, denoted by d(n) gives the number of divisors of a natural number. For example, d(18) = 6. Similarly, the sum of divisors function, denoted by σ(n), gives the sum of divisors of n. Thus, σ(18) = 1+2+3+6+9+18 = 39. Following properties are worth nothing about these two functions:

a) If p is a prime, then d(p) = 2. Also, d(pk) = k+1, and σ(p) = p+1  
b) If n is a product of two distinct primes, say n = pq, then σ(n) = n+1+(p+q). Also observe that in this case, φ(n) = n+1-(p+q).  
c) In general, Let n = p1a1 * p2a2 * .... * pkak . Then d(n) = (a1+1) * (a2+1) * ... (ak + 1), and σ(n) is given by the following product:

σ(n) = ( (p1(a1+1) - 1) / (p1-1) ) * ( (p2(a2+1) - 1) / (p2-1) ) * ... * ( (pk(ak+1) - 1) / (pk-1) )

A number is called "perfect number" if σ(n) =2n. In other words, the sum of proper divisors of a perfect number equals the number itself.

The **mobius function**, µ(n) is defined over all positive integers as follows:  
µ(n) = 1 if n is square free (i.e. no prime-square divides n) and n has even number of distinct prime factors  
µ(n) = -1 if n is square free (i.e. no prime-square divides n) and n has off number of distinct prime factors  
µ(n) = 0 if n is not square free, i.e. when n is divisible by a square.

Mobius function is multiplicative, i.e. when a and b are coprime, µ(ab) = µ(a)*µ(b).

A useful formula to calculate Euler's totient function can be given in terms of mobius function: Let d1, d2, ...dk be all divisors of n. Then

φ(n) = (d1 * mu (n/d1) ) + (d2 * µ(n/d2) ) + .... + (dk * µ(n/dk) )

It can also be written as

φ(n) = (µ(d1) * (n/d1) ) + (µ(d2) * (n/d2) ) + .... + (µ(dk) * (n/dk) )

Java Implementation for computing phi[n] using sieve algorithm

[code]

//read/get n

int phi[] = new int[n+1];

for(int i=2; i <= n; i++) phi[i] = i; //phi[1] is 0

for(int i=2; i <= n; i++)

if( phi[i] == i )

for(int j=i; j <= n; j += i )

phi[j] = (phi[j]/i)*(i-1);

[/code]

### Factorials

Factorials are extremely important. A factorial of N = (N)*(N-1)*(N-2)*(N-3)...1. Factorials are used while computing nPr nCr. They quickly grow very large like [this](http://www.thelearningpoint.net/home/mathematics/factorial/factorial-157) and so they need extremely careful handling with large numbers, big integer representation etc.

This completes the discussion of basic number theory concepts. For those who are specifically interested in number theory, here are some books worth reading -

[An introduction to the theory of numbers:](http://www.amazon.com/Introduction-Theory-Numbers-Ivan-Niven/dp/0471625469) by Niven, Zukerman and Montgomery

There are some popular integer sequences. Some of them are based on recursive relations. The Master theorem is popularly used to understand the complexity and bounds with recurring relationships. Some popular integer relations are the [Fibonacci Series](http://www.thelearningpoint.net/home/mathematics/fibonacci-numbers), [Lusas Numbers](http://www.thelearningpoint.net/home/mathematics/lucas-numbers), [Stern Diatomic Numbers](http://www.thelearningpoint.net/home/mathematics/stern-diatomic-numbers), [Lazy Carter](http://www.thelearningpoint.net/home/mathematics/lazy-carter-numbers), [Padovan Numbers](http://www.thelearningpoint.net/home/mathematics/padovan-numbers) and polygonal numbers such as [Pentagonal Numbers](http://www.thelearningpoint.net/home/mathematics/pentagonal-numbers), [Hexagonal Numbers](http://www.thelearningpoint.net/home/mathematics/hexagonal-numbers).

[An introduction to the theory of numbers](http://www.amazon.com/Introduction-Theory-Numbers-Science-Publications/dp/0198531710): by Hardy and Wright

A tutorial on Mathematical Induction -a technique which if often used in proofs in discrete space
