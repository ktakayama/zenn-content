---
title: "JulesでFlutterアプリの環境設定をする"
emoji: "🎼"
type: "tech"
topics: ["jules", "flutter", "fvm"]
published: false
publication_name: arm_techblog
---

Googleが提供するCoding AgentのJulesが正式版となったようです。

https://jules.google/

Webブラウザから開発の指示ができるので、非同期で作業が進められるのが便利です。

早速個人のプロジェクトで開発をしてみようと触ったところ、いきなりFlutterのビルドができなくてつまずいてしまったので設定方法を書いておきます。しっかりドキュメントを読み進めれば問題はない内容ではありますけども、あまり情報が見当たらなかったもので、誰かの参考になれば。

https://jules.google/docs

## 初期状態では、エラーが発生

素の状態で開発を始めると、`flutter`や`fvm`コマンドが見つからないというエラーが発生します。

![](/images/ac41d0abcfc162/fail.png =500x)

エージェントだから自立的に動いて環境設定もしてくれるのかと思いきや、そのあたりはうまく動いてくれなさそうです。

## 解決のためには環境設定をする

結論としては、Configurationという画面でVirtual Machineのセットアップコマンドを設定して問題を解消します。`fvm`を使いたいだけならすごくシンプルです。

```sh
curl -fsSL https://fvm.app/install.sh | bash
fvm install
fvm flutter pub get
```

以下の画面から設定します。`Run and snapshot`をクリックして一旦実行しないと保存されないので注意してください。

![](/images/ac41d0abcfc162/configuration.png)

ドキュメントを見ると、PythonやNodeJSなどの環境は充実してるみたいですね。

https://jules.google/docs/environment/

Virtual MachineのOSはUbuntuのようです。なのでiOSのビルドはできませんが、cocoapodsをインストールしておくことはできそうでした。Rubyも、自前でインストールしないと使えない状態だったのは悲しかったです。

```sh
sudo apt install -y ruby-full
sudo gem install cocoapods
```



