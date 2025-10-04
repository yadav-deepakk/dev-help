## Steps to iTerm2 terminal customization (On MACOS)
1. install `brew` (skip if done already)
2. install `iTerm2` (skip if present already)
3. install `git` (skip if present already)
4. install `oh my zsh`
5. install `PowerLevel10K` Theme for `Oh My Zsh`
6. change `ZSH_THEME="powerlevel10k/powerlevel10k"` in the ~/.zshrc and do `source ~/.zshrc` file
7. configure `powerlevel10k` as terminal guides through (or do it manually) 
8. customise user profiles in settings of iTerm2 - `font-size`, `color theme`, `window`, `tabs` etc. 
9. Install `ZSH Plugins`
---

### 1. Make sure brew is installed, if not then install it via below command, also add to path
- install brew 
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
- add it to path
```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/[username]/.zprofile && 
eval "$(/opt/homebrew/bin/brew shellenv)"
```
---


### 2. Install iTerm2
```bash
brew install --cask iterm2
```
---


### 3. Install git 
```bash
brew install git
```
---


### 4. Install oh my zsh
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

---

### 5. Install PowerLevel10K Theme for Oh My Zsh
```bash
git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
```

---


### 6. change ZSH_THEME="powerlevel10k/powerlevel10k" in the ~/.zshrc and do source ~/.zshrc
- open the ~/.zshrc file and make changes in below line 
```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```
- run below command
```bash
source ~/.zshrc
```

---


### 7. configure powerlevel10k as terminal guides through
- when you terminal will guide you through many questions related to powerlevel10k configuration
- you have to select what is applicable and you'r done
- if no configuration question asked then you need to configure manually by below command
- ```bash
  p10k configure
  ```
---


### 8. customise user profiles in settings of iTerm2 (if you want) 
- Increase Terminal Font Size
- Change iTerm2 Colors differnt theme
- change tab, window etc settings in the profile
----


### 9. Install ZSH Plugins
- Install zsh-autosuggestions
```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

- Install zsh-syntax-highlighting:
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

- Open the ”~/.zshrc” file in your desired editor and modify the plugins line to what you see below.
```
plugins=(git zsh-autosuggestions zsh-syntax-highlighting web-search)
```

- Load these new plugins by running:
```
source ~/.zshrc
```
---


### Credits
[Josean Martinez](https://www.josean.com/posts/terminal-setup)
