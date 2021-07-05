## Dockerを使ってみる

### 本セクションの概要

### DockerHubからhello-worldをpullする
- docker login
- docker pull hello-world
- docker images

### hello-worldのコンテナを作ってみる
- docker run hello-world
    - 1. run (hello-worldを起動)
    - 2. create (コンテナを作成)R
    - 3. execute (プログラム実行)
    - 4. exit
- docker ps (activeなコンテナだけ表示)
- docker ps -a (全てのコンテナを表示)

### UbuntuのDocker imageをrunする
- docker run -it ubuntu bash
    - `-it` bash起動時に必要なおまじない(オプション)
    - `bash` コンテナ起動時に実行するプログラム
    - docker runは実行したいimageがホストになければ勝手にpullしてくれる
- docker imageは複数のimage layerで構成されている
    - dockerのコンテナ作成 = 書き込み可能な新規layerが作成される
    - 同じimageから複数コンテナを作成する場合、新規layer以外同じlayerを参照することでスペースを節約できる

### Ubuntuのコンテナを更新する
- pwd (/)
- touch test
- exit

### コンテナをrestartして再度コンテナを起動する
- docker restart <container>
- docker exec -it <container> bash
    - docker run = imageからコンテナを作成する
    - docker exec = すでにあるコンテナを起動する (引数で指定したプログラムを実行する)
- detach: ctrl + p + q
    - exit コンテナを出る時にコンテナを動かしているプロセスを切ってでる (Exited)
    - detach プロセスを残したままコンテナから出る (Up)
- docker attach <container>
    - 元のプロセスでコンテナに入ることができる

### コンテナをcommitして更新内容をDocker imageにする
- docker commit <container> <new image>

### DockerHubにリポジトリを作成する

### Docker imageを別名で保存する
- docker tag <source> <target>

### DockerHubにDocker imageをpushする
- docker push <image>

### pushしたDocker imageをpullしてみる
- docker rmi <image>
- docker images
- docker pull <image>
- docker run -it <image> bash

### 本セクションまとめ
- docker login
- docker pull <image>
- docker run -it <image> bash
- exit
- docker ps -a
- docker images
- docker restart <container>
- docker exec -it <container> bash
- docker commit <container> <image>
- docker tag <source> <target>
- docker push <image>
- docker rmi <image>

