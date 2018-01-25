# download virtualbox

# enable DHCP for HostOnly NIC

# download ubuntu server 

#create a vm with two nic

nic1:for nat

nic2:for HostOnly

# install ubuntu server

#flush system software list & install zsh

apt-get update 

sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)" 

#install docker

curl https://releases.rancher.com/install-docker/17.03.sh | sh

#add daemon configuration file ,enable remote API access
 
sudo tee /etc/docker/daemon.json <<-'EOF'  



{   
   
  "hosts": [     "tcp://0.0.0.0:2375",     "fd://"   ]

}



EOF


sed -i 's/-H fd:\/\///g' /etc/systemd/system/multi-user.target.wants/docker.service 

sudo systemctl daemon-reload 

sudo systemctl restart docker


#export remote docker engine,change ip with your hostOnly network interface

echo "export DOCKER_HOST=tcp://192.168.207.4:2375" >> ~/.zshrc

source ~/.zshrc

#do a test 

docker pull nginx

