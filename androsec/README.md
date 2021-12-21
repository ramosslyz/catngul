# Android Penetration Testing

## Vulnerability
- Insecure Connection

## Tools
- adb
- apktool
- MobSF
- Frida
- Objection
- Termux
- Mobexler
- Android Studio's built-in Device File Explorer

## Information Gathering
- __Extracting apps__
  - gplaycli
    ```
    gplaycli -p -v -d com.google.android.keep
    ```
  - Extract from device (adb)
    ```
    adb shell pm list packages
    adb shell pm path <package name>
    adb pull <apk path>
    ```
  - Alternative App Store (Pilihan terakhir)
    - APKMirror
    - APKPure
## Reversing 

## SAST

## DAST

## Resource
- [Ignitetechnologies - Android Penetration Testing](https://github.com/Ignitetechnologies/Android-Penetration-Testing)
- [sundaysec - Android-Exploits](https://github.com/sundaysec/Android-Exploits)
- [Guide to Setting Up Android Pentesting Lab](https://securityjunky.com/guide-to-setting-up-android-pentesting-lab/)
- [LevelUp 0x04 - Fun with Frida on Mobile](https://www.youtube.com/watch?v=dqA38-1UMxI)
- [Resources-for-Beginner-Bug-Bounty-Hunters - Mobile Hacking](https://github.com/nahamsec/Resources-for-Beginner-Bug-Bounty-Hunters/blob/master/assets/mobile.md)
