## Dockerfileの書き方の基本

### Dockerfileのinstructionの紹介

### FROM
- ベースとなるイメージを決定
- DockerfileはFROMから書き始める

### RUN
- Linuxコマンドを実行
- RUNを使うことで好きなようにカスタマイズ
- RUNごとにLayerが作られる

### Layer数を最小限にするために
- ベストプラクティス: Docker imageのLayer数は最小限にする！
- Layerを作るのはRUN, COPY, ADDの3つ
- コマンドを&&でつなげる
- バックスラッシュ(\)で改行する
- Ubuntuではapt-get(またはapt)というコマンドでパッケージ管理をする
    - $apt-get update: 新しいパッケージリストを取得
    - $apt-get install <package>: <package>をインストール
    
### cacheを使おう
- 一度実行したLayerはcacheを使用してくれる
- RUNを分ける = Layerを分ける ながらパッケージを追加することでインストールにかかる時間を短縮することができる
- 作ってく途中はRUNを細かく分けてcacheを活用する
- 最後にうまく動くことを確認したらRUNの数を減らす = なるべく1行にまとめる = Docker imageのサイズを小さくする

### CMD
- CMD: コンテナのデフォルトのコマンドを指定
- CMD ["executable", "param1", "param2"]
- 原則Dockerfileの最後に記述

### RUNとCMDの違い
- RUNはLayerを作る、CMDは作らない

### 本セクションまとめ
- はじまり FROM <image>: Docker imageのベースとなるDocker imageを指定
- RUN <command>: コマンドを実行 (Image Layerを作成)
- おわり CMD ["executable", "param1", "param2"]