# dotfiles-simple

Some simple dotfiles for `tmux` and `zsh` to get you started.

# Zsh

## Install zsh
This will be system dependent, on ubuntu you can run:
```
sudo apt-get -y install zsh
```
On newer versions of MacOS, zsh comes pre-installed.  On older versions you will have to install it using Homebrew.

## Add zsh plugins

Install oh-my-zsh and plugins
```
sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"

git clone https://github.com/zsh-users/zsh-history-substring-search ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-history-substring-search
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/agkozak/zsh-z ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-z

```

## Link
```
ln -sf ~/dotfiles-simple/zshrc ~/.zshrc
```

## Launch zsh
chsh -s $(which zsh)

# tmux

## Install
This should come installed on most systems!  Maybe you will want to use homebrew
```
brew install tmux
```

## Add plugins
```
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```
Then open tmux and run PREFIX+I

## Link
```
ln -sf ~/dotfiles-simple/tmux.conf ~/.tmux.conf
```
