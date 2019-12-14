# My dot files

## Pre configurations
```bash
sudo apt install zsh
chsh -s /bin/zsh
git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.7.5
asdf plugin-add nodejs
asdf plugin-add python
asdf install python 3.7.5
asdf install nodejs 12.13.1
bash ~/.asdf/plugins/nodejs/bin/import-release-team-keyring
asdf global python 3.7.5
asdf global nodejs 12.13.1
pip install -U ipython neovim jupyterlab
asdf reshim
sudo apt-get -y install stow
cd ~
git clone https://github.com/tarjoilija/zgen.git "${HOME}/.zgen"
git clone git@github.com:unixorn/zsh-quickstart-kit.git .zsh-quickstart-kit
cd .zsh-quickstart-kit
stow --target=/home/eltonplima
```

## How restore
```bash
rm -rf .config/i3* .local/bin/lock .gitignore .git .profile .vimrc .zgen-local-plugins .zshrc
cd ~ && git remote add origin git@github.com:eltonplima/home.git && git pull origin master
```

or
```bash
cd ~ && git init && git remote add origin git@github.com:eltonplima/home.git && git pull origin master
```
