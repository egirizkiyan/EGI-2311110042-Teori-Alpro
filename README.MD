# <h1 align="center">Laporan Praktikum Modul Tipe Data</h1>
<p align="center">Egi Rizkiyansyah</p>

CPMK 2 – SubCPMK 2 
## Unguided 
### 1. [Soal]

Berikut adalah penjelasan mengenai alur dari tiga algoritma sorting yang umum digunakan, yaitu Bubble Sort, Selection Sort, dan Merge Sort, beserta penjelasan mengenai runtime best case dan worst case masing-masing algoritma:

1. Bubble Sort
Alur:
   1. Algoritma ini bekerja dengan membandingkan pasangan elemen yang bersebelahan dan menukar mereka jika berada dalam urutan yang salah.
   2. Proses ini diulang untuk setiap elemen dalam array sampai tidak ada lagi elemen yang perlu ditukar.
   3. Pada setiap iterasi, elemen terbesar "mengambang" ke posisi akhirnya di akhir array.
Runtime:
   1. Best Case: O(n) - terjadi ketika array sudah terurut. Hanya perlu satu pass untuk memeriksa bahwa tidak ada elemen yang perlu ditukar.
   2. Worst Case: O(n^2) - terjadi ketika array diurutkan secara terbalik. Setiap elemen harus dipindahkan di setiap pass.
2. Selection Sort
Alur:
   1. Algoritma ini bekerja dengan membagi array menjadi dua bagian: bagian yang terurut dan bagian yang belum terurut.
   2. Pada setiap iterasi, elemen terkecil dari bagian yang belum terurut ditemukan dan ditukar dengan elemen pertama dari bagian yang belum terurut.
Kemudian, bagian yang terurut bertambah satu elemen dan bagian yang belum terurut berkurang satu elemen.
Runtime:
   1. Best Case: O(n^2) - Selection Sort selalu melakukan perbandingan yang sama jumlahnya terlepas dari apakah array sudah terurut atau tidak.
   2. Worst Case: O(n^2) - Sama seperti best case, jumlah perbandingan tidak berubah dengan urutan input.
3. Merge Sort
Alur:
   1. Algoritma ini bekerja berdasarkan prinsip divide and conquer.
   2. Array dibagi menjadi dua bagian hingga masing-masing bagian memiliki satu elemen.
   3. Kemudian, dua bagian tersebut digabungkan kembali (merge) dengan cara yang terurut.
Proses penggabungan ini dilakukan berulang kali hingga seluruh array kembali menjadi satu.
Runtime:
   1. Best Case: O(n log n) - Merge Sort selalu membagi array dan menggabungkannya kembali dalam urutan yang terurut, sehingga runtime tidak bergantung pada urutan input.
   2. Worst Case: O(n log n) - Sama seperti best case, karena cara kerja Merge Sort yang selalu membagi dan menggabungkan array dalam cara yang terstruktur.
Kesimpulan:
Bubble Sort: Best case O(n), Worst case O(n^2)
Selection Sort: Best case O(n^2), Worst case O(n^2)
Merge Sort: Best case O(n log n), Worst case O(n log n)
Bubble Sort dan Selection Sort memiliki runtime yang lebih buruk dibandingkan Merge Sort untuk kebanyakan kasus praktis, karena mereka memiliki runtime quadratic pada best dan worst case. Merge Sort, dengan runtime O(n log n), lebih efisien dan biasanya digunakan untuk data set yang lebih besar.

### 2. [Soal]

```C++

#include <iostream>
using namespace std;

void bubbleSort(int arr[], int n) {
    // Loop utama untuk setiap elemen dalam array
    for (int i = 0; i < n - 1; i++) {
        // Inisialisasi flag untuk mendeteksi apakah ada swap yang terjadi
        bool swapped = false;
        // Loop untuk membandingkan elemen berpasangan
        for (int j = 0; j < n - i - 1; j++) {
            // Jika elemen yang sekarang lebih besar dari elemen berikutnya, tukar elemen tersebut
            if (arr[j] > arr[j + 1]) {
                swap(arr[j], arr[j + 1]);
                swapped = true;
            }
        }
        // Jika tidak ada elemen yang ditukar, array sudah terurut dan kita bisa keluar dari loop
        if (!swapped) {
            break;
        }
    }
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr) / sizeof(arr[0]);
    cout << "Array sebelum disorting: ";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    bubbleSort(arr, n);

    cout << "Array setelah disorting: ";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}


```
#### Output:
![Screenshot 2024-05-15 232114](https://github.com/egirizkiyan/Egi3/assets/162097461/520058f8-38df-47af-b2de-83bed2a6913a)

#### Full code Screenshot:
![Screenshot 2024-05-15 231824](https://github.com/egirizkiyan/Egi3/assets/162097461/b38217d3-0f9f-4975-b68b-27d59328abca)

Penjelasan Program
A. Header File dan Namespace:

   1. #include <iostream>: Digunakan untuk input dan output.
   2. using namespace std;: Agar kita tidak perlu menuliskan std:: sebelum fungsi standar.

B. Fungsi bubbleSort:

   1. void bubbleSort(int arr[], int n): Fungsi ini menerima array arr dan panjang array n.

C. Loop Utama (Outer Loop):

   1. for (int i = 0; i < n - 1; i++): Loop ini berjalan dari i = 0 hingga i = n-2. Ini menentukan berapa banyak elemen yang telah diurutkan pada setiap iterasi luar.

D. Inisialisasi Flag:

   1. bool swapped = false;: Flag ini digunakan untuk mendeteksi apakah ada elemen yang ditukar pada iterasi saat ini.

E. Loop Dalam (Inner Loop):

   1. for (int j = 0; j < n - i - 1; j++): Loop ini berjalan dari j = 0 hingga j = n-i-2. Loop ini membandingkan dan menukar elemen berpasangan jika diperlukan.
   2. if (arr[j] > arr[j + 1]): Membandingkan elemen bersebelahan.
   3. swap(arr[j], arr[j + 1]);: Menukar elemen jika elemen yang sekarang lebih besar dari elemen berikutnya.
   4. swapped = true;: Jika ada penukaran, flag diatur ke true.

F. Pemeriksaan Flag:

   1. if (!swapped): Jika tidak ada elemen yang ditukar pada iterasi saat ini, artinya list sudah terurut dan kita bisa keluar dari loop utama lebih awal dengan break.

F. Fungsi main:

   1. Inisialisasi array arr dengan beberapa nilai acak.
   2. Menampilkan array sebelum pengurutan.
   3. Memanggil fungsi bubbleSort untuk mengurutkan array.
   4. Menampilkan array setelah pengurutan.

Kesimpulan
Algoritma Bubble Sort bekerja dengan cara berulang kali menukar elemen yang bersebelahan jika elemen tersebut berada dalam urutan yang salah. Proses ini berlanjut hingga tidak ada lagi elemen yang perlu ditukar, yang berarti array sudah terurut. Bubble Sort sederhana dan mudah dipahami, namun tidak efisien untuk array yang besar karena kompleksitas waktu terburuknya adalah O(n^2).

### 3. [Soal]
```C++
#include <iostream>
#include <algorithm>
using namespace std;

bool areAnagrams(string str1, string str2) {
    // Jika panjang kedua string tidak sama, maka pasti bukan anagram
    if (str1.length() != str2.length()) {
        return false;
    }

    // Sort kedua string
    sort(str1.begin(), str1.end());
    sort(str2.begin(), str2.end());

    // Bandingkan string yang sudah di-sort
    return str1 == str2;
}

int main() {
    string str1, str2;

    // Contoh input pertama
    str1 = "bahu";
    str2 = "buah";
    if (areAnagrams(str1, str2)) {
        cout << "Output: anagram" << endl;
    } else {
        cout << "Output: tidak anagram" << endl;
    }

    // Contoh input kedua
    str1 = "makan";
    str2 = "minum";
    if (areAnagrams(str1, str2)) {
        cout << "Output: anagram" << endl;
    } else {
        cout << "Output: tidak anagram" << endl;
    }

    return 0;
}
```
#### Output:
![Screenshot 2024-05-15 233330](https://github.com/egirizkiyan/Egi3/assets/162097461/aef6d57e-b344-4988-8ca3-914d2244da75)

#### Full code Screenshot:
![Screenshot 2024-05-15 233222](https://github.com/egirizkiyan/Egi3/assets/162097461/029d5c09-d5cb-47be-8874-7d4795a97278)

Penjelasan Program
A. Header File dan Namespace:

   1. #include <iostream>: Digunakan untuk input dan output.
   2. #include <algorithm>: Digunakan untuk fungsi sort.
   3. using namespace std;: Agar kita tidak perlu menuliskan std:: sebelum fungsi standar.

B. Fungsi areAnagrams:

   1. bool areAnagrams(string str1, string str2): Fungsi ini menerima dua string dan mengembalikan true jika kedua string merupakan anagram dan false jika tidak.

C. Pengecekan Panjang String:

   1. if (str1.length() != str2.length()): Jika panjang kedua string tidak sama, maka pasti bukan anagram dan fungsi mengembalikan false.

D. Sorting Kedua String:

  1. sort(str1.begin(), str1.end());: Mengurutkan string str1.
  2. sort(str2.begin(), str2.end());: Mengurutkan string str2.

E. Membandingkan String yang Sudah Di-sort:

  1. return str1 == str2;: Mengembalikan true jika kedua string yang sudah diurutkan sama, false jika tidak.

F. Fungsi main:

  1. Dua contoh input diberikan untuk menguji fungsi areAnagrams.
  2.Jika fungsi mengembalikan true, output adalah "anagram".
  3. Jika fungsi mengembalikan false, output adalah "tidak anagram".
Kesimpulan
  Program ini menggunakan pendekatan sederhana dengan mengurutkan kedua string dan kemudian membandingkannya. Jika kedua string yang sudah diurutkan sama, maka kedua string tersebut merupakan anagram. Pendekatan ini efisien untuk string pendek dan mudah dipahami.

### 4. [Soal]
```C++
#include <iostream>
using namespace std;

// Fungsi untuk menggabungkan dua array yang sudah diurutkan
void mergeSortedArrays(int A[], int m, int B[], int n) {
    // Index terakhir dari array A yang terisi
    int lastA = m - 1;
    // Index terakhir dari array B
    int lastB = n - 1;
    // Index terakhir dari array A setelah digabung dengan B
    int lastMerged = m + n - 1;

    // Gabungkan array A dan B mulai dari belakang
    while (lastA >= 0 && lastB >= 0) {
        if (A[lastA] > B[lastB]) {
            A[lastMerged--] = A[lastA--];
        } else {
            A[lastMerged--] = B[lastB--];
        }
    }

    // Jika masih ada elemen yang tersisa di array B, salin ke A
    while (lastB >= 0) {
        A[lastMerged--] = B[lastB--];
    }
}

int main() {
    int A[10] = {1, 3, 5, 7, 9};  // array A dengan indeks yang cukup untuk menampung array B
    int B[] = {2, 4, 6, 8};       // array B
    int m = 5; // Jumlah elemen efektif dalam array A
    int n = sizeof(B) / sizeof(B[0]); // Jumlah elemen dalam array B

    // Cetak array A sebelum penggabungan
    cout << "Array A sebelum penggabungan: ";
    for (int i = 0; i < m; i++) {
        cout << A[i] << " ";
    }
    cout << endl;

    // Cetak array B
    cout << "Array B: ";
    for (int i = 0; i < n; i++) {
        cout << B[i] << " ";
    }
    cout << endl;

    // Gabungkan array B ke dalam array A
    mergeSortedArrays(A, m, B, n);

    // Cetak array A setelah penggabungan
    cout << "Array A setelah penggabungan: ";
    for (int i = 0; i < m + n; i++) {
        cout << A[i] << " ";
    }
    cout << endl;

    return 0;
}

```
#### Output:
![Screenshot 2024-05-15 234204](https://github.com/egirizkiyan/Egi3/assets/162097461/c7983852-5273-4229-83eb-7700fe87bdd1)

#### Full code Screenshot:
![Screenshot 2024-05-15 234112](https://github.com/egirizkiyan/Egi3/assets/162097461/02a80827-8db0-477d-830c-952fbb08c30f)

Penjelasan Program
A. Header File dan Namespace:

   1. #include <iostream>: Digunakan untuk input dan output.
   2. using namespace std;: Agar kita tidak perlu menuliskan std:: sebelum fungsi standar.

B. Fungsi mergeSortedArrays:

  1. void mergeSortedArrays(int A[], int m, int B[], int n): Fungsi ini menerima dua array yang sudah diurutkan 
A dan B, serta jumlah elemen efektif di 
A dan B.

C. Inisialisasi Indeks:

  1. int lastA = m - 1;: Indeks terakhir dari elemen efektif di array A.
  2. int lastB = n - 1;: Indeks terakhir dari array B.
  3. int lastMerged = m + n - 1;: Indeks terakhir dari array A setelah digabung dengan B.

E. Menggabungkan Array dari Belakang:

  1. while (lastA >= 0 && lastB >= 0): Selama masih ada elemen yang tersisa di kedua array.
  2. if (A[lastA] > B[lastB]): Jika elemen di 
𝐴
A lebih besar, masukkan ke posisi terakhir di array gabungan.
  3. A[lastMerged--] = A[lastA--];: Masukkan elemen 
𝐴
A ke posisi terakhir dan kurangi indeks.
  4. else { A[lastMerged--] = B[lastB--]; }: Jika elemen di 
𝐵
B lebih besar atau sama, masukkan ke posisi terakhir di array gabungan.

F. Menyalin Elemen Tersisa dari Array B:

  1. while (lastB >= 0) { A[lastMerged--] = B[lastB--]; }: Jika masih ada elemen yang tersisa di array 
𝐵
B, salin ke array 
𝐴
A.
G. Fungsi main:

  1. Inisialisasi array 
𝐴
A dan 
𝐵
B, serta jumlah elemen efektif.
  2. Mencetak array 
𝐴
A sebelum dan sesudah penggabungan.
  3. Memanggil fungsi mergeSortedArrays untuk menggabungkan 
𝐵
B ke dalam 
𝐴
A.

Kesimpulan
Program ini menggabungkan dua array yang sudah diurutkan dengan memulai dari elemen terbesar di masing-masing array. Dengan cara ini, kita dapat mengisi array 
𝐴
A dari belakang ke depan, memastikan bahwa elemen-elemen tetap terurut tanpa perlu menggunakan memori tambahan untuk array gabungan. Pendekatan ini efisien dan optimal untuk masalah yang diberikan.

CPMK 2 – SubCPMK 3
## Unguided 
### 1. [Soal]

Linear Search

Alur Linear Search:
  1. Mulai dari elemen pertama dalam array atau list.
  2. Bandingkan elemen saat ini dengan elemen yang dicari.
  3. Jika elemen saat ini adalah elemen yang dicari, algoritma berhenti dan elemen tersebut ditemukan.
  4. Jika elemen saat ini bukan elemen yang dicari, lanjutkan ke elemen berikutnya.
  5. Ulangi langkah 2-4 sampai elemen ditemukan atau seluruh elemen dalam array telah diperiksa.
  6. Jika mencapai akhir array dan elemen belum ditemukan, maka elemen tersebut tidak ada dalam array.

Runtime Linear Search:
  1. Best Case: O(1)
    A. Elemen yang dicari adalah elemen pertama dalam array.
  2. Worst Case: O(n)
    A. Elemen yang dicari adalah elemen terakhir dalam array atau tidak ada dalam array sama sekali. Dalam kasus ini, setiap elemen harus diperiksa satu per satu.

Binary Search

Alur Binary Search:
  1. Pastikan array atau list telah diurutkan.
  2. Tentukan titik tengah dari array: mid = (low + high) / 2.
  3. Bandingkan elemen di tengah dengan elemen yang dicari:
    A. Jika elemen tengah adalah elemen yang dicari, algoritma berhenti dan elemen tersebut ditemukan.
    B. Jika elemen tengah lebih besar daripada elemen yang dicari, fokus pencarian pada subarray sebelah kiri (dari low sampai mid - 1).
    C. Jika elemen tengah lebih kecil daripada elemen yang dicari, fokus pencarian pada subarray sebelah kanan (dari mid + 1 sampai high).
  4. Ulangi langkah 2-3 sampai elemen ditemukan atau subarray tidak lagi valid (low > high).
  5. Jika subarray tidak valid dan elemen belum ditemukan, maka elemen tersebut tidak ada dalam array.

Runtime Binary Search:
1. Best Case: O(1)
  A. Elemen yang dicari adalah elemen di tengah array pada percobaan pertama.
2. Worst Case: O(log n)
  B. Pada setiap langkah, ukuran array dikurangi setengah, sehingga waktu yang dibutuhkan untuk menemukan elemen dalam kasus terburuk adalah logaritma basis 2 dari jumlah elemen dalam array.
Perbandingan Utama:
1. Linear Search bekerja pada array yang tidak terurut maupun terurut, tetapi tidak efisien untuk array besar karena waktu komputasinya linear terhadap jumlah elemen.
2. Binary Search memerlukan array yang terurut, tetapi jauh lebih efisien untuk array besar karena waktu komputasinya logaritmik terhadap jumlah elemen.
Kedua algoritma memiliki kegunaan masing-masing tergantung pada situasi dan kondisi data yang ada. Linear Search lebih fleksibel, sementara Binary Search jauh lebih cepat pada array yang sudah terurut.

### 2. [Soal]
```C++
#include <iostream>
using namespace std;

int binary_search(int arr[], int size, int target) {
    int low = 0;
    int high = size - 1;

    while (low <= high) {
        int mid = (low + high) / 2; // Tentukan elemen tengah
        int mid_val = arr[mid];

        if (mid_val == target) {
            return mid; // Elemen ditemukan, kembalikan indeks elemen
        } else if (mid_val < target) {
            low = mid + 1; // Fokus pada subarray sebelah kanan
        } else {
            high = mid - 1; // Fokus pada subarray sebelah kiri
        }
    }

    return -1; // Elemen tidak ditemukan dalam array
}

int main() {
    int arr[] = {1, 3, 5, 7, 9, 11, 13, 15, 17, 19};
    int size = sizeof(arr) / sizeof(arr[0]);
    int target = 7;

    int result = binary_search(arr, size, target);
    if (result != -1) {
        cout << "Elemen ditemukan pada indeks " << result << endl;
    } else {
        cout << "Elemen tidak ditemukan dalam array" << endl;
    }

    return 0;
}

```
#### Output:
![Screenshot 2024-05-15 234204](https://github.com/egirizkiyan/Egi3/assets/162097461/c7983852-5273-4229-83eb-7700fe87bdd1)

#### Full code Screenshot:
![Screenshot 2024-05-15 234112](https://github.com/egirizkiyan/Egi3/assets/162097461/02a80827-8db0-477d-830c-952fbb08c30f)

