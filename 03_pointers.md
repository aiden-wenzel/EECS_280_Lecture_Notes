## Hexidecimal Numbers
- Base 16 counting system
- Hexidecimal Digits: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, a, b, c, d, e, f
- Example: `0x4f9da938` = 0100 1111 1001 1101 1010 1001 0011 1000
- `0x` indicates the following number is hexidecimal.

## C++ Memory Model - 64 bit
- `0x0000 0000 0000 0000`: OS Area (REstricted Access RW)
- text and data (read only memory)
- heap
- ~
- Stack
- `0xffff ffff ffff ffff`: OS Area (Restricted Access RW)

## Variables in Memory
```cpp
int i = 12;
cout << &i; //prints 0x007abd0c to console
```

- Let's say the address of `i` = `0x007abd0c`
- `&` is the address of operator.
- This is different than reference semantics.

## Pointers
**Pointer**: *A variable which holds the address of a value.*

```cpp
int i = 12;
int *a = &i;
int **b = &a;
```
- `int *a = &i`: *the variable `a` can hold the address of `i`.*
- `a` is an **integer pointer**.
- `int **b = &a`: *the variable `b` is a pointer to another pointer `a`.*
- `b` is an *integer pointer pointer*

## Dereferencing a Pointer
```cpp
int x = 7; // declare a variable x with value of 7
int *ptr = &x; // declare an int pointer which holds the address of x
int j = *ptr; // declare a new variable which holds the value where ptr is pointing to 
*ptr = 70; // assign the value in the memory address of pointer to be 70
```
- When dereferencing pointers, make sure that pointers always point to valid memory.
- `*` is used to access the value pointed to by a pointer.

## Null Pointer
- Initialize all pointers which aren't assinged a memory addres to `nullptr` to avoid accessing random memory.
- Dereferencing unassigned pointers results undefined behavior.

```cpp
int *p = nullptr;
```

## Pointers in Functions
```cpp
// adds 1 to whatever x points to
void addOne(int *x) {
    *x += 1; 
    // assigns the value inside the memory address x to *x + 1
}

int main() {
    int z = 1;
    int *ptr = &z; // ptr "points to" z

    *ptr += 1; // adds 1 to z, without using the name z

    addOne(&z); // adds one to z
    addOne(ptr); // same thing
}
```







