# GabrielASD20Maret
Gabriel Chrisoberryl Guevara Kaawoan 1203230041 IF 03-03

Latihan Praktikum Algoritma Struktur Data - Array, Pointer, dan Fungsi

Soal No. 1 Source Code : 
```c
#include <stdio.h>
#include <stdbool.h>
int value(char card) {
    if (card >= '2' && card <= '9')
        return card - '0';
    else if (card == 'J')
        return 14; // J memiliki nilai 14 agar berada di belakang K
    else if (card == 'Q')
        return 15; // Q memiliki nilai 15 agar berada di belakang J
    else if (card == 'K')
        return 16; // K memiliki nilai 16 agar berada di belakang Q
    else // Assuming 'A' represents 1
        return 1;
}

void bubble_sort(char cards[], int n) {
    int i, j, steps = 0;
    bool swapped;
    char temp;

    printf("Initial order: %s\n", cards);

    for (i = 0; i < n; i++) {
        swapped = false;
        for (j = 0; j < n - i - 1; j++) {
            if (value(cards[j]) > value(cards[j+1])) {
                // Swap cards
                temp = cards[j];
                cards[j] = cards[j+1];
                cards[j+1] = temp;
                swapped = true;
                steps++;
                printf("Pertukaran %d: %s\n", steps, cards);
            }
        }
        if (!swapped)
            break;
    }
    printf("Jumlah minimal langkah pertukaran: %d\n", steps);
}

int main() {
    int n, i;
    printf("Masukkan jumlah kartu: ");
    scanf("%d", &n);

    char cards[n+1]; // +1 for '\0'
    printf("Masukkan nilai kartu: ");
    for (i = 0; i < n; i++) {
        scanf(" %c", &cards[i]); // Read cards one by one
    }
    cards[n] = '\0'; // Null-terminate the string

    bubble_sort(cards, n);

    return 0;
}
```
Penjelasan Source Code : 
```c
#include <stdio.h>
#include <stdbool.h>
```
#include <stdio.h> : Library standar untuk fungsi input-output (I/O) dalam bahasa C.

#include <stdbool.h> : Library standar yang menyediakan tipe data boolean dan nilai-nilainya true dan false.
```c
int value(char card) {
        if (card >= '2' && card <= '9')
            return card - '0';
        else if (card == 'J')
            return 14; // J memiliki nilai 14 agar berada di belakang K
        else if (card == 'Q')
            return 15; // Q memiliki nilai 15 agar berada di belakang J
        else if (card == 'K')
            return 16; // K memiliki nilai 16 agar berada di belakang Q
        else // Assuming 'A' represents 1
            return 1;
    }
```
value(char card) : Fungsi ini mengembalikan nilai numerik dari sebuah kartu. Misalnya, untuk kartu '2', nilainya adalah 2, untuk 'J' nilainya adalah 14, untuk 'Q' nilainya adalah 15, dan seterusnya. Ini membantu dalam pengurutan kartu berdasarkan nilai numeriknya.
```c
void bubble_sort(char cards[], int n) {
    int i, j, steps = 0;
    bool swapped;
    char temp;

    printf("Initial order: %s\n", cards);

    for (i = 0; i < n; i++) {
        swapped = false;
        for (j = 0; j < n - i - 1; j++) {
            if (value(cards[j]) > value(cards[j+1])) {
                // Swap cards
                temp = cards[j];
                cards[j] = cards[j+1];
                cards[j+1] = temp;
                swapped = true;
                steps++;
                printf("Pertukaran %d: %s\n", steps, cards);
            }
        }
        if (!swapped)
            break;
    }
    printf("Jumlah minimal langkah pertukaran: %d\n", steps);
}
```
bubble_sort(char cards[], int n) : Fungsi ini menerima array dari kartu dan jumlah kartu, dan mengurutkan kartu tersebut menggunakan algoritma Bubble Sort.

swapped : Variabel boolean untuk menandai apakah ada pertukaran pada iterasi tertentu.

temp : Variabel sementara untuk menukar kartu.

Algoritma Bubble Sort digunakan untuk membandingkan dua kartu berdekatan dan menukar posisinya jika tidak terurut. Ini diulangi hingga seluruh array terurut.

Setiap kali ada pertukaran, jumlah langkah (steps) ditambah satu, dan hasil pengurutan setiap langkah dicetak.
```c
int main() {
    int n, i;
    printf("Masukkan jumlah kartu: ");
    scanf("%d", &n);

    char cards[n+1]; // +1 for '\0'
    printf("Masukkan nilai kartu: ");
    for (i = 0; i < n; i++) {
        scanf(" %c", &cards[i]); // Read cards one by one
    }
    cards[n] = '\0'; // Null-terminate the string

    bubble_sort(cards, n);

    return 0;
}
```
Fungsi main() merupakan titik awal program yang akan dieksekusi.

Meminta pengguna untuk memasukkan jumlah kartu (n) dan nilai-nilai kartu.

Nilai-nilai kartu dimasukkan ke dalam array cards.

Memanggil fungsi bubble_sort() untuk mengurutkan kartu.

Mengembalikan nilai 0, menandakan bahwa program telah berakhir dengan sukses.

Hasil Run Program : 
![Screenshot 2024-03-19 234816](https://github.com/varrylkaawoan/GabrielASD20Maret/assets/162390856/76b7795f-5a75-4a89-a130-055a4526c292)
