## Stack
- data structure
- **Push**: *Add to the top of the stack.*
- **Pop**: *Remove from the top of the stack.*

## The Call Stack
- When a function is called, data for the execution is stored as an activtion record.
- Activation records are **pushed** on the call stack.

**Example:**
```cpp
int add1(int x) {
    x = x + 1;
    return x;
}

int add2(int x) {
    x = add1(x);
    x = add1(x);
    return x;
}

int main() {
    int result = 0;
    result = add1(result);
    result = add2(result);
    cout << result; // 3
}
```
Call Stack at `result = add2(result)`:
1. `add1()` *This will get called 2 **separate** times.*
2. `add2()`
3. `main()`

- `main()` has already been called
- `add2()` pushed to stack
- `add1()` pushed to stack
- first `add1()` poped from stack
- second `add1()` pushed to stack
- second `add1()` poped from stack
- `add2()` poped from stack
- `main()` poped from stack

## Function Call Process
1. **Evaluate** the **arguments** to the function.
2. Make a **new** and **unique** activate record for the **called** function.
3. **Pause** the **calling** function.
4. **Run** the **called** function.
5. **Start** the **calling** function where it left off.
6. **Pop** the **activation record** of the **called** function.

## Interfaces vs. Implementation vs. Client
- **Interface:** *Specifies what something does.*
- **Implementation:** *Specifies how it works.*
- **Client:** *Something that uses functionality.*

## How `#include` Works
- `#include "example.h"` goes to `example.h` and copies the text into `main.cpp`.
- We don't include `stats.cpp` because that would copy a lot of text into `main.cpp`.

## Specification Comments (RMEs)
- A comment that specifies the interface for a function.
- `//REQUIRES:` Specifies prerequisites for the function to make sense.
- `//MODIFIES:` Explains what the function modifies.
- `//EFFECTS: ` Explains what the function does.

**Example:**

```cpp
// REQUIRES: No requirements. If vector is empty, then loop never starts. No crashes.

// MODIFIES: vector<int> v

// EFFECTS: Changes each element in v to be the element divided by the size of the vector.

void mystery(vector<int> &v) {
    for (int i = 0; i < v.size(); i++) {
        v[i] = v[i] / v.size();
    }
}
```

## Properites of Procedural Abstraction

- **Local**: *The implementation of an abstraction can be understood without examining any other abstraction implementation.*
- **Substitutable:** *Changing the function algorithm should not change the way the abstraction is used.*

## Testing

- **Unit Testing:** *Make sure one piece works at a time.*
- **System Testing:** *Test the entire project.*
- **Regression testing:** *Automatically run all unit and system tests after a code change.*
- `assert()`: *Throws an error if expression in argument is false. Make sure to add* `#include <cassert>`.