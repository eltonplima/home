# My dot files

## How restore
```bash
rm -rf .config/i3* .local/bin/lock .gitignore .git .profile .vimrc .zgen-local-plugins .zshrc
cd ~ && git remote add origin git@github.com:eltonplima/home.git && git pull origin master
```

or
```bash
cd ~ && git init && git remote add origin git@github.com:eltonplima/home.git && git pull origin master
```
