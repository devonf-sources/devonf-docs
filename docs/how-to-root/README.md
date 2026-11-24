# How to root Moto G73 5G

## Table of Contents

- [Introduction](#introduction)
- [Unlocking the Bootloader](#unlocking-the-bootloader)
  - [Setting up the environment](#setting-up-the-environment)
  - [Enabling OEM Unlocking toggle](#enabling-oem-unlocking-toggle)
  - [Getting Device ID](#getting-device-id)
  - [Getting Unlock Token](#getting-unlock-token)
  - [Unlock process](#unlock-process)
- [Root](#root)
  - [Obtain boot image](#obtain-boot-image)
  - [Download Root Manager](#download-root-manager)
  - [Patch boot image](#patch-boot-image)
  - [Flash Patched boot image](#flash-patched-boot-image)

---

## Introduction

Before we begin, let me make it perfectly clear that,

```
Your warranty is now void.

I am not responsible for bricked devices, dead SD cards, thermonuclear war, or you getting fired because the alarm app failed.
Please do some research if you have any concerns about features included in this ROM before flashing it!
YOU are choosing to make these modifications, and if you point the finger at me for messing up your device, I will laugh at you.
```

Also to add: This guide is ONLY for devices that are codenamed devonf and that you need a PC to do this.

Be warned that if you are already progressing with an update on Stock, you must complete the update, reboot to system and then follow the instructions to unlock the bootloader and flash ROMs.

## Unlocking the Bootloader

### Setting up the environment

First and foremost, install the [Google USB Drivers (Windows)](https://dl.google.com/android/repository/usb_driver_r13-windows.zip) on your PC by extracting the zip and right-clicking on the `android_winusb.inf` file then clicking install. You can skip this step if you are on Linux or macOS.

Next, download and extract the Platform Tools required to unlock the bootloader and flash ROMs. You can get them from the links below:

[Platform Tools (Windows)](https://dl.google.com/android/repository/platform-tools-latest-windows.zip)

[Platform Tools (macOS)](https://dl.google.com/android/repository/platform-tools-latest-darwin.zip)

[Platform Tools (Linux)](https://dl.google.com/android/repository/platform-tools-latest-linux.zip)

### Enabling OEM Unlocking toggle

Moving on, you need to enable OEM Unlocking toggle from the Developer Options page.

If the phone is new, you would have to wait for 7 days before you can enable that toggle as it will be greyed out.

To enable the Developer Options page, you would need to go to About Phone -> Device Identifiers and Tap on the Build number for 7 times in the Settings app.

### Getting Device ID

Then, you would need to get your **Device ID** to generate the Unlock Token.

You do that by opening a Terminal / Command Prompt / PowerShell Terminal in the folder/directory where the Platform Tools are extracted.

Then, turn off your device, push and hold the power and volume down button at the same time and release once the phone has booted into the Bootloader Mode.

Run ```fastboot devices``` to see if the device is detected.

An example output would be as such:

```
ZY22HZLCR2	fastboot
```

If you have installed the USB drivers properly, it will show that the device is connected.

Run, ```fastboot oem get_unlock_data``` to get the Device ID.

e.g:

```
(bootloader) Unlock data:
(bootloader) 0A40040192024205#4C4D3556313230
(bootloader) 30373731363031303332323239#BD00
(bootloader) 8A672BA4746C2CE02328A2AC0C39F95
(bootloader) 1A3E5#1F53280002000000000000000
(bootloader) 0000000
```

### Getting Unlock Token

To generate the unlock token, you'll need to merge the 5 lines of output into one string without any extra spaces or additional text. An example of that would be:

```
0A40040192024205#4C4D355631323030373731363031303332323239#BD008A672BA4746C2CE02328A2AC0C39F951A3E5#1F532800020000000000000000000000
```

Then, go to the [Motorola Unlock Website](https://en-us.support.motorola.com/app/standalone/bootloader/unlock-your-device-b). Login to your account and paste the **Device ID** string and click on **Can my device be unlocked?** to check eligibility for unlock, then accept the legal agreement and click on **Request Unlock key**.

You will then receive an email with your Unlock Token. Check your spam folder if you had not received it. Within the email would contain a unique 20-character, alphanumeric code that you will use to unlock your device.

### Unlock process

Type ```fastboot oem unlock ``` and paste your unique 20-character, alphanumeric code that you have received via email and run it.

e.g: 

```
fastboot oem unlock MZMC6D342TBNNWI6TRP9
```

If you have run the command correctly, your device's screen will confirm that your device is unlocked.

**Congratulations**, you have just successfully unlocked the bootloader of your device, moving forward when you reboot, it will show a warning screen that your **Bootloader has been unlocked**.

## Root

### Obtain boot image

#### If you are on custom rom

  - Download the ROM you are using, Don't use boot image from initial\_install.

  - Download any payload dumper tool/app or payload dumper supported tool/app

    e.g: [Payload Dumper Go](https://github.com/ssut/payload-dumper-go/releases), [MT Manager](https://t.me/mtmanager), [Payload Dumper Android](https://github.com/rajmani7584/Payload-Dumper-Android/releases) etc.

  - Unzip Rom zip and open payload.bin by payload dumper/MT Manager.

  - Copy the boot image and send it to your phone.

#### If you are on stock rom

  - Open Setting, Go to About Phone and check build number

  - Download firmware with exact matching build version

  - Unzip firmware, Copy the boot image and send it to your phone.

---

### Download Root Manager

  **Magisk and Forks**
  - [Magisk Official](https://github.com/topjohnwu/Magisk/releases)
  - [Magisk Alpha](https://t.me/magiskalpha)

  **KernelSU and Forks**
  - [KernelSU Official](https://github.com/tiann/KernelSU/releases)
  - [KernelSU Next](https://github.com/KernelSU-Next/KernelSU-Next/releases)
  - [SukiSU](https://github.com/SukiSU-Nova/SukiSU-Nova/releases)
  - [BakaSU (ReSukiSU)](https://github.com/Baka-SU/BakaSU/releases)
  - [FinaSU](https://github.com/LyraVoid/FinaSU/releases)
  - [KowSU](https://t.me/kowsu_build)

  **Apatch and Forks**
  - [Apatch Official](https://github.com/bmax121/APatch/releases)
  - [FolkPatch](https://github.com/LyraVoid/FolkPatch/releases)

### Patch boot image

  - Open root manager

  - Click on install button/patch button

  - Select boot image which you have just copied

  - Click and Start patching

  - If you are patching via kernel based root mangaer like kernelSU, kernelSU Next etc. It will ask for kernel version then choose `android-12 5.10`.

  - After patching boot image, Go to `Download/` folder and copy the patched boot image to your PC.


### Flash Patched boot image

Turn off your device, push and hold the power and volume down button at the same time and release once the phone has booted into the Bootloader Mode.

Open a Terminal / Command Prompt / PowerShell Terminal and run ```fastboot reboot fastboot```.

Once the phone has booted into the FastbootD Mode, run ```fastboot devices``` to see if the device is detected.

An example output would be as such:

```
ZY22HZLCR2	fastbootd
```

Some operating systems may report FastbootD Mode as fastboot as well so to properly confirm if you are in FastbootD Mode, you may run ```fastboot getvar is-userspace```.

An example output would be as such:

```
is-userspace: yes
Finished. Total time: 0.001s
```

If it says no, re-read the instructions again.

The reason why you need to be in fastbootd and not bootloader (fastboot) is because you cannot flash images in bootloader due to Motorola implementing a sort of timestamp check within the bootloader which then results in an error like such:

```
Writing 'boot_b'                                   (bootloader) Preflash validation failed
FAILED (remote: '')
fastboot: error: Command failed
```

As such, you NEED to be in fastbootd to flash the patched boot image.

If it is not detected, you should re-read Unlocking the Bootloader part as to installing the relevant USB drivers.

Moving on, type ```fastboot flash boot ``` and then drag-and-drop the patched boot image into the terminal and run it.

e.g:

```
fastboot flash boot magisk_patched-xxxxx.img
```

After Successfully flashing, Reboot the device.
```
fastboot reboot
```

Voila, your device is now rooted.
