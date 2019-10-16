# Configures Raspberry Pi as a device to performe flashing of MR16s

- Disables console and bluetooth to be used for TTL
- Installs TFTP
- Downloads firmware
- Configures iterface

```
#Disable pis default serial susage
echo dtoverlay=pi3-disable-bt | sudo tee -a /boot/config.txt 
dtoverlay=pi3-disable-bt
sudo systemctl disable hciuart
sudo sed -i 's/console=serial0,115200//' /boot/cmdline.txt 

# install and populate tftpd
sudo apt-get install tftpd-hpa
cd /var/lib/tftpboot/
wget https://downloads.openwrt.org/releases/18.06.2/targets/ar71xx/generic/openwrt-18.06.2-ar71xx-generic-mr16-squashfs-kernel.bin
wget https://downloads.openwrt.org/releases/18.06.2/targets/ar71xx/generic/openwrt-18.06.2-ar71xx-generic-mr16-squashfs-rootfs.bin
sudo sed -i 's/exit 0/ifconfig eth0:1 192.168.1.101\/24\nexit 0/' /etc/rc.local

sudo reboot
```
Connect MR16 to as follows

6 GND
8 TX (RX on mr16)
10 RX (TX on mr16)
Source: https://docs.microsoft.com/en-us/windows/iot-core/media/pinmappingsrpi/rp2_pinout.png

Serial Port: /dev/ttyAMA0
