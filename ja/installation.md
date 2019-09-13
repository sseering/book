# Nuのインストール

今のところNuをインストールするもっともよい方法は、[crates.io](https://crates.io)からインストールするか、ビルド済のバイナリーを[リリースページ](https://github.com/nushell/nushell/releases)からダウンロードするか、ソースからビルドすることです。
Dockerを利用してビルド済のコンテナをプルしてくる方法もあります。

## ビルド済みのバイナリー

ビルド済のNuは[リリースページ](https://github.com/nushell/nushell/releases)からダウンロードできます。もし、[Homebrew](https://brew.sh/) for macOSを利用しているなら、`brew install nushell`を実行して、バイナリーをインストールできます。

## ビルド済のDockerコンテナ

ビルド済のDockerコンテナをプルしたい場合はQuay.io上で[nushell organization](https://quay.io/organization/nushell)のためのタグを閲覧できます。
コンテナのプルは以下のように行います。

```bash
$ docker pull quay.io/nushell/nu
$ docker pull quay.io/nushell/nu-base
```

"nu-base"と"nu"のどちらにもバイナリーが含まれますが、nu-baseには`/code`内にソースコードと全ての依存関係も含まれています。

オプションで提供されている[dockerfiles provided](https://github.com/nushell/nushell/tree/master/docker)を利用してローカルにコンテナをビルドすることもできます。
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

### Rustのインストール

Rustがシステムにまだインストールされていない場合は、[rustup](https://rustup.rs/)を利用してRustをインストールする方法がベストです。Rustupは、異なるRustのバージョンのインストールを管理するツールです。

Nuは現在、Rustの**nightly** バージョンを必要とします。最初に"rustup"を実行すると、インストールするRustのバージョンを尋ねられます。

```
Current installation options:

   default host triple: x86_64-unknown-linux-gnu
     default toolchain: stable
  modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
```

オプション#2を選択してインストールをカスタマイズします。

```
Default host triple?
```

Enterを押してデフォルトを選択します。

```
Default toolchain? (stable/beta/nightly/none)
```

ここでは必ず、"nightly"と入力してEnterを押してください。こうすることで次のセットアップが行われます。

```
Modify PATH variable? (y/n)
```

オプションでパスを更新できます。これは、後の手順を簡単にするために一般的には良いアイデアです。


```
Current installation options:

   default host triple: x86_64-unknown-linux-gnu
     default toolchain: nightly
  modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
```

デフォルトのツールチェインがnightlyになっていることがわかります。不安に思われるかもしれませんが、心配しないでください。Rustのコンパイラーは一連のテストすべてを通過しています。大抵の場合、安定バージョンと同じくらい信頼できます。

準備ができたら、1を押します。"rustup"の指示に従えば、Rustコンパイラーのインストールが完了するはずです。

もしも、"rustup"経由でRustをインストールしたくない場合は、他の方法(Linuxディストリビューションのパッケージ等)でインストールすることもできます。ただし、最新のnightlyバージョンのツールチェインがインストールされるようにしてください。

## 依存関係

### Debian/Ubuntu

"pkg-config"と"libssl-dev"パッケージをインストールしてください。

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
nushell> cargo build --all-features && cargo run --all-features
```

リリースモードでNuをビルドし実行することもできます。

```
nushell> cargo build --release && cargo run --release
```
Rustに慣れている人は、"run"はデフォルトでビルドを行うので、"build"と"run"の両方を実行することに疑問をもつかもしれません。これは、Cargoの新しい`default-run`オプションの欠点を回避して、すべてのプラグインが確実にビルドされるようにするためです。ただし、将来的には必要なくなるかもしれません。
