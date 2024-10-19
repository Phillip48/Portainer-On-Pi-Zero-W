# Portainer-On-Pi-Zero-W
[Portainer](https://www.portainer.io/) is your container management software to deploy, troubleshoot, and secure applications across cloud, datacenter, and Industrial IoT use cases. There are many benefits to running this on the Raspberry Pi Zero 2 W: 
1. Raspberry Pi Zero 2 W are cheap, unlike their big brothers.
2. Portainer and Docker is light weight allowing you to run multiple projects in them such as:
   * Pi-Hole
   * Hosting your own web server
   * Jellyfin
   * Etc...

## Table of Contents 
[Hardware](#hardware) <BR>
[Important links](#important-links)<BR>
[Steps To Install](#steps-to-install)<BR>
[Prerequisite](#prerequisite)<BR>

## Hardware
To build this there are a few things you'll need:
1. A Raspberry Pi Zero or Zero 2 W.
2. A USB data cable
3. Micro SD card
4. Optionally you can buy an SSD for more storage and an adapter to go with your Pi Zero.

## Prerequisite 
You'll need to do a few things before getting started:
1. You'll need to download a software to flash your micro SD card. You can use the [Raspberry Pi Imager](https://www.raspberrypi.com/software/) which is what i used.
2. Flash your micro SD card by selecting your device, the OS which will be the Raspberry Pi OS Lite (32 bit) and then the micro sd card as the storage.

## Important links
* https://docs.docker.com/engine/install/raspberry-pi-os/
* https://www.raspberrypi.com/software/

## Steps To Install
1. You'll need to install Docker on your Raspberry Pi to get started. To do that follow the instructions in the [Docker docs](https://docs.docker.com/engine/install/raspberry-pi-os/). You'll want to follow the steps called: Install using the apt repository since you'' be doing this from  the CLI.
2. Once you've completed the final steps in the docs which is: `sudo docker run hello-world`. You run that to make sure the install worked. Once that is done we can install Portainer.
3. We'll want to make sure everything is upto date:
`sudo apt update && sudo apt upgrade`
4. Now we want to install Portainer:
`sudo docker pull portainer/portainer-ce:latest`
5. Now that it's installed we'll want to run it:
`sudo docker run -d -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest`
  * A few of the things we do here is first define the ports we want Portainer to have access to. In our case, this will be port 9000. We also assign this docker container the name “portainer” so we can quickly identify it if we ever needed. Lastly, we also tell the Docker manager that we want it to restart this Docker if it is ever unintentionally offline.
6. After following those steps you're ready to use Portainer. If you dont know the hostname of your pi you can find out by running `hostname` in your terminal. Alternatively you can run `hostname -I` to find the ip address assigned to the pi.
7. In a browser type 
`http://[PIIPADDRESS]:9000` or `http://[PIHOSTNAME]:9000`
8. Create a user and you should be good to go.
