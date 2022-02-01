## ホストとコンテナの関係を理解する

### -vオプションを使ってファイルシステムを共有する
- オプションでホストのファイルシステムをコンテナにマウントする
- `docker run -v <host>:<container>`
- コンテナを肥大化させないためにも、コードが記述されたファイルなどはホストに置いておく
- コンテナは実行環境として使用する
- マウントされたファイルやディレクトリはコンテナの中にあるわけではなく、あくまでもホストに置いてあるのが見えている
- マウントのオプションに指定したディレクトリが存在しない場合は自動で作成される
- つまりDockerfileで指定した`RUN mkdir /new_dir`は記述しなくてもいい

### -uオプションを使って，ホストとコンテナのアクセス権限を共有する
- ユーザIDとグループIDを指定してコンテナをrunする
- `docker run -u <user_id>:<group_id>`
- `id -u`: ユーザーID確認
- `id -g`: グループID確認
- `d` `rwx` `rwx` `rwx`
    - ファイルの種類
    - 所有者
    - 所有グループ
    - その他
- パーミッションの見方
    - `-`: ファイル
    - `d`: ディレクトリ
    - `l`: シムリンク
    - `r`: 読み取り
    - `w`: 書き込み
    - `x`: 実行
    
### -pオプションを使って，ホストとコンテナのポートを繋げる
- ホストのポートをコンテナのポートにつなげる
- `docker run -p <host_port>:<container_port>`
- -p = publish = ポートをつなげる
- IPアドレス・ホスト名 = 建物の住所
- ポート = 部屋番号

### コンテナで使えるコンピュータリソースの上限を設定する
- `docker run --cpus`
    - コンテナがアクセスできる上限のCPU(物理コア)を設定
- `docker run --memory`
    - コンテナがアクセスできる上限のメモリを設定
- MacでのCPU・メモリ確認コマンド
    - `sysctl -n hw.physicalcpu_max`: 物理コア数
    - `sysctl -n hw.logicalcpu_max`: 論理コア数
    - `sysctl hw.memsize`: メモリ(byte)
- `docker run -it --rm --cpus 1 --memory 2g ubuntu bash`
- `docker inspect <container>` = コンテナのあらゆる情報を表示する
- `docker inspect <container> | grep -i cpu`
    - -iオプションはignore、アッパーケース・ロワーケース(大文字小文字)を無視して指定した文字を含む箇所を探してくれる
    - `NanoCpus`: コンテナが使用できるCPU