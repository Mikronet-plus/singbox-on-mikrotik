# singbox-on-mikrotik

**install sing-box on mikrotik** 

**How to use singbox configs on Mikrotik router  This is very interesting, especially with the addition of Docker to Mikrotik  With the Docker container feature in the tutorial below, you can easily and without any hassle use it on Mikrotik**


youtube video:  
https://www.youtube.com/watch?v=7rJgk30xIs0

  
**Installation commands via MikroTik Docker container**

**Enter the following commands in order in the terminal**

**enable mikrotik container**

/system/device-mode/update container=yes  
/system/device-mode/print    

**Creating a virtual interface and giving it an IP address, and finally adding it to the Docker bridge and providing access to the internet**

/interface/bridge/add name=dockers  
/ip/address/add address=172.17.0.1/24 interface=dockers  
/interface/veth/add name=veth1 address=172.17.0.2/24 gateway=172.17.0.1  
/interface/bridge/port add bridge=dockers interface=veth1  
/ip/firewall/nat/add chain=srcnat action=masquerade src-address=172.17.0.0/24    

**Configuring Docker Registry Link**  

container config: https://registry-1.docker.io  

**Finally, add mounts and pull the Docker image**  
Mounts:  
src:/s-ui/db  
dst:/app/db  

Docker image : alireza7/s-ui:latest    

**Why we use this image for Docker**
**Ease of use, support for many protocols and most importantly, automatic restart after possible router reboot**

**If you have any problems, please refer to our YouTube video**  

https://www.youtube.com/@mikronet_plus

#singbox #mikrotik
