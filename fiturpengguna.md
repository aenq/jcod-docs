# Fitur Pengguna

Berikut adalah fitur yang dapat digunakan oleh user:
1. Pengelolaan akun dan profil(User)
    * <a href="/#/fiturpengguna?id=register">Register</a>
    * <a href="#/sidebar/login">Login</a>
    * <a href="#/">Lupa Password</a>
    * <a href="#/">Edit Profile</a>
    * <a href="#/">Member</a>
2. Transaksi(transactions)
    * <a href="#/">Buat Pengiriman</a>
    * <a href="#/">Cek Resi</a>
    * <a href="#/sidebar/cekongkir">Cek Ongkos Kirim</a>
    * <a href="#/">Membuat Rekap Pembelian</a>
    * <a href="#/">Tiket dan Claim</a>
    * <a href="#/">Katalog Produk</a>
3. Keuangan(finance)
    * <a href="#/">Pembayaran</a>
    * <a href="#/">Penarikan Saldo</a>
    * <a href="#/">Cek Saldo</a>

> ## Pengelolaan Akun dan Profil

### Register

Tahap melakukan registrasi akun:
1. Mengisi form register
2. Verifikasi nomor Whatsapp
3. Verifikasi email

#### Mengisi form register
![Halaman Register](../images/register.png)
- Silahkan akses <b>JuraganCOD.com</b>
- Klik <b>Daftar</b>
- Isi form pendaftaran <br>
Contoh data JSON untuk dikirim melalui API <b><i>register-seller</i></b>:
```
{
    "fullname": "M Dhifta",
    "email": "dhifta48@gmail.com",
    "password": "123456",
    "phone_number":"6285791419626",
    "code_referal": ""
}
```

!> Hal yang perlu diperhatikan: <br>
![Form Register](../images/form-register.png)
** Semua kolom kecuali `Kode Referral` <b>wajib</b> diisi. <br>
** `No. Whatsapp` minimal berisi 8 angka. <br>
** `Kata Sandi` minimal 8 angka dengan gabungan huruf kapital atau kecil, angka, dan simbol.

Setelah form berhasil dikirim dengan kriteria data yang sesuai, maka akan dialihkan ke halaman Verifikasi OTP.

#### Verifikasi nomor Whatsapp
Tombol <b>Submit</b> pada form registrasi akan mentrigger API <b><i>send-whatsapp-api</i></b> yang mengirimkan OTP ke nomor Whatsapp yang telah anda input. <br>
![Halaman Verifikasi OTP](../images/OTP.png)

- Cek kode OTP yang dikirim pada nomor Whatsapp anda. <br>
Apabila belum menerima kode, maka lakukan <b>Kirim ulang kode.</b> <br>
Apabila kode OTP telah muncul maka masukkan kode tersebut pada kolom yang tersedia. <br>

- Klik tombol <b>lanjutkan</b> yang akan mengirim data atau kode OTP ke API <b><i>verification-otp</i></b> <br>
Apabila kode yang dikirim salah, API akan merespon ```Upps, your email or number not found.``` maka anda dapat melakukan <b>Kirim ulang kode.</b> <br>
Apabila kode OTP yang dimasukkan benar, maka nomor Whatsapp anda berhasil terverifikasi.<br>
<!-- kayaknya responnya masih salah untuk yg kode OTP salah, harusnya Kode OTP Salah bukan email/no hp not found -->

#### Verifikasi email
Tombol <b>Lanjutkan</b> yang diklik dan berhasil memverifikasi nomor Whatsapp pada tahap sebelumnya, akan memuat halaman Verifikasi Email sekaligus mentrigger API <b><i>verification-email</i></b> yang otomatis mengirimkan email verification ke alamat email anda.

- Cek email anda yang telah dikirim <i>email verification</i>
- Klik pada tombol atau link yang diarahkan pada email untuk memverifikasi email anda. <br>
Apabila gagal memverifikasi, anda dapat meminta untuk melakukan <b>Kirim ulang email</b>. <br>
Apabila email berhasil terverifikasi, maka anda akan langsung diarahkan ke <b>Halaman Dashboard</b>.

### Login
Pada halaman login, anda hanya perlu melakukan input <b>Email atau No Telfon</b> dan <b>Password</b> yang telah anda buat pada proses Registrasi Akun.<br>

#### Mengisi data login
![Halaman Login](../images/login.png)
Contoh data JSON untuk dikirim melalui API <b><i>login</i></b>:
```
{
    "email": "hifisaputra1@gmail.com",
    "password": "123456"    
}
```

Apabila data yang dimasukkan sesuai dengan akun yang ada pada database, maka API <b><i>login</i></b> akan merespon sebagai berikut yang artinya anda berhasil login dan otomatis diarahkan ke <b>Halaman Dashboard</b>:
```
```
Apabila gagal melakukan login, maka API akan merespon sebagai berikut dan anda dapat mengulangi proses login yang sama:
```
```
### Lupa Password
### Edit Profil
### Member
> ## Transaksi
### Membuat pengiriman
### Cek Resi
### Cek Ongkos Kirim
!> User perlu **login** ke dalam **akun JuraganCOD** terlebih dahulu

Langkah-langkah untuk mengecek ongkos kirim:

1. Klik "Cek Ongkir"

![Klik "Cek Ongkir"](../images/cekongkir-1.png)

2. Form untuk mengecek ongkos kirim akan muncul
3. Masukan data asal serta tujuan pengiriman, dan berat barang
4. Anda juga dapat mengecek ongkos kirim jika barang yang akan dikirim berdasarkan ukuran (bukan berat)

5. Klik "Cari"

![buttonsearch"](../images/cekongkir-4.png)

Berikut data dalam bentuk JSON yang dikirimkan ke API check-ongkir:
```
{
    "berat": 1000,
    "berat_dimensi": 100,
    "id_kecamatan_penerima":3233,
    "id_kecamatan_pengirim":1953
}
```

>6. Data yang anda inginkan akan muncul

Jika sukses, maka anda akan mendapatkan respon dari API check-ongkir dan tampilan pada dashboard sebagai berikut  
**Tampilan pada dashboard**

![result](../images/cekongkir-5.png)

**Respon API check-ongkir**
```
{
    "code": 200,
    "data": {
        "cargo": [
            {
                "DbnpOngkir": "{\n  \"price\" : [ {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR\",\n    \"service_code\" : \"JTR23\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"5500000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR250\",\n    \"service_code\" : \"JTR250\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"1100000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR<150\",\n    \"service_code\" : \"JTR<150\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"600000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR>250\",\n    \"service_code\" : \"JTR>250\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"1500000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"OKE\",\n    \"service_code\" : \"OKE23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"17000000\",\n    \"etd_from\" : \"2\",\n    \"etd_thru\" : \"3\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"REG\",\n    \"service_code\" : \"REG23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"19000000\",\n    \"etd_from\" : \"1\",\n    \"etd_thru\" : \"2\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"SPS\",\n    \"service_code\" : \"SPS23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"45398000\",\n    \"etd_from\" : \"0\",\n    \"etd_thru\" : \"0\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"YES\",\n    \"service_code\" : \"YES23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"35000000\",\n    \"etd_from\" : \"1\",\n    \"etd_thru\" : \"1\",\n    \"times\" : \"D\"\n  } ]\n}",
                "Ekspedisi": "jne",
                "Service": "JTR23 (JTR Min 5kg)",
                "Service_tag": "(JTR Min 5kg)",
                "Etd": "ETD : 3 - 4",
                "Ongkir": "5500000",
                "Sort": "5500000"
            },
            {
                "DbnpOngkir": "{\n  \"price\" : [ {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR\",\n    \"service_code\" : \"JTR23\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"5500000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR250\",\n    \"service_code\" : \"JTR250\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"1100000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR<150\",\n    \"service_code\" : \"JTR<150\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"600000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR>250\",\n    \"service_code\" : \"JTR>250\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"1500000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"OKE\",\n    \"service_code\" : \"OKE23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"17000000\",\n    \"etd_from\" : \"2\",\n    \"etd_thru\" : \"3\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"REG\",\n    \"service_code\" : \"REG23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"19000000\",\n    \"etd_from\" : \"1\",\n    \"etd_thru\" : \"2\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"SPS\",\n    \"service_code\" : \"SPS23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"45398000\",\n    \"etd_from\" : \"0\",\n    \"etd_thru\" : \"0\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"YES\",\n    \"service_code\" : \"YES23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"35000000\",\n    \"etd_from\" : \"1\",\n    \"etd_thru\" : \"1\",\n    \"times\" : \"D\"\n  } ]\n}",
                "Ekspedisi": "jne",
                "Service": "JTR250 (JTR250 Min 5kg)",
                "Service_tag": "(JTR250 Min 5kg)",
                "Etd": "ETD : 3 - 4",
                "Ongkir": "1100000",
                "Sort": "1100000"
            },
            {
                "DbnpOngkir": "{\n  \"price\" : [ {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR\",\n    \"service_code\" : \"JTR23\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"5500000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR250\",\n    \"service_code\" : \"JTR250\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"1100000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR<150\",\n    \"service_code\" : \"JTR<150\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"600000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR>250\",\n    \"service_code\" : \"JTR>250\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"1500000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"OKE\",\n    \"service_code\" : \"OKE23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"17000000\",\n    \"etd_from\" : \"2\",\n    \"etd_thru\" : \"3\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"REG\",\n    \"service_code\" : \"REG23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"19000000\",\n    \"etd_from\" : \"1\",\n    \"etd_thru\" : \"2\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"SPS\",\n    \"service_code\" : \"SPS23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"45398000\",\n    \"etd_from\" : \"0\",\n    \"etd_thru\" : \"0\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"YES\",\n    \"service_code\" : \"YES23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"35000000\",\n    \"etd_from\" : \"1\",\n    \"etd_thru\" : \"1\",\n    \"times\" : \"D\"\n  } ]\n}",
                "Ekspedisi": "jne",
                "Service": "JTR<150 (JTR<150 Min 5kg)",
                "Service_tag": "(JTR<150 Min 5kg)",
                "Etd": "ETD : 3 - 4",
                "Ongkir": "600000",
                "Sort": "600000"
            },
            {
                "DbnpOngkir": "{\n  \"price\" : [ {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR\",\n    \"service_code\" : \"JTR23\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"5500000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR250\",\n    \"service_code\" : \"JTR250\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"1100000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR<150\",\n    \"service_code\" : \"JTR<150\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"600000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR>250\",\n    \"service_code\" : \"JTR>250\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"1500000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"OKE\",\n    \"service_code\" : \"OKE23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"17000000\",\n    \"etd_from\" : \"2\",\n    \"etd_thru\" : \"3\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"REG\",\n    \"service_code\" : \"REG23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"19000000\",\n    \"etd_from\" : \"1\",\n    \"etd_thru\" : \"2\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"SPS\",\n    \"service_code\" : \"SPS23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"45398000\",\n    \"etd_from\" : \"0\",\n    \"etd_thru\" : \"0\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"YES\",\n    \"service_code\" : \"YES23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"35000000\",\n    \"etd_from\" : \"1\",\n    \"etd_thru\" : \"1\",\n    \"times\" : \"D\"\n  } ]\n}",
                "Ekspedisi": "jne",
                "Service": "JTR>250 (JTR>250 Min 5kg)",
                "Service_tag": "(JTR>250 Min 5kg)",
                "Etd": "ETD : 3 - 4",
                "Ongkir": "1500000",
                "Sort": "1500000"
            },
            {
                "DbnpOngkir": "{\"sicepat\":{\"status\":{\"code\":200,\"description\":\"OK\"},\"results\":[{\"service\":\"BEST\",\"description\":\"Besok Sampai Tujuan\",\"tariff\":37000000,\"minPrice\":37000,\"unitPrice\":37000,\"etd\":\"1 hari\"},{\"service\":\"GOKIL\",\"description\":\"Cargo (minimal 10Kg)\",\"tariff\":5000000,\"minPrice\":50000,\"unitPrice\":5000,\"etd\":\"3 - 4 hari\"},{\"service\":\"REG\",\"description\":\"Regular\",\"tariff\":20000000,\"minPrice\":20000,\"unitPrice\":20000,\"etd\":\"1 - 2 hari\"},{\"service\":\"SIUNT\",\"description\":\"SiUntung\",\"tariff\":19500000,\"minPrice\":19500,\"unitPrice\":19500,\"etd\":\"1 - 2 hari\"}]}}",
                "Ekspedisi": "sicepat",
                "Service": "GOKIL(Cargo (minimal 10Kg))",
                "Service_tag": "Cargo Min 10Kg",
                "Etd": "ETD : 3 - 4 hari",
                "Ongkir": "5000000",
                "Sort": "5000000"
            },
            {
                "DbnpOngkir": "{\"code\":-1,\"data\":null,\"desc\":\"Exceeded maximum weight limit\",\"total\":null}\n",
                "Ekspedisi": "id_express",
                "Service": "06",
                "Service_tag": "iDtruck",
                "Etd": "ETD : -",
                "Ongkir": "0",
                "Sort": "0"
            }
        ],
        "reguler": [
            {
                "DbnpOngkir": "{\"code\":\"200\",\"data\":[{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"NRS(Regular Service)\",\"Etd\":\"2-3\",\"MainPrice\":\"10000\",\"AddPrice\":\"5000\",\"MinKG\":\"2\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"5000000\"},{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"ONS(One Night Service)\",\"Etd\":\"1-1\",\"MainPrice\":\"33000\",\"AddPrice\":\"0\",\"MinKG\":\"1\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"33000000\"},{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"SDS(SameDay Service)\",\"Etd\":\"0-0\",\"MainPrice\":\"66000\",\"AddPrice\":\"33000\",\"MinKG\":\"5\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"33165000\"},{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"NFO(Food-One Night Service)\",\"Etd\":\"1-1\",\"MainPrice\":\"78000\",\"AddPrice\":\"7800\",\"MinKG\":\"5\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"7839000\"},{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"DRT(Regular Darat)\",\"Etd\":\"3-4\",\"MainPrice\":\"8000\",\"AddPrice\":\"0\",\"MinKG\":\"10\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"8000000\"}]}",
                "Ekspedisi": "ncs",
                "Service": "NRS(Regular Service)",
                "Service_tag": "regular",
                "Etd": "ETD : 2-3",
                "Ongkir": "10000",
                "Sort": "10000"
            },
            {
                "DbnpOngkir": "{\"code\":\"200\",\"data\":[{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"NRS(Regular Service)\",\"Etd\":\"2-3\",\"MainPrice\":\"10000\",\"AddPrice\":\"5000\",\"MinKG\":\"2\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"5000000\"},{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"ONS(One Night Service)\",\"Etd\":\"1-1\",\"MainPrice\":\"33000\",\"AddPrice\":\"0\",\"MinKG\":\"1\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"33000000\"},{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"SDS(SameDay Service)\",\"Etd\":\"0-0\",\"MainPrice\":\"66000\",\"AddPrice\":\"33000\",\"MinKG\":\"5\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"33165000\"},{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"NFO(Food-One Night Service)\",\"Etd\":\"1-1\",\"MainPrice\":\"78000\",\"AddPrice\":\"7800\",\"MinKG\":\"5\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"7839000\"},{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"DRT(Regular Darat)\",\"Etd\":\"3-4\",\"MainPrice\":\"8000\",\"AddPrice\":\"0\",\"MinKG\":\"10\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"8000000\"}]}",
                "Ekspedisi": "ncs",
                "Service": "ONS(One Night Service)",
                "Service_tag": "regular",
                "Etd": "ETD : 1-1",
                "Ongkir": "33000",
                "Sort": "33000"
            },
            {
                "DbnpOngkir": "{\"code\":\"200\",\"data\":[{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"NRS(Regular Service)\",\"Etd\":\"2-3\",\"MainPrice\":\"10000\",\"AddPrice\":\"5000\",\"MinKG\":\"2\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"5000000\"},{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"ONS(One Night Service)\",\"Etd\":\"1-1\",\"MainPrice\":\"33000\",\"AddPrice\":\"0\",\"MinKG\":\"1\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"33000000\"},{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"SDS(SameDay Service)\",\"Etd\":\"0-0\",\"MainPrice\":\"66000\",\"AddPrice\":\"33000\",\"MinKG\":\"5\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"33165000\"},{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"NFO(Food-One Night Service)\",\"Etd\":\"1-1\",\"MainPrice\":\"78000\",\"AddPrice\":\"7800\",\"MinKG\":\"5\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"7839000\"},{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"DRT(Regular Darat)\",\"Etd\":\"3-4\",\"MainPrice\":\"8000\",\"AddPrice\":\"0\",\"MinKG\":\"10\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"8000000\"}]}",
                "Ekspedisi": "ncs",
                "Service": "SDS(SameDay Service)",
                "Service_tag": "regular",
                "Etd": "ETD : 0-0",
                "Ongkir": "66000",
                "Sort": "66000"
            },
            {
                "DbnpOngkir": "{\"code\":\"200\",\"data\":[{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"NRS(Regular Service)\",\"Etd\":\"2-3\",\"MainPrice\":\"10000\",\"AddPrice\":\"5000\",\"MinKG\":\"2\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"5000000\"},{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"ONS(One Night Service)\",\"Etd\":\"1-1\",\"MainPrice\":\"33000\",\"AddPrice\":\"0\",\"MinKG\":\"1\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"33000000\"},{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"SDS(SameDay Service)\",\"Etd\":\"0-0\",\"MainPrice\":\"66000\",\"AddPrice\":\"33000\",\"MinKG\":\"5\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"33165000\"},{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"NFO(Food-One Night Service)\",\"Etd\":\"1-1\",\"MainPrice\":\"78000\",\"AddPrice\":\"7800\",\"MinKG\":\"5\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"7839000\"},{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"DRT(Regular Darat)\",\"Etd\":\"3-4\",\"MainPrice\":\"8000\",\"AddPrice\":\"0\",\"MinKG\":\"10\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"8000000\"}]}",
                "Ekspedisi": "ncs",
                "Service": "NFO(Food-One Night Service)",
                "Service_tag": "regular",
                "Etd": "ETD : 1-1",
                "Ongkir": "78000",
                "Sort": "78000"
            },
            {
                "DbnpOngkir": "{\"code\":\"200\",\"data\":[{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"NRS(Regular Service)\",\"Etd\":\"2-3\",\"MainPrice\":\"10000\",\"AddPrice\":\"5000\",\"MinKG\":\"2\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"5000000\"},{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"ONS(One Night Service)\",\"Etd\":\"1-1\",\"MainPrice\":\"33000\",\"AddPrice\":\"0\",\"MinKG\":\"1\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"33000000\"},{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"SDS(SameDay Service)\",\"Etd\":\"0-0\",\"MainPrice\":\"66000\",\"AddPrice\":\"33000\",\"MinKG\":\"5\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"33165000\"},{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"NFO(Food-One Night Service)\",\"Etd\":\"1-1\",\"MainPrice\":\"78000\",\"AddPrice\":\"7800\",\"MinKG\":\"5\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"7839000\"},{\"OriginCity\":\"KOTA ADM. JAKARTA TIMUR\",\"OriginDistrict\":\"JATINEGARA\",\"DestinationCity\":\"KOTA YOGYAKARTA\",\"DestinationDistrict\":\"WIROBRAJAN\",\"Service\":\"DRT(Regular Darat)\",\"Etd\":\"3-4\",\"MainPrice\":\"8000\",\"AddPrice\":\"0\",\"MinKG\":\"10\",\"TotalWeight\":\"1000 Kg\",\"TotalPrice\":\"8000000\"}]}",
                "Ekspedisi": "ncs",
                "Service": "DRT(Regular Darat)",
                "Service_tag": "regular",
                "Etd": "ETD : 3-4",
                "Ongkir": "8000",
                "Sort": "8000"
            },
            {
                "DbnpOngkir": "{\"status\":200,\"info\":\"OK\",\"content\":{\"origin\":\"31.75.03\",\"destination\":\"34.71.07\",\"services\":[{\"product_code\":\"REG\",\"product_name\":\"Anteraja Regular\",\"etd\":\"2-4 Day\",\"rates\":21200,\"is_cod\":false,\"surcharges\":null}]}}",
                "Ekspedisi": "antaraja",
                "Service": "REG(Anteraja Regular)",
                "Service_tag": "regular",
                "Etd": "ETD : 2-4 Day",
                "Ongkir": "19716",
                "Sort": "19716"
            },
            {
                "DbnpOngkir": "{\n  \"price\" : [ {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR\",\n    \"service_code\" : \"JTR23\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"5500000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR250\",\n    \"service_code\" : \"JTR250\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"1100000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR<150\",\n    \"service_code\" : \"JTR<150\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"600000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR>250\",\n    \"service_code\" : \"JTR>250\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"1500000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"OKE\",\n    \"service_code\" : \"OKE23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"17000000\",\n    \"etd_from\" : \"2\",\n    \"etd_thru\" : \"3\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"REG\",\n    \"service_code\" : \"REG23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"19000000\",\n    \"etd_from\" : \"1\",\n    \"etd_thru\" : \"2\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"SPS\",\n    \"service_code\" : \"SPS23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"45398000\",\n    \"etd_from\" : \"0\",\n    \"etd_thru\" : \"0\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"YES\",\n    \"service_code\" : \"YES23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"35000000\",\n    \"etd_from\" : \"1\",\n    \"etd_thru\" : \"1\",\n    \"times\" : \"D\"\n  } ]\n}",
                "Ekspedisi": "jne",
                "Service": "OKE23 (OKE Min 5kg)",
                "Service_tag": "(OKE Min 5kg)",
                "Etd": "ETD : 2 - 3",
                "Ongkir": "17000000",
                "Sort": "17000000"
            },
            {
                "DbnpOngkir": "{\n  \"price\" : [ {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR\",\n    \"service_code\" : \"JTR23\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"5500000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR250\",\n    \"service_code\" : \"JTR250\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"1100000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR<150\",\n    \"service_code\" : \"JTR<150\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"600000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR>250\",\n    \"service_code\" : \"JTR>250\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"1500000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"OKE\",\n    \"service_code\" : \"OKE23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"17000000\",\n    \"etd_from\" : \"2\",\n    \"etd_thru\" : \"3\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"REG\",\n    \"service_code\" : \"REG23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"19000000\",\n    \"etd_from\" : \"1\",\n    \"etd_thru\" : \"2\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"SPS\",\n    \"service_code\" : \"SPS23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"45398000\",\n    \"etd_from\" : \"0\",\n    \"etd_thru\" : \"0\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"YES\",\n    \"service_code\" : \"YES23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"35000000\",\n    \"etd_from\" : \"1\",\n    \"etd_thru\" : \"1\",\n    \"times\" : \"D\"\n  } ]\n}",
                "Ekspedisi": "jne",
                "Service": "REG23 (REG Min 5kg)",
                "Service_tag": "(REG Min 5kg)",
                "Etd": "ETD : 1 - 2",
                "Ongkir": "19000000",
                "Sort": "19000000"
            },
            {
                "DbnpOngkir": "{\n  \"price\" : [ {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR\",\n    \"service_code\" : \"JTR23\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"5500000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR250\",\n    \"service_code\" : \"JTR250\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"1100000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR<150\",\n    \"service_code\" : \"JTR<150\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"600000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR>250\",\n    \"service_code\" : \"JTR>250\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"1500000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"OKE\",\n    \"service_code\" : \"OKE23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"17000000\",\n    \"etd_from\" : \"2\",\n    \"etd_thru\" : \"3\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"REG\",\n    \"service_code\" : \"REG23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"19000000\",\n    \"etd_from\" : \"1\",\n    \"etd_thru\" : \"2\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"SPS\",\n    \"service_code\" : \"SPS23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"45398000\",\n    \"etd_from\" : \"0\",\n    \"etd_thru\" : \"0\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"YES\",\n    \"service_code\" : \"YES23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"35000000\",\n    \"etd_from\" : \"1\",\n    \"etd_thru\" : \"1\",\n    \"times\" : \"D\"\n  } ]\n}",
                "Ekspedisi": "jne",
                "Service": "SPS23 (SPS Min 5kg)",
                "Service_tag": "(SPS Min 5kg)",
                "Etd": "ETD : 0 - 0",
                "Ongkir": "45398000",
                "Sort": "45398000"
            },
            {
                "DbnpOngkir": "{\n  \"price\" : [ {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR\",\n    \"service_code\" : \"JTR23\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"5500000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR250\",\n    \"service_code\" : \"JTR250\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"1100000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR<150\",\n    \"service_code\" : \"JTR<150\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"600000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"JTR>250\",\n    \"service_code\" : \"JTR>250\",\n    \"goods_type\" : \"Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"1500000\",\n    \"etd_from\" : \"3\",\n    \"etd_thru\" : \"4\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"OKE\",\n    \"service_code\" : \"OKE23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"17000000\",\n    \"etd_from\" : \"2\",\n    \"etd_thru\" : \"3\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"REG\",\n    \"service_code\" : \"REG23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"19000000\",\n    \"etd_from\" : \"1\",\n    \"etd_thru\" : \"2\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"SPS\",\n    \"service_code\" : \"SPS23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"45398000\",\n    \"etd_from\" : \"0\",\n    \"etd_thru\" : \"0\",\n    \"times\" : \"D\"\n  }, {\n    \"origin_name\" : \"JAKARTA\",\n    \"destination_name\" : \"WIROBRAJAN,YOGYAKARTA\",\n    \"service_display\" : \"YES\",\n    \"service_code\" : \"YES23\",\n    \"goods_type\" : \"Document/Paket\",\n    \"currency\" : \"IDR\",\n    \"price\" : \"35000000\",\n    \"etd_from\" : \"1\",\n    \"etd_thru\" : \"1\",\n    \"times\" : \"D\"\n  } ]\n}",
                "Ekspedisi": "jne",
                "Service": "YES23 (YES Min 5kg)",
                "Service_tag": "(YES Min 5kg)",
                "Etd": "ETD : 1 - 1",
                "Ongkir": "35000000",
                "Sort": "35000000"
            },
            {
                "DbnpOngkir": "{\"sicepat\":{\"status\":{\"code\":200,\"description\":\"OK\"},\"results\":[{\"service\":\"BEST\",\"description\":\"Besok Sampai Tujuan\",\"tariff\":37000000,\"minPrice\":37000,\"unitPrice\":37000,\"etd\":\"1 hari\"},{\"service\":\"GOKIL\",\"description\":\"Cargo (minimal 10Kg)\",\"tariff\":5000000,\"minPrice\":50000,\"unitPrice\":5000,\"etd\":\"3 - 4 hari\"},{\"service\":\"REG\",\"description\":\"Regular\",\"tariff\":20000000,\"minPrice\":20000,\"unitPrice\":20000,\"etd\":\"1 - 2 hari\"},{\"service\":\"SIUNT\",\"description\":\"SiUntung\",\"tariff\":19500000,\"minPrice\":19500,\"unitPrice\":19500,\"etd\":\"1 - 2 hari\"}]}}",
                "Ekspedisi": "sicepat",
                "Service": "BEST(Besok Sampai Tujuan)",
                "Service_tag": "Besok Sampai Tujuan",
                "Etd": "ETD : 1 hari",
                "Ongkir": "37000000",
                "Sort": "37000000"
            },
            {
                "DbnpOngkir": "{\"sicepat\":{\"status\":{\"code\":200,\"description\":\"OK\"},\"results\":[{\"service\":\"BEST\",\"description\":\"Besok Sampai Tujuan\",\"tariff\":37000000,\"minPrice\":37000,\"unitPrice\":37000,\"etd\":\"1 hari\"},{\"service\":\"GOKIL\",\"description\":\"Cargo (minimal 10Kg)\",\"tariff\":5000000,\"minPrice\":50000,\"unitPrice\":5000,\"etd\":\"3 - 4 hari\"},{\"service\":\"REG\",\"description\":\"Regular\",\"tariff\":20000000,\"minPrice\":20000,\"unitPrice\":20000,\"etd\":\"1 - 2 hari\"},{\"service\":\"SIUNT\",\"description\":\"SiUntung\",\"tariff\":19500000,\"minPrice\":19500,\"unitPrice\":19500,\"etd\":\"1 - 2 hari\"}]}}",
                "Ekspedisi": "sicepat",
                "Service": "REG(Regular)",
                "Service_tag": "Regular",
                "Etd": "ETD : 1 - 2 hari",
                "Ongkir": "20000000",
                "Sort": "20000000"
            },
            {
                "DbnpOngkir": "{\"sicepat\":{\"status\":{\"code\":200,\"description\":\"OK\"},\"results\":[{\"service\":\"BEST\",\"description\":\"Besok Sampai Tujuan\",\"tariff\":37000000,\"minPrice\":37000,\"unitPrice\":37000,\"etd\":\"1 hari\"},{\"service\":\"GOKIL\",\"description\":\"Cargo (minimal 10Kg)\",\"tariff\":5000000,\"minPrice\":50000,\"unitPrice\":5000,\"etd\":\"3 - 4 hari\"},{\"service\":\"REG\",\"description\":\"Regular\",\"tariff\":20000000,\"minPrice\":20000,\"unitPrice\":20000,\"etd\":\"1 - 2 hari\"},{\"service\":\"SIUNT\",\"description\":\"SiUntung\",\"tariff\":19500000,\"minPrice\":19500,\"unitPrice\":19500,\"etd\":\"1 - 2 hari\"}]}}",
                "Ekspedisi": "sicepat",
                "Service": "SIUNT(SiUntung)",
                "Service_tag": "SiUntung",
                "Etd": "ETD : 1 - 2 hari",
                "Ongkir": "17550000",
                "Sort": "17550000"
            },
            {
                "DbnpOngkir": "{\"origin\":\"JK1005\",\"destination\":\"YO0514\",\"weight\":\"1000\",\"price\":{\"UDRREG\":10000000},\"price_detail\":{\"UDRREG\":{\"service_type_code\":\"UDRREG\",\"service_type_name\":\"REGULER\",\"unit_price\":\"10000\",\"minimum_kilo\":1000,\"price\":10000000,\"sla\":\"2-4 Hari\",\"id\":\"58164232\"}},\"price_array\":[{\"service_type_code\":\"UDRREG\",\"service_type_name\":\"REGULER\",\"unit_price\":\"10000\",\"minimum_kilo\":1000,\"price\":10000000,\"sla\":\"2-4 Hari\",\"id\":\"58164232\"}]}",
                "Ekspedisi": "sap",
                "Service": "UDRREG(REGULER)",
                "Service_tag": "REGULER",
                "Etd": "ETD : 2-4 Hari",
                "Ongkir": "9900000",
                "Sort": "9900000"
            }
        ]
    },
    "message": "Success get data ongkir!",
    "status": true
}
```

### Membuat Rekap Pembelian
### Tiket dan Claim
### Katalog Produk
> ## Keuangan
### Pembayaran
### Penarikan Saldo
### Cek Saldo
