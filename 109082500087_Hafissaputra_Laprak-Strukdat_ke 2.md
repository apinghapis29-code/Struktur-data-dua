# <h1 align="center">Laporan Praktikum Modul 1 - Codeblocks IDE & Pengenalan Bahas C++ (Bagian Pertama)</h1>
<p align="center">Hafis Saputra - 109082500087</p>

## Dasar Teori
Visual Studio Code (VS Code) merupakan source-code editor yang
bersifat ringan, open-source, dan cross-platform, yang mendukung
berbagai bahasa pemrograman termasuk C++ melalui ekstensi
tambahan. Editor ini digunakan pada praktikum Struktur Data untuk
menulis kode program, kemudian meng-compile dan menjalankannya
melalui terminal terintegrasi menggunakan compiler g++ (GNU
Compiler Collection untuk C++).
Bahasa C++ merupakan pengembangan dari bahasa C yang
diciptakan oleh Bjarne Stroustrup di AT&T Bell Laboratories pada
awal tahun 1980-an, yang pada mulanya disebut “C with class”
sebelum akhirnya disempurnakan dengan fasilitas pembebanlebihan
operator dan fungsi[2]. Struktur dasar program C++ terdiri dari
header file (misalnya #include <iostream>), deklarasi variabel dan
konstanta, serta fungsi utama main() sebagai titik masuk eksekusi
program.
Untuk berinteraksi dengan pengguna, C++ menyediakan fungsi cout
untuk mencetak (output) data ke layar dan cin untuk menerima
(input) data dari keyboard[2]. Selain itu, C++ juga menyediakan
berbagai jenis operator seperti operator aritmatika, operator
pengerjaan (assignment), operator logika, dan operator kondisional,
serta struktur kendali seperti if, if-else, dan switch untuk
pengambilan keputusan dalam program.

## Unguided 

### 1. Program Operasi Penjumlahan, Pengurangan, dan Perkalian Matriks 3×3

Program menerima input dua buah matriks berukuran 3×3, kemudian melakukan operasi penjumlahan, pengurangan, dan perkalian dari kedua matriks tersebut.


```C++
#include <iostream>
using namespace std;

int main() {
    int A[3][3], B[3][3];
    int tambah[3][3], kurang[3][3], kali[3][3];

    cout << "Masukkan Matriks A:\n";
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cin >> A[i][j];
        }
    }

    cout << "Masukkan Matriks B:\n";
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cin >> B[i][j];
        }
    }

    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            tambah[i][j] = A[i][j] + B[i][j];
            kurang[i][j] = A[i][j] - B[i][j];

            kali[i][j] = 0;
            for (int k = 0; k < 3; k++) {
                kali[i][j] += A[i][k] * B[k][j];
            }
        }
    }

    cout << "\nHasil Penjumlahan:\n";
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++)
            cout << tambah[i][j] << " ";
        cout << endl;
    }

    cout << "\nHasil Pengurangan:\n";
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++)
            cout << kurang[i][j] << " ";
        cout << endl;
    }

    cout << "\nHasil Perkalian:\n";
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++)
            cout << kali[i][j] << " ";
        cout << endl;
    }

    return 0;
}

Program di atas menggunakan array dua dimensi untuk menyimpan matriks A dan B dengan ukuran 3×3. Perulangan for digunakan untuk memasukkan dan mengakses setiap elemen matriks. Operasi penjumlahan dilakukan dengan menjumlahkan elemen yang memiliki posisi sama, sedangkan pengurangan dilakukan dengan mengurangkan elemen matriks A dengan B. Pada perkalian matriks digunakan tiga buah perulangan untuk mengalikan setiap baris matriks A dengan kolom matriks B..

link gituhub:



###  2. Program Menukar Nilai 3 Variabel Menggunakan Pointer dan Reference

Program digunakan untuk menukar nilai dari tiga variabel dengan memanfaatkan pointer dan reference.

#include <iostream>
using namespace std;

void tukar(int *a, int *b, int *c) {
    int temp = *a;
    *a = *b;
    *b = *c;
    *c = temp;
}

int main() {
    int a = 10, b = 20, c = 30;

    cout << "Sebelum ditukar : ";
    cout << a << " " << b << " " << c << endl;

    tukar(&a, &b, &c);

    cout << "Setelah ditukar : ";
    cout << a << " " << b << " " << c << endl;

    return 0;
}
```
Program di atas menggunakan pointer untuk mengakses alamat dari variabel a, b, dan c. Tanda & digunakan untuk mengirim alamat variabel ke fungsi, sedangkan tanda * digunakan untuk mengakses nilai yang terdapat pada alamat tersebut. Nilai awal 10 20 30 kemudian ditukar menjadi 20 30 10 menggunakan variabel sementara temp.

Linkgituhub:



### b Menggunakan Reference

```C++
#include <iostream>
using namespace std;

void tukar(int &a, int &b, int &c) {
    int temp = a;
    a = b;
    b = c;
    c = temp;
}

int main() {
    int a = 10, b = 20, c = 30;

    cout << "Sebelum ditukar : ";
    cout << a << " " << b << " " << c << endl;

    tukar(a, b, c);

    cout << "Setelah ditukar : ";
    cout << a << " " << b << " " << c << endl;

    return 0;
}

penjelasan singkat guided b

Program reference memiliki fungsi yang sama dengan pointer, yaitu menukar nilai tiga variabel. Perbedaannya terletak pada parameter fungsi yang menggunakan tanda &. Reference secara langsung mengacu pada variabel asli sehingga perubahan nilai di dalam fungsi akan memengaruhi nilai variabel tersebut.

Linkgithub:
https://github.com/apinghapis29-code/Strukdat/commit/b147e6020f0fd22619e50a3579f398b718f1b59b




### 3  Program Mencari Nilai Minimum, Maksimum, dan Rata-rata Array

Program menggunakan array satu dimensi arrA yang berisi 10 nilai. Program menyediakan menu untuk menampilkan array, mencari nilai maksimum, mencari nilai minimum, dan menghitung rata-rata.

```C++
#include <iostream>
using namespace std;

int cariMinimum(int arr[], int n) {
    int min = arr[0];

    for (int i = 1; i < n; i++) {
        if (arr[i] < min)
            min = arr[i];
    }

    return min;
}

int cariMaksimum(int arr[], int n) {
    int max = arr[0];

    for (int i = 1; i < n; i++) {
        if (arr[i] > max)
            max = arr[i];
    }

    return max;
}

void hitungRataRata(int arr[], int n) {
    int jumlah = 0;

    for (int i = 0; i < n; i++)
        jumlah += arr[i];

    cout << "Nilai rata-rata = " << (double)jumlah / n << endl;
}

int main() {
    int arrA[] = {11, 8, 5, 7, 12, 26, 3, 54, 33, 55};
    int n = 10;
    int pilihan;

    do {
        cout << "\n--- Menu Program Array ---\n";
        cout << "1. Tampilkan isi array\n";
        cout << "2. Cari nilai maksimum\n";
        cout << "3. Cari nilai minimum\n";
        cout << "4. Hitung nilai rata-rata\n";
        cout << "5. Keluar\n";
        cout << "Pilih menu: ";
        cin >> pilihan;

        switch (pilihan) {
            case 1:
                cout << "Isi array: ";
                for (int i = 0; i < n; i++)
                    cout << arrA[i] << " ";
                cout << endl;
                break;

            case 2:
                cout << "Nilai maksimum = "
                     << cariMaksimum(arrA, n) << endl;
                break;

            case 3:
                cout << "Nilai minimum = "
                     << cariMinimum(arrA, n) << endl;
                break;

            case 4:
                hitungRataRata(arrA, n);
                break;

            case 5:
                cout << "Program selesai.\n";
                break;

            default:
                cout << "Pilihan tidak tersedia.\n";
        }

    } while (pilihan != 5);

    return 0;
}
penjelasan singkat guided 3

Program di atas menggunakan array arrA yang berisi {11, 8, 5, 7, 12, 26, 3, 54, 33, 55}. Function cariMinimum() digunakan untuk mencari nilai terkecil dan menghasilkan nilai 3, sedangkan cariMaksimum() digunakan untuk mencari nilai terbesar dan menghasilkan 55. Procedure hitungRataRata() menjumlahkan seluruh elemen array kemudian membaginya dengan jumlah data sehingga diperoleh rata-rata 21,4. Menu program menggunakan switch-case untuk menentukan operasi berdasarkan pilihan pengguna

Linkgithub:


Kesimpulan;  
Berdasarkan praktikum yang telah dilakukan, dapat disimpulkan bahwa matriks dapat digunakan untuk mengolah data dalam bentuk baris dan kolom, sedangkan pointer dan reference dapat digunakan untuk mengubah nilai variabel melalui fungsi. Array dapat digunakan untuk menyimpan kumpulan data dan diolah menggunakan function maupun procedure untuk mendapatkan nilai minimum, maksimum, dan rata-rata. Penggunaan switch-case juga mempermudah pembuatan menu sehingga pengguna dapat memilih operasi yang ingin dijalankan

## Referensi
