# My tips and custom environment configurations

## Docker

Increase docker container shell columns [link](https://github.com/moby/moby/issues/33794#issuecomment-380969582)

```bash
docker exec -e COLUMNS="`tput cols`" -e LINES="`tput lines`" -ti container bash
```

Remove all stoped containers:

```bash
docker container prune
```

### Open the docker daemon to the network

/etc/default/docker
```
DOCKER_OPTS="--dns 1.1.1.1 --dns 8.8.4.4 -H 0.0.0.0:2375 -H unix:///var/run/docker.sock"
```

/lib/systemd/system/docker.service
```
EnvironmentFile=/etc/default/docker
ExecStart=/usr/bin/dockerd $DOCKER_OPTS
```

```
sudo systemctl daemon-reload && sudo systemctl restart docker.service
```

### Build from git repository

```
# https://docs.docker.com/engine/reference/commandline/build/#git-repositories
#                                                                                 #branch(default: master):directory of Dockerfile
docker build -t apachepulsar/pulsar-dashboard https://github.com/apache/pulsar.git#master:dashboard
```

### Tool to explore docker images

https://github.com/wagoodman/dive

### Solve the pip bug on Ubuntu 18.04

After running `pip3 install -U pip` the pip breaks with the following error:

```
Traceback (most recent call last):
  File "/usr/bin/pip3", line 9, in <module>
    from pip import main
ImportError: cannot import name 'main'
```

To solve this problem execute:

```
RUN bash -c "hash -d pip3"
```

You can found more details about the problem and the solution [here](https://stackoverflow.com/questions/49836676/error-after-upgrading-pip-cannot-import-name-main).

## Linux

When the system is very slow or not responding use the following key combinations:

```bash
# Wait 1 second between each letter key press
# Maintain the CTRL + ALT + SysRQ pressed
CTRL + ALT + SysRQ r e i s u b
```

Find all hosts online on network:

```
sudo arp-scan --interface=eth0 --localnet
```

Monitoring files and running command. In this example I will run the python unittest.

```
while inotifywait -e close_write -r .; do python -m unittest discover; done
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

## Git

Remove remote tag
```
git push --delete origin tagname
```

Remove local tag

```
git tag --delete tagname
```

Create commit message template

```
git config --global commit.template ~/.gitmessage

echo > ~/.gitmessage << EOF
# [Add/Fix/Remove/Update/Refactor/Document] [summary]


# Why is it necessary? (Bug fix, feature, improvements?)
-
# How does the change address the issue? 
-
# What side effects does this change have?
-
# Include a link to the ticket, if any.
EOF
```

## Arch

Remove a package and all dependencies.

```bash
pacman -Runs gnome
```
## Tools
* [gitmoji](https://github.com/carloscuesta/gitmoji-cli)
* [pbpst](https://github.com/HalosGhost/pbpst)
* [jq playground](https://jqplay.org/)
* [regex101](https://regex101.com/)

## KDE 5
* [shortcuts](https://defkey.com/kde-plasma-shortcuts)

## Gnome 3

### Disable keyboard layout switch with *ALT+Shift*

```bash
dconf write /org/gnome/desktop/input-sources/xkb-options "['grp_led:scroll']"
```

## asdf install python and erlang

### Dependencies(Ubuntu)

```
sudo apt-get install build-essential libbz2-dev libsqlite3-dev libreadline-dev \
libssl-dev libffi-dev libc6-dev zlib1g-dev automake autoconf libncurses5-dev \
unixodbc-dev libwxgtk3.0-dev libxslt1-dev xsltproc fop libxml2-utils
```

## httpie

[cheatsheet](https://devhints.io/httpie)

## Minikube

### How to manage using systemctl

```
systemctl status snap.docker.dockerd.service
```
## Load test tools

* [hey](https://github.com/rakyll/hey)
* [siege](https://github.com/JoeDog/siege)
