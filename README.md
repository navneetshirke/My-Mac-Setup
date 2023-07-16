# My-Mac-Setup

# 1 For `.zshrc` file (showing Git Repo name & current working directory)

```bash

autoload -Uz compinit && compinit
autoload -Uz add-zsh-hook
autoload -Uz vcs_info
add-zsh-hook precmd vcs_info
zstyle ':vcs_info:*' enable git
zstyle ':vcs_info:*' formats " %F{cyan}%c%u(%b)%f"
zstyle ':vcs_info:*' actionformats " %F{cyan}%c%u(%b)%f %a"
zstyle ':vcs_info:*' stagedstr "%F{green}"
zstyle ':vcs_info:*' unstagedstr "%F{blue}"
zstyle ':vcs_info:*' check-for-changes true
zstyle ':vcs_info:git*+set-message:*' hooks git-untracked
+vi-git-untracked() {
  if git --no-optional-locks status --porcelain 2> /dev/null | grep -q "^??"; then
    hook_com[staged]+="%F{blue}"
  fi
}
setopt PROMPT_SUBST
export PROMPT='%n::%4~$vcs_info_msg_0_ %#'
```

# 2 install Brew

```bash

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

```

# 3 install Apps

```bash
 brew install --cask google-chrome visual-studio-code slack iterm2 appcleaner sublime-text docker asdf
```

# 4 Install Ruby

```bash
cd
git clone https://github.com/excid3/asdf.git ~/.asdf
echo '. "$HOME/.asdf/asdf.sh"' >> ~/.zshrc
echo '. "$HOME/.asdf/completions/asdf.bash"' >> ~/.zshrc
echo 'legacy_version_file = yes' >> ~/.asdfrc
exec $SHELL
```

# 5 Install plugin
```bash
asdf plugin add ruby
asdf plugin add nodejs
asdf install ruby 3.2.2
asdf global ruby 3.2.2
# Update to the latest Rubygems version
gem update --system

which ruby
#=> /Users/username/.asdf/shims/ruby
ruby -v
#=> 3.2.2
asdf install nodejs 18.16.1
asdf global nodejs 18.16.1

which node
#=> /Users/username/.asdf/shims/node
node -v
#=> 18.16.1

# Install yarn for Rails jsbundling/cssbundling or webpacker
npm install -g yarn
```


# 6 Config Git

```bash
git config --global color.ui true
git config --global user.name "YOUR NAME"
git config --global user.email "YOUR@EMAIL.com"
ssh-keygen -t ed25519 -C "YOUR@EMAIL.com"
```

# 7 Install Rails

```bash
gem install rails -v 7.0.6
rails -v
# Rails 7.0.6
```

# 8 Setting Up A Database

```bash
brew install postgresql
# To have launchd start postgresql at login:
brew services start postgresql

```
# 9 Iterm iTerm Themes
create a file ` .theme.itermcolors` & paste from this link for `synthwave` & also try (Breeze ,Brogrammer ,Builtin Dark)

```bash
https://raw.githubusercontent.com/mbadolato/iTerm2-Color-Schemes/master/schemes/synthwave.itermcolors
```
