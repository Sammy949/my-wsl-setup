# ⚙️ My WSL Terminal Setup

This guide will take you from a fresh **Windows Subsystem for Linux (WSL)** install to a fully customised Ubuntu terminal with **zsh**, **Oh My Zsh**, and **Oh My Posh**.

---

## 🖥️ Goal

Make the WSL terminal:

- Look sleek and modern (with a powerline + arrow-styled prompt)
- Have developer-friendly CLI tools
- Match the look of my PowerShell Oh My Posh setup
- Easy to reset, tweak, or share

---

## 1. Installing WSL

### Enable WSL
Open **PowerShell** as Administrator and run:
```powershell
wsl --install
```
This will:
- Install WSL 2
- Install Ubuntu (default) unless specified otherwise

---

### Install a Specific Distro (Ubuntu)
```powershell
wsl --install -d Ubuntu
```
If you get a `0x80072ee2` timeout error:
- Connect to a **VPN** and try again (this can happen if Microsoft/GitHub servers are blocked).

---

### First-Time Ubuntu Setup
When Ubuntu launches for the first time, it will prompt you for:
- **Username**
- **Password**
  
Example:
```plaintext
Create a default Unix user account: samuel
New password:
Retype new password:
```

---

## 2. Preparing Ubuntu

Update and upgrade packages:
```bash
sudo apt update && sudo apt upgrade -y
```

---

## 3. Installing and Setting zsh

Install zsh:
```bash
sudo apt install zsh -y
```

Set zsh as the default shell:
```bash
chsh -s $(which zsh)
```

Restart WSL:
```bash
exit
wsl
```

---

## 4. Installing Oh My Zsh

Run:
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
Press **Y** when prompted to change your default shell.

---

## 5. Installing Oh My Posh

Download and install Oh My Posh:
```bash
sudo wget https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/posh-linux-amd64 -O /usr/local/bin/oh-my-posh
sudo chmod +x /usr/local/bin/oh-my-posh
```

---

## 6. Installing Oh My Posh Themes

Create the theme folder:
```bash
mkdir ~/.poshthemes
```

Download themes:
```bash
wget https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/themes.zip -O ~/.poshthemes/themes.zip
sudo apt install unzip -y
unzip ~/.poshthemes/themes.zip -d ~/.poshthemes
chmod u+rw ~/.poshthemes/*.omp.*
rm ~/.poshthemes/themes.zip
```

---

## 7. Configuring zsh to Use Oh My Posh

Open `.zshrc`:
```bash
nano ~/.zshrc
```

Add the following line at the end (you can change the theme later):
```bash
eval "$(oh-my-posh init zsh --config ~/.poshthemes/jandedobbeleer.omp.json)"
```

Save (`CTRL+O`, Enter) and exit (`CTRL+X`).

Reload zsh:
```bash
source ~/.zshrc
```

---

## 8. Optional: Install Useful zsh Plugins

### Autosuggestions
```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

### Syntax Highlighting
```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

Enable them in `.zshrc`:
```bash
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

Reload:
```bash
source ~/.zshrc
```

---

## Final Result
You now have:
- WSL Ubuntu
- zsh as your default shell
- Oh My Zsh for shell configuration
- Oh My Posh for a beautiful prompt
- Optional plugins for extra functionality

---

## Key Takeaways
- WSL runs Linux on Windows without a VM.
- zsh offers powerful shell features.
- Oh My Zsh simplifies zsh management.
- Oh My Posh makes your terminal visually appealing.
- Plugins improve productivity.

## 🧑‍💻 Author

**Samuel Urah Yahaya**  
[GitHub](https://github.com/Sammy949) • [X](https://www.x.com/I_am_SamY01/)  
📧 urahsamuel0202@gmail.com
