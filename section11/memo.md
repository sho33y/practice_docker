## 応用編第一弾(part2)：AWSにデータサイエンス環境を構築する

### 前セクションで使ったデータサイエンスの環境をAWSに作ろう！

### AWSへの登録
- クラウドサービス
  - 手元に物理サーバーを置くのではなく、企業やサービスが持っているサーバーの一部(AWSだとAmazonが持っているサーバー)を使わせてもらう
  - サーバーを買う必要がなく、必要な時だけ借りることで安く済む
  - クラウドサービスがサーバーを管理してくれているので、セキュリティ面もこちらが気にする必要がない

### AWSのインスタンスにSSHでアクセスする
- `chmod 400 <file>`
  - パーミッションを変更する
  - `chmod <権限> <file>`
  - 400
    - 4 = 所有者
    - 0 = 所有グループ
    - 0 = その他
  - 権限
    - 4: read
    - 2: write
    - 1: execute
    - 0: no permission
    - 合計値を使用
      - ex) 全権限であれば4 + 2 + 1 = 7
      - 読み書きだけなら4 + 2 = 6
- sshコマンド
  - `ssh -i xx.pem username@hostname`

ssh -i mydocker.pem ubuntu@ec2-18-183-8-167.ap-northeast-1.compute.amazonaws.com

### AWSのインスタンスにDockerをセットアップする
- dockerインストール
  - `sudo apt-get update`
  - `sudo apt-get install docker.io`
- dockerグループ作成
  - `sudo gpasswd -a ubuntu docker`

### Docker imageをAWSのインスタンスにアップロードする
- アップロード方法
  - 1.Dockerレジストリを使う
  - 2.Dockerfileを送る
  - 3.Docker imageをtarにして送る
    - サーバーをセキュアにしたい時、外部(インターネット)と接続できない時などに利用する
- tarへ圧縮
  - `docker save <image> > myimage.tar`

### SFTPを使ってファイルの転送をする
- SFTP
  - Secure File Transfer Protocol
  - `sftp -i mydocker.pem ubuntu@<hostname>`
  - `put local/path [remote/path]`
    - ファイルをアップロード
  - `get remote/path [local/path]`
    - ファイルをダウンロード

### .tarからDocker imageに戻す
- 解凍コマンド
  - `docker load < myimage.tar`

### Dockerfileを転送する
- `df -h`
  - コンピュータのディスク容量を確認するコマンド

### 番外編：コンテナのアクセス権限について解説！
- ユーザーの作成
  - `sudo adduser --uid <uid> <username>`
- コマンドの使い方の調べ方
  - `man <command>`
  - man = manual
