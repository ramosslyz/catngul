# SQL Injection

## Resource
- [Web Security Academy - SQL injection cheat sheet](https://portswigger.net/web-security/sql-injection/cheat-sheet)
- [HackTricks -  SQL Injection](https://book.hacktricks.xyz/pentesting-web/sql-injection)

## Tips
- Tidak semua payload biasa dijalankan di address-bar browser, kadang harus menggunakan burpsuite (repeater)
- Suppose that the attacker does not know the administrator’s username. In most applications, the first account in the database is an administrative user,
because this account normally is created manually and then is used to generateall other accounts via the application. Furthermore, if the query returns the
details for more than one user, most applications will simply process the first user whose details are returned. An attacker can often exploit this behavior to
log in as the first user in the database by supplying the username: `' OR 1=1--`
- Hampir di semua aplikasi, first account pada DB adalah administrative user, karena akun tersebut dibuat secara manual untuk men-generate akun lainnya. Lebih lanjut, jika query menampilkan lebih dari 1 user, hampir semua aplikasi akan menampilkan user pertama yaitu administrator. Hacker bisa memanfaat 

## langkah-langkah
1. Identify kapan aplikasi berinteraksi dengan DB Server untuk mengakses data. Berikut kondisi umum aplikasi berinteraksi dengan DB server.
    - Authentication form, user dan password akan dicek pada database apakah ada atau tidak (kadang juga hash)
    - Search Engine, string yang disubmit oleh user digunakan untuk mengeksract semua data yang relevant pada database
    - E-commerce site, semua produk e-commerce stored di DB
    - Reflected
2. List entry point/parameter yang bisa digunakan untuk menginputkan SQL query, seperti (__GET parameter, POST parameter, HTTP header, cookies__)
3. Coba generate error pada entry point/parameter yang sudah dikumpulkan pada langkah sebelumnya menggunakan `'` (digunakan untuk memisahkan string) dan `;` (digunakan untuk mengakhiri kueri SQL)
    - Oldschool
      ```
      <spasi_kosong>
      ' atau ') atau '))
      " atau ") atau "))
      ` atau `) atau `))
      ;
      ```
    - New
      - delay/sleep payload
        ```
        ' or sleep(15) and 1=1#
        ' or sleep(15)#
        ' union select sleep(15),null#
        ```
4. Coba meng-injek payload tanpa break query, bisa mengguna comment

|Database|Comment|
|---|---|
|Oracle|`--comment`|
|MySQL|`-- comment` `#comment` `/*comment*/`|
|MariaDB|`-- comment` `#comment` `/*comment*/`|
|PostgreSQL|`--comment` `/*comment*/`|
|Microsoft|`--comment` `/*comment*/`|


