# OSイメージに関する情報

## ROSインストール済みOSイメージ

* バグ除去済みのRaspberry Pi 3用 Ubuntu 16.04 Server: [ダウンロード(1.1GB)](https://lab.ueda.asia/misc/ubuntu-16.04-preinstalled-server-armhf+raspi3-upgradable.img.xz)
    * GPLでの配布です
    * 8GBのmicroSDで作りましたので16GBのmicroSDで使う場合、そのまま使うかパーティションを拡張して使います。

* その他の情報: https://lab.ueda.asia/?page_id=2885

## Pi3 + Ubuntu 16.04 Serverでアップグレードしてもクラッシュしない方法

2017年1月現在、https://wiki.ubuntu.com/ARM/RaspberryPi で配布されているPi3用のイメージをapt upgradeするとクラッシュする現象が起きています。
これは次の方法で回避できます。

### 情報元

https://bugs.launchpad.net/ubuntu/+source/linux-raspi2/+bug/1652270/comments/31

### 方法

/boot/firmware/config.txt から、次の記述を見つけます。
```
ubuntu@ubuntu:~$ grep -A 1 device_tree_address /boot/firmware/config.txt 
device_tree_address=0x100
device_tree_end=0x8000
```
この2行を次のように書き換えます。元の行はコメントアウトします。
```
ubuntu@ubuntu:~$ grep -A 1 device_tree_address /boot/firmware/config.txt 
device_tree_address=0x02008000
```
この状態でupdateとupgradeを行います。

```
ubuntu@ubuntu:~$ sudo apt update
ubuntu@ubuntu:~$ sudo apt upgrade
```
書き換えた設定が残っているか確認します。
```
ubuntu@ubuntu:~$ uname -r
4.4.0-1009-raspi2
ubuntu@ubuntu:~$ grep -A 1 device_tree_address /boot/firmware/config.txt 
device_tree_address=0x02008000
```
これで再起動すると
```
ubuntu@ubuntu:~$ uname -r
4.4.0-1042-raspi2
```
というようにカーネルがアップデートされます。


## Ubuntu MATEのOSイメージ

ラズパイで使いやすいようにしたものがこちらにあります。

https://tiryoh.com/blog/archives/1101
というようにカーネルがアップデートされます。
