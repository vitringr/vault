---
context:
  - "[[Linux]]"
---

# Linux Working With USB

Practical reminder for basic USB stuff.

---

## Listing USB Devices

Use `lsblk`.

If `usbutils` is installed, you can also use `lsusb`.

You can also use `demsg` to check for kernel USB detection messages:

```bash
dmesg | grep -i usb
```

## Mounting a USB Drive

Mount the USB drive:

```bash
sudo mount /dev/sdX1 /mnt/usb
```

replace `sdX1` with your partition.

You can use `fdisk -l` to identify the correct partition.

## Unmounting a USB Drive

Before physically ejecting, unmount safely:

```bash
sudo umount /mnt/usb
```
