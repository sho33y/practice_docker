## $docker buildの詳細と、その他のInstruction

### $docker buildは何をしているのか
- `docker build` は指定したフォルダをDocker daemonに渡す
- Docker daemonが渡されたフォルダとDockerfileを元にimageを作る
- なのでimageを作るときはDockerfileだけでなく、それを置くフォルダも必要になる
- この時のフォルダのことをbuild contextという

### Docker daemonとは？
- 普段打っているコマンドはClient(docker CLI)からDocker daemonへ命令を出していた
- Docker daemonはDocker Hostに置かれている
- Client(docker CLI)からDocker Host(Docker daemon)へ命令を出す
- 開発環境は手元のマシン(Macなど)で完結するが、テスト環境などは別サーバーを用意するため、そこでDockerを動かせる(Docker daemonへ命令を出す)ようなアーキテクチャが作られている
- Client = コマンドを打つ側、DockerHost = 実際にコンテナやイメージを操作する
daemonがいるところ、Registry = イメージをストレージしていくところ(DockerHubなど)の3つ分かれているアーキテクチャイメージ
- Docker object = container, image, network, data volumesなど
- Docker daemonはDocker objectを管理するためのもの

### build contextとは？
- context = 「状況」や「環境」の意味
- buildに使わないファイルはbuild contextに入れない
- ADDやCOPYでbuild contextの中にあるファイルをimageへ持っていける

### COPY
- `COPY <src> <dest>`
- docker buildをする時にホストからコンテナにファイルやフォルダを受け渡すことができる

### COPY vs ADD
- `ADD <src> <dest>`
- 単純にファイルやフォルダをコピーする場合はCOPYを使おう
- tarの圧縮ファイルをコピーして解凍したいときはADDを使う

### Dockerfileがbuild contextにない場合
- `docker build -f <dockerfilename> <build context>`
- fオプションを使用するケース
    - Dockerfileが複数ある時
    
### CMD vs ENTRYPOINT
- ENTRYPOINTでもデフォルトのコマンドを指定することができる
- ENTRYPOINTは、run時に上書きできない
- ENTRYPOINTがある場合は、CMDは["param1", "param2", ...]の形をとる(つまりENTRYPOINTで指定したコマンドの引数)
- run時に上書きできるのはCMDの部分のみ
- コンテナをコマンドのようにして使いたいときに使う

### ENV
- ENV(環境変数)の書き方
    - `ENV <key> <value>`
    - `ENV <key>=<value>`
    
### WORKDIR
- Docker instructionの実行ディレクトリを変更する
- WORKDIR <絶対path>
- 指定したディレクトリが存在しなければ、自動で作成してくれる