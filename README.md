# OnePlus 13 - installing LineageOS

## Step 1. Preparation
- install ADB (`Android Debug Bridge`)
    - MacOS:
      ```sh
      brew install android-platform-tools
      ```
    - Linux:
      ```sh
      sudo apt install android-tools-adb android-tools-fastboot
      ```
    - Windows:
      Download from:
      ```html
      https://dl.google.com/android/repository/platform-tools-latest-windows.zip
      ```
      and then unzip
- Make sure your OnePlus 13 has USB debugging and OEM Unlocking
  - Open Settings -> About device -> Version -> Tap 7 times on the version number and enter your password/pattern
  - Settings -> System & Update -> Developer Options -> OEM Unlocking ✓ USB Debugging ✓
- Plug your phone into yor PC
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

- Flash boot. This will flash the boot partition that helps the phone boot into the small linux kernel 
  ```sh
  fastboot flash boot boot.img
  ```
- Flash DTBO. Device Tree Blob for Overlay lets android's bootloader apply a hardware specific overlay so the kernel can boot correctly for the specific phone
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

# Return back to OxygenOS
- Download from here: https://danielspringer.at/index.php?dir=Oneplus+13%2FRegional+Flashers
  - Pick your region `(eg. EU, IN, Global, Etc.)`
  - and download the top leftmost version
- Once downloaded unzip the file.
- On the phone go to Settings -> About phone -> Tap Build number 7 times -> Go back, System -> Developer Options -> USB debugging ✓
- Plug your OnePlus 13 in your PC and run this to go into the bootloader
  ```sh
  adb reboot bootloader
  ```
- Once the phone is in the bootloader go to your PC and open the folder you just unzipped
    - double click the `Regional_Flasher.bat`
    - and follow the instrucions given on screen
- if you are on Mac. Intel/Apple Silicon
      - use the script given in this Repositories Releases.
      - Once you have the script Open terminal and run the script with
      ```sh
      chmod +x Regional_Flasher_macos.sh
      ```
      - and then
      ```sh
      ./Regional_Flasher_macos.sh
      ```
      - but make sure you run the script in the folder you unzipped.
      - again, follow the instrucions on screen.

## Enjoy OxygenOS
- if you want to lock the bootloader
   - Open Settings -> About device -> Version -> Tap 7 times on the version number and enter your password/pattern
   - Settings -> System & Update -> Developer Options -> USB Debugging ✓
- Plug your phone into your pc and run:
  ```sh
  adb reboot bootloader
  ```
  once it rebooted to the bootloader run:
  ```sh
  fastboot flashing lock
  ```
  and with the volume keys you select and with power you confirm
  Select `LOCK THE BOOTLOADER`
### Now your phone is good as new! Enjoy!
