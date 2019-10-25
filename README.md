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
詳しい操作は自分で調べて
## MySQL8.0　rootユーザのパスワード再設定方法
すでにパスワードがあるらしく、パスワードの設定ができない...
```
$ sudo mysqld  --initialize-insecure
$ sudo mysql_secure_installation

Securing the MySQL server deployment.

Enter password for user root: 
Error: Access denied for user 'root'@'localhost' (using password: YES)
```

### #1 パスワードを無効化
```conf:/etc/my.conf
[mysqld]
  ・
  ・
  ・
skip-grant-tables # ここを追記
```

結果：パスワードなしでログインできる

```
$ sudo systemctl restart mysqld.service
$ mysql -u root -p
Enter password: # Enterで入れる
```

### #2 パスワードを再設定
```
mysql> flush privileges;
mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'NewPassword';
mysql> exit
```

```conf:/etc/my.conf
[mysqld]
  ・
  ・
  ・
# skip-grant-tables # ここを`#`でコメントアウトする
```
```
$ sudo systemctl restart mysqld.service
$ mysql -u root -p
Enter password: 
```
## 後始末
```
exit # CentOSからログアウト
vagrant halt # CentOSをシャットダウン
vagrant destroy -f # CentOSの環境を削除(任意)
```
