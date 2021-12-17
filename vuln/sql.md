# SQL Injection

## Resource
- [Web Security Academy - SQL injection cheat sheet](https://portswigger.net/web-security/sql-injection/cheat-sheet)
- [HackTricks -  SQL Injection](https://book.hacktricks.xyz/pentesting-web/sql-injection)

## Tips
- Tidak semua payload biasa dijalankan di address-bar browser, kadang harus menggunakan burpsuite (repeater)

## langkah-langkah
1. Identify kapan aplikasi berinteraksi dengan DB Server untuk mengakses data. Berikut kondisi umum aplikasi berinteraksi dengan DB server.
- Authentication form, user dan password akan dicek pada database apakah ada atau tidak (kadang juga hash)
- Search Engine, string yang disubmit oleh user digunakan untuk mengeksract semua data yang relevant pada database
- E-commerce site, semua produk e-commerce stored di DB
2. List entry point/parameter yang bisa digunakan untuk menginputkan SQL query, seperti (__GET parameter, POST parameter, HTTP header, cookies__)
3. Coba generate error pada entry point/parameter yang sudah dikumpulkan pada langkah sebelumnya menggunakan `'` (digunakan untuk memisahkan string) dan `;` (digunakan untuk mengakhiri kueri SQL)
  ```
  <spasi_kosong>
  '
  ')
  '))
  " / ") / "))
  `
  `)
  `))
  ```
4. Coba meng-injek payload tanpa break query, bisa mengguna comment

|Database|Comment|
|---|---|
|Oracle|`--comment`|
|MySQL|`-- comment` `#comment` `/*comment*/`|
|MariaDB|`-- comment` `#comment` `/*comment*/`|
|PostgreSQL|`--comment` `/*comment*/`|
|Microsoft|`--comment` `/*comment*/`|


