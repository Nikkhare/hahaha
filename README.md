# MERN: Full-stack Chat Application

#### Introduction

The MERN stack which consists of **Mongo DB**, **Express.js**, **Node.js**, and **React.js** is a popular stack for building full-stack web-based applications because of its simplicity and ease of use. In recent years, with the explosive popularity and the growing maturity of the JavaScript ecosystem, the MERN stack has been the goto stack for a large number of web applications. This stack is also highly popular among newcomers to the JS field because of how easy it is to get started with this stack.
<br/><br/>
This repo consists of a **Chat Application** built with the MERN stack. I built this sometime back when I was trying to learn the stack and I have left it here for anyone new to the stack so that they can use this repo as a guide.
<br/><br/>
This is a full-stack chat application that can be up and running with just a few steps. 
Its frontend is built with [Material UI](https://material-ui.com/) running on top of React.
The backend is built with Express.js and Node.js.
Real-time message broadcasting is developed using [Socket.IO](https://socket.io/).

### Features

This application provides users with the following features
<br/>
* Authentication using **JWT Tokens**
* A **Global Chat** which can be used by anyone using the application to broadcast messages to everyone else.
* A **Private Chat** functionality where users can chat with other users privately.
* Real-time updates to the user list, conversation list, and conversation messages

#### Screenshots

##### Global Chat
![Global Chat](https://i.imgur.com/VkdwAme.png)
<br/><br/>
##### Private Chat
![Private Chat](https://i.imgur.com/jdCBYu4.png)
<br/><br/>
##### Login
![Login](https://i.imgur.com/6iobucn.png)
<br/><br/>
##### Register
![Register](https://i.imgur.com/AMkpl9C.png)

### How to use

You can have this application up and running with just a few steps because it has both the frontend and the backend in a single repository. Follow the steps below to do so.

1. Clone this repo
2. Once you have the repo, you need to install its dependencies. So using a terminal, move into the root directory of the project and execute `npm install` to install the dependencies of the Node.js server and then run `npm run client-install` to install the dependencies of the frontend. The second command is a custom command that I wrote to simplify the installation process.
3. This application uses MongoDB as its Database. So make sure you have it installed. You can find detailed guides on how to do so [here](https://docs.mongodb.com/manual/administration/install-community/). Once installed, make sure that your local MongoDB server is not protected by any kind of authentication. If there is authentication involved, make sure you edit the `mongoURI` in the `config/keys.js` file.
4. Finally, all you have to do is simply run `npm run dev`. If this command fails, try installing the package [concurrently](https://www.npmjs.com/package/concurrently) globally by running `npm install -g concurrently` and then running the `dev` command.
5. The frontend of the application will be automatically opened in your web browser and you can test it away.


### Things to note

* The frontend is created using [create-react-app](https://github.com/facebook/create-react-app)
* Database connections in the backend are handled using the [Mongoose ORM](https://mongoosejs.com/)
* Code quality is ensured using (ESLint)[https://eslint.org/]

### Disclaimer

This repository contains beginner level code and might contain some things I wish to change or remove. I have not maintained this for quite some time, but now I am trying to slowly fix these issues. You are welcome to open issues if you find any and I will accept PR's as well.
<br/><br/>

Cheers 💻 🍺 🔥 🙌



#HOW TO DEPLOY HYPERLEDGER FABRIC 2.0 NETWORK
#Prerequisites
## install curl wget and git
sudo apt update
sudo apt install curl wget git

## install python
## this command will install python 2.7
sudo apt install python
## this will install python version 3.6
sudo apt update && apt install -y build-essential flex bison wget subversion m4 python3 python3-dev python3-setuptools libgmp-dev libssl-dev

## install go
### download file
wget https://dl.google.com/go/go1.14.2.linux-amd64.tar.gz
### extract file to home directory
tar xvzf go1.14.2.linux-amd64.tar.gz
### extract file to /usr/local 
sudo tar -C /usr/local -xzf go1.14.2.linux-amd64.tar.gz
###add these export to ~/.bashrc file
sudo gedit ~/.bashrc
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin
###save and exit

##install nvm npm nodejs
### install nvm this will download .nvm hidden folder
git clone https://github.com/creationix/nvm.git
sudo mv nvm .nvm
cd ~/.nvm && git checkout v0.34.0 
. nvm.sh

###add this to ~/.bashrc
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion" # This loads nvm bash_completion
##Save and exit
nvm --version
##install node
nvm install v11.10.0 
nvm use node v11.10.0
## make that version default
nvm alias default v11.10.0 

##install npm
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.35.2/install.sh | bash
npm install npm@5.6.0 -g

##install nodejs
##this will install nodejs v12.22.12
sudo apt-get install nodejs 

##docker
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common gnupg lsb-release

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
sudo apt update
## this command is use to check available version
apt-cache madison docker-ce 
### can choose the version we want, sudo apt-get install docker-ce= docker-ce-cli= containerd.io docker-compose-plugin
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
### test if docker is working
sudo docker run hello-world
### check docker version 
docker -v

#Hyperledger Fabric 2.0
##if it is not working, use root user to download the images
##curl -sSL https://bit.ly/2ysbOFE | bash -s — 
cd ~
mkdir hyperledger
cd hyperledger
curl -sSL https://bit.ly/2ysbOFE | bash -s 2.0.1 1.4.6 0.4.18

#Go to fabric-samples/test-network
## If it can not find the docker image, it will pull immediately
## Need to pull hyperledger/fabric-tools:latest hyperledger/fabric-peer:latest
##
sudo docker pull hyperledger/fabric-tools:latest
sudo docker pull hyperledger/fabric-peer:latest

cd ~/hyperledger/fabric-samples/test-network/
sudo ./network.sh up
sudo ./network.sh createChannel -c mychannel
sudo ./network.sh deployCC
sudo ./network.sh down

//Install docker-compose
sudo apt install docker-compose

//Pull hyperledger docker images version 2.2.2
docker pull hyperledger/fabric-tools:2.2.2
docker pull hyperledger/fabric-peer:2.2.2
docker pull hyperledger/fabric-orderer:2.2.2
docker pull hyperledger/fabric-ca:1.4.9
docker pull hyperledger/fabric-ccenv:2.2.2
docker pull hyperledger/fabric-baseos:2.2.2

//Rename orderer to the latest version
docker tag hyperledger/fabric-orderer:2.2.2 hyperledger/fabric-orderer:latest
sudo ./network.sh up

//start network
sudo ./network.sh up 

//create channel
sudo ./network.sh createChannel -c mychannel 
//install smart contract only install one of the following language 
//install smart contract in go language
sudo ./network.sh deployCC -ccn basic -ccp ../asset-transfer-basic/chaincode-go -ccl go
//install smart contract in nodejs javascript language
sudo ./network.sh deployCC -ccn basic -ccp ../asset-transfer-basic/chaincode-javascript -ccl javascript

//check if the smart contract container successfully created
docker ps

