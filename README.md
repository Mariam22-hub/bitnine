# Bitnine Assessment

## Development environment & Operating system

````
Compiler version: gcc.exe (x86_64-win32-sjlj-rev0, Built by MinGW-W64 project) 8.1.0
Operating system: Windows 10 pro
IDE: Visual studio code

````
### Contents

#### 1) Readme file

#### Note: The structure for both solutions is the same (enum, struct, and calculate)
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
a) The main solution ([Solution 1] (https://github.com/Mariam22-hub/bitnine/blob/main/question%201/q1.c)) treats the add/sub/mul/fib nodes as parent nodes (created by the makeParentNodes function, and the makeChildNodes function creates the left and right of each parent (which hold the values to be operated on) 

The calculate function is the same for both solutions, it uses recursion to calculate all left nodes of a parent together, then all right nodes, and eventually calculate the resulta together to obtain the final results

Notes:
1- ```` TypeTag globalType; ````
The globalType gets reassigned each time a new parent node is created to acommodate the needed type for the node. It gets re-assigned in the makefunc function to the type input, then it equates it to the node->type in the makeParentNode function

2- ````
Node* parentNodeArray[100]; // Array to store parent nodes
int count = 0;
    ````
This array is used to store all created parent nodes so that we can linearly search for the nodes in the nodeExists function. The search is used to check if an input node has already been created before or not. Because if it has, then we equate a child node with it.

The global variable count is used to index the nodes into the array, each time a node is added, it gets incremented. The index of each node is equal to the count at the time of adding it to the array

#### 3) Problem 2 folder
