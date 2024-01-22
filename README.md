# linux-preferences
Preferences for my Operative System

## System preferences

### Packages

```
sudo apt install htop
sudo apt install gdebi
sudo apt install net-tools
```

### Configure Terminal

- Install NVM
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash

export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"

source ~/.bashrc
```

- Install ZSH
```bash
sudo apt install git zsh
chsh -s $(which zsh) # define ZSH as default terminal

# Instal Oh My ZSH
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

# install zsh-autosuggestion plugin
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

cp ./home/.zshrc ~/.zshrc
```

- Configure Git
```bash
sudo apt-get install git
git config --global user.name "Erick Saravia"
git config --global user.email "ericksaravia16@gmail.com"
```

- Configure Access on [Github SSh and GPG keys](https://github.com/settings/keys)
```bash
ssh-keygen -t ed25519 -f ~/.ssh/github -C "ericksaravia16@gmail.com"
ssh-keygen -t ed25519 -f ~/.ssh/gitlab -C "ericksaravia16@gmail.com"

cat ~/.ssh/github.pub
cat ~/.ssh/gitlab.pub
```

## Docker

**NOTE:** Read documentation [here](https://docs.docker.com/engine/install/ubuntu/)

```bash
# uninstall conflicting packages before
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done

# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update"

# Install docker packages
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Try installation
```

## Applications

Application | Type | Link
--- | --- | ---
Visual Studio Code | Code Editor | [download](https://code.visualstudio.com/sha/download?build=stable&os=linux-deb-x64)
Google Chrome | Browser | [download](https://www.google.com/chrome/)
Microsoft Edge | Browser | [download](https://www.microsoft.com/en-us/edge/download?form=MA13FJ)
DBeaver | Database Client | [download](https://dbeaver.io/files/dbeaver-ce_latest_amd64.deb)

## References
- [ZSH Autosuggestions](https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md)