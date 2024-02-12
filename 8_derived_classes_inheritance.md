## Derived Classes
- Idea: factor out common features from multiple classes into another class.
- We could represent a Car, Motorcycle, Boat, or a Bicycle

## Inheritance
- You can repesent a relationship between two c++ classes which extends a base classes functionality.
- Child classes inherit from parent classes.

```cpp
class Bicycle : public Vehicle {
    // Bicycle has all the member variables and member functions as the Vehicle class
    // "Bicylce inherits from Vehicle"
private: 
    // Bicylce now has member variables of vehicle as well as type
    string type;
public: 
    Bicycle(); // default constructor for a bike
    Bicycle(string color_in int year_in ...); // another constructor
    string get_type(); // get type for a bike
};
```

## Derived Class Constructors
- Constructors are **not** inherited
- You must define another constructor
- When a an object is initialized, the parent constructor is called first, then the child constructor is called second

```cpp
// bike.hpp
class Bicycle : public Vehicle {
    Bicycle();
}
``` 

## Protected Members
- `protected` keyword allows child classes to access parent member variables directly (only inside class definitions).
```cpp
class Vehicle {
public:
// stuff
protected:
int num_wheels;
}

class Bicycle : public Vehicle {
    // you can access num_wheels directly
}
```


## Enumerated Types
```cpp
// this is a new type called bicycletype
enum Bicycletype {
    MOUNTAIN, // 0
    ROAD, // 1
    ELECTRIC, // 2
    RACING // 3
};

int main() {
    Bicycletype a = ROAD;
}
```






