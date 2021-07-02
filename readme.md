# Installing working containers on Windows with WSL 2, Ubuntu and docker

## Steps followe from these sets of documentation
https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-git
https://docs.microsoft.com/en-us/windows/wsl/install-win10

## Installing Ubuntu WSL
Go to the windows store and install the latest version of Ubuntu

Ubuntu is the flavour of choice just because I currently know how to use it and understand most of the commands

Once installed, open Ubuntu and wait for the installation to finish

Enter your new username and password for the Ubuntu instance

## Installing GIT
Whilst in Ubuntu, you need to install git. Follow the commands below
1. sudo apt update
2. sudo apt-get install git

## Setting your git credentials
The following steps assumes you've already setup your credentials on Windows as they share the credentials
Run the following commands
1. git config --global user.name "Your Name"
2. git config --global user.email "youremail@domain.com"
3. git config --global credential.helper "/mnt/c/Program\ Files/Git/mingw64/libexec/git-core/git-credential-manager-core.exe"

## Upgrading WSL to WSL 2
Open powershell or your command prompt of choice
Run the following
1. wsl --set-default-version 2
2. wsl --list --verbose
    * The next step involves you entering the Ubuntu WSL version installed to upgrade it (if it's not version 2)
    * wsl --set-version <distribution name> <versionNumber> e.g. wsl --set-version Ubuntu-20.04 2
    * Wait for the conversion to finish, it should only take a minute or so 

## Integrating Docker with WSL 2
Go back into Docker on Windows and go to Settings -> Resource -> WSL and select your distro and enable WSL 2 integration

Restart Docker

## Troubleshooting

### Git saying credential manager core could not be found
Weird one this, even after installing I couldn't find it. I simply changed the path it used to
git config --global credential.helper "/mnt/c/Program\ Files/Git/mingw64/libexec/git-core/git-credential-manager.exe"