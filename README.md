# Introduction
1. Connect a small usb drive to kali linux.
2. Identify the disk path. e.g. /dev/sdb1
    ```
    lsblk
    ```
3. Create a mount path
    ```
    mkdir ~/usb
    ```
4. Mount the usb drive as readonly
    ```
    sudo mount -ro /dev/sdb1 ~/usb
    ```
5. Create a dd image using block size of 4096 for efficient copying
    ```
    sudo dd if=/dev/sdb1 of=/mnt/external_drive/image.dd bs=4096
    ```
6. Create an E01 image using ewfacquire
    ```
    sudo apt-get install libewf-tools
    sudo ewfacquire -f ewf -t /mnt/external_drive/image.E01 /dev/sdb1
    ```