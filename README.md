package binarysearch;
/*
Nama              : Dian Avila
NIM               : 250401010377
Kelas             : IF207
Mata Kuliah       : Struktur Data dan Algoritma
Dosen Pengajar    : Alun Sujjada, S.Kom., M.T
*/

public class Binarysearch {

    public static void main(String[] args) {

        int[] data = {19, 40, 10, 90, 2, 50, 60, 50, 1};
        int[] indeks = {1, 2, 3, 4, 5, 6, 7, 8, 9};
        
        for (int i = 0; i < data.length - 1; i++) {
            for (int j = 0; j < data.length - 1 - i; j++) {

                if (data[j] > data[j + 1]) {

                    int temp = data[j];
                    data[j] = data[j + 1];
                    data[j + 1] = temp;

                    int tempIndeks = indeks[j];
                    indeks[j] = indeks[j + 1];
                    indeks[j + 1] = tempIndeks;
                }
            }
        }

        cari(data, indeks, 1);

        cari(data, indeks, 50);

        cari(data, indeks, 100);
    }
    public static void cari(int[] data, int[] indeks, int angka) {

        int kiri = 0;
        int kanan = data.length - 1;
        boolean ditemukan = false;

        while (kiri <= kanan) {

            int tengah = (kiri + kanan) / 2;

            if (data[tengah] == angka) {
                ditemukan = true;
                break;
            } else if (data[tengah] < angka) {
                kiri = tengah + 1;
            } else {
                kanan = tengah - 1;
            }
        }

        System.out.println("Input : " + angka);

        if (ditemukan) {

            System.out.print("Output : Angka " + angka + " ada di indeks ke ");

            boolean pertama = true;

            for (int i = 0; i < data.length; i++) {

                if (data[i] == angka) {

                    if (!pertama) {
                        System.out.print(" dan ");
                    }

                    System.out.print(indeks[i]);
                    pertama = false;
                }
            }

            System.out.println();

        } else {

            System.out.println("Output : Angka " + angka
                    + " tidak ada dalam array");
        }
        System.out.println();
/*
Angka sesuai urutan aslinya
Karena Binary Search butuh data urut
diurutkan secara manual,angka asli ikut ditukar agar posisi awal diketahui
Binary Search gunanya untuk mencari angka
1 (urutan 9), 50(urutan 6 & 8), dan 100 Tidak ada
*/
    }
}
