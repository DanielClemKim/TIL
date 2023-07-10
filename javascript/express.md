# Express

## EJS を使う時、ディレクトリ設定

```javascript
app.set("view engine", "ejs");
app.set("views", path.join(__dirname, "/views"));
```

作業ディレクトリの外部からサーバを動かす場合は、`app.set()`で`path`を設定してあげる必要がある。
