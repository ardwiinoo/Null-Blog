---
author: "Arif Dwi Nugroho"
title: "Konversi Array 2D ke 1D C++"
date: 2021-12-31
description: "Algoritma untuk merubah array 2 dimensi menjadi 1 dimensi pemrograman c++"
tags: ["C++", "Source Code", "Algoritma"]
thumbnail: https://blogger.googleusercontent.com/img/a/AVvXsEiB4cVpVMOH5yzk5dTtv7PvIHY8xLafa0qa6eo8E1DqqQQuRbtQoo8hngcBqTqVHSKIT6PVt2YFsIb9nzo2K-_Tfd8EUzD2i2qdvxuc-ZwjBRUf5CyfFomTenGOl1rtV71o6CIdc7Nge9E8GXUMKNqRFLf7lRrEqdAEW_1XdiCavrxGzUWT3XhN1yUz=s16000
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
Disini kita akan mengkonversi dua array 2 dimensi 3X3 menjadi satu array 1 dimensi.
Maka algoritma yang digunakan: 

{
  Pertama, menerima input jumlah baris dan jumlah kolom arrayA yang akan disimpan pada variabel b1 dan k1, selanjutnya mengisi data arrayA dengan perulangan. Kedua, menerima input jumlah baris dan jumlah kolom arrayB yang akan disimpan pada variabel b2 dan k2, selanjutnya mengisi data arrayB dengan perulangan. Ketiga, menampilkan data arrayA dan arrayB menggunakan perulangan bersarang. Keempat, menggabungkan arrayA dan arrayB yang akan disimpan pada arrayC, membuat variabel b3 = 0 untuk batas baris arrayC, kemudian menggunakan perulangan bersarang yang terdiri dari 3 perulangan, perulangan pertama digunakan untuk baris, memiliki kondisi (i < b1), kemudian perulangan kedua digunakan untuk kolom arrayA memiliki kondisi (j < k1), untuk memindahkan data arrayA ke arrayC (arrC[b3] = arrA[i][j]) dan setiap selesai memindah data variabel b3 akan ditambah dengan 1. Kemudian perulangan ketiga digunakan untuk kolom arrayB memiliki kondisi (k < k2), untuk memindahkan data arrayB ke arrayC (arrC[b3] = arrB[i][j]) dan setiap selesai memindah data variabel b3 akan ditambah dengan 1. Kelima, menampilkan hasil penggabungan dengan perulangan yang memiliki kondisi (i < (b1 * k1) + (b2 * k2)).
}

## Pseudocode
Ini adalah gambaran kode semu dari algoritma diatas.

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
  int main(){
    
    int b1, k1, b2, k2, b3;
    int arrA[100][100], arrB[100][100], arrC[100];
```

Menerima input baris dan kolom untuk `arrA` dan mengisi datanya.
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

Menerima input baris dan kolom untuk `arrB` dan mengisi datanya.
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

Menampilkan data dari `arrA` dan `arrB` dengan nested loop agar lebih praktis.
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

Menggabungkan data `arrA` dan `arrB` kedalam `arrC`, karena array berordo 3X3 maka dalam satu perulangan kita dapat memindahkan 3 data dari `arrA` kemudian dilanjutkan dengan 3 data dari `arrB`.
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

Terakhir menampilkan data `arrC`. Karena `arrC` merupakan hasil penggabungan data dari `arrA` dan `arrB` maka `arrC` memiliki 18 index.
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