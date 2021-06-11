## Linuxの基礎知識

### Linuxとは？
- Unixから派生されたオープンソースのOS
- Linus Torvalds
- プログラマーの世界標準OS
- MacはUnixベースのOS
- MacでLinuxコマンドを学習

### シェルについて知ろう
- Kernel(核)
- 私たちユーザーはKernelに対して直接命令を出せない
- Kernelの周りについてるShell(殻)に対して命令を出していく
- Shellの種類 bash, zsh, sh...
- Shellを使用するのに必要なアプリケーション = ターミナル

### 環境変数について知ろう
- 環境変数 = OSの上で動くプロセスが情報を共有するための変数
- Shellの環境変数 = $SHELL
- echo $SHELL (自分の環境 /bin/bash)
- export AGE=20
- echo $AGE

### Linuxの基礎コマンド
- cd <path> : <path>に移動する (change directory)
- pwd : 今いるディレクトリを表示 (print working directory)
- mkdir <new folder> : 新しいフォルダ<new folder>を作成 (make directory)
- touch <new file> : 新しいファイル<new file>を作成
- ls : カレントディレクトリのファイル,フォルダを一覧表示 (list)
- rm <file> : <file>を削除
- rm -r <folder> : <folder>を削除