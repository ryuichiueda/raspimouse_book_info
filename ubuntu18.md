# Ubuntu 18.04情報

## インストール

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
