# Cara Register Akun di JuraganCOD.com
API digunakan untuk mendaftarkan akun anda ke JuraganCOD sebagai seller sebelum dapat melakukan transaksi.

>Tahap melakukan registrasi akun:
````
1. Mengisi form register
2. Verifikasi nomor HP dengan OTP
3. Verifikasi email
````
## 1. Mengisi form register
- Silahkan akses <b>JuraganCOD.com</b>
- Klik <b>Daftar</b>
- Isi form pendaftaran <br>
Contoh data JSON untuk dikirim melalui API:
```
{
    "fullname": "M Dhifta",
    "email": "dhifta48@gmail.com",
    "password": "123456",
    "phone_number":"6285791419626",
    "code_referal": ""
}
```

!> Pastikan data <b>tidak <i>null</i></b> dan telah <b>sesuai kriteria</b> untuk dapat lanjut ke tahap berikutnya


## 2. Verifikasi nomor HP dengan OTP
- Apabila berhasil mengisi form register, klik tombol yang akan mentrigger API <b>send-whatsapp-api</b> untuk mengirimkan OTP ke nomor whatsapp yang anda input. <br>
Bila <b>berhasil</b> mengirim kode ke nomor whatsapp anda, API akan merespon:
```
```
Bila <b>gagal</b> mengirimkan kode, API akan merespon seperti berikut yang artinya anda dapat melakukan kirim ulang kode OTP:
```
```

- Masukkan kode OTP yang telah dikirim melalui nomor whatsapp anda pada kolom tersedia.
- Apabila kode yang anda masukkan sesuai, maka anda dapat lanjut ke tahap verifikasi email. Namun apabila gagal, anda perlu melakukan kirim ulang kode.



## 3. Verifikasi email
Setelah berhasil melakukan verifikasi nomor HP, anda perlu melakukan verifikasi email.

- Klik tombol verifikasi email untuk mentrigger API <b>verifivation-email</b>, maka API akan otomatis merespon untuk mengirim email verification ke email anda.
- Ikuti arahan yang ada pada email verification, klik tombol yang disarankan untuk memverifikasi akun anda. <br>
Apabila berhasil, maka API akan merespon sebagai berikut yang artinya akun email anda berhasil diverifikasi:
```
```
Apabila gagal, API akan merespon sebagai berikut yang artinya anda dapat melakukan kirim ulang email verification:
```
```

#### Selamat akun anda telah berhasil dibuat. Anda dapat melanjutkan ke halaman login.