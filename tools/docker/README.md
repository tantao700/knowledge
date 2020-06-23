## Docker in Mac

### Configurations
System Version: macOS 10.14.3 (18D109)
Kernel Version: Darwin 18.2.0
Shell         : zsh
Package manager:    Homebrew

### TL;DR
For short, the entire installation process is as follows.

    $ brew install docker docker-machine
    
    $ brew cask install virtualbox
    -> need password
    -> possibly need to address System Preference setting
   
    $ docker-machine create --driver virtualbox default
    $ docker-machine env default
    $ eval "$(docker-machine env default)"
  
    $ docker run hello-world
    $ docker-machine stop default
    
### Step by step installation Process

Docker installation via Homebrew

    $ brew install docker
    $ docker --version
    Docker version 18.09.5, build e8ff056

