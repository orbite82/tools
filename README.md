# Workstation Tools

This repository contains scripts to automate and speedup the workflow and preparation for my machine.

> **_Disclaimer_** :  
> Those scripts are ubuntu related with major version 18+, for other distributions you'll need to adapt it
___

## Prepare Workstation

> Read the `ubuntu.yml` file before applying and be sure to understand everything that will be done.

1. Install Ansible
```bash
sudo apt update && sudo apt install ansible -y
```
2. Install Git
```bash
sudo apt install git -y
```
3. Clone this repository
```bash
git clone https://github.com/orbite82/tools.git
```

4. Apply the configuration
```bash
ansible-playbook tools/ubuntu.yml --ask-become-pass
```
>Type your password when asked to give root permissions for some actions.

5. Corrigindo erro "failed: [localhost] (item=terminator)"
 
 [Link de Referencia](https://www.tecmint.com/fix-unable-to-lock-the-administration-directory-var-lib-dpkg-lock/)

```
    ps -A | grep apt
    31700 ?        00:00:04 aptd
    sudo kill -9 31700
```    
```
    ps -A | grep apt
```
```
    sudo rm /var/lib/dpkg/lock
```
```
    sudo dpkg --configure -a    
    Setting up opera-stable (80.0.4170.40) ...
    update-alternatives: using /usr/bin/opera to provide /usr/bin/x-www-browser (x-www-browser) in auto mode
    update-alternatives: warning: skip creation of /usr/share/man/man1/x-www-browser.1.gz because associated file /usr/share/man/man1/opera.1.gz (of link group x-www-browser) doesn't exist
    update-alternatives: using /usr/bin/opera to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode
    update-alternatives: warning: skip creation of /usr/share/man/man1/gnome-www-browser.1.gz because associated file /usr/share/man/man1/opera.1.gz (of link group gnome-www-browser) doesn't exist
    Processing triggers for mime-support (3.64ubuntu1) ...
    Processing triggers for hicolor-icon-theme (0.17-2) ...
    Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
    Processing triggers for shared-mime-info (1.15-1) ...
    Processing triggers for desktop-file-utils (0.24+linuxmint1) ...
```
```    
    sudo rm /var/cache/apt/archives/lock
```
```
    ansible-playbook tools/ubuntu.yml --ask-become-pass
    BECOME password: 
    [WARNING]: provided hosts list is empty, only localhost is available. Note that the implicit localhost does not match 'all'

    PLAY [Preparing Workstation] *************************************************************************************************************************************************************************

    TASK [Gathering Facts] *******************************************************************************************************************************************************************************
    ok: [localhost]

    TASK [Installing Linux Apps] *************************************************************************************************************************************************************************
    ok: [localhost] => (item=vim)
    ok: [localhost] => (item=htop)
    ok: [localhost] => (item=curl)
    ok: [localhost] => (item=wget)
    ok: [localhost] => (item=ncdu)
    ok: [localhost] => (item=tree)
    ok: [localhost] => (item=apt-transport-https)
    ok: [localhost] => (item=ca-certificates)
    ok: [localhost] => (item=gnupg)
    ok: [localhost] => (item=python3-pip)
    ok: [localhost] => (item=make)
    ok: [localhost] => (item=git)
    ok: [localhost] => (item=bash-completion)
    ok: [localhost] => (item=gnupg-agent)
    ok: [localhost] => (item=flameshot)
    ok: [localhost] => (item=fonts-hack)
    ok: [localhost] => (item=tilix)
    ok: [localhost] => (item=virtualbox)
    changed: [localhost] => (item=terminator)
    changed: [localhost] => (item=vlc)
    changed: [localhost] => (item=simplescreenrecorder)

    TASK [Installing AWS CLI via pip3] *******************************************************************************************************************************************************************
    changed: [localhost]

    TASK [Install Google Key] ****************************************************************************************************************************************************************************
    changed: [localhost]

    TASK [Install Google Repository] *********************************************************************************************************************************************************************
    changed: [localhost]

    TASK [Install Google Chrome] *************************************************************************************************************************************************************************
    changed: [localhost]

    TASK [Installing Vagrant 2.2.10] *********************************************************************************************************************************************************************
    changed: [localhost]

    TASK [Installing Terraform 0.15.0] *******************************************************************************************************************************************************************
    changed: [localhost]

    TASK [Installing Vault 1.5.0] ************************************************************************************************************************************************************************
    changed: [localhost]

    TASK [Installing gomplate 3.7.0] *********************************************************************************************************************************************************************
    [WARNING]: The value True (type bool) in a string field was converted to 'True' (type string). If this does not look like what you expect, quote the entire value to ensure it does not change.
    changed: [localhost]

    TASK [Installing Stern 1.11.0] ***********************************************************************************************************************************************************************
    changed: [localhost]

    TASK [Install Microsoft Key] *************************************************************************************************************************************************************************
    changed: [localhost]

    TASK [Install VSCode Repository] *********************************************************************************************************************************************************************
    changed: [localhost]

    TASK [Install Visual Studio Code] ********************************************************************************************************************************************************************
    changed: [localhost]

    TASK [Install Virtual Studio Code Extensions] ********************************************************************************************************************************************************
    changed: [localhost] => (item=ms-python.python)
    changed: [localhost] => (item=ms-azuretools.vscode-docker)
    changed: [localhost] => (item=bbenoist.vagrant)
    changed: [localhost] => (item=hashicorp.terraform)
    changed: [localhost] => (item=gruntfuggly.todo-tree)
    changed: [localhost] => (item=njpwerner.autodocstring)
    changed: [localhost] => (item=eamodio.gitlens)

    TASK [Installing Kubectl 1.21.0] *********************************************************************************************************************************************************************
    changed: [localhost]

    TASK [Downloading Kubectx and Kubens] ****************************************************************************************************************************************************************
    changed: [localhost]

    TASK [Creating Symlink to kubectx and kubens] ********************************************************************************************************************************************************
    changed: [localhost] => (item=kubectx)
    changed: [localhost] => (item=kubens)

    PLAY RECAP *******************************************************************************************************************************************************************************************
    localhost                  : ok=18   changed=17   unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

```
6. History

```
    1  rm /var/cache/apt/archives/lock
    2  sudo su
    3  ls
    4  ansible-playbook tools/ubuntu.yml --ask-become-pass
    5  ps -A | grep apt
    6  sudo kill -9 31700
    7  ps -A | grep apt
    8  sudo rm /var/lib/dpkg/lock
    9  sudo dpkg --configure -a
   10  sudo rm /var/cache/apt/archives/lock
   11  ansible-playbook tools/ubuntu.yml --ask-become-pass
   12  history
```  ___

# License
GPLv3

# Author Information
Created by [Caio Delgado](https://linktr.ee/caiodelgadonew)

Contributions are more than welcome!
