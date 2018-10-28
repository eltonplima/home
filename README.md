# My tips and custom environment configurations

## Docker

Increase docker constainer shell columns [link](https://github.com/moby/moby/issues/33794#issuecomment-380969582)

```bash
docker exec -e COLUMNS="`tput cols`" -e LINES="`tput lines`" -ti container bash
```
### Build from git repository

```
# https://docs.docker.com/engine/reference/commandline/build/#git-repositories
#                                                                                 #branch(default: master):directory of Dockerfile
docker build -t apachepulsar/pulsar-dashboard https://github.com/apache/pulsar.git#master:dashboard
```

## Linux

When the system is very slow or not responding use the following key combinations:

```bash
# Wait 1 second between each letter key press
# Maintain the CTRL + ALT + SysRQ pressed
CTRL + ALT + SysRQ r e i s u b
```

## Shell

### install zgen

```bash
git clone https://github.com/tarjoilija/zgen.git "${HOME}/.zgen"
# edit .zshrc to load zgen
source "${HOME}/.zgen/zgen.zsh"
```

[spaceship prompt](https://github.com/denysdovhan/spaceship-prompt)

### emoji

Arch

sudo pacman -Sy noto-fonts-emoji

Ubuntu

https://launchpad.net/~ubuntu-desktop/+archive/ubuntu/transitions/+files/fonts-noto-color-emoji_0~20170913-0ubuntu1~bionic1_all.deb?_ga=2.144106620.812436444.1537798894-1076452805.1537798894

## Arch

Remove a package and all dependencies.

```bash
pacman -Runs gnome
```
## Tools
* [gitmoji](https://github.com/carloscuesta/gitmoji-cli)
* [pbpst](https://github.com/HalosGhost/pbpst)
