# Shopify-Theme

## 1. Dockerコンテナの起動

下記コマンドを実行し、コンテナを起動する。
``` sh
docker compose up -d --build
```

下記コマンドを実行し、appコンテナに入る。
``` sh
docker compose exec app bash
```


## 2. Shopifyテーマの初期化

`shopify theme init`コマンドで、GitリポジトリからローカルにShopifyテーマをクローンする。

```sh
shopify theme init [ディレクトリ名] -u [ShopifyテーマのGitリポジトリのURL]
```

#### 例

```sh
shopify theme init theme -u https://github.com/Shopify/dawn.git
```


## 3. ローカル開発サーバーの起動

作成したテーマのディレクトリに移動し、`shopify theme dev`コマンドで、ローカル開発サーバーを起動する。

```sh
cd [ディレクトリ名]
```
```sh
shopify theme dev --store [ストアのURL]
```

#### 例

```sh
cd theme
```
```sh
shopify theme dev --store fork-yoshino-training.myshopify.com
```

`sopify theme dev`で開発サーバーを起動すると、初回はShopifyアカウントへのログインが求められる。

アカウントにログインすると、`http://127.0.0.1:3456`にリダイレクトされるが、
localhostのみでしかリクエストを受け入れないようになっているためかエラーとなるので、
リダイレクトしたURLをコピーし、ターミナルを追加で開き、コンテナ内で`curl`コマンドを実行しログインをする。

```sh
# URLに&が入っているため、ダブルクォートで囲う
curl "リダイレクト先のURL"
```

`shopify theme dev`をしたターミナルに戻り、`✔ Logged in.`という文字列が出力されログインに成功すると、開発サーバーを起動が再開される。

Webブラウザで http://127.0.0.1:9292 へアクセスし、開発サーバーが起動していることを確認する。


## 参考

https://zenn.dev/merutin/scraps/c7219fe318c02d<br>
