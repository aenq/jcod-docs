
# List API yang Tersedia

___

## generate-token

*generate-token* merupakan API yang digunakan untuk menghasilkan token sebagai autorisasi ketika user melakukan pemesanan pengiriman. API ini merupakan API jenis GET yang berperan untuk mendapatkan data dari backend. Berikut adalah contoh payload yang dikirimkan oleh API "generate-token":
```
Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6IndpZGlhbXVzeWFyb2ZhaDE5QGdtYWlsLmNvbSIsImV4cCI6MjU2MDQyNTM3NywiaWQiOjF9.BSiXVZVo8Kq5vRocEv4BIJ2JKXjUoXbGMHavqyc_zWE
```

!> Setiap akun hanya dapt memiliki 1 token. Apabila user ingin membuat token baru, maka token yang lama tidak akan dapat digunakan

___

## show-token

*show-token* merupakan API yang digunakan untuk merupakan API yang digunakan untuk menampilkan token yang sudah dihasilkan sebelumnya saat user melakukan pemesanan pengiriman. API ini merupakan API jenis GET yang berperan untuk mendapatkan data dari backend. Berikut adalah contoh payload yang dikirimkan oleh API "show-token":
```
Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6IndpZGlhbXVzeWFyb2ZhaDE5QGdtYWlsLmNvbSIsImV4cCI6MjU2MDQyNTM3NywiaWQiOjF9.BSiXVZVo8Kq5vRocEv4BIJ2JKXjUoXbGMHavqyc_zWE
```
___

## create-order

*create-order* merupakan API yang digunakan oleh user untuk melakukan pemesanan pengiriman. API ini merupakan API jenis POST yang berperan untuk mendorong data ke backend kemudian mendapatkan respon dari backend. Berikut adalah contoh payload yang dikirimkan oleh API "create-order":

!> semua data tidak boleh ***null***

```json
{
    "layanan": "ncs",
    "kode_layanan": "UDRREG",
    "metode_pickup": "pickup",
    "tipe_transaksi": 0,
    "id_alamat_pengirim": 50,
    "nama_penerima": "Sulistari",
    "no_hp_penerima": "08579142977",
    "id_kecamatan_penerima": 2934,
    "alamat_penerima": "Jl. Sendorow",
    "etd": "3-5 Hari",
    "asuransi": 0,
    "custome_cod": 0,
    "ongkir": 10000,
    "biaya_cod": 1000,
    "total": 11000,
    "pencairan": 10000,
    "id_produk": 1,
    "harga_produk": 10000,
    "nama_produk": "Baju Anak",
    "notes": "Baju anak-anak",
    "jumlah_produk": 1,
    "dimensi_produk": 1,
    "lebar_produk": 0.1,
    "panjang_produk": 0.1,
    "tinggi_produk": 0.1,
    "diskon_ongkir": 0,
    "berat": 0.5,
    "waktu_pickup": "2023-05-20 21:04"
}
//pickup/dropoff
```

### *layanan* dan *kode_layanan* (string)

Variabel *layanan* merupakan layanan ekspedisi yang user ingin gunakan. **Pengisian variabel *layanan* harus sesuai dengan Layanan ekspedisi yang tersedia (JNE, SiCepat, ID Express, NCS, atau SAP).** Sementara, *kode_layanan* adalah jenis layanan yang diberikan oleh ekspedisi yang dipilih sehingga **pengisian** *kode_layanan* **harus sesuai dengan jenis layanan yang disediakan oleh layanan ekspedisi.** Berikut layanan ekspedisi yang dapat dipilih beserta jenis layanannya:

|Nama Ekspedisi|*layanan*|*kode_layanan*|
|--------------|---------|--------------|
|JNE|"jne"|"CTCJTR23", "JTR250", "JTR<150", "JTR>250", "CTC23", "CTCSPS23", "CTCYES23"|
|SiCepat|"sicepat"|"GOKIL", "REG", "SIUNT"|
|ID Express|"id_express"|"06", "00"|
|NCS|"ncs"|"NRS(Regular Service)"|
|SAP|"sap"|"UDRREG"|

### *metode_pickup* (string)

Variabel *metode_pickup* merupakan pilihan yang diberikan kepada user mengenai cara pengambilan paket yang akan dikirimkan. Pengirim dapat memilih agar paketnya dijemput di rumah kemudian dikirimkan kepada penerima paket, dengan kata lain pickup; atau paket yang akan dikirimkan diantar ke pihak ekspedisi agar paket tersebut dikirimkan kepada pihak penerima, atau dropoff. **Jika user ingin menggunakan metode pickup, maka variabel *metode_pickup* diisi dengan value "pickup"; sementara, jika user ingin menggunakan metode dropoff, maka variabel diisi dengan value "dropoff"**

### *tipe_transaksi* (boolean)

Variabel *tipe_transaksi* merupakan pilihan yang diberikan kepada user mengenai cara pembayaran terhadap paket atau barang yang dikirimkan. Variabel ini menggunakan value dengan jenis data boolean; isi "1" untuk menggunakan metode pembayaran cash on deliver (COD), atau isi "0" untuk menggunakan metode pembayaran non-COD.

### *id_alamat_pengirim* dan *id_kecamtan_penerima* (integer)

Variabel *id_alamat_pengirim* menunjukkan alamat asal pengirim paket; sementara, *id_kecamatan_penerima* merupakan asal kecamatan penerima paket. Value dari variable *id_alamat_pengirim* dan *id_kecamatan_penerima* harus sesuai dengan id alamat yang tersedia dan dapat diambil menggunakan API [get-kecamatan](#get-kecamatan)

### *etd* (string)

Varabel *etd* menunjukkan estimasi lama pengiriman. Value *etd* harus sesuai dengan data yang diberikan oleh API ongkir

### *asuransi* (integer)

Untuk menggunakan layanan asuransi dari JuraganCOD, harus mengikuti syarat dan ketentuan dari Website JuraganCOD. Variabel *asuransi* adalah biaya dalam mata uang IDR yang digunakan untuk menggunakan layanan asuransi. Jika tidak menggunakan asuransi, maka value yang diisikan sejumlah "0"

### *custome_cod* (integer)

*custome_cod* adalah variabel yang menunjukkan biaya COD yang dimodifikasi oleh pihak pengirim atau penjual. Value diisi sebanyak yang diinginkan dalam mata uang rupiah

### *ongkir* (integer)

*ongkir* merupakan variabel yang menunjukkan ongkos kirim yang harus ditanggung. Data biaya dapat didapatkan menggunakan API ongkir

### *total* (integer)

*total* merupakan variabel yang menunjukkan harga total yang harus dibayarkan. Harga total didaptkan dengan menambahkan harga produk, ongkos kirim, dan asuransi.

### *id_produk* (integer)

Variabel *id_produk* menunjukkan produk yang ingin dikirimkan. Produk dapat berupa produk yang telah didaftarkan ke server (value yang diisikan sesuai dengan id produknya, dapat dilihat menggunakan API [show-catalog-product](#show-catalog-product)) atau dengan membuat produk baru (diisi menggunakan value "0")

### *harga_produk* (integer)

Variabel *harga_produk* menunjukkan jumlah harga dalam mata uang IDR terkait produk yang akan dikirimkan sendiri (tidak termasuk ongkos kirim dan asuransi).

### *jumlah_produk* (integer)

Variabel *jumlah_produk* menunjukkan banyaknya produk yang akan dikirimkan

### *dimensi_produk* (integer)

Variabel *dimensi_produk* merupakan pilihan yang diberikan kepada user untuk menentukan paketnya diukur bersarakan dimensi atau tidak. Variabel ini merupakan data boolean, sehingga jika paketnya diukur berdasarkan dimensi, maka diisi dengan value "1"; jika tidak, maka diisi dengan value "0"

### *lebar_produk*, *panjang_produk*, dan *tinggi_produk* (float)

Variabel ini hanya akan efektif apabila *dimensi_produk* diset "1" yang menunjukkan lebar produk (*lebar_produk*), panjang produk (*panjang_produk*), dan tinggi produk (*tinggi_produk*) dengan satuan meter.

### *diskon_ongkir* (integer)

Variabel *diskon_ongkir* merupakan harga pengurang menurut IDR yang didapatkan berdasarkan kesepakatan dengan pihak JuraganCOD

### *berat* (float)

Variabel *berat* menunjukkan berat paket yang akan dikirim dengan satuan kilogram.

### *waktu_pickup* (string)

*waktu_pickup* hanya akan efektif ketika user memilih metode pickup. Variabel ini menunjukan waktu paket akan di-pickup.
___

## address

*address* merupakan API yang digunakan untuk mendapatkan data mengenai alamat pengirim yang sudah terdaftarkan ke akun user. API ini merupakan API jenis GET sehingga sistem kerja API hanya meminta data dari backend tanpa mendorong data ke backend. Berikut adalah contoh payload yang dikirimkan oleh API "address":
```
Authorization: EGJO50oWAalDLo+xcDuBAKDXL+SPd4Vwzb4uq12OyIQwl6BxC8QktKQmQsCn0Zy7XJS3rJOr3s3PfIItSNjr8myYbo2Y/sahyzA=
```
___

## address-add

*address-add* merupakan API yang digunakan untuk menambahkan data mengenai alamat pengirim ke dalam akun user. API ini merupakan API jenis POST sehingga perannya mendorong data ke backend. Berikut adalah contoh payload yang dikirimkan oleh API "address-add":
```json
{
    "pengirim": "Samsudin",
    "no_hp": "6285673830927",
    "alamat": "Jl. Magelang, Sleman",
    "id_kecamatan_lkp": 12,
    "nm_kecamatan_lkp": "Sleman"
}
```
### *pengirim* (string)

Variabel ini menunjukkan nama dari pengirim

### *no_hp* (integer)

Variabel ini menunjukkan no_hp dari pengirim

### *alamat* (string)

Variabel ini menunjukkan alamat dari pengirim

### *id_kecamatan_lkp* (integer)

Variabel ini menunjukkan id dari kecamatan asal pengirim. Data id kecamatan dapat didapatkan dari API [get-kecamatan](#get-kecamatan)

### *nm_kecamatan_lkp* (integer)

Variabel ini menunjukkan nama dari kecamatan asal pengirim
___

## get-kecamatan

*get-kecamatan* adalah API yang digunakan untuk menampilkan data mengenai kecamatan. API ini merupakan API jenis GET yang berperan untuk mendapatkan data dari backend. Berikut adalah contoh payload yang dikirimkan oleh API "get-kecamatan":
```
Authorization: EGJO50oWAalDLo+xcDuBAKDXL+SPd4Vwzb4uq12OyIQwl6BxC8QktKQmQsCn0Zy7XJS3rJOr3s3PfIItSNjr8myYbo2Y/sahyzA=
```
___

## check-ongkir

*check-ongkir* adalah API yang digunakan oleh user untuk mendapatkan data mengenai ongkos kirim pengiriman. API ini merupakan API jenis POST sehingga user mendorong data ke backend untuk mendapatkan data mengenai ongkos kirim yang harus ditanggung. Berikut adalah contoh payload yang dikirimkan oleh API "check-ongkir":
```json
{
    "berat": 1,
    "berat_dimensi": 1,
    "lebar": 1.0,
    "panjang": 1.0,
    "tinggi": 1.0,
    "id_kecamatan_penerima": 3239,
    "id_kecamatan_pengirim": 3239
}
```

### *berat* (integer)

Variabel *berat* menunjukkan berat paket yang akan dicek ongkos kirimnya dengan satuan kilogram.

### *berat_dimensi* (boolean)

Variabel *berat_dimensi* merupakan pilihan yang diberikan kepada user untuk menentukan paketnya diukur bersarakan dimensi atau tidak. Variabel ini merupakan data boolean, sehingga jika paketnya diukur berdasarkan dimensi, maka diisi dengan value "1"; jika tidak, maka diisi dengan value "0"

### *lebar*, *panjang*, dan *tinggi* (float)

Variabel ini hanya akan efektif apabila *berat_dimensi* diset "1" yang menunjukkan lebar produk (*lebar*), panjang produk (*panjang*), dan tinggi produk (*tinggi*) dengan satuan meter.

### *id_kecamatan_penerima* (integer)

Variabel ini menunjukkan id dari kecamatan asal penerima. Data id kecamatan dapat didapatkan dari API [get-kecamatan](#get-kecamatan)

### *id_kecamatan_pengirim* (integer)

Variabel ini menunjukkan id dari kecamatan asal pengirim. Data id kecamatan dapat didapatkan dari API [get-kecamatan](#get-kecamatan)
___

## delivery-show

*delivery-show* merupakan API yang digunakan untuk mengetahui detail pesanan pengiriman yang telah dilakukan oleh user. API ini merupakan API jenis GET sehingga user tidak mendorong data apapun ke backend. Berikut adalah contoh payload yang dikirimkan oleh API "delivery-show":
```
Authorization: EGJO50oWAalDLo+xcDuBAKDXL+SPd4Vwzb4uq12OyIQwl6BxC8QktKQmQsCn0Zy7XJS3rJOr3s3PfIItSNjr8myYbo2Y/sahyzA=
```

## show-catalog-product

*show-catalog-product* Merupakan API yang digunakan untuk mengetahui katalog dari produk yang sudah didaftarkan oleh user. API ini merupakan API jenis GET sehingga user tidak mendorong data apapun ke backend. Berikut adalah contoh payload yang dikirimkan oleh API "show-catalog-product":
```
Authorization: EGJO50oWAalDLo+xcDuBAKDXL+SPd4Vwzb4uq12OyIQwl6BxC8QktKQmQsCn0Zy7XJS3rJOr3s3PfIItSNjr8myYbo2Y/sahyzA=
```
___

## show-catalog-product-by-id

*show-catalog-product-by-id* hampir sama seperti *show-catalog-product* hanya dengan pengurutan berdasarkan id katalog. Berikut adalah contoh payload yang dikirimkan oleh API "show-catalog-product-by-id":
```
Authorization: EGJO50oWAalDLo+xcDuBAKDXL+SPd4Vwzb4uq12OyIQwl6BxC8QktKQmQsCn0Zy7XJS3rJOr3s3PfIItSNjr8myYbo2Y/sahyzA=
```
___

## delete-catalog-product

*delete-catalog-product* merupakan API yang digunakan untuk menghapus katalog dari produk yang sudah didaftarkan user sehingga tidak terjadi tumpang tindih di database. API ini adalah API dengan jenis DELETE yang mengirimkan perintah kepada backend untuk menghapus data tertentu. Berikut adalah contoh payload yang dikirimkan oleh API "delete-catalog-product":
```
Authorization: EGJO50oWAalDLo+xcDuBAKDXL+SPd4Vwzb4uq12OyIQwl6BxC8QktKQmQsCn0Zy7XJS3rJOr3s3PfIItSNjr8myYbo2Y/sahyzA=
```
___
