# Javascript Obfuscation

## Alphanumeric encoding
- string casting<br>
```
""+1234 or 1234+"" //return "1234"
[]+1234 or 1234+[] //return "1234"

x = "hello"
[1,"a",x] //return [1,"a", "hello"]
[1,"a",x]+"" //return [1,"a", "hello"]
```
- Boolean

|false|true|
|---|---|
|![]|!![]|
|!{}|!!{}|
|!!""|!""|
|[]=={}|[]==""|
|[!![]]+""|[![]]+""|

- Number<br>
<img width="500" src="https://user-images.githubusercontent.com/52058660/161236374-fbc41101-760b-4fd7-9383-4431ba0aac1a.png"><br>
<img width="500" src="https://user-images.githubusercontent.com/52058660/161236618-cdb51a07-9e83-4c50-8739-43435bf3ab36.png">

- String
  - [jjencode](https://utf-8.jp/public/jjencode.html)
  - [aaencode](https://utf-8.jp/public/aaencode.html)
  - [jsfuck](http://www.jsfuck.com/)

## Compressing
<img width="500" src="https://user-images.githubusercontent.com/52058660/161283669-7507b16f-69d8-4af8-9258-a592fdbc3b4a.png"><br>
