## Template Declaration

```cpp
template<typename T> // make a template and call the type T
class Set {
public:
    Set();
    void insert(T e);
    void remove(T e);
}

// for simplicity, I left out private member variables (use your imaginantion)

Set<int> set_ints; // creates a set of ints
Set<char> set_chars; // creates a set of chars
```

## Template Member Functions
- each function begins with `template <typename T>`
- add each method name must be in scope `Set<T>`

```cpp
// function definition outside of class in .cpp file
bool Set<T>::constains(T e) {
    return index_of(e) != -1;
}
```

## Include Guards

```cpp
#ifndef SET_H
#define SET_H

class Set {
    //...
};

#endif
```