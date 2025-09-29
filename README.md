# Program-CPP-Ihsannabigh-Mayka-Iskandar_ARIEL_TLS25
Tugas TLS Pemrograman 2
// Soal Nomor 1
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



// Soal Nomor 2
#include <iostream>
#include <string>
using namespace std;

bool isVowel(char c) {
    c = tolower(c);
    return (c == 'a' || c == 'i' || c == 'u' || c == 'e' || c == 'o');
}

string myReverse(string s) {
    string res = "";
    for (int i = s.size() - 1; i >= 0; i--) {
        res += s[i];
    }
    return res;
}

string makePassword(string word) {
    string temp = "";
    for (char c : word) {
        if (!isVowel(c)) temp += c;
    }
    string reversed = myReverse(temp);
    int asciiFirst = (int)word[0];
    string code = to_string(asciiFirst);
    int mid = reversed.size() / 2;
    string result = reversed.substr(0, mid) + code + reversed.substr(mid) + word[0];
    return result;
}

string reconstruct(string sandi) {
    string angka = "";
    string kiri = "", kanan = "";
    for (char c : sandi) {
        if (isdigit(c)) angka += c;
    }
    int pos = sandi.find(angka);
    kiri = sandi.substr(0, pos);
    kanan = sandi.substr(pos + angka.size());
    int asciiVal = stoi(angka);
    char firstChar = (char)asciiVal;
    string gabungan = kiri + kanan;
    if (!gabungan.empty() && gabungan.back() == firstChar)
        gabungan.pop_back();
    string reversed = myReverse(gabungan);
    string hasil = firstChar + reversed;
    return hasil;
}

int main() {
    string kata;
    cin >> kata;
    string sandi = makePassword(kata);
    cout << "Sandi: " << sandi << endl;
    string hasil = reconstruct(sandi);
    cout << "Hasil rekonstruksi (tanpa vokal): " << hasil << endl;
    return 0;
}



// Soal Nomor 3
#include <iostream>
using namespace std;

string trafficLight(int t) {
    int cycle = 103;
    int delta = (t - 45) % cycle;
    if (delta < 3) return "Kuning";
    else if (delta < 83) return "Merah";
    else return "Hijau";
}

int main() {
    int times[] = {80, 135, 150, 212};
    for (int t : times) {
        cout << "Detik " << t << " → " << trafficLight(t) << endl;
    }
    return 0;
}
