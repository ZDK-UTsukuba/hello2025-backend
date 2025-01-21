# hello2025-backend

新入生情報Web2025バックエンド

## 事前準備

- [Node.js](https://nodejs.org/ja/)
- [wrangler](https://developers.cloudflare.com/workers/cli-wrangler/install-update)
- [Docker](https://www.docker.com/get-started)
- [docker compose](https://docs.docker.com/compose/install/)

## 環境構築


1. ローカル実行（dev）向けの環境変数設定
    - `sample.dev.vars` をコピーして `.dev.vars` を作成
    - `.dev.vars` に環境変数を設定
        - `ESA_TOKEN` はesaのユーザーページの外部アプリ連携の項から取得
2. `node_modules` のインストール
    - 直接実行: `npm install`
    - docker compose: `docker compose run --rm app npm install`

## docker compose

- バックグラウンド実行
  - 起動: `docker compose up -d`
  - 停止: `docker compose stop`
- フォアグラウンド実行: `docker compose up`

## ローカル実行

wranglerを使ってローカルで実行する

- `npx wrangler login`（初回のみ）
- `npx wrangler dev`

## デプロイ

wranglerを使ってデプロイする

1. ワーカーに環境変数を設定
    - ワーカーの設定画面から環境変数を設定
    - `.dev.vars` の内容をコピペすることで簡単に設定できる
        - もっとよいやり方があるかもしれない
2. デプロイする
    - `npx wrangler login`（初回のみ）
    - `npx wrangler deploy`

## API

### GET `/posts`

記事一覧を返す

example

```json
[
    {
        "number":971,
        "name":"テスト2",
        "created_at":"2024-02-01T22:17:30+09:00",
        "categories":["test"]
    }
]
```

### GET `posts/:number`

記事の内容を返す

example

```json
{
    "number":971,
    "name":"テスト2",
    "created_at":"2024-02-01T22:17:30+09:00",
    "categories":["test"],
    "body":"テストの2番目のページです"
}
```

### GET `/faqs`

FAQを返す

example

```json
[
    {
        "question": "そぽたんってなんですか",
        "answer": "筑波山に住む妖精です。\r\nそぽ～。\r\n\r\n"
    },
    {
        "question": "筑波大学の住所を教えてください",
        "answer": "茨城県つくば市天王台1-1-1です。\r\n\r\n"
    }
]
```
