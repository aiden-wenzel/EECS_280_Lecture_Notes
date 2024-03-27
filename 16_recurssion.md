## The Factorial Function

- Recall that `n! = n * (n-1) * (n-2) * ... * 1` if `n` isn't 1 or 0.

```cpp
// traditional implementation
int factorial(int n) {
    int result = 1;
    while (n > 0) {
        result *= n;
        n--;
    }
    return result;
}
```

- Additionally we can see that `n! = n * (n-1)!`.
- This is called a *recurrence relation* in math.
- A recursive function in cpp calls itself
```cpp
// recursive implementation
int factorial(int n) {
    if (n == 0 || n == 1) {
        return 1;
    }
    else {
        return n * factorial(n - 1);
    }
}
```

## Good Recurssion Practices
- A reurssive abstraction should have a **base case** and a **recursive case**
- **Base Case**: cases can be implemented without using recursion
- **Recursive Cases**: breaks the problem into subproblems that are similar to the problem

```cpp
// REQUIRES: end >= start
// MODIFIES: cout
// EFFECTS: Prints the numbers in [start, end) in order.
void print_numbers(int start, int end) {
    //base case
    if (start == end) {
        return;
    }

    // recursive case
    cout << start << endl;
    print_numbers(start + 1, end);
}
```

```cpp
// EFFECTS: Reverses the array starting at 'left' and ending at (and including) 'right'.
// 
void reverse_array(int* left, int* right) {
    if (left < right) {
        reverse_array(left + 1, right - 1);
        int temp = *left;
        *left = *right;
        *right = temp;
    }
}
```

## Tail Recursion
- The `reverse_array` function has O(n) time and O(n) space.

```cpp
// Since no other work is done after the reverse_array call, there is no need toretain the activation record of the caller, so it can be discraded for O(1) space complexity.
void reverse_array(int* left, int* right) {
    if (left < right) {
        int temp = *left;
        *left = *right;
        *right = temp;
        reverse_array(left + 1, right -1);
    }
}

```
- A function is **Tail Recrusive** if it is recursive, and all recursive calls are tail calls.

## Tree Recursion
- A function is **tree recursive** if a single invocation of the function can make more than one recursive call.
- Recusive call graphs could look something like a **binary tree**.

## Iteration vs. Recursion
- Itteration: divides a computation into individual discrete steps, and the combination of those form the solution.
- Recusion: expresses a computation in terms of smaller versions of the same problem.