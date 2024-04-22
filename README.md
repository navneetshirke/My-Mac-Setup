# My-Mac-Setup

# For `.zshrc` file (showing Git Repo name & current working directory)

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

# install Brew

```bash

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

```

# install Apps via BREW

```bash
 brew install --cask google-chrome visual-studio-code slack appcleaner sublime-text docker asdf postman vlc pgadmin4 libreoffice git git-gui subler imazing
```
for update - ``` brew upgrade  ```

# install Apps via Link/AppStore

```
1 Today App: https://apps.apple.com/in/app/today/id6443714928?mt=12
2 Usage App: https://apps.apple.com/in/app/usage-system-activity-monitor/id1561788435?mt=12
3 FlipCLock: https://apps.apple.com/in/app/flip-clock-digital-widgets/id1181028777 
4 upscayl: https://www.upscayl.org/
```

# Install Ruby

```bash
cd
git clone https://github.com/excid3/asdf.git ~/.asdf
echo '. "$HOME/.asdf/asdf.sh"' >> ~/.zshrc
echo '. "$HOME/.asdf/completions/asdf.bash"' >> ~/.zshrc
echo 'legacy_version_file = yes' >> ~/.asdfrc
exec $SHELL
```

# Install plugin
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


# Config Git

```bash
git config --global color.ui true
git config --global user.name "YOUR NAME"
git config --global user.email "YOUR@EMAIL.com"
ssh-keygen -t ed25519 -C "YOUR@EMAIL.com"
```

# Install Rails

```bash
gem install rails -v 7.0.6
rails -v
# Rails 7.0.6
```

# Setting Up A Database

```bash
brew install postgresql
# To have launchd start postgresql at login:
brew services start postgresql

postgres -V
# Configuring Postgres
1 psql postgres
2 \du
# Creating Users
3 CREATE ROLE USERNAME WITH LOGIN PASSWORD 'PASSWORD'; 
# Enable permission
4 ALTER ROLE patrick CREATEDB; 
5 CREATE DATABASE  db_name;
```

# Sublime textEditor setting 

You can simply go to file `preferences/settings/preferences.sublime_setting`

```bash
{
	"color_scheme": "Monokai.sublime-color-scheme",
	"font_size": 15,
	"tab_size": 2,
	"translate_tabs_to_spaces": true,
	"detect_indentation": false,
	"preview_on_click": false
}
```
