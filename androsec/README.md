# ANDROID HACKING

2. [Vulnerability](https://github.com/acvn/catngul/blob/master/androsec/android-vuln.md)
3. [Tools](https://github.com/acvn/catngul/blob/master/androsec/android-tools.md)
4. [DIVA](https://github.com/acvn/catngul/blob/master/androsec/diva.md)

## Tips N Trick
1. Cek __versi__ aplikasi, apakah sesuai dengan kickoff meeting
2. Langkah pertama adalah review __AndroidManifest.xml__, adalah bluetprint aplikasi android
3. Cek activity yang memiliki atribut `android:exported:"true"` , pastikan activity yang __confidential__ memiliki atribut `android:exported:"false"`
4. Cek sensitive value pada string reference string.xml, kadang disana terdapat API key dan credential tertentu
5. Decode semua value Base64
6. Cek certificate pinning dan SSL pinning
7. Bypass root detection
8. Aplikasi yang menggunakan flutter perlu modifikasi tertentu untuk intercept
9. Cek logcat
10. cek jwt, lalu extract pake jwt toll
11. Cek mobsf, konfirmasi vulnerabilitynya
12. android debug dan android backup tidak boleh enabled
13. cek memory dump
14. cek anti brute protection pada authentication
15. Apabila apk tidak bisa didecompile dengan jadx, pull apk langsung dari androidnya
16. Selalu scan subdomain dari situs yang berhubungan dengan aplikasi, kemungkinan credential yang terdapat pada apk bisa berfungsi di subdomain tersebut
17. Check device binding
18. Jika ada fitur QR, coba scan QR lain

## Resource
- [Ignitetechnologies - Android Penetration Testing](https://github.com/Ignitetechnologies/Android-Penetration-Testing)
- [sundaysec - Android-Exploits](https://github.com/sundaysec/Android-Exploits)
- [LevelUp 0x04 - Fun with Frida on Mobile](https://www.youtube.com/watch?v=dqA38-1UMxI)
- [Resources-for-Beginner-Bug-Bounty-Hunters - Mobile Hacking](https://github.com/nahamsec/Resources-for-Beginner-Bug-Bounty-Hunters/blob/master/assets/mobile.md)
- [The Mobile Hacking CheatSheet](https://github.com/randorisec/MobileHackingCheatSheet)
- [Introduction to Android Hacking by @0xteknogeek](https://www.hackerone.com/blog/androidhackingmonth-intro-to-android-hacking)
- [Android App Reverse Engineering 101](https://www.ragingrock.com/AndroidAppRE/)
- [Q&A With Android Hacker bagipro](https://www.hackerone.com/blog/AndroidHackingMonth-qa-with-bagipro)
- [ndroid-Reports-and-Resources](https://github.com/B3nac/Android-Reports-and-Resources)
- [Android Application Pentesting - Mystikcon 2020](https://www.youtube.com/watch?v=NrxTBcjAL8A)
- [Android App Penetration Testing 101](https://www.youtube.com/watch?v=2uwhrfXCl4I)
- [CodePath Android Cliffnotes](https://guides.codepath.com/android)
- [Android APK Checklist](https://book.hacktricks.xyz/mobile-apps-pentesting)
- [Mobile Application Penetration Testing Cheat Sheet](https://github.com/tanprathan/MobileApp-Pentest-Cheatsheet)
- [Android security checklist: WebView](https://blog.oversecured.com/Android-security-checklist-webview/)

## Methodolody
- Static analysis & app recon 
  - Cek AndroidManifest dan REST API with MobSF
  - Cek list installed package with adb
  - Cek and find packege info with drozer
- Network communication capture analysis
  - Cek Insecure communication (Non encrypted tools, Certificate pinning, MITM exposure and proxy impact, Certificate Validation) with Burp Suite
  - Cek ful packet capture with WIFI soft AP, wireshark, tcpdump, tshark, Bro
- Insecure data storage with adb shell and linux utilities (diff, grep, strings)
- Extraneous functionality
  - Cek interesting functionality with jadx and manipulate with drozer
    - getExtra
    - putExtra
    - ACTION_CALL
    - getCellLocation
    - processBuilder
 - Code level quality and tampering

## Write-up
### Hackthebox
- [Dont Overreact](https://rfmirror.com/Thread-Tutorial-Don-t-Overreact-Mobile)
- [Cat](https://infosecwriteups.com/extract-an-android-backup-file-96172efd4d86)
- [APkey](https://acvn.github.io/write-ups/APKey.html)


