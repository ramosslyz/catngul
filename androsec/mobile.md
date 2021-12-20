# MOBSEC

## Fundamental Knowledge
- Java
- Kotlin
- APK
- SDK


## Methodolody
- Static analysis & app recon 
  - Cek AndroidManifest dan REST API with MobSF
  - Cek list installed package with adb
  - Cek and find packege info with drozer
- Network communication capture analysis
  - Cek Insecure communication (Non encrypted tools, Certificate pinning, MITM exposure and proxy impact, Certificate Validation) with Burp Suite
  - Cek full packet capture with WIFI soft AP, wireshark, tcpdump, tshark, Bro
- Insecure data storage with adb shell and linux utilities (diff, grep, strings)
- Extraneous functionality
  - Cek interesting functionality with jadx and manipulate with drozer
    - getExtra
    - putExtra
    - ACTION_CALL
    - getCellLocation
    - processBuilder
 - Code level quality and tampering


## Tools
- Static Analysis
  - apktool
  - mobsf
  - jadx
  - adb
  - dex2jar
- Dynamic Analysis
  - Frida
  - Drozer
  - Runtime Mobile Security (RMS)
  - Objection

## Write-up
### Hackthebox
- [Dont Overreact](https://rfmirror.com/Thread-Tutorial-Don-t-Overreact-Mobile)
- [Cat](https://infosecwriteups.com/extract-an-android-backup-file-96172efd4d86)
- [APkey](https://acvn.github.io/write-ups/APKey.html)

## Resource
- [The Mobile Hacking CheatSheet](https://github.com/randorisec/MobileHackingCheatSheet)
- [Introduction to Android Hacking by @0xteknogeek](https://www.hackerone.com/blog/androidhackingmonth-intro-to-android-hacking)
- [Android App Reverse Engineering 101](https://www.ragingrock.com/AndroidAppRE/)
- [Q&A With Android Hacker bagipro](https://www.hackerone.com/blog/AndroidHackingMonth-qa-with-bagipro)
- [ndroid-Reports-and-Resources](https://github.com/B3nac/Android-Reports-and-Resources)
- [Android Application Pentesting - Mystikcon 2020](https://www.youtube.com/watch?v=NrxTBcjAL8A)
- [Android App Penetration Testing 101](https://www.youtube.com/watch?v=2uwhrfXCl4I)
- [CodePath Android Cliffnotes](https://guides.codepath.com/android)
- [Android APK Checklist](https://book.hacktricks.xyz/mobile-apps-pentesting)
