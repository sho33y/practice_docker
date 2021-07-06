## Dockerfileについて知ろう

### Dockerfileとは？
- Docker imageの設計図

### Dockerfileを見てみよう！
- [ubuntuのDockerFile](https://github.com/tianon/docker-brew-ubuntu-core/blob/1c090689a541a57452ae21cb76ef038b9f339fb2/bionic/Dockerfile)

- DockerFileとは
    - Docker imageの設計図でDockerFileからDocker Imageを作る
    - "DockerFile"というファイル名のテキストファイル
    - "INSTRUCTION arguments"の形でずらーっと記載していく
    
### Dockerfileを作ってみよう！

### DockerfileをbuildしDocker imageを作る
- docker build <directory>
- docker build -t <name> <directory>

### ビルドしたDocker imageをrunする
- docker run -it <DockerFileから作ったimage> bash