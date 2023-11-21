### Algorithm Notes

```
    Data Structures + Algorithms => Programs
    Class {} + fxn() => Programs

    Main Types To Focus On:

    Sorting
    Dynamic Programming
    BFS + DFS (Search)
    Recursion
```

### Recursion (Not Technically an algorithm)
```
=> More of a concept instead of an algorithm;

=> Define something inside of itself;

=> Anything that you can do with recursion, CAN be done iteratively (for loop, etc.) and vice versa
    -There are pros and cons to both approaches:
    Pros: DRY and Readable
    Cons: Large Stack

=> WHEN TO USE RECURSION:
    => BFS and DFS is super good to use recursion
    => Everytime we use a tree or conert something into a tree, consider recursion
    => Divide a big problem into smaller subproblems => identical in nature in terms of calculations => solutions for each subproblem are combined to solve the big problem
    => DIVIDE AND CONQUER

=> Example:
    Recursion function calls itself:

    fxn inception() {
        inception();
    }

    => when inception runs, it calls itself again over and over again;
    => Note that this is a stack overflow; solved using a base case

=> Great for repeated sub tasks

=> Anatomy:

    1. Base Case
    2. Recursive Case
    3. Get closer and closer to base case
    4. return when needed and usually there are two returns

    steps:
    => check base case => recursive call => repeat => if base case is hit => return inside base case => pops fxns out of the stack

    let counter = 0
    fxn inception() {
        if (counter > 3) return 'done!'
        counter++
        return inception();
    }

    This is how the returns look like:
    inception(inception(inception(inception('done!'))))
    inception(inception(inception('done!')))
    inception(inception('done!'))
    inception('done!')
    'done!'

    And this is how the counter is:
    0 => 1 => 2 => 3 => 4 (hit base case)
```

### Recursion Application
```
Factorial => n!
5! = 5 x 4 x 3 x 2 x 1
5! = 5 x 4!
5! = 5 x 4 x 3!
5! = 5 x 4 x 3 x 2!
5! = 5 x 4 x 3 x 2 x 1

fxn findFactorialRecursive(num) {
    if (num === 2) return 2
    return num * findFactorialRecursive(num - 1)
}

fxn findFactorialIterative(num) {
    let ans = 1;
    if (num === 2) ans = 2
    for (let i = 2; i <= num; i++) {
        ans = ans x i
    }
    return ans
}

Fibonacci => 0,1,1,2,3,5...

fxn fibIterative(n) {
    let arr = [0, 1]
    for (let i = 2; i < n + 1; i++) {
        //sum prev two nums and push to arr
        arr.push(arr[i-2] arr[i-1])
    }
    return arr[n]
}

fxn fibRecursive(n) { //O(2^n)
    if (n < 2) return n
    return fibRecursive(n - 1) + fibRecursive(n - 2)
}
```
