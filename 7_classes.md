# Classes
## Defining a class
- similar to defining a struct
- use `class` key word

```cpp
class Triangle {
public: 
    double a, b, c;

    double perimeter() {
        return this->a + this->b + this->c;
    }
};
```

## Properties of a Class
- classes contains both data and functionality
- member data
- member functions

## Public Keyword
- `public` means that members can be accessed outside the class
- `a`, `b`, `c`, and `perimeter()` can be accessed outside of Trianlge definition

## This Keyword
- `this` is a pointer to the object which called the function
- `this->a` dereferences a in the object it resides

## Class in Memory
- member variables are stored in memory
- member functions are not stored in memory

## For Each Loop
```cpp
// these are the same loop written differently
for (int i = 0; i < tirangles.size(); i++) {
    Triangle t = triangles[i];
    cout << t.perimeter() << endl;
}

for (Triangle t : triangles) { // for Triangles t in triangles
    cout << t.perimeter();
}

for (auto t : triangles) { // auto automatically finds the type of t
    cout << t.perimeter();
}
```

## Constructors
- Used to initialize member data
- Names the same as the class
- Constuctor is automatically called when object is defined
- Constructors can have parameters
- A default constructor has no input perameters

```cpp
class Triangle {
public:
    double a, b, c;
    double perimeter() {/*computer perimeter*/}
    Triangle() {
        a = 0;
        b = 0;
        c = 0;
    }
}

int main() {
    // triangle t is created and it's constructor is called
    Triangle t; 
}
```

```cpp
class Triangle {
public:
    double a, b, c;
    Triangle(double a_in, double b_in, double c_in) {
        this->a = a_in;
        this->b = b_in;
        this->c = c_in;
    }
}

int main() {
    // both are the same
    // sets a = 3, b = 4, and c = 5

    Triangle t = Triangle(3, 4, 5); 
    Triangle t(3, 4, 5); // most common syntax
}
```

## Private Keyword
- `private` keyword specifies that only member variables can be accessed inside the class
- member variables are private by default
- generally, member variables should be private

```cpp
class Triangle {
private:
    double, a, b, c; // these can only be accessed by member functions
public:
    double perimeter() {
        return this->a + this->b + this->c;
    }
};

int main() {
    Triangle t;
    t.c = 9; // this will throw an error
}
```

## Checking for Invalid Constructors
- good practice to make sure your object is valid
```cpp
class Triangle {
private:
    double a, b, c;
    void check_invariants() {
        assert(0 < a && 0 < b && 0 < c);
        assert(a + b > c && a + c > b && b + c > a);
    }
public:
    Triangle(double a_in, double b_in, double c_in) {
        this->a = a_in;
        this->b = a_in;
        this->c = c_in;
        check_invariants();
    }
}
```

## Get and Set Functions
```cpp
class Triangle {
private:
    double a, b, c;
public:
    double get_a() {
        return a;
    }
    void set_a(double a_in) {
        this->a = a_in;
    }
};
```

## Class Abstraction Design
- classes allow us to group data and behavior together (encapsulation)
- classes allow us to 

## Classes in header files
- class should only contain interface
- this goes into `.hpp` file

```cpp
class Triangle {
private:
    double a, b, c;
public:
    Triangle(double a_in, double b_in, double c_in);
}
```

## Classes in cpp files
- class should contain 
- `::` is called the scope resolution operator
- needed so that the compiler knows which functions belong to class
- this sould go in a `.cpp` file
- you can now include the class in any other `.cpp` file
```cpp
Triangle::Triangle() { //constructor
    //implementation
}; 
```
