# chore_flutter

Webサイトも作れるようになるらしいのでちょっと見る

- https://flutter.dev

- macOSで開発が安定してるらしい
  - https://flutter.dev/docs/get-started/install/macos

- sdkはzipを展開してflutter/binにPATHを通すだけ
  - 展開先は ~/.flutter はダメ（configが格納されるのでディレクトリが作れないと動かない）

- dart/flutterパッケージにrenovatebotが効くらしいので、renovateはオンにしておくと良さそう

- 初期化なのかなんなのか？

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

## いずれ見る

- flutter redux
  - https://qiita.com/ko2ic/items/97aeaa4bdbaa6a7e6cbe
