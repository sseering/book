---
layout: content
title: Nuのインストール
prev: 開始
next: はじめに
link_prev: /ja/table_of_contents.html
link_next: /ja/introduction.html
---

今のところNuをインストールするもっともよい方法は、[crates.io](https://crates.io)からインストールするか、ビルド済のバイナリーを[リリースページ](https://github.com/nushell/nushell/releases)からダウンロードするか、ソースからビルドすることです。
Dockerを利用してビルド済のコンテナをプルしてくる方法もあります。

## ビルド済みのバイナリー

ビルド済のNuは[リリースページ](https://github.com/nushell/nushell/releases)からダウンロードできます。もし、macOSで[Homebrew](https://brew.sh/) を利用しているなら、`brew install nushell`を実行して、バイナリーをインストールできます。

## Windows

**Note** NuはWindows 10で動作しますが、現在のところ7/8.1のサポートはありません。

[リリースページ](https://github.com/nushell/nushell/releases)から`.zip`ファイルをダウンロードして、例えば次の箇所に解凍します。

```
C:\Program Files
```

そして、`nu`フォルダをPATHに追加します。これが済めば、`nu`コマンドでNuを起動できます。

```
> nu
C:\Users\user>
```

もし、[Windows Terminal](https://github.com/microsoft/terminal)を使っているなら、次のようにして`nu`をデフォルトシェルに指定できます。

```         
            {
            "guid": "{2b372ca1-1ee2-403d-a839-6d63077ad871}",
            "hidden": false,
            "name": "Nu Shell",
            "commandline": "nu.exe"
            }
```

この設定をTerminal Settingsの`"profiles"`に追加します。そして、`"defaultProfile"を次のように変更します。

```
"defaultProfile": "{2b372ca1-1ee2-403d-a839-6d63077ad871}",
```

これで`nu`がWindows Terminalの起動時にロードされます。

## ビルド済のDockerコンテナ

ビルド済のDockerコンテナをプルしたい場合はQuay.io上で[nushell organization](https://quay.io/organization/nushell)のためのタグを閲覧できます。
コンテナのプルは以下のように行います。

```bash
$ docker pull quay.io/nushell/nu
$ docker pull quay.io/nushell/nu-base
```

"nu-base"と"nu"のどちらにもバイナリーが含まれますが、nu-baseには`/code`内にソースコードと全ての依存関係も含まれています。

[dockerfiles](https://github.com/nushell/nushell/tree/master/docker)を利用してローカルにコンテナをビルドすることもできます。
ベースイメージをビルドするには:

```bash
$ docker build -f docker/Dockerfile.nu-base -t nushell/nu-base .
```

そして、小さなコンテナをビルドするには(マルチステージビルドを利用):

```bash
$ docker build -f docker/Dockerfile -t nushell/nu .
```

どちらの方法でも、次のようにコンテナを実行できます:

```bash
$ docker run -it nushell/nu-base
$ docker run -it nushell/nu
/> exit
```

サイズを重要視する場合は、２番目のコンテナのほうが少し小さくなります。

## 事前準備

Nuをインストールする前に、システムに必要なツールがそろっているか確認する必要があります。現在、Rustのツールチェインといくつかの依存関係が必要です。

### コンパイラスイートのインストール

Rustが適切に機能するには、互換性のあるコンパイラスイートがシステムにインストールされている必要があります。推奨されるコンパイラスイートは次のとおりです。

* Linux: GCC or Clang
* macOS: Clang (install Xcode)
* Windows: [Visual Studio Community Edition](https://visualstudio.microsoft.com/vs/community/)

LinuxとmacOSの場合、コンパイラのインストールが完了すれば、`rustup`でのRustのインストールの準備が整います。

Windowsの場合、Visual Studio Community Editionをインストールするときに、「C ++ビルドツール」をインストールする必要があります。
オプショナルなインストールとして提供されている`link.exe`が必要なためです。これで次のステップに進む準備ができました。

### Rustのインストール

Rustがシステムにまだインストールされていない場合は、[rustup](https://rustup.rs/)を利用してRustをインストールする方法がベストです。Rustupは、異なるRustのバージョンのインストールを管理するツールです。

Nuは現在、**最新のstable(1.39 or later)** バージョンのRustを必要とします。
`rustup`で正しいversionを選択するのが良い方法です。
最初に"rustup"を実行すると、インストールするRustのバージョンを尋ねられます。

```
Current installation options:

   default host triple: x86_64-unknown-linux-gnu
     default toolchain: stable
  modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
```

準備ができたら、1を押してからエンターを押します。

もし、`rustup`を経由してRustをインストールしたくない場合、他の方法でもインストールすることができます。(例えば、Linuxディストリビューションのパッケージから)
その場合でもRustの1.39以上のバージョンがインストールされるようにしてください。
## 依存関係

### Debian / Ubuntu

"pkg-config"および"libssl-dev"パッケージをインストールしてください。

```
apt install pkg-config libssl-dev
```

`rawkey`や`clipboard`機能を使用するLinuxユーザーは"libx11-dev"および"libxcb-composite0-dev"パッケージをインストールする必要があります。

```
apt install libxcb-composite0-dev libx11-dev
```

### macOS

[Homebrew](https://brew.sh/)を利用して、"openssl"と"cmake"をインストールしてください。

```
brew install openssl cmake
```

## [crates.io](https://crates.io)からのインストール

必要となる依存関係が準備できたら、Rustコンパイラーに付属している`cargo`を使って、Nuをインストールできます。

```
> cargo install nu
```

これでおしまいです！`cargo`はNuのソースコードとその依存関係をダウンロードしてビルドし、`cargo`のバイナリーパスにインストールすることでNuを実行できるようにします。

より多くの機能をインストールするには、次のようにします。

```
> cargo install nu --features=stable
```

すべての機能を利用するための最も簡単な方法はNuをチェックアウトして、Rustツールを利用してビルドすることです。

```
> git clone https://github.com/nushell/nushell.git
> cd nushell
nushell> cargo install --path . --force --features=stable
```

インストールが完了すると、`nu`コマンドでNuを実行できます。

```
$ nu
/home/jonathan/Source>
```

## ソースからビルド

githubのソースから直接ビルドすることもできます。こうすることで、最新の機能やバグ修正にすぐにアクセスすることができます。

```
> git clone https://github.com/nushell/nushell.git
```

Gitでメインのnushellリポジトリをクローンし、Nuをビルドして実行できます。

```
> cd nushell
nushell> cargo build --workspace --features=stable && cargo run --features=stable
```

リリースモードでNuをビルドし実行することもできます。

```
nushell> cargo build --release --workspace --features=stable && cargo run --release --features=stable
```
Rustに慣れている人は、"run"はデフォルトでビルドを行うので、"build"と"run"の両方を実行することに疑問をもつかもしれません。これは、Cargoの新しい`default-run`オプションの欠点を回避して、すべてのプラグインが確実にビルドされるようにするためです。ただし、将来的には必要なくなるかもしれません。


## ログインシェルとして設定するには

**!!! Nuは開発中なので、日常使いのシェルとしての安定性を欠く可能性があります!!!**

[`chsh`](https://linux.die.net/man/1/chsh)コマンドを使用して、ログインシェルを設定できます。
一部のLinuxディストリビューションには`/etc/shells`に有効なシェルのリストが記載されており、Nuがホワイトリストに登録されるまで変更ができません。
`shells`ファイルを更新していない場合は次のようなエラーが表示される場合があります。

```
chsh: /home/username/.cargo/bin/nu is an invalid shell
```

Nuバイナリを`shells`ファイルに追加することにより、許可されたシェルのリストにNuを追加できます。
追加するパスは`which nu`コマンドで見つけることができます。通常は`$HOME/.cargo/bin/nu`です。
