# Drone 0.8をローカルでテストする

## ngrokを起動

```bash
ngrok http 80
```

https://hogehoge.ngrok.io をコピー

## github OAuthを登録

上記https://hogehoge.ngrok.io を使ってOAuth作成
Client IDとSecretをコピー

## env作成

先にenv作成しないとdrone 0.8は動かない
qiita的にはとりあえずlocalhostで動かしているが

まず `DRONE_SECRET` 用文字列作成

```bash
ruby -r securerandom -e "puts SecureRandom.urlsafe_base64"
```

↑なくても動くかはやってみる

.envはこんな感じ

```text
DRONE_GITHUB_URL=https://hogehoge.ngrok.io
DRONE_GITHUB_CLIENT=Githubで取得
DRONE_GITHUB_SECRET=Githubで取得
DRONE_SECRET=ランダムな文字列
DRONE_HOST=ngrokで取得したURL
```

## docker-compose 起動

```bash
docker-compose up
```

https://hogehoge.ngrok.io にアクセス
