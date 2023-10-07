# List API yang Tersedia
## generate-token

"generate-token" merupakan API yang digunakan untuk menghasilkan token sebagai autorisasi ketika user melakukan pemesanan pengiriman. API ini merupakan API jenis GET yang berperan untuk mendapatkan data dari backend. Berikut adalah contoh payload yang dikirimkan oleh API "generate-token":
```
Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6IndpZGlhbXVzeWFyb2ZhaDE5QGdtYWlsLmNvbSIsImV4cCI6MjU2MDQyNTM3NywiaWQiOjF9.BSiXVZVo8Kq5vRocEv4BIJ2JKXjUoXbGMHavqyc_zWE
```
## show-token

"show-token" merupakan API yang digunakan untuk merupakan API yang digunakan untuk menampilkan token yang sudah dihasilkan sebelumnya saat user melakukan pemesanan pengiriman. API ini merupakan API jenis GET yang berperan untuk mendapatkan data dari backend. Berikut adalah contoh payload yang dikirimkan oleh API "show-token":
```
Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6IndpZGlhbXVzeWFyb2ZhaDE5QGdtYWlsLmNvbSIsImV4cCI6MjU2MDQyNTM3NywiaWQiOjF9.BSiXVZVo8Kq5vRocEv4BIJ2JKXjUoXbGMHavqyc_zWE
```

## create-order

"create-order" merupakan API yang digunakan oleh user untuk melakukan pemesanan pengiriman. API ini merupakan API jenis POST yang berperan untuk mendorong data ke backend kemudian mendapatkan respon dari backend. Berikut adalah contoh payload yang dikirimkan oleh API "create-order":
```
{
    "layanan": "ncs", // ekpedisi yang digunakan
    "kode_layanan": "UDRREG", // jenis layanan (ex : REG)
    "metode_pickup": "pickup", // pickup/dropoff
    "tipe_transaksi": 0, // cod (1) / non-cod (0)
    "id_alamat_pengirim": 50, // id_kecamatan_lkp
    "nama_penerima": "Sulistari", // nama penerima
    "no_hp_penerima": "08579142977", // no hp penerima
    "id_kecamatan_penerima": 2934, // id kecamatan lkp
    "alamat_penerima": "Jl. Sendorow", // alamat penerima
    "etd": "3-5 Hari", // estimasi dari ongkir api
    "asuransi": 0, // asuransi ada atau tidak (jika ada tulis total asuransi)
    "custome_cod": 0, // nilai cod custome input
    "ongkir": 10000, // ongkir di dapat dari api ongki
    "biaya_cod": 1000, // biaya cod di dapat input kalkulasi harga produk
    "total": 11000, // total di dapat input kalkulasi ongkir + harga produk + asuransi
    "pencairan": 10000, // harga produk/custome cod
    "id_produk": 1, // id produk (0 jika tidak ada produk atau buat baru)
    "harga_produk": 10000, // harga produk
    "nama_produk": "Baju Anak", // nama produk
    "notes": "Baju anak-anak", // catatan produk
    "jumlah_produk": 1, // jumlah produk dikrim
    "dimensi_produk": 1, // 0 jika tidak pakai, 1 jika pakai
    "lebar_produk": 0.1, // jika menggunakan dimensi produk
    "panjang_produk": 0.1, // jika menggunakan dimensi produk
    "tinggi_produk": 0.1, // jika menggunakan dimensi produk
    "diskon_ongkir": 0, // di dapat dari kalulasi ongkir kesepakatan juragancod
    "berat": 0.5, // berat keseluruhan paket
    "waktu_pickup": "2023-05-20 21:04" // request pickup
}
//pickup/dropoff
```
!> **Pengisian value variabel "layanan" harus sesuai dengan layanan ekspedisi yang ada, dan "kode_layanan" harus sesuai dengan layanan yang dipilih.**

**Berikut layanan ekspedisi yang dapat dipilih beserta kode layanannya** (**'NAMA EKSPEDISI'** - "layanan"/"kode_layanan"1, "kode_layanan"2, ...):  
1. **JNE** - "jne"/"CTCJTR23", "JTR250", "JTR<150", "JTR>250", "CTC23", "CTCSPS23", "CTCYES23",
2. **SiCepat** - "sicepat"/"GOKIL", "REG", "SIUNT"
3. **IDEXPRESS** - "id_express"/"06", "00"
4. **NCS** - "ncs"/"NRS(Regular Service)"
5. **SAP** - "sap"/"UDRREG"

## address

"address" merupakan API yang digunakan untuk mendapatkan data mengenai alamat pengirim yang sudah terdaftarkan ke akun user. API ini merupakan API jenis GET sehingga sistem kerja API hanya meminta data dari backend tanpa mendorong data ke backend. Berikut adalah contoh payload yang dikirimkan oleh API "address":
```
Authorization: EGJO50oWAalDLo+xcDuBAKDXL+SPd4Vwzb4uq12OyIQwl6BxC8QktKQmQsCn0Zy7XJS3rJOr3s3PfIItSNjr8myYbo2Y/sahyzA=
```

## address-add

"address-add" merupakan API yang digunakan untuk menambahkan data mengenai alamat pengirim ke dalam akun user. API ini merupakan API jenis POST sehingga perannya mendorong data ke backend. Berikut adalah contoh payload yang dikirimkan oleh API "address-add":
```
{
    "pengirim": "Samsudin", // nama pengirim
    "no_hp": "6285673830927", // nomor handphone pengirim
    "alamat": "Jl. Magelang, Sleman", // alamat pengirim
    "id_kecamatan_lkp": 12, // id kecamatan pengirim
    "nm_kecamatan_lkp": "Sleman" // nama kecamatan pengirim
}
```

## get-kecamatan

"get-kecamatan" adalah API yang digunakan untuk menampilkan data mengenai kecamatan. API ini merupakan API jenis GET yang berperan untuk mendapatkan data dari backend. Berikut adalah contoh payload yang dikirimkan oleh API "get-kecamatan":
```
Authorization: EGJO50oWAalDLo+xcDuBAKDXL+SPd4Vwzb4uq12OyIQwl6BxC8QktKQmQsCn0Zy7XJS3rJOr3s3PfIItSNjr8myYbo2Y/sahyzA=
```

## check-ongkir

"check-ongkir" adalah API yang digunakan oleh user untuk mendapatkan data mengenai ongkos kirim pengiriman. API ini merupakan API jenis POST sehingga user mendorong data ke backend untuk mendapatkan data mengenai ongkos kirim yang harus ditanggung. Berikut adalah contoh payload yang dikirimkan oleh API "check-ongkir":
```
{
    "berat": 1, // berat produk
    "berat_dimensi": 1, // berat dimensi ya (1) atau tidak (0)
    "lebar": 1.0, // jika berat dimensi 1
    "panjang": 1.0, // jika berat dimensi 1
    "tinggi": 1.0, // jika berat dimensi 1
    "id_kecamatan_penerima": 3239, // id od atau kecamatan_lkp
    "id_kecamatan_pengirim": 3239 // id od atau kecamatan_lkp
}
```

## delivery-show

"delivery-show" merupakan API yang digunakan untuk mengetahui detail pesanan pengiriman yang telah dilakukan oleh user. API ini merupakan API jenis GET sehingga user tidak mendorong data apapun ke backend. Berikut adalah contoh payload yang dikirimkan oleh API "delivery-show":
```
Authorization: EGJO50oWAalDLo+xcDuBAKDXL+SPd4Vwzb4uq12OyIQwl6BxC8QktKQmQsCn0Zy7XJS3rJOr3s3PfIItSNjr8myYbo2Y/sahyzA=
```

## show-catalog-product

"show-catalog-product" Merupakan API yang digunakan untuk mengetahui katalog dari produk yang sudah didaftarkan oleh user. API ini merupakan API jenis GET sehingga user tidak mendorong data apapun ke backend. Berikut adalah contoh payload yang dikirimkan oleh API "show-catalog-product":
```
Authorization: EGJO50oWAalDLo+xcDuBAKDXL+SPd4Vwzb4uq12OyIQwl6BxC8QktKQmQsCn0Zy7XJS3rJOr3s3PfIItSNjr8myYbo2Y/sahyzA=
```

## show-catalog-product-by-id

"show-catalog-product-by-id" hampir sama seperti "show-catalog-product" hanya dengan pengurutan berdasarkan id katalog. Berikut adalah contoh payload yang dikirimkan oleh API "show-catalog-product-by-id":
```
Authorization: EGJO50oWAalDLo+xcDuBAKDXL+SPd4Vwzb4uq12OyIQwl6BxC8QktKQmQsCn0Zy7XJS3rJOr3s3PfIItSNjr8myYbo2Y/sahyzA=
```

## delete-catalog-product

"delete-catalog-product" merupakan API yang digunakan untuk menghapus katalog dari produk yang sudah didaftarkan user sehingga tidak terjadi tumpang tindih di database. API ini adalah API dengan jenis DELETE yang mengirimkan perintah kepada backend untuk menghapus data tertentu. Berikut adalah contoh payload yang dikirimkan oleh API "delete-catalog-product":
```
Authorization: EGJO50oWAalDLo+xcDuBAKDXL+SPd4Vwzb4uq12OyIQwl6BxC8QktKQmQsCn0Zy7XJS3rJOr3s3PfIItSNjr8myYbo2Y/sahyzA=
```
