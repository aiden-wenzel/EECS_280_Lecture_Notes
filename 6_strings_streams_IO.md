# Input and Output Stream

## Cin and Cout
- stands for console input and console output
- arrows point into the direction of where data is flowing
- whenever cin is reached, program waits for user input

```cpp
cin >> word; // data flows from cin to word
cout << "Hello"; // data flows from string to cout

// this loop will stop when "end of file" character is read.
// to type this at the cnsole, use ctrl+d
string word;
while (cin >> word;) {
    cout << "word = " << word << endl; 
}
```

## Input Redirection
- `./words.exe < words.in` means to take inputs from words.in instead of user input.

## Converting Strings to Integers
- You can convert strings such as `"2"`, into an equivalent integer type.

```cpp
#include <string>

//EFFECTS: parses s as a number and returns its int value
int stoi(const string &s);

const string number = "2";
int number_converted = stoi(&number); // 2 is now an int
```

## File I/O with Streams
- we can read and write to files using ifstream and ofstream objects from the `<fstream>` library.

## Input File Stream
- Read strings from a text file
```cpp
#include <fstream> //File IO Stream Lib

string filename = "hello.txt"; 
ifstream fin; // create an input file stream object called fin
fin.open(filename); // open input stream from "hello.txt"

// check to make sure that fin is open
if (!fin.is_open()) {
    cout << "openfailed" << endl;
    return 1;
}

string word; 
fin >> word; // store word in "hello.txt" into variable called word

fin.close; // make sure to close file because of limited memory
```

## Output File Stream
- Write strings to a text file

```cpp
#include <fstream>

int main() {

    const int SIZE = 4;
    int data[SIZE] = {1, 2, 3, 4};
    string filename = "output.txt";
    
    ofstream fout; // create output file stream called fout
    fout.open(filename); // output to output.txt

    if (!fout.is_open()) {
        cout << "open failed" << endl;
    }

    for (int i = 0; i < SIZE; i++) {
        fout << data[i] << " "; 
    } // will print to output.txt: 1 2 3 4

    fout.close(); // always close output stream when done
}
```

# C++ Streams

