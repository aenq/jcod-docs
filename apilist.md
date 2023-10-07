# List API yang Tersedia
## generate-token

"generate-token" merupakan API yang digunakan untuk menghasilkan token sebagai autorisasi ketika user melakukan pemesanan pengiriman. API ini merupakan API jenis GET yang berperan untuk mendapatkan data dari backend
## show-token

"show-token" merupakan API yang digunakan untuk merupakan API yang digunakan untuk menampilkan token yang sudah dihasilkan sebelumnya saat user melakukan pemesanan pengiriman. API ini merupakan API jenis GET yang berperan untuk mendapatkan data dari backend

## create-order

"create-order" merupakan API yang digunakan oleh user untuk melakukan pemesanan pengiriman. API ini merupakan API jenis POST yang berperan untuk mendorong data ke backend kemudian mendapatkan respon dari backend

## address

"address" merupakan API yang digunakan untuk mendapatkan data mengenai alamat yang sudah terdaftarkan ke akun user. API ini merupakan API jenis GET sehingga sistem kerja API hanya meminta data dari backend tanpa mendorong data ke backend

## address-add

"address-add" merupakan API yang digunakan untuk menambahkan data mengenai alamat pengiriman ke dalam akun user. API ini merupakan API jenis POST sehingga perannya mendorong data ke backend

## get-kecamatan

"get-kecamatan" adalah API yang digunakan untuk menampilkan data mengenai kecamatan. API ini merupakan API jenis GET yang berperan untuk mendapatkan data dari backend

## check-ongkir

"check-ongkir" adalah API yang digunakan oleh user untuk mendapatkan data mengenai ongkos kirim pengiriman. API ini merupakan API jenis POST sehingga user mendorong data ke backend untuk mendapatkan data mengenai ongkos kirim yang harus ditanggung.

## delivery-show

"delivery-show" merupakan API yang digunakan untuk mengetahui detail pesanan pengiriman yang telah dilakukan oleh user. API ini merupakan API jenis GET sehingga user tidak mendorong data apapun ke backend

## show-catalog-product

"show-catalog-product" Merupakan API yang digunakan untuk mengetahui katalog dari produk yang sudah didaftarkan oleh user. API ini merupakan API jenis GET sehingga user tidak mendorong data apapun ke backend

## show-catalog-product-by-id

"show-catalog-product-by-id" hampir sama seperti "show-catalog-product" hanya dengan pengurutan berdasarkan id katalog

## delete-catalog-product

"delete-catalog-product" merupakan API yang digunakan untuk menghapus katalog dari produk yang sudah didaftarkan user sehingga tidak terjadi tumpang tindih di database. API ini adalah API dengan jenis DELETE yang mengirimkan perintah kepada backend untuk menghapus data tertentu
