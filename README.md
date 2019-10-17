# mysql_practice
MYSQL環境を構築します

## 環境構築
### Winのかた
1. Git Bash(git for windows)をインストールする  
    ダウンロードリンクは[こちら](https://gitforwindows.org/)
2. Vagrantをインストール  
    ダウンロードリンクは[こちら](https://www.vagrantup.com/downloads.html)
3. gitbashを起動
### Macのかた
1. Vagrantをインストール
    ダウンロードリンクは[こちら](https://www.vagrantup.com/downloads.html)
    Vagrantをインストールする
2. ターミナルを開く
## LINUX環境を作成
以下のコマンドを実行する
```
git clone https://github.com/SaKu2110/mysql_practice.git
cd mysql_practice
vagrant box add centos/7
vagrant up # CentOSを起動
vagrant ssh # CentOS内にログイン
```
※ Vagrantの詳しい使い方は自分で調べて
## MySQLの初期設定
```
# how to setup mysql
mysql_secure_installation
# how to login mysql
mysql -u root -p
```
詳しい操作はん自分で調べて
## 後始末
```
exit # CentOSからログアウト
vagrant halt # CentOSをシャットダウン
vagrant destroy -f # CentOSの環境を削除
```
