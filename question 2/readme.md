#### Method 1 (Using recursion):
````
int fib1(int n)
{
    if (n <= 2)
        return n;
    return fib1(n - 2) + fib1(n - 3);
}
````
##### Advantages
- Simplicity: The code is straightforward and easy to understand, as it directly follows the mathematical definition of the Fibonacci sequence.
- Readability: The recursive function mirrors the recursive nature of the Fibonacci sequence, making the code readable and intuitive.
- Conciseness: The code is relatively short, which can be advantageous in terms of code maintenance and debugging. 
- It's a perfect demonstration of how recursion works, for newbies
- Debugging: Recursive code can be harder to debug and understand than non-recursive code, especially if the function has multiple base cases or if the recursion is nested.

##### Disadvantages
- Exponential Time Complexity: The main disadvantage of this approach is the exponential time complexity. The function makes multiple recursive calls, resulting in redundant computations and a high number of function calls. As a result, the time complexity is approximately O(2^n), making it highly inefficient for larger values of n.
- Redundant Computations: The function recalculates the Fibonacci values for the same input multiple times. For example, fib1(n-2) and fib1(n-3) both calculate the Fibonacci value for n-3, leading to redundant computations and performance overhead.
- Stack Overflow: For large values of n, the recursive function may exceed the stack's capacity, causing a stack overflow and program termination.
- Lack of Memoization: The code does not incorporate any form of memoization, meaning it does not store intermediate Fibonacci values for reuse. This further contributes to redundant computations and worsens the time complexity.
- Slow for large numbers: Calculating the Fibonacci series using recursion can be slower than using an iterative approach for large numbers, as the function has to be called multiple times to calculate each term.

#### Method 2 (Using Dynamic Programming):
````
int fib2(int n)
{
    int f[n+2];
    int i;

    f[0] = 0;
    f[1] = 1;
    f[2] = 2;

    for (i = 3; i <= n; i++)
    {
        f[i] = f[i-2] + f[i-3];
    }

    return f[n];
}
````
##### Advantages
- This demonstrates the importance of choosing an efficient way to tackle a problem and also a good exercise for it (particularly when the problem has a recursive nature requiring the use of previously computed values).
- Improved Time Complexity: The iterative approach with dynamic programming significantly improves the time complexity compared to the recursive approach. The time complexity of this code is O(n), as it iterates from 3 to n to calculate the Fibonacci numbers, avoiding redundant computations.
- The code uses an array f to store Fibonacci numbers. By storing previously computed values, it eliminates redundant calculations and ensures that each Fibonacci number is computed only once.

##### Disadvantages
- Avoids Stack Overflow: Since the code uses an iterative approach instead of recursion, it avoids the risk of stack overflow for large values of n.
- It takes a lot of memory to store the calculated result of every subproblem without ensuring if the stored value will be utilized or not.
- Many times, output value gets stored and never gets utilized in the next subproblems while execution. It leads to unnecessary memory utilization.

#### Method 3 (Using Optimized Space (aka iterative)):
````
int fib3(int n)
{
    int a = 0, b = 1, c = 2, d, i;

    if (n<=2) return n;

    for (i = 3; i <= n; i++)
    {
        d = a + b;
        a = b;
        b = c;
        c = d;
    }
    return d;
}
````
##### Advantages
- Simplicity: The code is straightforward and easy to understand.
- Efficiency: The code has a time complexity of O(n) since it iterates from 3 to n and calculates Fibonacci numbers iteratively without redundant computations.
- No Stack Overflow: The iterative nature of the code avoids potential issues related to stack overflow, which can occur in recursive approaches when dealing with large values of n.
- Space Efficiency: The fib3 approach uses a constant amount of additional space regardless of the input size. It only requires a few integer variables (a, b, c, d, and i) to perform the calculations, resulting in efficient memory usage.

##### Disadvantages
- Lack of Reusability: This code directly calculates the nth Fibonacci number and doesn't store intermediate values for potential reuse, unlike the dynamic programming approaches.
- If you need to compute multiple Fibonacci numbers or reuse intermediate results, this approach may not be optimal. Each time you need to calculate a different Fibonacci number, the loop needs to start from the beginning.
