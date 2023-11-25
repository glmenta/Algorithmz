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

### Sorting
```
O(NlogN)

Bubble Sort
fxn bubbleSort(nums) {
    for (let i = 0; i < nums.length; i++) {
        for (let j = 0; j < nums.length; j++) {
            if (nums[j] > nums[j + 1]) {
                let temp = nums[j];
                nums[j] = nums[j + 1]
                nums[j + 1] = temp;
            }
        }
    }
}

function insertionSort(arr) {
    // the `i` loop will iterate through every element of the array
    // we begin at i = 1, because we can consider the first element of the array as a
    // trivially sorted region of only one element
    // insertion sort allows us to insert new elements anywhere within the sorted region
    for (let i = 1; i < arr.length; i++) {
        // grab the first element of the unsorted region
        let currElement = arr[i];

        // the `j` loop will iterate left through the sorted region,
        // looking for a legal spot to insert currElement
        for (var j = i - 1; j >= 0 && currElement < arr[j]; j--) {
            // keep moving left while currElement is less than the j-th element

            arr[j + 1] = arr[j];
            // the line above will move the j-th element to the right,
            // leaving a gap to potentially insert currElement
        }
        // insert currElement into that gap
        arr[j + 1] = currElement;
    }
    return arr;
}

Merge Sort
"Divide and Conquer"
function merge(array1, array2) {
    let merged = [];

    // keep running while either array still contains elements
    while (array1.length || array2.length) {
        // if array1 is nonempty, take its the first element as ele1
        // otherwise array1 is empty, so take Infinity as ele1
        let ele1 = array1.length ? array1[0] : Infinity;

        // do the same for array2, ele2
        let ele2 = array2.length ? array2[0] : Infinity;

        let next;
        // remove the smaller of the eles from it's array
        if (ele1 < ele2) {
            next = array1.shift();
        } else {
            next = array2.shift();
        }

        // and add that ele to the new array
        merged.push(next);
    }

    return merged;
}

function mergeSort(array) {
    if (array.length <= 1) {
        return array;
    }

    let midIdx = Math.floor(array.length / 2);
    let leftHalf = array.slice(0, midIdx);
    let rightHalf = array.slice(midIdx);

    let sortedLeft = mergeSort(leftHalf);
    let sortedRight = mergeSort(rightHalf);

    return merge(sortedLeft, sortedRight);
}

Quick Sort => Pivot
"Divide and Conquer"
function quickSort(array) {
    if (array.length <= 1) {
        return array;
    }

    let pivot = array.shift();
    let left = array.filter(el => el < pivot);
    let right = array.filter(el => el >= pivot);

    let leftSorted = quickSort(left);
    let rightSorted = quickSort(right);

    return leftSorted.concat([pivot]).concat(rightSorted);
}
```

### When to use each sort
```
Insertion => best if few inputs/data and items are mostly sorted; it uses very little space;
Bubble => only educational; sucks for implementing it in real life application
Selection => only educational; same as bubble sort

Merge => since it is nlogN; it is decent for most cases; stable; space complexity a bit worse than quicksort
Quicksort => best for space complexity (not care about worst case) and also usually fastest; only downside if the list is already mostly sorted
            => terrible pivot => even worse than merge sort; if this is the case, pick merge/insertion probably

TLDR: Merge/Quicksort/Insertion all used in most cases depending on situation

Is it possible to beat O(n log N)?
=> mathematically, it is impossible b/c o(N log N) sorts by comparison; all of the sorts above are thru that concept

=> However, we can bypass this scenario thru different sorts that are non-comparison
    => Counting sort, Radix Sort
    => These ONLY work with numbers though
```
