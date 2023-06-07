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
*This folder contains 2 solutions for question 1*

<br>

**a)** [The Main solution](https://github.com/Mariam22-hub/bitnine/blob/main/question%201/q1.c) treats the add/sub/mul/fib nodes as parent nodes (created by the makeParentNodes function, and the makeChildNodes function creates the left and right of each parent (which hold the values to be operated on) 

The calculate function is the same for both solutions, it uses recursion to calculate all left nodes of a parent together, then all right nodes, and eventually calculate the resulta together to obtain the final results

#### Notes: 

1- 
```` 
TypeTag globalType; 
````
The globalType gets reassigned each time a new parent node is created to acommodate the needed type for the node. It gets re-assigned in the makefunc function to the type input, then it equates it to the node->type in the makeParentNode function

2-
````
Node* parentNodeArray[100]; // Array to store parent nodes
int count = 0;
````
This array is used to store all created parent nodes so that we can linearly search for the nodes in the nodeExists function. The search is used to check if an input node has already been created before or not. Because if it has, then we equate a child node with it.

The global variable count is used to index the nodes into the array, each time a node is added, it gets incremented. The index of each node is equal to the count at the time of adding it to the array
<br>

**b)**  The [Second Solution](https://github.com/Mariam22-hub/bitnine/blob/main/question%201/anotherSolution_q1.c) contains the same logic. The difference is this utilizes the factory design pattern. It's implemented using functions to pointers where each operation (add/sub/...) has it's own function to create its objects from. I thought this problem is perfect for a design pattern such as this, but C is not an object-oriented language. So after reading some articles, i found a way to get the same functionality without using OOP.


#### Notes:

1- 
````
Node* (*makeFunc(TypeTag type))(void*, void*)
{
    switch(type)
    {
        case ADD : return &add; break;
        case MUL : return &multiply; break;
        case SUB : return &subtract; break;
        case FIB : return &fib; break;
    }
}
````
This is the factory function, each case would call the appropriate function, in which it builds the parent nodes

2- 
````
Node* sideOperation (void* num1, void* num2, Node* parentNode){

//    equate the left and right nodes of the parent created with these input nodes, if they already exist
    if (nodeExists(num1)){
        parentNode->left = num1;
    }
    else {
        parentNode->left = makeChildNodes((int) num1);
    }

    if (nodeExists(num2)){
        parentNode->right = num2;
    }
    else {
        parentNode->right = makeChildNodes((int) num2);
    }

    return parentNode;
}
````
This operation handles the special case of the sub node (which takes 2 nodes instead of 2 numbers). Its the same logic as the makeParentNode function in the 1st solution, with the exception of not creating the parent nodes themselves inside of it 

#### 3) [Problem 2 folder](https://github.com/Mariam22-hub/bitnine/tree/main/question%202)







