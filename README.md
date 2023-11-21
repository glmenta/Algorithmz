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
