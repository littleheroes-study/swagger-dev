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
<summary>基本的なデータ型</summary>
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
    title: "美容院予約管理API"
    description: "美容院予約機能を提供するAPI"
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

<details>
<summary>パスと操作の定義（Paths Object）</summary>

APIのパスと操作、リクエスト・レスポンスを定義します。
### Paths Object
    * 個々のエンドポイントへの相対パスです。このフィールド名はスラッシュ（/）で始まる必要があります。
    * パスは、Servers Objectのurlフィールドからの拡張されたURLに追加されます（相対URLの解決は行いません）。
    * パステンプレートを使用することができます。URLのマッチングでは、具象的な（テンプレートを含まない）パスが、テンプレートを含むものよりも先にマッチされます。
    * 同じ階層にあるがテンプレート名が異なるテンプレート化されたパスは存在してはいけません。曖昧なマッチングの場合、どちらを使用するかはツール次第です。

> note
>
> ### パステンプレートのマッチング
> 次のパスを想定すると、具体的な定義が最初に一致されます。
> ```
> /reservations/{reservationId}
> /reservations/mine // このパスが採用される
> ```
> 次のパスは同一とみなされ、無効になります。
> ```
> /reservations/{reservationId}
> /reservations/{mine}
> ```
>

<details>
<summary>Path Item Object</summary>

単一のパスで利用可能な操作を定義します。

このフィールドに書ける代表的なフィールド名は以下になります。
* summary
* description
* get
* put
* post
* delete

### 各エンドポイントの記述

<details>
<summary>GET：一覧取得</summary>

予約可能な美容院の一覧を取得するAPIを定義していきます。

OpenAPIドキュメントは以下になります。
```openapi.yml
paths:
  /reservations:
    get:
        summary: "一覧取得"
        description: "予約可能な美容院一覧を取得する"
        parameters:
            - in: query
                name: page
                schema: { type: integer }
                required: true
        responses:
            "200":
                description: "一覧"
                content:
                application/json:
                    schema:
                    type: object
                    properties:
                        last_page: { type: integer }
                        data: { type: array, items: {} }
```
</details>

<details>
<summary>POST：予約登録</summary>
</details>

<details>
<summary>GET：予約詳細取得</summary>
</details>

<details>
<summary>PUT：予約変更</summary>
</details>

<details>
<summary>DELETE：予約キャンセル</summary>
</details>


</details>


</details>
