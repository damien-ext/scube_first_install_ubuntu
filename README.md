# scube_first_install_ubuntu

## 1 : Install Dependencies Ubuntu 

**from: https://docs.docker.com/engine/security/rootless/**

```zsh
echo 'install docker stuff'
curl -fsSL https://get.docker.com | sudo bash


echo 'setup docker to be rootless'
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
sudo systemctl disable --now docker.service docker.socket
sudo rm /var/run/docker.sock
sudo apt-get install -y uidmap
dockerd-rootless-setuptool.sh install

echo "path+=('/usr/bin')" > ~/.zshrc 
echo 'export DOCKER_HOST=unix:///run/user/1000/docker.sock' > ~/.zshrc

echo 'install build stuff like make'
sudo apt-get install build-essential

echo 'install scube mise en place'
curl https://mise.run | sh

```


## 2 : AWS CLI
- [To configure AWS CLI in your environment to use the SRE platform, follow ](https://cip.docs.safran-ai.tech/how-to/cloud-aws/connect_platform) ACCESS NOT GRANTED