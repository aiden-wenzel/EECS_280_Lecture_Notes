## Static Keyword for Member Variables
- `static` keyword for member variables specifies a variable which is only declared once
- All instances of the class share this member variable
- Allows the variable to live throughout the whole program
- Lives in the scope in of the class (more organized than global scope)

```cpp
class Set {
public:

private:
    static const int CAPACITY = 100;
    int elts[CAPACITY];
    int elts_size;
}

Set::CAPACITY; // this is valid since it is static!
```

## size_t type
- `size_t` is a spcial usinged integer type (not negative)
- Many container ADTs use size_t.

```cpp
class Set {
public:
    size_t size() const; // gets size
private:
    size_t elts_size; // this is good since elts_size can't be negative now
}
```