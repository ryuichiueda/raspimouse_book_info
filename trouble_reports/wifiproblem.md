# UbuntuをアップデートするとWiFiが使えなくなる問題について（2017年5月6日）

2017年4月13日にapt update, apt upgradeするとWi-Fiが見えなくなるという不具合の報告がありましたが、以下の方法で対処できます。

1. 1.2節の内容に従ってOSをアップデートする（iwconfigでwlan0が見えなくなる）
1. 以下を実行（iwconfigで再度wlan0が見えるようになる）

```
$ cd /lib/firmware/brcm/
$ sudo wget https://github.com/RPi-Distro/firmware-nonfree/raw/master/brcm80211/brcm/brcmfmac43430-sdio.bin -O brcmfmac43430-sdio.bin
$ sudo wget https://github.com/RPi-Distro/firmware-nonfree/raw/master/brcm80211/brcm/brcmfmac43430-sdio.txt -O brcmfmac43430-sdio.txt
$ sudo reboot
```


# contributer

* FurqanHabibi: https://github.com/FurqanHabibi

# 過去の解決法

* [2017/4/13](https://github.com/ryuichiueda/raspimouse_book_info/blob/master/trouble_reports/20170413_wifiproblem.md)
