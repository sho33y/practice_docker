## 応用編第一弾(part1)：Dockerでプロレベルのデータサイエンスの解析環境を構築する

### Jupyter Labとは？
- ブラウザ上で動くPythonのIDEのようなもの
    - ブラウザ上でコードを書いて実行結果を表示する
- ipython = pythonの出力を見やすくしたもの
- ipython notebook = ipythonをブラウザ上で動かすためのツール
- ipython notebookが進化してJupyter Labになった

### なぜDockerを使うのか？
- Hostには全く関係ないところに構築できる
- 環境破棄が容易
- 他の人への共有が容易(すぐに、確実にできる)
- クラウドへの環境構築も容易

### Dockerfileを書く
- sudo
    - ubuntu上でroot以外のユーザーがroot権限でコマンドを使用したい時に使う
- wget
    - インターネットからパッケージをダウンロードするためのツール
- vim
    - ubuntuでファイルを編集するためのエディタ
- anacondaからダウンロードしたファイルをroot直下に置いてしまうと、他のユーザーがアクセスしにくくなってしまうため、`/opt`ディレクトリを作成し、そこへanacondaをダウンロードする

### Anacondaのインストール
- Dockerfileを作る時は、まずコンテナ上でコマンドを実行して動作を確認し、後からDockerfile追記していくケースが多い
- 「パスを通す」とは？
    - 環境変数$PATHにパスを追加することで、コンピュータがプログラムをそのパスから探してきてくれるようになる
    - `echo $PATH`で今どこにパスが通っているか確認する
    - `export PATH=/path/to/something:$PATH`でパスを追加する
- `sh -x バッシュファイル`
    - -xオプション = shが実行するプログラムのオプションの一覧を表示してくれる

### Dockerfileの続きを書く

### ファイルシステムの共有
- `docker run -p 8888:8888 -v ~/<path>/ds_python:/work --name my-lab <image>`