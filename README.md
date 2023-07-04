# Create a bootable USB installer for macOS
### How to create a bootable installer for macOS check this [link](https://support.apple.com/en-us/HT201372)
<br/>

# Setup New Machine without dotfile

## Create Working directory

```
mkdir ~/Workspace
```

## Change shell

```
chsh -s /bin/zsh

```

## Add Z-shell resource

```
touch  ~/.zshrc
```

## Reload Z-shell resource

```
source  ~/.zshrc
```


1. `xcode-select --install` (Command Line Tools are required for Git and Homebrew)
2. [Generate ssh key](https://help.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh)

    ```zsh
    # Generate SSH key in default location (~/.ssh/config)
    ssh-keygen -t rsa -b 4096 -C "5990717+jallynme@users.noreply.github.com"

    # Start the ssh-agent
    eval "$(ssh-agent -s)"

    # Create config file with necessary settings
    << EOF > ~/.ssh/config
    Host *
      AddKeysToAgent yes
      UseKeychain yes
      IdentityFile ~/.ssh/id_rsa
    EOF

    # Add private key to ssh-agent
    ssh-add -K ~/.ssh/id_rsa

    # Copy public key and add to github.com > Settings > SSH and GPG keys
    pbcopy < ~/.ssh/id_rsa.pub

    # Test SSH connection, then verify fingerprint and username
    # https://help.github.com/en/github/authenticating-to-github/testing-your-ssh-connection
    ssh -T git@github.com
    # Hi jallynme! You've successfully authenticated, but GitHub does not provide shell access.


    # Switch from HTTPS to SSH
    git remote set-url origin git@github.com:jallynme/dotfiles.git
    ```
<br/>

## GPG

```
https://gist.github.com/troyfontaine/18c9146295168ee9ca2b30c00bd1b41e
```

## Brew

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
brew bundle

```

## vscode

```
sudo ln -fs "/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code" /usr/local/bin/code
cat vscode_extensions | xargs -L 1 code --install-extension
```

## export vscod extension 
```
code --list-extensions | xargs -L 1 echo code --install-extension

```

## nvm

```
`# nvm`
export NVM_DIR="$HOME/.nvm"
[ -s "/opt/homebrew/opt/nvm/nvm.sh" ] && \. "/opt/homebrew/opt/nvm/nvm.sh"  # This loads nvm
[ -s "/opt/homebrew/opt/nvm/etc/bash_completion.d/nvm" ] && \. "/opt/homebrew/opt/nvm/etc/bash_completion.d/nvm"  # This loads nvm bash_completion
```


```
npm install -g npm-check-updates
npm install -g prettier
```
## list global npm package

```
npm list -g --depth=0
```
## ruby

```
# run this and follow the printed instructions:
rbenv init
export PATH="$HOME/.rbenv/bin:$PATH"
eval "$(rbenv init -)"
```


## GO

```
Install go

brew install go
bash < <(curl -s -S -L https://raw.githubusercontent.com/moovweb/gvm/master/binscripts/gvm-installer)
gvm install go1.19
gvm use go1.19 --default
brew uninstall go
export GOROOT_BOOTSTRAP=$GOROOT
```


## pyenv

```
brew install pyenv pyenv-which-ext
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
```




## fvm

```
# fvm
export PATH=$PATH:"/Users/jeremy/fvm/default/bin"
export PATH="$PATH:$HOME/.pub-cache/bin"
```
