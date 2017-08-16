# MINGW-KDE-Frameworks
Initial MINGW-KDE-Frameworks
The KDE Frameworks build on the Qt framework, providing everything from simple utility classes (such as those in KCoreAddons) to integrated solutions for common requirements of desktop applications (such as KNewStuff, for fetching downloadable add-on content in an application, or the powerful KIO multi-protocol file access framework).


# Using Hosted Binaries
### 1. Add to MSYS pacman config:

edit /etc/pacman.conf

[kde]
Include = /etc/pacman.d/mirrorlist.kde
```
$ patch  -i pacmanconf.patch  /etc/pacman.conf
```
```
$ echo 'Server = https://github.com/claydonkey/MINGW-KDE-Frameworks/releases/download/v0.1/' > /etc/pacman.d/mirrorlist.kde 
```
### 2. Update pacman db

```
$ pacman -Sy

error: kde: key "CBD471804F360D3F" is unknown
:: Import PGP key 4096R/88ABBE3705D3B232380AAAE5CBD471804F360D3F, "Anthony Campbell (claydonkey) <anthony@claydonkey.com>", created:      2017-07-25? [Y/n] Y
:: Synchronizing package databases...
```

### 3. Add gpg to pacman:
```
$ pacman-key --lsign-key CBD471804F360D3F
```
check imported correctly
```
$ gpg --homedir /etc/pacman.d/gnupg/ --list-keys --keyid-format long
...
pub   4096R/CBD471804F360D3F 2017-07-25
uid                          Anthony Campbell (claydonkey) <anthony@claydonkey.com>
...
```

### 4. Update pacman db
```
pacman -Sy
```


### Building all packages:

```
cd mingw-w64-PKGBUILD-common
```

```
./build-install VERSION [GPGPHRASE]
```

using build-kf5
```
./build-kf5 -[shared static] -[release debug] -[nostrip strip] -[install] -[version] VERSION -[sign] GPGPHRASE 

```


