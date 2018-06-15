2018/5/26: リポジトリのファイルが利用できなくなっていることが確認されました。現在調査中・・・


# UbuntuをアップデートするとWiFiが使えなくなる問題について（2017年6月15日）

2018年5月26日にも再度ありましたが、現在は、以下の方法で対処できます。

1. 第2章2.1.6の内容に従ってOSをアップデートする（iwconfigでwlan0が見えなくなる）
1. 以下を実行（iwconfigで再度wlan0が見えるようになる）

```
mkdir wifi-firmware
cd wifi-firmware
wget https://github.com/RPi-Distro/firmware-nonfree/raw/master/brcm/brcmfmac43430-sdio.bin
wget https://github.com/RPi-Distro/firmware-nonfree/raw/master/brcm/brcmfmac43430-sdio.txt
sudo cp *sdio* /lib/firmware/brcm/
sudo reboot
```

# 過去の解決法

* [2017/5/26](https://github.com/ryuichiueda/raspimouse_book_info/blob/master/trouble_reports/20170528_wifiproblem.md)
* [2017/4/13](https://github.com/ryuichiueda/raspimouse_book_info/blob/master/trouble_reports/20170413_wifiproblem.md)
