# ansible-docker-runner

ansibleがインストール済みのコンテナを立ち上げる。

# 使い方

docker-compose.ymlのANSIBLE_VERSIONを利用したいansibleのバージョンに変更する。  

```
version: '3'
services:
  runner:
    build:
      context: ./runner
      args:
        http_proxy: ${HTTP_PROXY}
        https_proxy: ${HTTP_PROXY}
        HTTP_PROXY: ${HTTP_PROXY}
        HTTPS_PROXY: ${HTTP_PROXY}
        ANSIBLE_VERSION: 2.5.0 # ここを変更する
    tty: true
    volumes:
      - ./playbook:/playbook
```

ansible実行に必要なplaybook等ファイルをホストの./playbookディレクトリに配置  
（./playbookはコンテナ上の/playbookにマウントされています）  


runnerコンテナを起動しAnsible実行  

```
docker-compose up -d
docker-compose exec runner ansible-playbook ～～～～～
```
