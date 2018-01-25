# enable unix subsystem

appwiz.cpl

#enable new function

linux sub system

#update system & install zsh

apt-get update 

sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)" 

#download min cmder

https://github.com/cmderdev/cmder/releases/download/v1.3.4/cmder_mini.zip

#setting cmder startup ,command line

bash.exe ~ -c zsh -cur_console:p:n

#install docker client

curl https://releases.rancher.com/install-docker/17.03.sh | sh

#export remote docker engine 

echo "export DOCKER_HOST=tcp://192.168.207.4:2375" >> ~/.zshrc

source ~/.zshrc

#do a test

docker images

