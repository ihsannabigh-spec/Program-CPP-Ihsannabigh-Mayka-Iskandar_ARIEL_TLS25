# Program-CPP-Ihsannabigh-Mayka-Iskandar_ARIEL_TLS25
Tugas TLS Pemrograman 2
#include <iostream>
using namespace std;

// Fungsi untuk membalik digit angka secara matematis
int reverseNumber(int x) {
    if (x == 0) return 0;
    bool neg = x < 0;
    if (neg) x = -x;

    int rev = 0;
    while (x > 0) {
        rev = rev * 10 + (x % 10);
        x /= 10;
    }

    return neg ? -rev : rev;
}

int main() {
    int n;
    cin >> n; // jumlah elemen
    int arr[n];
    for (int i = 0; i < n; i++) cin >> arr[i];

    int total = 0;
    for (int i = 0; i < n; i++) {
        int transformed = (i % 2 == 0) ? reverseNumber(arr[i]) : arr[i];
        total += transformed;
    }

    cout << total << endl;
    return 0;
}
