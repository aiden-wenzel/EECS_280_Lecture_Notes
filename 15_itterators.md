## Iterators
- We can't itterate through the list from outside the class
- `Node` and `first` are private member variables
- Instead, itterate using a custom itterator class
```cpp
List<int> list;

for (Iterator it = list.begin(); it != list.end(); it++) {
    cout << *it << endl;
}
```

## Operation Requirements
- We must provide the following operators for the itterator class
- `*` Dereference returns the element the itterator is pointing to by reference
- `++` Increment moves the iterator to point to the next element
- `==` and `!=` Equality operators return true or false if the itterators are different

## Method Requirements 
- `begin()` returns an iterator to the start of the list
- `end()` retuns a position that is past the ned of the list

```cpp
// this should be defined under public: in the list class
template <typename T>
class Iterator {
public:
    T& operator*() const;

    Iterator& operator++();

    bool operator==(Iterator rhs) const;

    bool operator!=(Iterator rhs) const;

private:
    Node* node_ptr; // points to the current node
}
```

## Dereference Operator

```cpp
template <typename T>
T& List<T>::Iterator::operator*() const {
    assert(node_ptr); // check that this isn't past the end (nullptr)
    return this->node_ptr->datum;
}
```

## Incremenet Operator

```cpp
template <typename T>
typename List<T>::Iterator& List<T>::Iterator::operator++() {
    assert(node_ptr); // check that this isn't past the end (nullptr)
    node_ptr = node_ptr->next;
    return *this;
}
```

## Equivalence Operator

```cpp
template <typename T>
bool List<T>::Iterator::operator==(Iterator rhs) const {
    return node_ptr == rhs.node_ptr;
}

template <typename T>
bool List<T>::Iterator::operator==(Iterator rhs) const {
    return node_ptr != rhs.node_ptr;
}
```

## Itterator Constructor
```cpp
class Iterator {
public:
    Iterator() {
        this->node_ptr = nullptr;
    }
private:
    Iterator(Node* node_ptr_in) {
        this->node_ptr = node_ptr_in;
    }
}
```