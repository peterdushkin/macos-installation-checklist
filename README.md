- [ ] - Download macOS Monterey (12): [App Store](https://apps.apple.com/us/app/macos-monterey/id1576738294)
  - [ ] - For MacBook Pro 2020 - macOS Catalina (10.15): [App Store](https://apps.apple.com/us/app/macos-catalina/id1466841314) 
- [ ] - Verify macOS signature using the `pkgutil --check-signature` or `codesign -dvv` commands.
- [ ] - Create a bootable USB installer:
  - [ ] diskutil list
  - [ ] diskutil unmountDisk /dev/disk4 
  - [ ] diskutil partitionDisk /dev/disk4 1 JHFS+ Installer 100%
  - [ ] cd /Applications/Install\ macOS\ Monterey.app 
  - [ ] sudo ./Contents/Resources/createinstallmedia --volume /Volumes/Installer --nointeraction
- [ ] - On first boot, hold `Command` `Option` `P` `R` keys to [clear NVRAM](https://support.apple.com/en-us/HT204063)
- [ ] Change default ( username-based) computer name:
   - `$ sudo scutil --set ComputerName MacBook`
   - `$ sudo scutil --set LocalHostName MacBook`
- [ ] - Firmware

Setting a firmware password prevents a Mac from starting up from any device other than the startup disk. It may also be set to be required on each boot. This may be useful for mitigating some attacks which require physical access to hardware.  See [How to set a firmware password on your Mac](https://support.apple.com/en-au/HT204455) for official documentation.

This feature [can be helpful if your laptop is lost or stolen](https://www.ftc.gov/news-events/blogs/techftc/2015/08/virtues-strong-enduser-device-controls), protects against Direct Memory Access (DMA) attacks which can read your FileVault passwords and inject kernel modules such as [pcileech](https://github.com/ufrisk/pcileech), as the only way to reset the firmware password is through an Apple Store, or by using an [SPI programmer](https://reverse.put.as/2016/06/25/apple-efi-firmware-passwords-and-the-scbo-myth/), such as [Bus Pirate](http://ho.ax/posts/2012/06/unbricking-a-macbook/) or other flash IC programmer.

1. Start up pressing `Command` and `R` keys to boot to [Recovery Mode](https://support.apple.com/en-au/HT201314) mode.
2. When the Recovery window appears, choose **Firmware Password Utility** from the Utilities menu.
3. In the Firmware Utility window that appears, select **Turn On Firmware Password**.
4. Enter a new password, then enter the same password in the **Verify** field.
5. Select **Set Password**.
6. Select **Quit Firmware Utility** to close the Firmware Password Utility.
7. Select Restart or Shutdown from the Apple menu in the top-left corner.

The firmware password will activate at next boot. To validate the password, hold `Alt` during boot - you should be prompted to enter the password.

The firmware password can also be managed with the `firmwarepasswd` utility while booted into the OS. For example, to prompt for the firmware password when attempting to boot from a different volume:

```console
$ sudo firmwarepasswd -setpasswd -setmode command
```

To verify the firmware password:

```console
$ sudo firmwarepasswd -verify
Verifying Firmware Password
Enter password:
Correct
```
- [ ]
