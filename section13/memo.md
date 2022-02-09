## 応用編第二弾(part1):Docker composeを使って超本格Webアプリ開発環境を構築する

### 業務で使える超本格Web開発環境を構築する

### Rails開発用Dockerfileを作成
- フレームワーク
  - Webアプリを簡単に作るためのツール

### Docker composeを使って楽をしよう！
- Docker composeを使う時
  - $docker runのコマンドが長くなる時
  - 複数のコンテナをまとめて起動する時
- docker-compose.yml
  - Docker composeを使うのに必要なファイル
  - コンテナの情報を書いていく
  - yml = YAML = YAML ain't markup language

### docker-compose.ymlの書き方
- ttyとstdin_open
  - docker run `-it`オプションと同じ
  - stdin_open = `-i` = stdinというチャネルを開いて入力チャネルを開く
  - tty = `-t` = コマンドの出力結果をpretty(綺麗)にする

### Docker composeを使ってコンテナを起動する
  - `docker build <build contexts>` = `docker-compose build`
  - `docker run` = `docker-compose up`
  - `docker ps` = `docker-compose ps`
  - `docker exec command <container> <command>` = `docker-compose exec <service>`
  - `docker-compose up --build` = buildしてrun
  - `docker-comopose down` = stopしてrm

### Railsのセットアップ
- `rails new` = 新しいアプリを作成するコマンド
  - `--force` = 全て上書きする
  - `--database` = データベースを指定する(Railsがそれ用にセットアップしてくれる)
  - `--skip-bundle` = bundleインストールをskipしてくれる
- `rails s -b 0.0.0.0` = railsのサーバーを起動する
  - s = server

### docker-compose.ymlにDB部分を追記する
- `rails db:create` = databaseを作ってくれる
- Docker volume
  - コンテナにおいて生成され利用されるデータを、永続的に保持する目的で利用される仕組み
  - コンテナのデータをホスト側に持っておきたい時
  - 他のコンテナとも共有して持っておきたい時
- docker-compose.yml
  - `enviroment` = 環境変数を設定する
  - `depends_on` = 指定したコンテナができたらdocker runする(先に作って欲しいコンテナを指定する)
  - `links` = 指定したコンテナにアクセスできるようにする

### RailsのWebアプリ作成
- `docker volume`
  - docker volumeに対して様々な操作をするためのコマンド
  - 今回はpostgresqlのデータをdb-dataという名前のvolumeにマウントしている
- `rails g scaffold`
  - `rails g scaffold product name:string price:integer vendor:string`
  - g = generate
- `rails db:migrate`