## Properties of Arrays
- Fixed size
- Elements are the same type.
- Elements are stored next to each other in memeory.
- Contiguous memory
- Constant time random access (takes the same amount of time to access arr[1] as arr[500])

## Declaring Array
```cpp
int arr[4] = {1, 2, 3, 4};
```
## Indexing out of Bounds
- Indexing outside the array will return a random value in memory
- No error or warning will be printed

```cpp
int array[5] = {1, 2, 3, 4, 5};
int access_index = 5

assert(access_index < 5); // add this to prove that you don't index out of bounds

cout << array[5]; //BAD! Returns some random integer in memory with no error!
```

## Getting the Size of an Array
- `sizeof(some_array)` returns the space the array takes up in ***BYTES***.

```cpp
int array[5] = {1, 2, 3, 4, 5};
cout << sizeof(array) // prints 20 because array of 5 integer values takes up 20 bytes
```

## Calling raw array
- Calling an array will be converted into a pointer which points to the first element in the array.

```cpp
int array[3] = {1, 2, 3};
cout << array; //prints the memory address where array starts
```

```cpp
int array[4] = {1, 2, 3};
array[2]; 
```
How the compiler interprets `array[2]`: array turns into a pointer which points to `array[0]`. Then, it is offset by 2 so that it points to the 3rd element of the array.

This is why the first element of most arrays, lists, vectors, ect... start at index 0!

## Array Decay

### Consequence 1
```cpp
int arr1[4] = {1, 2, 3, 4};
int arr2[4] = {5, 6, 7, 8};

arr2 = arr1; //ERROR: Type mismatch. arr2 is still an array while arr1 turns into an int pointer!
```

### Consequence 2
```cpp
int i = 3;
int arr[4] = {1, 2, 3, 4};
int *aptr = arr;

cout << sizeof(i); // 4 bc int are 4 bytes
cout << sizeof(arr); //16 bc 4 * 4 = 16 since arr is still an array
cout << sizeof(aptr);> // 8 bc a pointer, which is a hexidecimal address of 8 btyes
```

## Array Traversal by Pointer
- You can traverse an array using pointers instead of by index.
- This is cool but adds no other functionality.
- Some code is written like this so it's nice to know.

```cpp
int const SIZE = 5;
int arr[SIZE] = {1, 2, 3, 4, 5};

int *end = arr + size; // stores the end memory address in the variable end

// start at &arr[0]; while the ptr < &arr[4]; add one memory address to ptr
for (int *ptr = arr; ptr < end; ptr++) {
    cout << *ptr << endl;
}
```

## 

