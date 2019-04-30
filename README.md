# DistNN

##  Usage

```
cd src
make
./main
```

## Code Description

**/layers/layers.cu/h** : This file implements a basic abstraction of a layer in a neural network. It has a class Layer which is responsible for storing x,y,b and their corresponding derivatives. It also implements the relu activation, backprop, addtion kernel and other operations that are usually performed on a layer.

**/utils/matrix.cu/h** : This file implements a normal matrix class to ease the allocation of GPU memory, matrix multiplication and moving of data between cpu and gpu.


## Distributed NN

- 0-(#nodes-1) in the cluster
- input node is at rank 0
- we try to divide the amount of weights, and not layers, evenly among the nodes.
- each layer store the rank on which it is actually present

int my_node;
int is_next_on_my_node; // -1 -> doesn't exist; 1 -> on the same node; 0 -> on different node , which is my_node + 1
int is_previous_on_my_node;  // -1 -> doesn't exist; 1 -> on the same node; 0 -> on different node , which is my_node 


## communication

n-1th node: x
n+1th node: y

x -> x`
g` <- g

if (my_node == rank) {
    
    if(is_next_on_my_node == 0) {
        MPI_Reve
    }
    if(is_previous_on_my_node == 0){

    }

    // code

    if (is_next_on_my_node == 0) {
        
    }
}