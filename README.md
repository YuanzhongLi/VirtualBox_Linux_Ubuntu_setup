# Mac Setup Ubuntu on VirtualBox


## DownLoads
- [Virtual Box](https://www.oracle.com/jp/virtualization/technologies/vm/downloads/virtualbox-downloads.html)

- [Ubuntu](https://ubuntu.com/download/desktop)  
download Ubuntu version you want use
```
ex.)
ubuntu-20.04.1-desktop-amd64.iso
```

## Setup
### 1. Create new VM
Open virtual box and seclect tool and selcet create new(N)
```
# type name
Ubuntu20.04LTS

# machine folder (optional)
/Users/<user_name>/VirtualBox VMs

# machine RAM size (optional)
ex.) 8192 MB (8GB)

# hard disc
create virtual hard disc

# hard disc file type
VDI (VirtualBox Disk image)

# storage
mutable size

# file directory and file size (optional)
ex.) /Users/<user_name>/VirtualBox VMs/Ubuntu20.04LTS
ex.) 32.00 GB
```

### 2. Install Ubuntu
Select start(T)
```
# click folder icon and attach disc
ubuntu-20.04.1-desktop-amd64.iso

# select lanuage and click install
ex.) English

# install type
erase disc and install Ubuntu

# where you are
ex.) Tokyo

# fill your personal data
<your_name>
<your_computer_name>
<user_name>
<user_password>

# after install click restart

# software update
// jsut in case, after restart make a snapshot (<name: after_install>)
```

### 3. Update packages
open terminal
```
$ sudo apt update
$ sudo apt upgrade
```

## 4. Options
### Mutable screen size
Virtual Boxのスクリーンを調整すると自動でUbuntuのデスクトップも調整される
```
# window
device
Guest Additions CD image ...
Run

# Authentication
Power Off
Restart
```

### Share Clipboard (Host <-> VM)
ホストとVMでクリップボードを共有する．  
ホスト（VM）でコピーしたものがVM（ホスト）でペーストできるようになる．
```
# Bidirectional copy
device
Shared Clipboard
```
![clipboard](clipboard.png)

### Japanese keyboard (Only if you use US keyboard)
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

# select A(right up)
Input Mode (A)
Hiragana
// superkey + space (change input)
```

if you can not find Japanese (Mozc)
```
sudo apt remove ibus-mozc
reboot
```

### Ignore upper or lower case at bash
```
# wirte at /etc/inputrc
set completion-ignore-case on
// push Ctrl-x and Ctrl-r
```

### Change browser to Chrome
[link](https://inab818.site/linux/ubuntu-20-04-lts-google-chrome-download-install/)

### Git
```
$ sudo apt install git
// check
$ dpkg -l git

$ git config --global user.name <your_user_name>
$ git config --global user.email <your_email>

# add your id_rsa(secret key)
~/.ssh/id_rsa
-----BEGIN OPENSSH PRIVATE KEY-----
<your_secret_key>
-----END OPENSSH PRIVATE KEY-----

# if you do not have keys
cd ~/.ssh
ssh-keygen -t rsa
# put your public key on github

# set your config
~/.ssh/config
Host github
  HostName github.com
  IdentityFile ~/.ssh/id_rsa
  User git

# check id_rsa access right
$ cd ~/.ssh
$ ls -l
// if the right is too loose
$ chmod 600 id_rsa
$ ssh-add id_ras

// NOTE: if you access gitbub before add secret key, you should erase known_hosts


// ~/.bashrc
# display github branch
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
if [ -f /etc/bash_completion.d/git-prompt ]; then
    export PS1='\[\033[01;32m\]\u@\h\[\033[01;33m\] \w$(__git_ps1) \n\[\033[01;34m\]\$\[\033[00m\] '
else
    export PS1='\[\033[01;32m\]\u@\h\[\033[01;33m\] \w \n\[\033[01;34m\]\$\[\033[00m\] '
fi

```

### VSCode
Download deb from [VSCode official site](https://code.visualstudio.com/)
```
$ sudo apt install ./<Downloaded>.deb
$ sudo apt install -y apt-transport-https
$ sudo apt update

# open VSCode
$ code
```

### Extensions
```
- Emacs Friendly Keymap
```

### Typing and Mouse
```
Mouse & Touchpad
Universal Access -> Typing -> Repeat Keys
```
