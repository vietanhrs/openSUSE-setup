# openSUSE-setup

## Permanently set the MTU to 1490 to prevent slow page loading
```bash
nmcli connection show
sudo nmcli connection modify "<wifi name>" wifi.mtu 1490
sudo nmcli connection up "<wifi name>"
```

## Essential tools
```bash
sudo zypper install git
sudo zypper install --type pattern devel_basis
```
### Google Chrome
```bash
sudo rpm --import https://dl.google.com/linux/linux_signing_key.pub
sudo zypper ar http://dl.google.com/linux/chrome/rpm/stable/x86_64 google
sudo zypper refresh && sudo zypper install google-chrome-stable
```

### VS Code
```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc && echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\nautorefresh=1\ntype=rpm-md\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" | sudo tee /etc/zypp/repos.d/vscode.repo > /dev/null
sudo zypper install code
```

## GNOME Extensions
Requires: `gnome-browser-connector` installed above

- [App Indicators](https://extensions.gnome.org/extension/615/appindicator-support/)
- [Apps Menu](https://extensions.gnome.org/extension/6/applications-menu/)
- [Arc Menu](https://extensions.gnome.org/extension/3628/arcmenu/)
- [Blur My Shell](https://extensions.gnome.org/extension/3193/blur-my-shell/)
- [Clipboard Indicator](https://extensions.gnome.org/extension/779/clipboard-indicator/)
- [Dash To Dock](https://extensions.gnome.org/extension/307/dash-to-dock/)
- [Lockscreen Extension](https://extensions.gnome.org/extension/7472/lockscreen-extension/)
- [User Themes](https://extensions.gnome.org/extension/19/user-themes/)
- [Vitals](https://extensions.gnome.org/extension/1460/vitals/)

## Git setup
```bash
ssh-keygen -t ed25519 -C "vietanhtran.uet@gmail.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
cat ~/.ssh/id_ed25519.pub
git config --global user.name "vietanhrs"
git config --global user.email "vietanhtran.uet@gmail.com"
```

## Rust setup
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source "$HOME/.cargo/env.fish"
```

## Install Node.js with nvm
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.6/install.sh | bash
export NVM_DIR="$HOME/.config/nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"
nvm install v24
nvm use v24
npm install -g corepack
```
