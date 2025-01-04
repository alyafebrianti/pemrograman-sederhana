# Project UAS Pemograman Sederhana Menginput Data Nilai Mahasiswa

## Class Data dan Class Proses
Berikut adalah penjelasan dari program Python di atas:

### Deskripsi Program
Program ini adalah sebuah aplikasi berbasis objek yang memungkinkan pengguna untuk mengelola data mahasiswa, seperti melihat data, menambah data, mengubah data, dan menghapus data. Program ini menggunakan Class Mahasiswa sebagai kerangka kerja utama untuk menyimpan dan memproses data mahasiswa.

---

### Penjelasan Tiap Bagian

#### 1. __init__ (Constructor)
```python
def __init__(self):
    self.data_mahasiswa = {}
```
- Fungsi: 
  - Konstruktor ini digunakan untuk menginisialisasi atribut data_mahasiswa, yang merupakan sebuah dictionary kosong untuk menyimpan data mahasiswa.
  - Setiap mahasiswa akan diidentifikasi menggunakan NIM sebagai kunci pada dictionary ini.

---

#### 2. lihat_data
```python
def lihat_data(self):
    if not self.data_mahasiswa:
```
- Fungsi: Menampilkan data mahasiswa yang ada di dalam dictionary data_mahasiswa.
- Penjelasan:
  1. Cek data kosong: 
     - Jika data_mahasiswa kosong, maka program akan menampilkan pesan bahwa tidak ada data yang tersimpan.
  2. Format tampilan: 
     - Data mahasiswa ditampilkan dalam bentuk tabel dengan kolom:
       - No: Nomor urut.
       - Nama: Nama mahasiswa.
       - NIM: Nomor Induk Mahasiswa.
       - Nilai Tugas, Nilai UTS, Nilai UAS, dan Nilai Akhir.
     - Nilai Akhir dihitung menggunakan rumus:
       
       ```python
       \[
       \text{Nilai Akhir} = (\text{Nilai Tugas} \times 0.3) + (\text{Nilai UTS} \times 0.35) + (\text{Nilai UAS} \times 0.35)
       \]
       ```
---

#### 3. tambah_data
```python
def tambah_data(self, nim, nama, tugas, uts, uas):
    nilai_akhir = (tugas  0.3) + (uts  0.35) + (uas  0.35)
    self.data_mahasiswa[nim] = {
        "nama": nama,
        "tugas": tugas,
        "uts": uts,
        "uas": uas,
        "nilai_akhir": nilai_akhir
    }
    print("Data berhasil ditambahkan!")
```

- Fungsi: Menambahkan data mahasiswa baru ke dalam dictionary data_mahasiswa.
- Parameter:
  - nim: Nomor Induk Mahasiswa.
  - nama: Nama mahasiswa.
  - tugas, uts, uas: Nilai tugas, UTS, dan UAS.
- Proses:
  - Menghitung Nilai Akhir berdasarkan formula yang sama.
  - Menyimpan data ke dalam dictionary data_mahasiswa dengan format:
    ```python
    {
        "nama": nama,
        "tugas": tugas,
        "uts": uts,
        "uas": uas,
        "nilai_akhir": nilai_akhir
    }
    ```
- Hasil: Menampilkan pesan bahwa data berhasil ditambahkan.

---

#### 4. ubah_data
python
def ubah_data(self, nim, nama=None, tugas=None, uts=None, uas=None):
    ...

- *Fungsi: Mengubah data mahasiswa yang sudah ada berdasarkan NIM.
- Parameter:
  - nim: Nomor Induk Mahasiswa (digunakan untuk mencari data mahasiswa).
  - nama, tugas, uts, uas: Nilai baru yang ingin diubah (opsional, bisa salah satu atau semuanya).
- Proses:
  - Mengecek apakah NIM ada dalam data_mahasiswa.
  - Memperbarui data yang diberikan (hanya jika nilai tidak None).
  - Menghitung ulang Nilai Akhir setelah data diperbarui.
- Hasil: Menampilkan pesan apakah data berhasil diubah atau tidak.

---

#### 5. hapus_data
```python
def hapus_data(self, nim):
    if nim in self.data_mahasiswa:
        del self.data_mahasiswa[nim]
        print("Data berhasil dihapus!")
    else:
        print("Data dengan NIM tersebut tidak ditemukan!")
```
- Fungsi: Menghapus data mahasiswa berdasarkan NIM.
- Proses:
  - Mengecek apakah NIM ada dalam data_mahasiswa.
  - Jika ditemukan, data dengan NIM tersebut dihapus dari dictionary.
  - Jika tidak ditemukan, menampilkan pesan bahwa data tidak ditemukan.
- Hasil: Menampilkan pesan apakah data berhasil dihapus atau tidak.

---

### Fitur Utama
1. Melihat Data Mahasiswa: Menampilkan data mahasiswa dalam bentuk tabel, termasuk Nilai Akhir.
2. Menambah Data Mahasiswa: Menambahkan data mahasiswa baru dengan nilai tugas, UTS, dan UAS.
3. Mengubah Data Mahasiswa: Mengubah data tertentu (nama atau nilai) dari mahasiswa yang sudah ada.
4. Menghapus Data Mahasiswa: Menghapus data mahasiswa berdasarkan NIM.

---

### Kelebihan
- Struktur yang rapi: Menggunakan pemrograman berbasis objek untuk mengelola data.
- Fleksibel: Metode ubah_data mendukung perubahan sebagian data (misalnya, hanya tugas atau nama saja).
- Interaktif: Memberikan pesan untuk setiap operasi, baik berhasil atau gagal.

## Class View dan Main
Berikut adalah penjelasan dari masing-masing metode:

---

### 1. Kelas InputForm
```python
class InputForm:
```
- Deskripsi: 
  - Kelas ini bersifat statis (tidak perlu membuat instance) karena semua metode didefinisikan dengan dekorator @staticmethod.
  - Tujuan utamanya adalah mengelompokkan metode untuk input data mahasiswa.

---

### 2. input_data
```python
@staticmethod
def input_data():
    nim = input("NIM: ")
    nama = input("Nama: ")
    tugas = float(input("Nilai Tugas: "))
    uts = float(input("Nilai UTS: "))
    uas = float(input("Nilai UAS: "))
    return nim, nama, tugas, uts, uas
```
- Fungsi: Mengambil input data mahasiswa secara lengkap dari pengguna.
- Penjelasan:
  1. NIM dan Nama:
     - input("NIM: "): Meminta input berupa NIM (String).
     - input("Nama: "): Meminta input berupa Nama mahasiswa (String).
  2. Nilai Tugas, UTS, dan UAS:
     - float(input("Nilai Tugas: ")): Mengambil input untuk nilai tugas dan mengonversinya menjadi tipe float (karena nilai adalah angka desimal).
     - Demikian pula untuk nilai UTS dan UAS.
  3. Pengembalian (Return):
     - Mengembalikan tuple berisi data: (nim, nama, tugas, uts, uas).

- Contoh Penggunaan:
  - Jika pengguna menginput:
    
    NIM: 12345
    Nama: Budi
    Nilai Tugas: 80
    Nilai UTS: 85
    Nilai UAS: 90
    
  - Maka outputnya adalah:
    python
    ('12345', 'Budi', 80.0, 85.0, 90.0)
    

---

### 3. input_ubah_data
```python
@staticmethod
def input_ubah_data():
    nim = input("Masukkan NIM: ")
    print("Masukkan data baru (tekan Enter jika tidak ingin mengubah):")
    nama = input("Nama: ").strip() or None
    tugas = input("Nilai Tugas: ").strip()
    tugas = float(tugas) if tugas else None
    uts = input("Nilai UTS: ").strip()
    uts = float(uts) if uts else None
    uas = input("Nilai UAS: ").strip()
    uas = float(uas) if uas else None
    return nim, nama, tugas, uts, uas
```
- Fungsi: Mengambil input data baru untuk mengubah data mahasiswa yang sudah ada.
- Penjelasan:
  1. Input NIM:
     - nim = input("Masukkan NIM: "): Meminta pengguna memasukkan NIM mahasiswa yang datanya ingin diubah.
  2. Meminta Data Baru:
     - Pengguna diberi opsi untuk mengubah nilai-nilai tertentu (nama, tugas, UTS, atau UAS).
     - Jika pengguna menekan Enter tanpa mengetik apa pun, data tersebut dianggap tidak diubah.
     - Proses Pengolahan Input:
       - nama = input("Nama: ").strip() or None:
         - Menghilangkan spasi di awal/akhir input dengan .strip().
         - Jika input kosong, diisi dengan None.
       - tugas = float(tugas) if tugas else None:
         - Jika pengguna mengisi nilai tugas, diubah menjadi tipe float.
         - Jika kosong, diisi dengan None.
       - Proses serupa dilakukan untuk uts dan uas.
  3. Pengembalian (Return):
     - Mengembalikan tuple berisi data: (nim, nama, tugas, uts, uas).

- Contoh Penggunaan:
  - Jika pengguna menginput:
    
    Masukkan NIM: 12345
    Masukkan data baru (tekan Enter jika tidak ingin mengubah):
    Nama: Budi Santoso
    Nilai Tugas: 
    Nilai UTS: 87
    Nilai UAS: 
    
  - Maka outputnya adalah:
    
    ```python
    ('12345', 'Budi Santoso', None, 87.0, None)
    ```

### Kesimpulan
Kelas InputForm menyediakan dua metode:
1. input_data:
   - Untuk menambahkan data baru dengan input lengkap.
2. input_ubah_data:
   - Untuk mengubah data yang sudah ada, dengan fleksibilitas memilih data mana yang ingin diubah.

### Kelebihan
- Fleksibel:
  - Pengguna dapat memilih untuk mengubah sebagian atau semua data melalui input_ubah_data.
- Efisien:
  - Input diolah langsung menjadi tipe data yang benar (float) sehingga mempermudah pengolahan lebih lanjut.

Berikut adalah penjelasan mendetail dari setiap bagian:

---

### 1. Import Statement
```python
from data.mahasiswa import Mahasiswa
from view.input_form import InputForm
from view.mahasiswa import ViewMahasiswa
```
- Import Mahasiswa:
  - Berasal dari modul data.mahasiswa, ini adalah kelas yang mengelola data mahasiswa, seperti menambah, mengubah, menghapus, dan menampilkan data.

- Import InputForm:
  - Berasal dari modul view.input_form, digunakan untuk menangani input data dari pengguna (baik untuk menambah atau mengubah data).

- Import ViewMahasiswa:
  - Berasal dari modul view.mahasiswa, bertugas untuk menampilkan data mahasiswa.

---

### **2. Fungsi main**
```python
def main():
    mahasiswa = Mahasiswa()
```
- *Deskripsi*:
  - Fungsi utama program yang berisi menu interaktif untuk pengguna.
  - Membuat objek mahasiswa dari kelas Mahasiswa untuk mengelola data.

---

### **3. **Perulangan Utama (while True)**
```python
while True:
    pilihan = input("[(L)ihat (T)ambah (U)bah (H)apus (K)eluar] : ").lower()
```
- *Tujuan*:
  - Menyediakan menu interaktif untuk pengguna sampai mereka memilih opsi keluar (K).
  - Menggunakan perintah input untuk menerima pilihan dari pengguna.
  - Fungsi lower() memastikan input selalu dalam huruf kecil untuk memudahkan pengecekan.

---

### *4. **Pilihan Menu*

#### *a. Pilihan "L" (Lihat Data)*
```python
if pilihan == 'l':
    ViewMahasiswa.tampilkan_data(mahasiswa)
```
- *Deskripsi*:
  - Memanggil metode tampilkan_data dari kelas ViewMahasiswa, yang pada gilirannya memanggil lihat_data dari objek mahasiswa.
  - Menampilkan semua data mahasiswa yang sudah terdaftar dalam format tabel.

---

#### *b. Pilihan "T" (Tambah Data)*
```python
elif pilihan == 't':
    nim, nama, tugas, uts, uas = InputForm.input_data()
    mahasiswa.tambah_data(nim, nama, tugas, uts, uas)
```
- *Deskripsi*:
  1. Menggunakan metode input_data dari InputForm untuk meminta pengguna memasukkan data mahasiswa:
     - *NIM, Nama, Nilai Tugas, Nilai UTS, Nilai UAS*.
  2. Memanggil metode tambah_data dari objek mahasiswa untuk menyimpan data tersebut.
  3. Data disimpan dalam dictionary data_mahasiswa.

---

#### *c. Pilihan "U" (Ubah Data)*
```python
elif pilihan == 'u':
    nim, nama, tugas, uts, uas = InputForm.input_ubah_data()
    mahasiswa.ubah_data(nim, nama, tugas, uts, uas)
```
- *Deskripsi*:
  1. Menggunakan metode input_ubah_data dari InputForm untuk meminta pengguna memasukkan data baru.
     - Pengguna dapat mengubah salah satu atau semua informasi mahasiswa berdasarkan NIM.
  2. Memanggil metode ubah_data dari objek mahasiswa untuk memperbarui data.

---

#### *d. Pilihan "H" (Hapus Data)*
```python
elif pilihan == 'h':
    nim = input("Masukkan NIM yang akan dihapus: ")
    mahasiswa.hapus_data(nim)
```
- *Deskripsi*:
  1. Meminta input *NIM* mahasiswa yang datanya ingin dihapus.
  2. Memanggil metode hapus_data dari objek mahasiswa untuk menghapus data berdasarkan NIM.
  3. Jika NIM tidak ditemukan, program akan menampilkan pesan kesalahan.

---

#### *e. Pilihan "K" (Keluar Program)*
```python
elif pilihan == 'k':
    print("Program selesai.")
    break
```
- *Deskripsi*:
  - Menampilkan pesan "Program selesai." dan keluar dari perulangan menggunakan perintah break.

---

#### *f. Pilihan Lain (Invalid)*
```python
else:
    print("Pilihan tidak valid!")
```
- *Deskripsi*:
  - Jika pengguna memasukkan pilihan yang tidak valid, program menampilkan pesan kesalahan.

---

### *5. Blok Eksekusi Utama*
```python
if __name__ == "__main__":
    main()
```
- *Tujuan*:
  - Memastikan fungsi main() hanya dijalankan jika file ini dieksekusi secara langsung, bukan diimpor sebagai modul.
  - *Best Practice*: Membantu menjaga modularitas kode.

---

### *Alur Program*
1. *Program dimulai*, objek Mahasiswa dibuat.
2. *Menu ditampilkan* kepada pengguna:
   - *L*: Melihat data mahasiswa.
   - *T*: Menambah data mahasiswa.
   - *U*: Mengubah data mahasiswa.
   - *H*: Menghapus data mahasiswa.
   - *K*: Keluar dari program.
3. Berdasarkan input, program menjalankan perintah sesuai pilihan.
4. *Program terus berjalan* hingga pengguna memilih "K" untuk keluar.

---

### *Kelebihan*
1. *Modular*:
   - Kode dipisahkan ke dalam beberapa modul (data, view, dan fungsi utama), sehingga mudah untuk dibaca, diuji, dan dikembangkan.
2. *Interaktif*:
   - Program menyediakan antarmuka sederhana untuk pengguna dalam bentuk menu teks.
3. *Reusable Components*:
   - Komponen seperti InputForm dan ViewMahasiswa dapat digunakan kembali di program lain.

---

## Link Video
https://youtu.be/SZlYENflYjE?si=P9CodPHUSRt5O51k

## Flowchart
![Flowchart](/flowchart.png)
