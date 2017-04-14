# UbuntuをアップデートするとWiFiが使えなくなる問題について

かなり攻めた構成になっているので織り込み済みといえば織り込み済みですが、最初の壁が発生しました。2017年4月14日現在、apt update, apt upgradeするとWiFiが見えなくなります。ここではラズパイマウス本向けにいくつかの対策を書いておきます。

## 1. [ubuntu.comのイメージ](https://wiki.ubuntu.com/ARM/RaspberryPi) を使ってインストールする場合

立ち上げ後、素早く（ゆっくりやると失敗する場合もあり）

```
$ sudo systemctl disable apt-daily.service
$ sudo systemctl disable apt-daily.timer
$ sudo apt purge unattended-upgrades
$ sudo apt purge cloud-init
```

を実行します。この後、本の内容にしたがって自身でWiFiをセットアップします。上の3つは自動アップデートを止める設定です。その後はアップデートしないようにします。ただし、次の注意事項があります。

* アップデートしないとセキュリティー上の脆弱性が残る場合があるので、むやみにラズパイ自身で変なものをダウンロードしたり、インターネットに直接露出させないようにします。
* /boot/firmware/config.txtはそのままにしておきます。

## 2. Ubuntu MATEを使う

https://github.com/ryuichiueda/raspimouse_book_info/issues/1#issuecomment-293842720 で [ishigem](https://github.com/ishigem)さんから情報をいただきました。

## ファームウェアのアップデートを止める

linux-firmwareのアップデートをholdすれば、他のパッケージはアップデートしても動作することを確認しています。[ubuntu.comのイメージ](https://wiki.ubuntu.com/ARM/RaspberryPi) を使ってインストールした後、次の手順を踏みます。

```
### 手順（現在、もう一回確認中）###
$ echo linux-firmware hold | sudo dpkg --set-selections           # もしかしたら
$ echo linux-firmware-raspi2 hold | sudo dpkg --set-selections    # このどちらかは不要（どなたか実験を）
$ vi /boot/firmware/config.txt
（2.1.6の手順でファイルを書き換え）
$ sudo apt purge cloud-init
$ sudo apt update
$ sudo apt upgrade
```


