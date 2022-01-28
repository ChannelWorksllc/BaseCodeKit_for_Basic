# PJT名称
利用するプロジェクト名称を記載してください。

# Starter Kit について

gulp で FLOCSS × Dart Sass のコーディングをするためのスターターキット。
Git のリポジトリをコピー後、ターミナルで以下のコマンドを実行。

`git clone https://github.com/ChannelWorksllc/BassCodeKit_for_Basic.git`

`npm install`

`npx gulp`

「http://localhost:3000/」
上記 URL にてローカルサーバーが立ち上がる。  
HTML の編集や Sass のコンパイルに対して自動でリロード。

Wordpressを利用する場合は、Dockerが導入されている前提で、
「/docs/wordpress」にcdで移行し、以下を実行。
「docker-compose.yml」において、my_wordpressの箇所などは任意に変更。

# M1 Macの場合事前に以下
$ docker pull --platform linux/amd64 mysql:5.7

# コンテナ起動
$ docker-compose up -d

Wordpress利用しない場合は、
「/src/_component/_head.ejs」におけるWordpress周りの記載を変更する。


# 技術構成

構成としては、以下のようなディレクトリになっています。

```
docs
 │ index.html
 │
 └─wordpress
    └─wp-content
        └─themes 
          └─edu_style
            └─asset
                └─css
                ├─img
                └─js
 │
src
 │ index.ejs
 │
 └─about
 │ index.ejs
 │
 └─_component
 │ _header.ejs
 │ _footer.ejs
 │ _head.ejs
 │
 └─asset
    ├─img
    ├─js
    └─sass
       │ style.scss
       │
       ├─foundation
       │   _base.scss
       │   _reset.scss
       │   _system.scss
       │
       ├─layout
       │   _footer.scss
       │   _header.scss
       │   _main
       │
       └─object
          ├─component
          │   _sample1.scss
          │
          ├─pages
          │   _top.scss
          │
          └─utility
          │   _sample2.scss
```

`src`内でコーディングして`docs`にコンパイルしたファイルを出力する構成。


## gulpの機能

gulpfileに書いている機能としては大体以下の5つの機能。

- Dart Sass のコンパイル
- CSS の縮小化
- JavaScript の縮小化
- ローカルサーバーの立ち上げ
- 作業ファイルの監視（自動更新）

## ファイル構成
### gulpfile.js

上述した gulp の機能を記載しているファイルです。

### docs

コンパイル後の HTML や CSS（納品・デプロイするフォルダ）

github pages の公開ディレクトリで docs を選択すると通常通り公開することも可能です。

### src

コーディング用の HTML や SCSS ファイル。

### src/asset/sass

Sass のコーディングファイル。CSS 設計は FLOCSS を採用しています。
Sass 自体は Dart Sass でコーディングして、sass フォルダ直下の style.scss ですべての Sass ファイルを`@use`しています。
Sass の構成一覧は以下のような感じです。


# 使い方
## 前提条件

前提として node.js と npm 、Dockerがインストールされていること。

## 実際に使う流れ

前提条件が整っていれば、以下のような流れで進行。

1. 開発フォルダに `cd` コマンドで移動。
2. `git clone https://github.com/ChannelWorksllc/BassCodeKit_for_Basic.git` を実行
3. `npm install` を実行
4. `npx gulp` を実行
5. `src` 内でコーディング
6. `docs` 内のファイルを納品・デプロイ

まずは、gitをcloneします。

```
git clone https://github.com/ChannelWorksllc/BassCodeKit_for_Basic.git
``` 

ファイルが生成されるので、`npm install` で `node_module` など必要なファイルをインストール。

```
npm install
``` 

そのまま、 `npx gulp` を実行すれば、Dart Sassがコンパイルされ「コンパイルが成功されました」と表記されて、
`http://localhost:3000/`が自動的にローカルサーバーが立ち上がる。

```
npx gulp
``` 

そのままコーディングしたら随時反映されるようになるので、`src` でコーディングしていきましょう。
コーディングが終われば、`docs` ファイルに必要なHTML,CSS,JavaScript,画像ファイルが出来上がっているかと思うので、こちらを納品、もしくはデプロイしていけばOK。

Wordpressを利用する場合は、Dockerが導入されている前提で、
「/docs/wordpress」にcdで移行し、以下を実行。

```
$ docker-compose up -d
``` 
「docker-compose.yml」において、my_wordpressの箇所などは任意に変更。


不明なことは、以下までお問い合わせください。
https://channelworks.biz/contact_us