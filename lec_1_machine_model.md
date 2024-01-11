## Runtime - Terminology

- Object: value stored in memory
- Address: location where an object is stored

## Object Lifetime

- Static: lives for the whole program (managed by compiler)
- Local: lives during the exeution of local block (managed by compiler)
- Dynamic: you control the lifetime

## Value Semantics

- `=` operator initializes, assigns, or copies values

```cpp
int x = 42; // initialize value of x to 42
int y = 99; // initialize value of y to 99
x = y; // copy value of y into x
some_function(x); // pass the value in x to some_function
```

## Reference Semantics
- In C++ you can declare a reference (alias) to a variable

```cpp
int x = 42; // initialize value of x to 42
int z = 3; // initialize value of z to 3
int &y = x; // declares reference variable 'y' which refers to variable 'x'
x = 24; // assigns 24 to object named x/y
y = z; // Does NOT re-bind y to a different object
cout << x;
```
- `x` and `y` share the same memory location.
- when the value of `y` changes, the value of `x` will also change

## Pass by Value

```cpp
void swap(int x, int y) {
    int temp = x;
    x = y;
    y = temp;
}

int main() {
    int a = 2; // a initialized to 2
    int b = 7; // b initialized to 7
    void swap(a, b); // COPIES of a and b are passed into function
}
```

## Pass by Reference
```cpp
void swap(int &x, int &y) {
    int temp = x;
    x = y;
    y = temp;
}

int main() {
    int a = 2; // a initialized to 2
    int b = 7; // b initialized to 7
    void swap(a, b); //
}
```
- x and y are now references to the values passed into the functions
