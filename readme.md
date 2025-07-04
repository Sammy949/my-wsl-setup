# ⚙️ My WSL Terminal Setup

This here is my custom WSL setup guide. This repo contains all the steps, commands, and tools I used to make my Ubuntu (WSL) terminal clean, fast, and visually stunning.

---

## 🖥️ Goal

Make the WSL terminal:

- Look sleek and modern (with a powerline + arrow-styled prompt)
- Have developer-friendly CLI tools
- Match the look of my PowerShell Oh My Posh setup
- Easy to reset, tweak, or share

---

## 🚀 Setup Instructions

### 1. 🧰 Install essential tools

```bash
sudo apt update && sudo apt install -y \
  zsh git curl wget bat eza htop ncdu neofetch fonts-powerline
```

> Note: On some Ubuntu versions, `bat` is installed as `batcat`. I aliased it later.

---

### 2. 🧪 Set Zsh as your default shell

```bash
chsh -s $(which zsh)
```

---

### 3. 🌟 Install Oh My Zsh

```bash
export RUNZSH=no
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

---

### 4. 💎 Install Powerlevel10k theme

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git \
  ~/.oh-my-zsh/custom/themes/powerlevel10k
```

---

### 5. 🔌 (Optional) Zsh Plugins

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions \
  ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions

git clone https://github.com/zsh-users/zsh-syntax-highlighting \
  ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting
```

---

### 6. 📝 `.zshrc` Configuration

Here's the config I use:

```zsh
export ZSH="$HOME/.oh-my-zsh"
ZSH_THEME="powerlevel10k/powerlevel10k"

plugins=(
  git
  sudo
  zsh-autosuggestions
  zsh-syntax-highlighting
)

source $ZSH/oh-my-zsh.sh

# Aliases
alias bat='batcat'
alias ls='eza -al --color=always --group-directories-first --icons'
alias sys='neofetch'
alias dux='ncdu'
```

Save that to your `~/.zshrc` file.

---

### 7. 🎨 Customise Powerlevel10k

After restarting the terminal, run:

```bash
p10k configure
```

Then pick your preferred style (I used the **arrow-backed** style to match PowerShell's Oh My Posh layout).

---

## 📦 Optional Tools I Installed

| Tool       | Use Case            |
|------------|---------------------|
| `eza`      | Modern `ls`         |
| `bat`      | Modern `cat`        |
| `ncdu`     | Disk usage viewer   |
| `neofetch` | System info summary |
| `htop`     | Process viewer      |

---

## 📁 Backup Configs

I keep my configs backed up:

```bash
mkdir -p ~/terminal-configs
cp ~/.zshrc ~/.p10k.zsh ~/.oh-my-zsh/themes/powerlevel10k/powerlevel10k.zsh-theme ~/terminal-configs/
```

Then I `git init` and push it to this repo.

---

## 🐧 Launching WSL

Just type `wsl` in your Windows Run dialog (`Win + R`) or any terminal to start your Linux shell.

---

## 🤝 License

MIT — feel free to copy, tweak, or fork this setup.

---

## 🧑‍💻 Author

**Samuel Urah Yahaya**  
[GitHub](https://github.com/Sammy949) • [X](https://www.x.com/I_am_SamY01/)  
📧 urahsamuel0202@gmail.com
