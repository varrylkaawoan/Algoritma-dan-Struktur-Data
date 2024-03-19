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
