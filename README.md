# chore_flutter

## 概要

Webサイトも作れるようになるらしいのでちょっと見る

- https://flutter.dev

- macOSで開発が安定してるらしい
  - https://flutter.dev/docs/get-started/install/macos

## 初期設定

- sdkはzipを展開してflutter/binにPATHを通すだけ
  - 展開先は ~/.flutter はダメ（configが格納されるのでディレクトリが作れないと動かない）

- dart/flutterパッケージにrenovatebotが効くらしいので、renovateはオンにしておくと良さそう

### 初期化なのかなんなのか？

```
$ flutter precache

  ╔════════════════════════════════════════════════════════════════════════════╗
  ║                 Welcome to Flutter! - https://flutter.dev                  ║
  ║                                                                            ║
  ║ The Flutter tool anonymously reports feature usage statistics and crash    ║
  ║ reports to Google in order to help Google contribute improvements to       ║
  ║ Flutter over time.                                                         ║
  ║                                                                            ║
  ║ Read about data we send with crash reports:                                ║
  ║ https://github.com/flutter/flutter/wiki/Flutter-CLI-crash-reporting        ║
  ║                                                                            ║
  ║ See Google's privacy policy:                                               ║
  ║ https://www.google.com/intl/en/policies/privacy/                           ║
  ║                                                                            ║
  ║ Use "flutter config --no-analytics" to disable analytics and crash         ║
  ║ reporting.                                                                 ║
  ╚════════════════════════════════════════════════════════════════════════════╝

```

### 必要なものが入ってるかチェック

チェックだけじゃなくってXcode系の何かを入れようとしたりする。
パスワードを求められた。

```
$ flutter doctor
Doctor summary (to see all details, run flutter doctor -v):


[✓] Flutter (Channel stable, v1.5.4-hotfix.2, on Mac OS X 10.14.4 18E226, locale ja-JP)
[✗] Android toolchain - develop for Android devices
    ✗ Unable to locate Android SDK.
      Install Android Studio from: https://developer.android.com/studio/index.html
      On first launch it will assist you in installing the Android SDK components.
      (or visit https://flutter.dev/setup/#android-setup for detailed instructions).
      If the Android SDK has been installed to a custom location, set ANDROID_HOME to that location.
      You may also want to add it to your PATH environment variable.

[!] iOS toolchain - develop for iOS devices (Xcode 10.2.1)
    ✗ Xcode requires additional components to be installed in order to run.
      Launch Xcode and install additional required components when prompted.
    ✗ libimobiledevice and ideviceinstaller are not installed. To install with Brew, run:
        brew update
        brew install --HEAD usbmuxd
        brew link usbmuxd
        brew install --HEAD libimobiledevice
        brew install ideviceinstaller
    ✗ ios-deploy not installed. To install:
        brew install ios-deploy
    ✗ CocoaPods not installed.
        CocoaPods is used to retrieve the iOS platform side's plugin code that responds to your plugin usage on the Dart side.
        Without resolving iOS dependencies with CocoaPods, plugins will not work on iOS.
        For more info, see https://flutter.dev/platform-plugins
      To install:
        brew install cocoapods
        pod setup
[!] Android Studio (not installed)
[!] Connected device
    ! No devices available

! Doctor found issues in 4 categories.
```

しばらく待つとgen_snapshotのアーキテクチャが古いみたいなアラートが出る。

- Android Studioを入れる
- Studioを起動しただけだとAndroid SDKのライセンスに同意するところはないらしいので確認しろって言われる
  - flutter doctor --android-licenses
- libimobiledevice and ideviceinstaller are not installed
  - brewで書いてある通りに

brew update
brew install --HEAD usbmuxd
brew link usbmuxd
brew install --HEAD libimobiledevice
brew install ideviceinstaller
brew install ios-deploy
brew install cocoapods
pod setup

libmobiledeviceあたりを入れるところでPythonの2.7系がインストールされてるって出てエラーになった。
/usr/local/Cellar/Python/2.7.14を取り除いてやり直し（3系が入った）。

If you need to have libxml2 first in your PATH run:
  echo 'export PATH="/usr/local/opt/libxml2/bin:$PATH"' >> ~/.zshrc

For compilers to find libxml2 you may need to set:
  export LDFLAGS="-L/usr/local/opt/libxml2/lib"
  export CPPFLAGS="-I/usr/local/opt/libxml2/include"

For pkg-config to find libxml2 you may need to set:
  export PKG_CONFIG_PATH="/usr/local/opt/libxml2/lib/pkgconfig"

flutter doctorでAndroid StudioのFlutter pluginとDart pluginが入ってないという問題が残る。
Android Studioを起動して、PreferecesからPlugin設定にいってインストール（Flutterを入れたら依存でDartも入った）。

Simulatorを起動してdoctorしたらNo issues found!になった。

```
$ flutter doctor
Doctor summary (to see all details, run flutter doctor -v):
[✓] Flutter (Channel stable, v1.5.4-hotfix.2, on Mac OS X 10.14.4 18E226, locale ja-JP)

[✓] Android toolchain - develop for Android devices (Android SDK version 28.0.3)
[✓] iOS toolchain - develop for iOS devices (Xcode 10.2.1)
[✓] Android Studio (version 3.4)
[✓] Connected device (1 available)

• No issues found!
```

## いずれ見る

- flutter redux
  - https://qiita.com/ko2ic/items/97aeaa4bdbaa6a7e6cbe
