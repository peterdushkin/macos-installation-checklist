- [ ] - Download macOS Monterey (12): [App Store](https://apps.apple.com/us/app/macos-monterey/id1576738294)
- [ ] - Verify macOS signature using the `pkgutil --check-signature` or `codesign -dvv` commands.
- [ ] - Create a bootable USB installer:
        diskutil list
        diskutil unmountDisk /dev/disk2
        diskutil partitionDisk /dev/disk2 1 JHFS+ Installer 100%
        cd /Applications/Install\ macOS\
- [ ]
- [ ]
- [ ]
- [ ]
