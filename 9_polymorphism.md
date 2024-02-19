## Polymorphism
- Means "many forms"
- In coding, refers to a piece of code which behaves differenltly depending on context

## Polymorphism Types
- *ad hoc polymorphism*: function overloading
- *parametric polymorphism*: in the form of templates
- *subtype polymorphism*: allows derived-class object to be used where a base-class object is expected

## Function Overloading
- ability to use a single name to refer to many different functions in a single scope.

```cpp
class Base {
public: 
    void foo(int a);
    int foo(string b);
};

int main() {
    Base b;

    // compiler determines which functino to use
    b.foo(42);
    b.foo("test");
}
```

- functions can only be overloaded when defined in the same scope.
- functions must also have different function signatures

```cpp
class Derived : public Base {
public: 
    int foo(int a);
    double foo(double b);
};

int main() {
    Derived d;
    d.foo("test") // ERROR; foo which uses string is in the scope of Base.

}
```

## Subtype Polymorphism
- allows derived-class object to be used where base-class is expected
- need to use indirection

```cpp
int main() {
    Chicken chicken("Myrtle");
    Bird *ptr_bird = &chicken;
    ptr_bird->name; // Myrtle
}
```

## Static and Dynamic Binding
- allows us to pass derived-class object to a function which expects a base-class
```cpp
void all_talk(Bird* birds[], int length) {
    for (int i = 0; i < length; i++) {
        array[i]->talk();
    }
}

int main() {
    Chicken c1 = //;
    Duck d = //;
    Chicken c2 = //;
    Bird *array[] = {&c1, &d, &c2};
    all_talk(array, 3);
    // will print tweet 3 times since array[i]'s static type is Bird, while the dynamic type is Chicken when i==0.
}
```

```cpp
// using virtual tells the compiler to use the dynamic type of the reciever
class Bird {
    virtual void talk() const {
        cout << "tweet" << endl;
    }
};
```