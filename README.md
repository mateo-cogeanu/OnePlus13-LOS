# OnePlus 13 - installing LineageOS

## Step 1. Preparation
- Make sure your OnePlus 13 has USB debugging and OEM Unlocking
  - Open Settings -> About device -> Version -> Tap 7 times on the version number and enter your password/pattern
  - Settings -> System & Update -> Developer Options -> OEM Unlocking ✓ USB Debugging ✓
- reboot to fastboot with:
  ```sh
  adb reboot bootloader
  ```
  make sure to use the Red cable that came in the box with the phone
- once rebooted run
  ```sh
  fastboot flashing unlock
  ```
- select `UNLOCK THE BOOTLOADER` with the volume keys and press the power button to confirm. Warning: ALL data will be erased after unlocking the bootloader so make sure you backed up everything important.
- go back through all the setup and dont log into any accounts
- Make sure your OnePlus 13 has USB debugging and OEM Unlocking
  - Open Settings -> About device -> Version -> Tap 7 times on the version number and enter your password/pattern
  - Settings -> System & Update -> Developer Options -> OEM Unlocking ✓ USB Debugging ✓
- reboot to fastboot with:
  ```sh
  adb reboot bootloader
  ```
- and here we do the fun stuff we flash LineageOS `(LOS)`
- here are the downloads for all the files: https://download.lineageos.org/devices/dodge/builds
- once you have them all run theese commands in order

- Flash boot
  ```sh
  fastboot flash boot boot.img
  ```
- Flash DTBO
  ```sh
  fastboot flash dtbo dtbo.img
  ```
- Flash Init Boot
  ```sh
  fastboot flash init_boot init_boot.img
  ```
- Flash VbMeta
  ```sh
  fastboot flash vbmeta vbmeta.img
  ```
- Flash Vendor Boot
  ```sh
  fastboot flash vendor_boot vendor_boot.img
  ```
- when these are all done reboot with
  ```sh
  fastboot reboot bootloader
  ```

- Now we flash Recovery
  ```sh
  fastboot flash recovery recovery.img
  ```
- we wipe super
  ```sh
  fastboot wipe-super super_empty.img

- with the volume keys find `Recovery mode`
  - press the power button to confirm
- press Wipe data factory reset
- go to Apply update and then apply from ADB `(Android Debug Bridge)`
- unplug and replug your USB cable
- and now we flash LineageOS!

  ```sh
  adb -d sideload lineage-23.2-*-nightly-dodge-signed.zip
  ```
- once done if you want to install Google Apps press yes on the screen if not press no `(Play store, Gmail, Youtube, Drive, etc.)`
  - look here: https://wiki.lineageos.org/gapps/
 
- now press reboot system now
### Enjoy LineageOS!

# Return back to stock
WIP

