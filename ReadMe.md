# WebKit for Android

WebKit for Android is a port of WebKit engine which runs on Android and Windows platforms.
Visit [WebKit on GitHub](https://github.com/WebKit/webkit) or [WebKit Project Home](https://webkit.org) to know more about the WebKit Project.

## Building WebKit Android

### Building for Android

You need Android SDK and NDK to build. If you need to know what to do for setup, visit [Android Developers](https://developer.android.com/ndk/index.html) and [Android NDK](https://developer.android.com/ndk/index.html).
You also need CMake, Python, Ruby and Java 1.7 to accomplish the building.

* Tested build host system is Windows 64bit and Ubuntu Linux 64bit.
* Tested NDK versions are r12, r12b and r14. 

First, download WebKitLibraries package for android and put the contents under WebKitLibraries/android.

You need to setup environment variables as written below:
```
export ANDROID_SDK=<path-to-android-sdk>
export ANDROID_NDK=<path-to-android-ndk>
export PATH=$ANDROID_NDK:$ANDROID_SDK/tools:$ANDROID_SDK/platform-tools:$PATH
```
You may also need ```JAVA_HOME=<path-to-jdk>``` environment variable and need to specify path to ant tool if you are going to build with NDK for Windows.

Then generate build scripts using CMake:
```
mkdir WebKitBuild
cd WebKitBuild
cmake -DCMAKE_TOOLCHAIN_FILE=../Tools/android/android.toolchain.cmake -DCMAKE_BUILD_TYPE=Release -DANDROID_TOOLCHAIN_NAME=clang -DANDROID_ABI="armeabi-v7a with NEON" -DPORT=Android ..
```

Using ninja as generator for CMake is recommended. Add '-G "Ninja"' to cmake command if you want to do so.

Then run the following command to build:
```
cmake --build .
```
or
```
ninja
```

Note that the MiniBrowser.apk is dropped under Tools/MiniBrowser/android/bin.

### Building for Windows

For building WebKit on Windows, see the [wiki page](https://webkit.org/webkit-on-windows/).
Download WebKitLibraries package for Windows and put the contents under WebKitLibraries/win.

Then generate build scripts using CMake:
```
mkdir WebKitBuild
cd WebKitBuild
cmake -G "Visual Studio 14 2015" -D PORT=Android ..
```

You'll see WebKit.sln in the build directory. Open it and hit 'Build Solution'.
Set MiniBrowser project as the startup project and run.

## External Links

WebKit for Android is built on unique projects you might found interesting. To completely understand how the Android WebKit is done, please visit the projects below:

* [WebKitAndroidLibraries](https://github.com/daewoong-jang/webkit-android-libraries) - Third-party libraries.
* [androidjni++](https://github.com/daewoong-jang/androidjnipp) - Object-Oriented JNI generator/binder library.
* [android++](https://github.com/daewoong-jang/androidpp) - Android-like application framework written in C++.

## Contribute

You're welcome to contribute. Be sure to read the instructions first which can be found on [Contributing Code](https://webkit.org/contributing-code/).

## Copyrights

Copyright (c) 2017 NAVER Corp.
