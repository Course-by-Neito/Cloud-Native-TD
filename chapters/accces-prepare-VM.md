# Accessing the VM

GCP provide [more complex and supposedly secure ways](https://cloud.google.com/compute/docs/oslogin/set-up-oslogin) but we're going ot use standard SSH keys to interact with our VMs.  

To access the instance you need to get its public IP. It is displayed in the VM instances summary

![Public IP](../images/public-ip.jpg)

Then you need to connect using the private key + the user + the ip
```
ssh -i ~/.ssh/cloud_key willem.houm@34.163.9.33 
```
> I specified the user when generated the key with the -C option
# Installing Docker 

Since Docker is available on many platform, please follow the instructions [from the official site](https://docs.docker.com/engine/install/) regarding the one you are using. 

> [example for CentOS](https://docs.docker.com/engine/install/centos/)
> ```
> sudo yum install -y yum-utils
> sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
> sudo yum install docker-ce docker-ce-cli containerd.io docker-compose-plugin
> ```

> Docker compose is now embedded with Docker as a internal plugin

# Post install operations

On Linux you'll need to add your user to the docker group (created during docker installation) in order to be able to interact with the installation

## Start and enable Docker

After the install docker might not be started, to start use the system control command relative to the system you're using 

> Example for CentOS 
> ```
> sudo systemctl start docker
> sudo systemctl enable docker
> ```

## Add your user to the docker group 

For your user to interact with the docker service you'll need to [add it to the docker group](https://docs.docker.com/engine/install/linux-postinstall/)

> Example for CentOS 
> ```
> sudo systemctl start docker
> sudo systemctl enable docker
> ```

## Install Git

Optional as well but required for oh-my-zsh. And can become handy if you want to share code.

On most linux distro you just to use the package manager there is a default git repo.

> Example for CentOS 
> ```
> sudo yum install git -y
> ```

## Install oh-my-zsh

This is optional, it's the most awesome shell to use for Linux

> Example for CentOS
> ```
> sudo apt install zsh
> sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
> ```

# Conclusion 

If you've done everything well you should able to do the following command : 

```sh
➜  ~ docker ps 
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```
