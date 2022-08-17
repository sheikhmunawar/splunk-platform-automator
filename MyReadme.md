# Setup Windows Subsystem for Linux (WSL2)
https://github.com/sheikhmunawar/splunk-platform-automator#framework-installation

## Vagrant Installation
```
# Vagrant must be installed within the Linux distribution used with WSL. While the vagrant.exe
https://releases.hashicorp.com/vagrant/2.3.0/vagrant_2.3.0_windows_amd64.msi

# Download the installer package for the Linux distribution from the releases page and install Vagrant.
# Ubuntu
wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install vagrant
```
## Install virtual box

## Setup Windows Subsystem for Linux (WSL2)
To allow vagrant to talk to virtualbox follow the steps below.

Create /etc/wsl.conf and reboot WSL (wsl --shutdown)
```
[automount]
options = "metadata"
```
Enable WSL2 port forwarding by installing a vagrant plugin with: 
```
vagrant plugin install virtualbox_WSL2

Add Environment Variables in WSL (maybe to your ~/.bashrc ~/.zshrc)
export VAGRANT_WSL_ENABLE_WINDOWS_ACCESS="1"
export PATH="$PATH:/mnt/c/Program Files/Oracle/VirtualBox"
```

## install Python3.9
```
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt install python3.9
python3.9 --version

```
## Framework Installation
```
cd /home/munawar/working/splunk
git clone https://github.com/splunk/splunk-platform-automator.git
cd splunk-platform-automator

```



## Create vitualenv for specific Ansible version
```
sudo apt install python3.9-dev python3.9-venv
python3.9 -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install ansible
ansible --version
exit and login again
```
## Install needed python libraries
You must install some additional modules for Splunk Platform Automator to work
```
pip install jmespath # required for json_query calls
pip install lxml     # required for license file checks
pip install boto3    # required for ec2 (aws) plugin
```