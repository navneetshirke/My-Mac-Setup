# My Mac Setup – Developer Environment

This guide sets up a complete development environment for macOS including terminal, Git, Ruby on Rails, VS Code, Sublime, and essential apps.

---

## 1️⃣ Zsh Terminal Setup

Add Git repo name and current working directory in your prompt:

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
export PROMPT='%n::%4~$vcs_info_msg_0_%#'
```

Reload:

```bash
source ~/.zshrc
```

---

## 2️⃣ Install Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

---

## 3️⃣ Install Apps via Homebrew

```bash
brew install \
  google-chrome \
  visual-studio-code \
  slack \
  appcleaner \
  sublime-text \
  docker \
  asdf \
  postman \
  vlc \
  pgadmin4 \
  libreoffice \
  git \
  git-gui \
  fsouza/prettierd/prettierd \
  chatgpt
```

Update apps:

```bash
brew upgrade
```

---

## 4️⃣ Install Apps via Links / AppStore

- **Today App**: [Link](https://apps.apple.com/in/app/today/id6443714928?mt=12)  
- **Usage App**: [Link](https://apps.apple.com/in/app/usage-system-activity-monitor/id1561788435?mt=12)  
- **Upscayl**: [Link](https://www.upscayl.org/)  

---

## 5️⃣ Git Setup

```bash
git config --global color.ui true
git config --global user.name "Navneet Shirke"
git config --global user.email "navneetshirke@gmail.com"
```

---

## 6️⃣ Install Ruby & Node via ASDF

```bash
cd
git clone https://github.com/asdf-vm/asdf.git ~/.asdf
echo '. "$HOME/.asdf/asdf.sh"' >> ~/.zshrc
echo '. "$HOME/.asdf/completions/asdf.bash"' >> ~/.zshrc
echo 'legacy_version_file = yes' >> ~/.asdfrc
exec $SHELL
```

### Add plugins & install

```bash
asdf plugin add ruby
asdf install ruby 3.2.2
asdf global ruby 3.2.2
asdf reshim ruby
gem update --system

asdf plugin add nodejs
asdf install nodejs 18.16.1
asdf global nodejs 18.16.1

npm install -g yarn
```

---

## 7️⃣ Rails Setup

```bash
gem install rails -v 7.0.6
rails -v
```

---

## 8️⃣ PostgreSQL Setup

```bash
brew install postgresql
brew services start postgresql
postgres -V
```

PostgreSQL commands:

```sql
psql postgres
\du
CREATE ROLE USERNAME WITH LOGIN PASSWORD 'PASSWORD';
ALTER ROLE USERNAME CREATEDB;
CREATE DATABASE db_name;
```

---

## 9️⃣ Sublime Text Settings

`Preferences > Settings`:

```json
{
  "color_scheme": "Monokai.sublime-color-scheme",
  "font_size": 18,
  "tab_size": 2,
  "translate_tabs_to_spaces": true,
  "detect_indentation": false,
  "word_wrap": false,
  "remove_trailing_whitespace_on_save": true,
  "ensure_single_trailing_newline": true,
  "ignored_packages": ["Vintage"]
}
```

Install Prettier:

```bash
npm install -g prettier
which prettier
```

`Preferences > Package Settings > JsPrettier > Settings - User`:

```json
{
  "prettier_cli_path": "/Users/navneetshirke/.asdf/shims/prettier",
  "auto_format_on_save": true,
  "auto_format_on_save_excludes": ["*/node_modules/*", "*/.git/*", "*/dist/*"],
  "additional_cli_args": {
    "tab_width": 2,
    "semi": true,
    "single_quote": true,
    "trailing_comma": "es5",
    "bracket_spacing": true
  }
}
```

---

## 🔟 VS Code Settings

`settings.json`:

```json
{
  "workbench.colorTheme": "Monokai",
  "editor.fontSize": 18,
  "editor.fontFamily": "JetBrains Mono",
  "editor.tabSize": 2,
  "editor.insertSpaces": true,
  "editor.detectIndentation": false,
  "editor.wordWrap": "off",
  "files.trimTrailingWhitespace": true,
  "files.insertFinalNewline": true,
  "workbench.editor.enablePreview": false,
  "editor.formatOnSave": true,
  "prettier.singleQuote": true,
  "prettier.trailingComma": "es5",
  "tailwindCSS.includeLanguages": {
    "javascript": "javascript",
    "typescript": "typescript",
    "ruby": "erb"
  },
  "editor.quickSuggestions": { "strings": true },
  "git.autofetch": true,
  "terminal.integrated.fontSize": 16,
  "js/ts.updateImportsOnFileMove.enabled": "always",
  "security.workspace.trust.untrustedFiles": "open"
}
```

---

## 1️⃣1️⃣ VS Code Extensions

```
bradlc.vscode-tailwindcss
craigmaslowski.erb
dbaeumer.vscode-eslint
eamodio.gitlens
esbenp.prettier-vscode
formulahendry.auto-rename-tag
misogi.ruby-rubocop
monokai.theme-monokai-pro-vscode
ms-python.black-formatter
ms-python.debugpy
ms-python.python
ms-python.vscode-pylance
ms-python.vscode-python-envs
ms-vscode.sublime-keybindings
openai.chatgpt
shopify.ruby-lsp
usernamehw.errorlens
```
