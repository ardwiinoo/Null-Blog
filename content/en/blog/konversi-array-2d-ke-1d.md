---
author: "Arif Dwi Nugroho"
title: "Convert 2D Array to 1D C++"
date: 2021-12-31
description: "Algorithm to convert 2 dimensional array into 1 dimensional c++ programming"
tags: ["C++", "Source Code", "Algoritma"]
thumbnail: https://blogger.googleusercontent.com/img/a/AVvXsEiB4cVpVMOH5yzk5dTtv7PvIHY8xLafa0qa6eo8E1DqqQQuRbtQoo8hngcBqTqVHSKIT6PVt2YFsIb9nzo2K-_Tfd8EUzD2i2qdvxuc-ZwjBRUf5CyfFomTenGOl1rtV71o6CIdc7Nge9E8GXUMKNqRFLf7lRrEqdAEW_1XdiCavrxGzUWT3XhN1yUz=s16000
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
Here we will convert two 2D 3X3 arrays into one 1D array.
Then the algorithm used:

{
First, it accepts the input of the number of rows and the number of columns in arrayA which will be stored in the variables b1 and k1, then fills the data in arrayA with a loop. Second, receive input the number of rows and the number of columns in arrayB which will be stored in variables b2 and k2, then fill in the data in arrayB with a loop. Third, display arrayA and arrayB data using nested loops. Fourth, combine arrayA and arrayB which will be stored in arrayC, create a variable b3 = 0 for the row limit of arrayC, then use nested loops consisting of 3 iterations, the first loop is used for rows, has a condition (i < b1), then the second loop is used for column arrayA has a condition (j < k1), to move data from arrayA to arrayC (arrC[b3] = arrA[i][j]) and every time you finish moving data, variable b3 will be added by 1. Then the third iteration is used for column arrayB has a condition (k < k2), to move data from arrayB to arrayC (arrC[b3] = arrB[i][j]) and each time it finishes moving data, the variable b3 will be added by 1. Fifth, display the result of merging with a loop that has conditions (i < (b1 * k1) + (b2 * k2)).
}

## Pseudocode
This is a pseudocode description of the above algorithm.

```
Program_konversi_array_2D_ke_1D
Deklarasi:
  i, j, k, b1, k1, b2, k2, b3, arrA[100][100], arrB[100][100] : integer (input)
  arrC[100]                                                   : integer (output)

Deskripsi:
  Write("Array A")
  Write("Jumlah baris: ")
  Read(b1)
  Write("Jumlah kolom: ")
  Read(k1)

  arrA[b1][k1]
  for(i <- 0; i < b1; i++) begin
    for(j <- 0; j < k1; j++) begin
      Read(arrA[i][j])
    End for
  End for

  Write("Array B")
  Write("Jumlah baris: ")
  Read(b2)
  Write("Jumlah kolom: ")
  Read(k2)

  arrB[b2][k2]
  for(i <- 0; i < b2; i++) begin
    for(j <- 0; j < k2; j++) begin
      Read(arrA[i][j])
    End for
  End for

  Write("\nA:\tB\n")
  for(i <- 0; i < b1; i++) begin
    for(j <- 0; j < k1; j++) begin
      Write(arrA[i][j])
    End for
    Write("\t")
    for(k <- 0; k < k2; k++) begin
      Write(arrB[i][j])
    End for
  End for

  b3 <- 0
  for(i <- 0; i < b1; i++) begin
    for(j <- 0; j < k1; j++) begin
      arrC[b3] <- arrA[i][j]
      b3++
    End for
    for(k <- 0; k < k2; k++) begin
      arrC[b3] <- arrB[i][j]
      b3++
    End for
  End for

  Write("Hasil Konversi")
  for(i <- 0; i < (b1 * k1) + (b2 * k2); i++) begin
    Write(arrC[i])
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
  int main(){
    
    int b1, k1, b2, k2, b3;
    int arrA[100][100], arrB[100][100], arrC[100];
```

Accepts row and column input for `arrA` and fills in the data.
```c++
  cout << "Array A\n";
  cout << "Jumlah baris: "; cin >> b1;
  cout << "Jumlah kolom: "; cin >> k1;
    
  arrA[b1][k1];
  for(int i=0; i < b1; i++){
    for(int j=0; j < k1; j++){
      cout << "Data [" << i+1 << "," << j+1 << "] = ";
      cin >> arrA[i][j];
    }
  }
```

Accepts row and column input for `arrB` and fills in the data.
```c++
  	cout << "\nArray B\n";
	cout << "Jumlah baris: "; cin >> b2;
	cout << "Jumlah kolom: "; cin >> k2;
	
	arrB[b2][k2];
	for(int i=0; i < b2; i++){
		for(int j=0; j < k2; j++){
			cout << "Data [" << i+1 << "," << j+1 << "] = ";
			cin >> arrB[i][j];
		}
	}
```

Displays data from `arrA` and `arrB` with nested loops for convenience.
```c++
  	cout << "\nA:\tB:\n";
	for(int i=0; i < b1; i++){
		for(int j=0; j < k1; j++){
			cout << arrA[i][j] << " ";
		}
		cout << "\t";
		for(int k=0; k < k2; k++){
			cout << arrB[i][k] << " ";
		}
		cout << endl;
	}
```

Combining `arrA` and `arrB` data into `arrC`, because the array is of order 3X3 then in one loop we can move 3 data from `arrA` and then continue with 3 data from `arrB`.
```c++
	b3=0;
	for (int i=0; i<b1; i++){
		for (int j=0; j< k1; j++){			
 			arrC[b3]= arrA[i][j];				
			b3++;
		}
		for(int k=0; k< k2; k++){
			arrC[b3] = arrB[i][k];
			b3++;
		}
	}
```

Finally displays the `arrC` data. Because `arrC` is the result of combining data from `arrA` and `arrB`, `arrC` has 18 indexes.
```c++
  	cout << "\nHasil Penggabungan : ";
	for(int i=0; i < (b1 * k1)+(b2 * k2); i++){
		cout << arrC[i] << " ";
	}
```

**Full Code**
```c++
#include <iostream>
using namespace std;

int main(){
	
	int b1, k1, b2, k2, b3;
	int arrA[100][100], arrB[100][100], arrC[100];
	
	cout << "Array A\n";
	cout << "Jumlah baris: "; cin >> b1;
	cout << "Jumlah kolom: "; cin >> k1;

	arrA[b1][k1];
	for(int i=0; i < b1; i++){
		for(int j=0; j < k1; j++){
			cout << "Data [" << i+1 << "," << j+1 << "] = ";
			cin >> arrA[i][j];
		}
	}

  	cout << "\nArray B\n";
	cout << "Jumlah baris: "; cin >> b2;
	cout << "Jumlah kolom: "; cin >> k2;
	
	arrB[b2][k2];
	for(int i=0; i < b2; i++){
		for(int j=0; j < k2; j++){
			cout << "Data [" << i+1 << "," << j+1 << "] = ";
			cin >> arrB[i][j];
		}
	}

  	cout << "\nA:\tB:\n";
	for(int i=0; i < b1; i++){
		for(int j=0; j < k1; j++){
			cout << arrA[i][j] << " ";
		}
		cout << "\t";
		for(int k=0; k < k2; k++){
			cout << arrB[i][k] << " ";
		}
		cout << endl;
	}

  	b3 = 0;
	for (int i=0; i<b1; i++){
		for (int j=0; j< k1; j++){			
 			arrC[b3]= arrA[i][j];				
			b3++;
		}
		for(int k=0; k< k2; k++){
			arrC[b3] = arrB[i][k];
			b3++;
		}
	}

  	cout << "\nHasil Penggabungan : ";
	for(int i=0; i < (b1 * k1)+(b2 * k2); i++){
		cout << arrC[i] << " ";
	}
```

**Output**

```
	Array A
	Jumlah baris: 3
	Jumlah kolom: 3
	Data [1,1] = 1
	Data [1,2] = 2
	Data [1,3] = 3
	Data [2,1] = 4
	Data [2,2] = 5
	Data [2,3] = 6
	Data [3,1] = 7
	Data [3,2] = 8
	Data [3,3] = 9

	Array B
	Jumlah baris: 3
	Jumlah kolom: 3
	Data [1,1] = 11
	Data [1,2] = 12
	Data [1,3] = 13
	Data [2,1] = 14
	Data [2,2] = 15
	Data [2,3] = 16
	Data [3,1] = 17
	Data [3,2] = 18
	Data [3,3] = 19

	A:      B:
	1 2 3   11 12 13
	4 5 6   14 15 16
	7 8 9   17 18 19

	Hasil Penggabungan : 1 2 3 11 12 13 4 5 6 14 15 16 7 8 9 17 18 19
```