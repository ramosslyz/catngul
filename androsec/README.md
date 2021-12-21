# Android Penetration Testing

## Vulnerability
## 1. Information Gathering
- __Extracting apps__
  - gplaycli
    ```
    gplaycli -p -v -d com.google.android.keep
    ```
  - Extract from device
    - adb
      ```
      adb shell pm list packages
      adb shell pm path <package name>
      adb pull <apk path>
      ```
  - Alternative App Store (Pilihan terakhir)
    - APKMirror
    - APKPure
- 
 
## 2. Reversing 
- __Tools__
  - adb
  - apktool

## 3. Static Analysis
- __Tools__
  - MobSF
  - Android Studio's built-in Device File Explorer

## 4. Dynamic Analysis
- __Tools__
  - MobSF
  - Frida
  - Objection
  - Termux

## Resource
- [Ignitetechnologies - Android Penetration Testing](https://github.com/Ignitetechnologies/Android-Penetration-Testing)
- [sundaysec - Android-Exploits](https://github.com/sundaysec/Android-Exploits)
- [Guide to Setting Up Android Pentesting Lab](https://securityjunky.com/guide-to-setting-up-android-pentesting-lab/)
