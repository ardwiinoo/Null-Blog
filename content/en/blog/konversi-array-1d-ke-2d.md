---
author: "Arif Dwi Nugroho"
title: "Convert 1D to 2D Array C++"
date: 2021-12-31
description: "Algorithm to convert 1 dimensional array into 2 dimensional c++ programming"
tags: ["C++", "Source Code", "Algoritma"]
thumbnail: https://blogger.googleusercontent.com/img/a/AVvXsEhC0CPfFFlNrFxzO0aZfl2bpcZuIY9EcgbCwEiJZDGGf3BIM0f76GerUDJPJeglFpODlGxIiV0RgGKu6XU-qpssXnGba1rjZpoJKQGnxLZ2eeVpBI4I7zKidJl4__puzTG-KbcNP8_P2bsO_kGretTc4cJPJDLWppxZPVKyIYTO4BrbsH4qsJr-jpgT=s16000
---

**Array** -> A data structure used to store a set of data in one place with the same `data type`.

```c++
  int arr[100];
```

**2 Dimensional Array** -> The term for an array whose index is numbered using 2 numbers, can be analogous to a `matrix`.

```c++
	int arr[100][100];
```

## Algorithm
To convert a 1-dimensional array into a 2-dimensional 3X3 array.
Then the algorithm used:

{
First, create a variable arrA (1D) and fill in the data, then display the contents of arrA using a loop that has a condition (i < row). Second, declare arrB (2D) variable which will be used to store arrA data. The third is using a While loop with condition (i < row), in While there are two for loops (nested), the first loop has a condition (j < 3) and the second loop has a condition (k < 3), inside the second loop (arrB[ j][k] = arrA[i]) to move arrA data into arrB, then increment i. Finally, displaying arrB data with nested loops, the first loop has a condition (i < 3) and the second loop has a condition (j < 3).
}

## Pseudocode
This is a pseudo code description of the above algorithm.

```
Program_konversi_array_1D_ke_2D
Deklarasi:
  i, j, k, arrA[10]     : integer (input)
  arrB[10][10]          : integer (output)

Deskripsi:
    arrA[10] <- {1, 2, 3, 4, 5, 6, 7, 8, 9}
    
    Write("Array A")
    for(i <- 0; i < 9; i++) begin
        Write(arrA[i])
    End for

    i <- 0
    while(i < 9) begin
        for(int j <- 0; j < 3; j++) begin
            for(int k <- 0; k < 3; k++) begin
                arrB[j][k] = arrA[i]
                i <- i + 1
            End for
        End for
    End while

    Write("Array B")
    for(i <- 0; i < 3; i++) begin
        for(j <- 0; j < 3; j++) begin
            Write(arrB[i][j])
        End for
        Write("\n")
    End for
```

## C++ Programs
From the pseudo code above we can apply it to the C++ programming language.

```c++
  #include <iostream>
  using namespace std;
```
**iostream** -> used for the input output stream.

**namespace std** -> used so that we don't always have to write `std::` for example in the `cout` command.

Next, declare a variable on `main`.
```c++
  int main() {
    int arrA[12]={1, 2, 3, 4, 5, 6, 7, 8, 9};
    int arrB[10][10];
```

Displays the data in `arrA`.
```c++
    for(int i=0; i < 9; i++){
        cout <<" " << arrA[i];
    }
```

Moves `arrA` data into `arrB` at each index. index `0` arrA will be index row `0` col `0` arrB.
```c++
    int i=0;
    while(i < 9){
        for(int j=0; j < 3; j++){
            for(int k=0; k < 3; k++){
                arrB[j][k] = arrA[i];
                i++;
        	}
        }
    }
```

Displays `arrB` data.
```c++
    cout << endl;
    for(int i=0; i < 3; i++){
        for(int j=0; j < 3; j++){
            cout << arrB[i][j] << " ";
        }
        cout << endl;
    }
```

**Full Code**
```c++
#include <iostream>
using namespace std;
 
int main() {
    int arrA[12]={1, 2, 3, 4, 5, 6, 7, 8, 9};
    int arrB[10][10];
    
    cout << "Array A\n";
    for(int i=0; i<9; i++){
        cout <<" " << arrA[i];
    }
    
    int i=0;
    while(i<9){
        for(int j=0; j<3; j++){
            for(int k=0;k<3; k++){
                arrB[j][k] = arrA[i];
                i++;
        	}
        }
    }
    cout << endl;
    cout << "Array B\n";
    for(int i=0; i<3; i++){
        for(int j=0; j<3; j++){
            cout << arrB[i][j] << " ";
        }
        cout << endl;
    }
    return 0;
}
```

**Output**

```
Array A
 1 2 3 4 5 6 7 8 9
Array B
1 2 3
4 5 6
7 8 9
```