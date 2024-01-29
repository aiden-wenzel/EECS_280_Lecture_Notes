## Constant Keyword
- `const` keyword forbids re-assignment.
- Must initialze a valriable with a value.
- Example: `const int x = 3; // x can't be reassigned later`

## Constant Pointers
```cpp
int a = 10;
int b = 1;
const *int ptr_a = &a; // * is on the left of int
*p = 12; // you can change the value at the address of a
ptr_a = &b; // you can't change where ptr_a points
```

## Pointer to a Constant
```cpp
int a = 10;
int b = 1;
const int* ptr_a = &a; // * is on the right of int
p = &b; //you can change where ptr_a points
*p = 12; //you can't change the value of int inside memory address p
```

## Structs
- compound type
- can hold multiple values of different types

### Assignment
```cpp
struct Pair {
    double value;
    int count;
}
```

### Initialization
```cpp
int main() {
    Pair p; // p.value and p.count is undefined
    p.value = 5; // p.value is now 5
    p.count = 12; // p.count is now 12
}
```

```cpp
int main() {
    Pair p = {5, 12}; // how to initialize all properties at once
}
```

### Reassignment
```cpp
Pair p1 = {5, 12};
Pair p2 = p1; // assigns p2 to have the same values as p2
```

## Structs and Functions
- You can pass structs into functions
```cpp 
double moreFrequent(Pair p1, Pair p2) {
    if (p1.count > p2.count) {
        return p1.value;
    }
    else {
        return p2.value;
    }
}
```

## Struct Pointers
- Pass by reference can be expensive using large structs.
- Instead, pass by reference or use a **pointer**.

```cpp
double moreFrequenct(Pair* p1, Pair* p2) {
    (*p1).count; // method one to dereference pointer and access property
    p1->count; // same thing
}
```

## Data Type Abstraction
- Let's represent a triangle data type
- we store it in a header file with the `.hpp` extension

```cpp
struct Triangle {
    double side1;
    double side2;
    double side3;
}
```

