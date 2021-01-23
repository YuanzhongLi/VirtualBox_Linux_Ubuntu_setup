# Setup Ubuntu on VirtualBox
[ref link](https://www.dev2qa.com/how-to-install-ubuntu-on-virtualbox-mac/#:~:text=Start%20the%20virtual%20machine%2C%20and,the%20guest%20additions%20cd%20image.)
## DownLoad
go to [Ubuntu.com/download/desktop](https://ubuntu.com/download/desktop) and download Ubuntu version you want use
```
ubuntu-20.04.1-desktop-amd64.iso
```

## Setup
### 1. Create new
Open virtual box and seclect tool and selcet create new(N)
```
# type name
Ubuntu20.04LTS

# machine folder (optional)
/Users/<user_name>/VirtualBox VMs

# machine RAM size (optional)
ex) 8192 MB (8GB)

# hard disc
create virtual hard disc

# hard disc file type
VDI (VirtualBox Disk image)

# storage
mutable size

# file directory and file size (optional)
ex) /Users/<user_name>/VirtualBox VMs/Ubuntu20.04LTS
ex) 32.00 GB
```

### 2.Install
Select start(T)
```
# click folder icon and attach disc
ubuntu-20.04.1-desktop-amd64.iso

# select lanuage and click install
English

# install type
erase disc and install Ubuntu

# where you are
Tokyo

# fill your personal data
<your_name>
<your_computer_name>
<user_name>
<user_password>

# after install click restart

# software update
// jsut in case, after restart make a snapshot (<name: after_install>)
```

### 3. Update
open terminal
```
$ sudo apt update
$ sudo apt upgrade
```

## 4. Options
### Mutable screen size
```
# install required packages
$ sudo apt install gcc g++ make

# window
device
Guest Additions CD image ...
Run

# Authentication
Power Off
Restart

# Bidirectional copy
device
Shared Clipboard
```

### Japanese keyboard
```
$ sudo dpkg-reconfigure keyboard-configuration
Generic 105-key PC (intl.)
Japanese
Japanese
The default for the keyboard layout
No compose key
Yes

$ gnome-session-properties
Add
Name: Set JP keyboard on X startup
Commannd: setxkbmap -layout jp -option ctrl:nocaps

$ setxkbmap -layout jp

# check
setxkbmap -print -verbose 10 | grep layout
// layout: jp
```

### Japanese input
```
# open Settings
Region & Language
Manage Installed Languages
Install (when first open this section)
Close
// restart

# open Settings and select Region & Language
Input Source +
Japanese
Japanese (Mozc)

# select en(right up)
Japanese (Mozc)

# secect A(right up)
Input Mode (A)
Hiragana
// superkey + space (change input)
```

### vscode

### git
