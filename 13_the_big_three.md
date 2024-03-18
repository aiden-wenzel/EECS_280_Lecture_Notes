## Copy Constructor
- constructor which makes a copy of an object by passing in an already existing object.
- make sure to pass by reference; else, the copy constructor will be called recursively
- making a copy using copy constructor is called a deep copy
```cpp
class student {
    int rno;
    char name[50];
    double fee;
 
public:
    student(int, char[], double);
    
    student(student& t) {
        rno = t.rno;
        strcpy(name, t.name);
    }
```

## The Big 3
- if you have a class which allocates dynamic memory,
- i. Create a destructor
- ii. Create a copy constructor
- iii. Overload the `=` operator
