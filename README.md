# Root BlueStacks Air macOS

## Tested on BlueStacks Air

- 5.21.680.7532
- 5.21.695.7506
- 5.21.700.7523
- 5.21.705.7515
- 5.21.712.7503
- 5.21.715.7538
- 5.21.720.7530
- 5.21.730.7536
- 5.21.735.7518
- 5.21.745.7536

![Screenshot](/images/bluestacks-air-root-magisk.png)

## Requirements

- [BlueStacks Air](https://www.bluestacks.com/mac)
- [Official Magisk](https://github.com/topjohnwu/Magisk/releases)  
  Recommended: latest stable release (v28.0+)

## Notes

- **Kitsune Mask replaced with Official Magisk:** The original repo required Kitsune Mask (now discontinued). This fork uses Official Magisk. The APK extraction logic is identical, so the same `root.sh` script works.
- **BlueStacks Air versions:** The versions listed above were tested by the original author up to `5.21.745.7536`. Newer releases (e.g. `5.21.755.x`) may work but are **untested**. If you try a newer version, please open an issue to report whether it succeeds or fails.
- **SELinux flags:** `magisk.rc` contains `--auto-selinux` flags inherited from the original implementation. These are not documented in official Magisk and were likely added by Kitsune Mask. If rooting fails with official Magisk, this is the first place to investigate.

## Rooting

- Install BlueStacks Air
- ‼️ **REQUIRED** ‼️ Open BlueStacks Air for the first time
- Close BlueStacks Air
- Download this repo and extract it
- Copy the downloaded Magisk APK to the project folder, and rename it to `magisk.apk`
- Open **Terminal.app** or **iTerm.app** and navigate to the project folder

  ```bash
  cd ~/Downloads/root-bluestacks-air
  ```

### Method 1: SIP enabled

- Execute `root.sh` specifying initrd output path and backup directory

  ```bash
  bash root.sh -o files/initrd_hvf.img -b files/backup
  ```

  the above command will backup the original `initrd_hvf.img` in `files/backup` and create a patched one in `files/initrd_hvf.img`, you may specify a different path for the output and backup directory
- Copy the patched `initrd_hvf.img` to `/Applications/BlueStacks.app/Contents/img/` and replace the original one
- Start BlueStacks Air
- Continue with [Next Steps](#next-steps)

### Method 2: SIP disabled

- Execute `root.sh` with sudo

  ```bash
  sudo bash root.sh
  ```

- Wait until BlueStacks Air starts
- Continue with [Next Steps](#next-steps)

### Next Steps

- Install Magisk (`magisk.apk`)
- Open Magisk and press **OK** when the **Requires Additional Setup** prompt appears. This will reboot BlueStacks Air.
  ![magisk-additional-setup](/images/magisk-additional-setup.png)
- Force quit BlueStacks Air if necessary
- Open BlueStacks Air and enjoy
- If you need **Zygisk**, enable it from Magisk settings and reboot BlueStacks Air

## Unrooting

### Method 1: SIP enabled

- Copy the backup `initrd_hvf.img` to `/Applications/BlueStacks.app/Contents/img/`
- Done

### Method 2: SIP disabled

- Make sure BlueStacks Air is closed
- Execute `unroot.sh` with sudo

  ```bash
  sudo bash unroot.sh
  ```

- Done

### Buy me a coffee

[![](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://paypal.me/hanreev)
