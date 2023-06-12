# SQL Injection

## Writeups
|Title|Description|
|---|---|
|[SQL Injection at Spotify](https://infosecwriteups.com/sql-injection-at-spotify-d19e0861ddf0)|inject `' atau / atau \` dan amati error yang.<br>![image](https://user-images.githubusercontent.com/52058660/159397667-09fa2fdc-f9ec-4a36-b8dc-cd6cce2bc1f1.png)<br>![image](https://user-images.githubusercontent.com/52058660/159397603-504a8a1c-acf9-4ae1-8725-978f06f6061a.png)<br>![image](https://user-images.githubusercontent.com/52058660/159397728-b70f35f9-ab12-43cc-9483-67b9806c1ba9.png)<br>![image](https://user-images.githubusercontent.com/52058660/159397801-3e97cac7-76cb-46ca-9b08-7dde6c0a73a7.png)|
|[How I Hacked the Dutch Government with SQLi and Won the Famous T-Shirt?](https://goktugkaya.medium.com/how-i-hacked-the-dutch-government-and-won-the-famous-t-shirt-b45cdf5dfaa1)|Change GET to POST|
|[How I found a critical P1 bug in 5 minutes using a cellphone — Bug Bounty](https://medium.com/@mrempy/how-i-found-a-critical-p1-bug-in-5-minutes-using-a-cellphone-bug-bounty-303ebec3edd6)|injeksi pada login form<br>`admin’ and (select * from(select(sleep(40)))SQLI) and ‘abc’ = ‘abc`<br>menggunakan kiwi browser untuk menangkap request|
|[120 Days of High Frequency Hunting](https://kuldeep.io/posts/120-days-of-high-frequency-hunting/)|time delay vuln<br>`'; WAITFOR DELAY '00:00:10'-- -`|
|[Making a Blind SQL Injection a Little Less Blind](https://medium.com/@tomnomnom/making-a-blind-sql-injection-a-little-less-blind-428dcb614ba8)|sqli pada json, jika inject ' -> error, coba netralisir dengan /*'*/|
|[bypass sql injection #1109311](https://hackerone.com/reports/1224660)|`0'XOR(if(now()=sysdate(),sleep(15),0))XOR'Z`|
|[FUZZING FOR HIDDEN PARAMS](https://medium.com/@calfcrusher/fuzzing-for-hidden-params-671724bf3fd7)|fuzzing hidden parameter menggunakan ffuf dan payload arjun<br>https://github.com/Bo0oM/ParamPamPam/blob/master/params.txt|
|[Box 3: HTB - Vaccine](https://vict0rle.medium.com/box-3-htb-vaccine-393b2484e018)<br>[某站点的简单测试](http://hone.cool/2018/08/17/%E6%9F%90%E7%AB%99%E7%82%B9%E7%9A%84%E7%AE%80%E5%8D%95%E6%B5%8B%E8%AF%95/)|unable to prompt for an interactive operating system shell via the back-end DBMS because stacked queries SQL injection is not supported|

## Resource
- [Web Security Academy - SQL injection cheat sheet](https://portswigger.net/web-security/sql-injection/cheat-sheet)
- [HackTricks -  SQL Injection](https://book.hacktricks.xyz/pentesting-web/sql-injection)
- [Netsparker - SQL Injection Cheat Sheet](https://www.netsparker.com/blog/web-security/sql-injection-cheat-sheet/)
- [Finding an unseen SQL Injection by bypassing escape functions in mysqljs/mysql](https://flattsecurity.medium.com/finding-an-unseen-sql-injection-by-bypassing-escape-functions-in-mysqljs-mysql-90b27f6542b4)
- [BigQuery SQL Injection Cheat Sheet](https://ozguralp.medium.com/bigquery-sql-injection-cheat-sheet-65ad70e11eac)
- [Dumping a complete database using SQL injection [updated 2021]](https://resources.infosecinstitute.com/topic/dumping-a-database-using-sql-injection/)
- [SQLMap - Operating System Takeover - Windows](https://amolnaik4.blogspot.com/2012/05/sqlmap-operating-system-takeover.html)
