# macでcaffe操作方法（CPU利用）

## 前準備
Xquartzをインストールする  
https://www.xquartz.org/  
dockerをインストールする  
https://www.docker.com/products/docker-toolbox  

## 1.Docker起動
```
$ docker run -v ~/test:/workspace -p 888:22 --name "caffe" -d yuki399/caffexorg /usr/sbin/sshd -D
```
*Docker停止：`$ docker stop caffe`  
*Docker削除：`$ docker rm caffe`  
*Dockerの`/workspace`とローカル`~/test`が繋がっている（~/testはdockerコマンド実行時自動生成される）  
なお、このDockerにはOpenCVも同梱されている  

## 2.Xquartzを起動
検索から「Xquartz」と入力し、起動する  

## 3.Xquartzのターミナルを起動
```
$ ssh -p 888 -YC root@127.0.0.1
```
*動作確認：`$ xeyes` を実行。目玉が表示されればOK  

## サンプルを学習
### Xquartzのターミナルからcifar10のデータセット取得
```
$ cd /opt/caffe
$ sh data/cifar10/get_cifar10.sh
$ sh examples/cifar10/create_cifar10.sh
```
### CPU設定に修正  
下記ファイルの`solver_mode = CPU`に変更
```
nano examples/cifar10/cifar10_quick_solver.prototxt
nano examples/cifar10/cifar10_quick_solver_lr1.prototxt
```
### 学習実行
```
$ sh examples/cifar10/train_quick.sh
```
再学習まで行われ、5000回まで学習します。  
最終的に`examples/cifar10/cifar10_quick_iter_5000.caffemodel.h5`を作成して終了です

## 画像識別
下記サイト参照  
http://portaltan.hatenablog.com/entry/2016/02/26/182545
サンプルとして紹介したサイトは使用しているモデルが4000（再学習していないモデル）であることと、識別前に平均化していないことからもう少し精度を上げることが期待できると思います。