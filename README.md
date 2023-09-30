# Swagger
## OpenAPIドキュメントの書き方

<details>
<summary>OpenAPIオブジェクト</summary>

OpenAPIドキュメントのルーティング設定ドキュメントオブジェクトの設定から行います。

定義されているオブジェクトは以下になります。[OpenAPI GitHub](https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.0.3.md#schema)から
フィールド名|タイプ|説明
---|---|---
openapi|string|**必須** OpenAPIのバージョン
info|Info Object|**必須** APIに関するメタデータを提供
7|8|9
10|11|12
</details>

<details>
<summary>OpenAPIバージョン指定</summary>

ここではOpenAPIのバージョンを指定します。
APIの仕様はバージョンごとに異なるため、使用するOpenAPIのバージョンを明示することが重要です。
現在の最新バージョンは3.0です。

```
openapi: "3.0.3"
```
</details>

<details>
<summary>情報の提供（Info Object）</summary>

`info`オブジェクトは以下のようなAPIに関する基本的な情報を提供します。
* APIのタイトル
* 説明
* 利用規約
* 連絡先
* ライセンス
* バージョン

※ここでのバージョンはOpenAPIのバージョンとは異なります。
API自体のバージョンになります。
```
info:
    title: "予約管理API"
    description: "予約機能を提供するAPI"
    version: "1.0.0#
```
※利用規約、連絡先、ライセンスを省いています。
</details>

<details>
<summary>サーバーの定義（Servers）</summary>

`Servers`はAPIがホストされているサーバーのエンドポイントの情報を提供します。
この情報は、APIを呼び出す際の基本URLやエンドポイントに関するものです。
※複数サーバー定義することが可能です。

```
servers:
  - url: "http://localhost:{post}"
    description: "開発環境サーバー"
    variables:
      port:
        enum: ["8080"]
        default: "8080"
```
※ローカルホストの8080番を定義しています。
</details>
