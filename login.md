# Cara Register Akun di JuraganCOD.com
API digunakan untuk masuk ke akun JuraganCOD untuk anda dapat melakukan transaksi.

## Mengisi data login
Pada halaman login, anda hanya perlu melakukan input <b>Email atau No Telfon</b> dan <b>Password</b>. <br>
Contoh data JSON untuk dikirim melalui API:
```
{
    "email": "hifisaputra1@gmail.com",
    "password": "123456"    
}
```

Apabila data yang dimasukkan sesuai dengan akun yang ada pada database, maka API akan merespon sebagai berikut yang artinya anda berhasil login dan otomatis diarahkan ke dashboard:
```
```
Apabila gagal melakukan login, maka API akan merespon sebagai berikut dan anda dapat mengulangi proses login yang sama:
```
```

#### Selamat anda berhasil melakukan login.