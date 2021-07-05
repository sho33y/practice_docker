## Dockerの動きをもう少し詳細に理解する

### 本セクションの概要
- コンテナをもっと理解する

### $docker runは何をしているのか
- run = create + start
- docker run <image>
- docker create <image>
- docker start -a <container>

### コマンドの上書き

### -itって何してるの？
- -i
    - インプット可能
    - ホストからコンテナへの入力チャネルを開く
    - STDIN
- t
    - 表示が綺麗になる
    
### コンテナの削除
- docker rm <container>
- docker stop <container>
- docker system prune

### コンテナのファイルシステムの独立性
- 同じイメージからコンテナを作成してもファイルシステムは独立している

### コンテナ名を指定してrunする
- docker run --name <name> <image>
- 名前をつけるとき
    - 起動させ続けるコンテナを立てるとき
    - 共有サーバを使うとき
    - 他のプログラムで使用するとき
    
### detachedモードとforegroundモード
- docker run -d <image>
    - detachedモード
    - コンテナを起動後にdetachする(バックグラウンドで動かす)
- docker run --rm <image>
    - コンテナをExit後に削除する(一回きりのコンテナ)
    
### 本セクションまとめ
- run = create + start
- デフォルトコマンドの上書き : $docker run <image> <command>
- -it
- コンテナの削除 ($docker rm, $docker system prune)
- コンテナの独立性
- コンテナ名の指定 ($docker run --name <container_name> <image>)
- detached vs foreground ($docker run -d <image>, $docker run --rm <image>)