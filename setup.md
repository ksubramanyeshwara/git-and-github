# Installion of Git and Configuration

## Install Git on Windows

- Go to the official website: https://git-scm.com/download/win
- Download the latest "64-bit Git for Windows Setup".
- Run the installer(.exe) file.
- Keep clicking Next and leave the default settings as they are (recommended).
- Click Install.
- Once finished, open a new terminal and type `git --version`.

## Install Git on macOS

- Open Terminal.
- Install Homebrew (if you don’t have it): `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
- Install Git: `brew install git`
- Verify `git --version`

## Install Git on Debian / Ubuntu / Linux Mint / Pop!\_OS etc.

- Refresh the list of available software `sudo apt update`
- Download and install Git without asking questions `sudo apt install git -y`
- Verify on any distro: `git --version`

## Git Configure

### Username

`git config --global user.name`

### Email

`git config --global user.email`

### Verify the configuration

`git config --global --list`
