## New and Initialization
- `new` keyword indicates to the compiler to allocate memory for a specific object
- `int* ptr = new int;` tells the compiler to allocate memory for an integer on the heap, and return the address of that memory.

## The Heap
- Separte region for memory used with dynamic storage.
- `new` allocates memory to the heap
- `delete` deallocates memory from the heap

## Problems with Dynamic Memory
- Dangling Pointers
```cpp
int foo() {
    int* p = new int(3);
    // do something with p
    delete p;
    cout << *p; // the stuff in p is now deleted
}
```

- Double delete
```cpp
int foo() {
    int *p = new int;
    //do something with p
    delete p;
    delete p; // p is already deleted
}
```

- Bad delete
```cpp
int foo() {
    int i = 0; // local variable
    int p* = &i;

    delete i; // i is not on the heap so you can't delete it
}
```

- Memory Leaks
```cpp
int foo() {
    int *p1 = new int(1);
    int *p2 = new int(2);
    p1 = p2; // nothing is pointing to 1 now! Can't deallocate the memory for 1  now.
}
```

## Pros of Dynamic Variables
- You want to manage the lifetime of the variable manually

- Many parts of the code refer to an object, but only want one copy in memory

- Large objects (Stack space is limited)

## Dynamic Arrays
- Normally the size of an array must be known at **compile time**.

- With dynamic memory, the size of dynamically allocated array can be determined at **runtime**.

```cpp 
int main() {
    cout << "How many elements?";
    int howMany;
    cin >> howMany;
    int *arrPtr = new int[howMany];

    // use this syntax to delete a dynamically allocated array
    delete[] arrPtr;
}
```

## Destructors
- the opposite of constructors in classes
- memory leaks will happen when an a class which dynamically allocates memory is not destroyed

- declare a destructor which calles `delete` when the object falls out of scope.
- to declare a destructor, write `~class_name()` in the public area of the class body
```cpp
class_name()::~class_name() {
    delete /*<Dynamically allocated memory>*/;
}
```
- Typically, constructors call `new` and destructors call `delete`.



