# hello2024-backend
新入生情報Web2024バックエンド

## docker compose

- 環境構築: `docker compose run --rm app npm install`
- バックグラウンド実行
    - 起動: `docker compose up -d`
    - 停止: `docker compose stop`
- フォアグラウンド実行: `docker compose up`

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
