# Bitnine Assessment

## Development environment & Operating system

````
Compiler version: gcc.exe (x86_64-win32-sjlj-rev0, Built by MinGW-W64 project) 8.1.0
Operating system: Windows 10 pro
IDE: Visual studio code

````
### Contents

#### 1) Readme file

#### Note: The structure for both solutions is the same
````
typedef enum {
    ADD, SUB, MUL, FIB, NUM
} TypeTag;


typedef struct Node {
    TypeTag type;

    int value;
    int index;

    struct Node *left;
    struct Node *right;
} Node;

````

#### 2) [Problem 1 folder](https://github.com/Mariam22-hub/bitnine/tree/main/question%201)
This folder contains 2 solutions for question 1
The main solution ([Solution 1] (https://github.com/Mariam22-hub/bitnine/blob/main/question%201/q1.c) treats the add/sub/mul/fib nodes as parent nodes (created by the makeParentNodes function, and the makeChildNodes function creates the left and right of each parent (which hold the values to be operated on) 

#### 3) Problem 2 folder
