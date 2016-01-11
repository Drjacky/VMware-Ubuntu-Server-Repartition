# VMware-Ubuntu-Server-Repartition
How to repartition ubuntu-server-cli

In VMware, expand disk.

Then download gparted.iso from
```javascript
http://free.nchc.org.tw/gparted-live/stable/
```

Then boot OS from CD(gparted).
*Note: If you can't boot from CD, add below line to .vmx file:

```javascript
bios.forceSetupOnce = "TRUE"
```
Reboot now.

Enter first item in opened UI.

Remove SWAP

Remove Extended

Increase sda1.
*Note: You should keep 16GB for SWAP disk.

Build Extended

Build SWAP

Apply and quit now.

If you get error after reboot, it's because SWAP UUID; Follow below step:

Press Ctrl+Alt+F2

```javascript
sudo fdisk -l

sudo swapoff -a

sudo rm -rf /swapfile

sudo mkswap /dev/sda5
```

Write given UUID somewhere for future use.

nano /etc/fstab

Replace new UUID with the old one.

```javascript
sudo swapon -a

sudo apt-get install gparted

reboot
```
