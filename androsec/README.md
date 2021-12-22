# Android Penetration Testing

## Vulnerability
1. __Insecure Connection__
  - Use insecure of network protocol
  - Data transmision over insecure protocol
  - Authentication over insecure protocol
2. __Cryptography and authentication__
  - Embedded third party secret
  - Embedded cryptography secret
  - Leaking OAuth token
3. __Private file access__
  - Private data sharing
  - Privata data overwrite due to path traversal
  - Private data overwrite due to ZIP file traversal
4. __Unprotected app parts__
  - Unprotected activities
  - Unprotected services
  - Typo in custom permisions
  - Intent redirection
  - implicit broadcast (sending)
  - implicit broadcast (receiving)
5. __Other__
  - Incorect url verification
  - Cross-app scripting
  - Incorect sandboxing of scripting language
  - Unprotected data on server
 
## Tools
- adb
- apktool
- MobSF
- Frida
- Objection
- Termux
- Mobexler
- Android Studio's built-in Device File Explorer
- Magisk -> Root Android device
- RootAVD -> Root Android emulator

## Set up
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

## Information Gathering
## Reversing 

## SAST

## DAST

## Resource
- [Ignitetechnologies - Android Penetration Testing](https://github.com/Ignitetechnologies/Android-Penetration-Testing)
- [sundaysec - Android-Exploits](https://github.com/sundaysec/Android-Exploits)
- [Guide to Setting Up Android Pentesting Lab](https://securityjunky.com/guide-to-setting-up-android-pentesting-lab/)
- [LevelUp 0x04 - Fun with Frida on Mobile](https://www.youtube.com/watch?v=dqA38-1UMxI)
- [Resources-for-Beginner-Bug-Bounty-Hunters - Mobile Hacking](https://github.com/nahamsec/Resources-for-Beginner-Bug-Bounty-Hunters/blob/master/assets/mobile.md)
