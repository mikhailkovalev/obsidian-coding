#linux #bootable #usb #dd #iso #image

[Source](https://askubuntu.com/questions/372607/how-to-create-a-bootable-ubuntu-usb-flash-drive-from-terminal/377561#377561)

1. Узнать какой раздел использовать с помощью `lsblk`
2. Отмонтировать этот раздел:
```bash
sudo umount /dev/sd<?><?>
```
3. Записать сам образ:
```bash
sudo dd bs=4M if=/path/to/input.iso of=/dev/sd<?><?> conv=fdatasync status=progress
```

