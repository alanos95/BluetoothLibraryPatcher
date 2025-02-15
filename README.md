# Bluetooth Library Patcher

## Description

This module attends to avoid losing bluetooth pairings after reboot or airplane mode switch on rooted samsung devices.

It patches on the fly the bluetooth library and should support most of samsung devices on android Oreo, Pie, 10 and 11.

This patch is NOT applicable with an aosp rom, only samsung stock/based.

In case installation fails, please upload the BluetoothLibPatcher-files.tar created in your internal storage to the XDA thread.

To fix Galaxy Wearable pairing issue, as the modifcations aren't applicable through Magisk :

Either go to [XDA](https://forum.xda-developers.com/galaxy-note-9/development/zip-libbluetooth-patcher-fix-losing-t4017735) twrp flashable zip.

Or you can directly execute these commands from a terminal app :
```bash
su
mount -o remount,rw /vendor
i=`grep -lr 'security.wsm' /vendor/etc/vintf` && [ ! -z $i ] && [ $i != *.bak ] && cp --preserve=all $i $i.bak && sed -i '/<.*security.wsm.*/,/<hal format="hidl">/d' $i
mount -o remount,ro /vendor
```


## Credits

• @topjohnwu for magisk and magiskboot used here for its easy-to-use hexpatcher

## Source code

[Github](https://github.com/Magisk-Modules-Repo/BluetoothLibraryPatcher)

## Support

[XDA](https://forum.xda-developers.com/galaxy-note-9/development/zip-libbluetooth-patcher-fix-losing-t4017735)

## Changelog

### v1.0

- Initial release

### v1.1

- Add verification point, to know if we successfully hexpatch

### v1.2

- Add recovery installation support

### v1.3

- Modify hexpatch (more safer patch)

### v1.4

- Add support for chinese variants

### v1.5

- Check we try to apply the patch on a Samsung device & add missing chinese Note10+ 5G variant

### v1.6

- Fix brand and model detection for magisk manager and recovery installation

### v1.7

- Add support for chinese/global snapdragon on Pie
- Add support for chinese/global S/N9 snapdragon on Q & simplify the hexpatch

### v1.8

- Add support for A6, A10, A80, some S10e and N10 variants
- Apply the only known qcom fix to all of them
- Add some checks to avoid false negatives

### v1.9

- Support more arm devices
- Auto create tar with needed files in internal storage to fix unsupported devices

### v2.0

- Support more devices
- Misc optimizations

### v2.1

- Android 11 support
- Android Nougat support
- Misc optimizations

### v2.1.1

- Divers Android 11 fixes

### v2.2

- Large rewrite
- Detect now OTAs and reapply the patch if needed

### v2.2.1

- Misc fixes

### v2.2.2

- Fix OTA survival script

### v2.2.3

- Handle library changes from latest A505FN firmware and possibly others devices
