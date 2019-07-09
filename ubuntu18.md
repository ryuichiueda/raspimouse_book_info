# Ubuntu 18.04情報

## ROS、デバイスドライバインストール済みイメージ

* https://b.ueda.tech/?post=20190618_raspimouse

## インストール方法

1. https://wiki.ubuntu.com/ARM/RaspberryPi から、「Raspberry Pi 3B/3B+: ubuntu-18.04.2-preinstalled-server-armhf+raspi3.img.xz」をダウンロード。
1. microSDに`dd`でコピー
    * Ubuntuでddする場合

    ```
    ### 注意: /dev/sdb は適宜変えること！！！（ストレージがぶっ飛びます） ###
    ### ~/Downloadsも適宜変更 ###
    $ xzcat ~/Downloads/ubuntu-18.04.2-preinstalled-server-armhf+raspi3.img.xz | sudo dd bs=4MB of=/dev/sdb conv=fsync
    ```

    * Macでddする場合

    ```
    $ diskutil umountDisk /dev/disk2
    $ xzcat ~/Downloads/ubuntu-18.04.2-preinstalled-server-armhf+raspi3.img.xz | sudo dd bs=4m of=/dev/rdisk2 conv=sync
    ```

## 初期セットアップ

1. https://github.com/ryuichiueda/ros_setup_scripts_Ubuntu18.04_desktop/blob/master/step1.bash でROSをインストール
1. https://github.com/rt-net/RaspberryPiMouse でデバイスドライバをセットアップ

    * デバイスドライバのコンパイル

    ```
    $ cd RaspberryPiMouse/utils
    $ ./build_install.bash
    ```

1. https://github.com/ryuichiueda/pimouse_setup で起動時にデバイスドライバがインストールされるようにする
    * crontabを使わないといけないようです

    ```
    $ sudo crontab -e 
    ...（次の1行を追加）...
    @reboot /home/ubuntu/pimouse_setup/setup.bash
    $ sudo reboot
    （再起動時にピッと言ったらOK）
    ```

1. power managementを切る
    * 無線の設定をしてから、次のようにcronにpower managementを切る設定を追加します。
    

    ```
    $ sudo apt install wireless-utils
    $ sudo crontab -e 
    ...（次の1行を追加）...
    @reboot /sbin/iwconfig wlan0 power off
    $ sudo reboot
   $ iwconfig 
   ....
   wlan0     ...
             Power Management:off
    ```

## 16.04->18.04での主な変更

### ネットワーク設定

ネットワークの設定がNetplanというものになりました。`/etc/network/interfaces`を編集しても何も起こらないのでご注意を。

* 参考: https://qiita.com/Aton-kish/items/e06d87626b21e21c1e33

### gmapping

まだ`apt`で入るパッケージがないので、自身でコンパイルします。

* 手順の例: https://www.robotech-note.com/entry/2018/12/16/ROS_melodic%28Ubuntu18_04%29%E3%81%A7map_server%2Cgmapping%2Cnavigation%E3%83%91%E3%83%83%E3%82%B1%E3%83%BC%E3%82%B8%E3%82%92%E5%B0%8E%E5%85%A5%E3%81%99%E3%82%8B

この時、メモリ不足を防ぐために、`make`で使うプロセスの数を1つにします。具体的には、

```
$ catkin_make -j1
```

と`catkin_make`の際に指定します。
