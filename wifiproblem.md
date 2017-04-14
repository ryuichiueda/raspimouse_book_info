ラズパイマウス本、かなり攻めた構成になっているので織り込み済みといえば織り込み済みですが、最初の壁が発生しました。2017年4月14日現在、apt update, apt upgradeするとWiFiが見えなくなります。ここではラズパイマウス本向けにいくつかの対策を書いておきます。

# https://wiki.ubuntu.com/ARM/RaspberryPi からインストールする場合

立ち上げ後、素早く（ゆっくりやると失敗する場合もあり）

```
$ sudo systemctl disable apt-daily.service
$ sudo systemctl disable apt-daily.timer
$ sudo apt purge unattended-upgrades
$ sudo apt purge cloud-init
```

を実行します。上の3つは自動アップデートを止める設定です。その後はアップデートしないようにします。ただし、次の注意事項があります。

* アップデートしないとセキュリティー上の脆弱性が残る場合があるので、むやみにラズパイ自身で変なものをダウンロードしたり、インターネットに直接露出させないようにします。
* /boot/firmware/config.txtはそのままにしておきます。
