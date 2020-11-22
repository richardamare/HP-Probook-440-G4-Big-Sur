# HP-Probook-440-G4-Big-Sur

This is the guide to install macOS 11 Big Sur on HP Probook 440 G4.

## My laptop config:
- CPU: i5-7200U
- RAM: 16 GB
- GPU: Intel HD 620 & NVIDIA 930MX
- Wifi & Bluetooth: Broadcom BCM94352Z DW1560
- Drive: 500 GB SSD
- Display: 1080p

## What works:
- Wifi & Bluetooth
- AirDrop
- GPU Acceleration
- Brightness
- Sleep
- Audio
- Fn Keys
- Battery management
- Trackpad (gestures like real MacBook)

## What does NOT work:
- NVIDIA GPU (not supported)
- Fingerprint sensor (also not supported)

## Installation

1. Download [macOS Big Sur bootable image]()
2. Download [Balena Etcher]()
3. Create USB installer using previously downloaded image and replace Olarilla's EFI with mine
4. Restart laptop
5. Press F9 to get into boot menu
6. Select USB stick
7. Select macOS installer
8. Open Disk Utility
9. Format disk using: APFS, GUID Partition Map and go back
9. Select macOS Install
10. Start the installation (your laptop will restart few times -> always select your USB stick in the boot menu and then select macOS Install)
11. Now you should be on the desktop

## Post-installation

1. Connect yout laptop to the network
2. Open terminal and paste this commands:
``` 
xcode-select --install
```
```
mkdir ~/Projects
cd ~/Projects
git clone https://github.com/RehabMan/HP-ProBook-4x30s-DSDT-Patch probook.git
```
```
cd ~/Projects/probook.git
./download.sh
./install_downloads.sh
```
This will install required kexts into our system

3. Now mount EFI using:
```
diskutil list
```
Find your EFI partition (in my case - disk0s1)
```
sudo diskutil mount disk0s1
```
4. Open EFI using Finder and copy dowloaded EFI onto that disk


Now restart your laptop and everything should be working.

Enjoy Big Sur
