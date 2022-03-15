# SQL Injection

## Tips
- Tidak semua payload biasa dijalankan di address-bar browser, kadang harus menggunakan burpsuite (repeater)
- Blind SQL injection generate error 500
- Pada injection login, coba test inject for username dahulu, kalau tidak bisa coba inject kedua username dan password
- Kalau value parameter yang injection kan adalah string maka mengunnakan 1='1 atau '1'='1'

## langkah-langkah
1. Identify kapan dan dimana aplikasi akan berinteraksi dengan DB Server untuk mengakses data. Berikut kondisi umum aplikasi berinteraksi dengan DB server.
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
|PostgreSQL|`--comment` `/*comment*/`|
|Microsoft|`--comment` `/*comment*/`|

## Payload
```
'or'1'='1
' OR 1=1--
' AND 1=1--
```

## Resource
- [Web Security Academy - SQL injection cheat sheet](https://portswigger.net/web-security/sql-injection/cheat-sheet)
- [HackTricks -  SQL Injection](https://book.hacktricks.xyz/pentesting-web/sql-injection)
- [Netsparker - SQL Injection Cheat Sheet](https://www.netsparker.com/blog/web-security/sql-injection-cheat-sheet/)
- [Finding an unseen SQL Injection by bypassing escape functions in mysqljs/mysql](https://flattsecurity.medium.com/finding-an-unseen-sql-injection-by-bypassing-escape-functions-in-mysqljs-mysql-90b27f6542b4)
- [BigQuery SQL Injection Cheat Sheet](https://ozguralp.medium.com/bigquery-sql-injection-cheat-sheet-65ad70e11eac)

## Writeups
- 
