# Linux Customization

Generally in Linux, I run Manjaro on my desktop. These tweaks are not meant for the servers I work on.

### Fish Shell

Install fish from:

- Manjaro: `sudo pacman -Syyu fish`
- Ubuntu: `sudo apt-add-repository ppa:fish-shell/release-3`
  - `sudo apt update`
  - `sudo apt install fish`
- `chsh -s /usr/bin/fish`

Install Oh My Fish from:

- `curl -L https://get.oh-my.fish | fish`

Install BobTheFish from:

- `omf install bobthefish`

Install Nerd Fonts from:

- `https://github.com/ryanoasis/nerd-fonts`
- Exectue `install.sh` in folder

    or

- Manjaro: Obtain `nerd-fonts-complete` from AUR.

Install MTR if not already:

- Manjaro: `sudo pacman -Syyu mtr`
- Ubuntu: `sudo apt install mtr`

Set fish color to dracula

- `set theme_color_scheme dracula`
- `fish_config` set colors to dracula

### Install Components for Android Studio

Install kvm and tools
- `sudo apt install qemu-kvm bridge-utils`
- `sudo adduser <username> kvm`

### Yubikey Luks Modifications
- `sudo apt-get install yubikey-personalization`
- `sudo yubikey-luks-enroll -d /dev/sda3 -s 7`
- Modify `/etc/crypttab` to have script appended.
  - `luks,keyscript=/usr/share/yubikey-luks/ykluks-keyscript`
- `systemctl enable yubikey-luks-suspend.service`
- `sudo update-initramfs -u`

### Yubikey GPG import and SSH enablement
- `gpg --keyserver keyserver.ubuntu.com --recv 62056042a03a3659ecc25c275cb770bf020e6336`
- set to ultimate trust
- unlock features of card
- enable ssh key support
```console
  sudo killall gpg-agent
  sudo killall ssh-agent
  # note: eval is used because the produced STDOUT is a bunch of ENV settings
  eval $( gpg-agent --daemon --enable-ssh-support )
  ssh-add -L
```
Add these to the shell `rc` file:

```console
export GPG_TTY="$(tty)"
export SSH_AUTH_SOCK="/run/user/$UID/gnupg/S.gpg-agent.ssh"
gpg-connect-agent updatestartuptty /bye > /dev/null
```

### Git Commit Signing
- `git config --global user.signingkey 5CB770BF020E6336`
- `git config --global commit.gpgsign true`
