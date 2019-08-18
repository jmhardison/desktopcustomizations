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