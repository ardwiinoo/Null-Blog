---
author: "Arif Dwi Nugroho"
title: "Konversi Array 1D ke 2D C++"
date: 2021-12-31
description: "Algoritma untuk merubah array 1 dimensi menjadi 2 dimensi pemrograman c++"
tags: ["C++", "Source Code", "Algoritma"]
thumbnail: https://blogger.googleusercontent.com/img/a/AVvXsEhC0CPfFFlNrFxzO0aZfl2bpcZuIY9EcgbCwEiJZDGGf3BIM0f76GerUDJPJeglFpODlGxIiV0RgGKu6XU-qpssXnGba1rjZpoJKQGnxLZ2eeVpBI4I7zKidJl4__puzTG-KbcNP8_P2bsO_kGretTc4cJPJDLWppxZPVKyIYTO4BrbsH4qsJr-jpgT=s16000
---

**Array** -> Struktur data yang digunakan untuk menyimpan sekumpulan data dalam satu tempat dengan `tipe data` yang sama.

```c++
  int arr[100];
```

**Array 2 Dimensi** -> Sebutan untuk array yang penomoran index-nya menggunakan 2 buah angka, dapat dianalogikan seperti sebuah `matriks`. 

```c++
	int arr[100][100];
```

## Algoritma
Untuk merubah suatu array 1 dimensi menjadi array 2 dimensi 3X3.
Maka algoritma yang digunakan: 

{
  Pertama, membuat variabel arrA (1D) dan mengisi datanya, kemudian menampilkan isi dari arrA dengan menggunakan perulangan yang memiliki kondisi (i < baris). Kedua, mendeklarasikan variabel arrB (2D) yang akan digunakan untuk menyimpan data arrA. Ketiga menggunakan perulangan While dengan kondisi (i < baris), di dalam While terdapat dua perulangan for (nested), perulangan pertama memiliki kondisi (j < 3) dan perulangan kedua memiliki kondisi (k < 3), di dalam perulangan kedua (arrB[j][k] = arrA[i]) untuk memindahkan data arrA kedalam arrB, kemudian increment i. Terakhir, menampilkan data arrB dengan perulangan bersarang, perulangan pertama memiliki kondisi (i < 3) dan perulangan kedua memiliki kondisi (j < 3).
}

## Pseudocode
Ini adalah gambaran kode semu dari algoritma diatas.

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

## Program C++
Dari kode semu diatas kita dapat menerapkannya ke dalam bahasa pemrograman c++.

```c++
  #include <iostream>
  using namespace std;
```
**iostream** -> digunakan untuk input output stream.

**namespace std** -> digunakan agar kita tidak harus selalu menulis `std::` contohnya pada perintah `cout`.

Selanjutnya deklarasikan variabel pada `main`. 
```c++
  int main() {
    int arrA[12]={1, 2, 3, 4, 5, 6, 7, 8, 9};
    int arrB[10][10];
```

Menampilkan data yang ada pada `arrA`.
```c++
    for(int i=0; i < 9; i++){
        cout <<" " << arrA[i];
    }
```

Memindahkan data `arrA` ke dalam `arrB` pada setiap index. index `0` arrA akan menjadi index row `0` col `0` arrB.
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

Menampilkan data `arrB`.
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