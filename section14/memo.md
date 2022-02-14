## 応用編第二弾(part2):Dockerを使ったCICDパイプラインを構築する

### Githubのリポジトリ作成

### Railsのテストを実行する
- rails test

### Travis CIをセットアップする
- https://www.travis-ci.com/
- .travis.yml

### .travis.ymlにテストの流れを書く
- 流れ
  1. 権限の設定
  2. Dockerを使う
  3. コンテナを起動
  4. DB準備
  5. テスト実行

### Travis CIのビルドを実行する

### Herokuに登録する

### travis.ymlにHerokuへのデプロイを記述する
- 流れ
  1. .travis.ymlにデプロイ用の処理を追記
     1. HerokuのDockerレジストリにログイン
     2. 本番環境用のDockerfileをビルド(image作成)
     3. HerokuのDockerレジストリに本番環境用のimageをpush
     4. アプリ起動
  2. Macにherokuをインストールしてtokenを取得
  3. Travis CIとHerokuに環境変数を設定
  4. 本番環境用Dockerfile.prodを作成

### GitとCICDを使った実際の開発フローを体験しよう！