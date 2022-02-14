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