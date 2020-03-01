# Insurgency Server Setup Guide
This guild is trying to show how to setup up an Insurgency dedicated server.

## 1. hardware requirement
To run a private dedicated server for cooperation game with your friends (3-6), <br>
believe it or not, the following machine (Linux exclusive) is good enought:
* 1 CPU core
* 2 GB Ram
* ~10 GB hard disk

Remember in your firewall and router setting:
* open 27015 UDP/TCP
* port forward for 27015 UDP/TCP, in the router, if any


## 2. Step up on Linux Environment
The following steps are based on Ubuntu 18.04 LTS. <br/>
To host Insurgency server on a Linux machine, please do the following step by step -

### 2.1 Software requirments
run the following commend to keep the system up-to-date:

``` shell
apt-get update
apt-get upgrade
```

then install all of the necessary packages:

``` shell
apt-get install lib32gcc1 
apt-get install lib32ncurses5
apt-get install lib32z1 
apt-get install lib32gomp1
apt-get install lib32quadmath0 
apt-get install lib32stdc++6 
apt-get install lib32tinfo5
apt-get install libc6-dev-i386 
apt-get install screen
apt-get install nano
```

create a folder to install SteamCmd:
(in here, using `~/SteamCmd`)

``` shell
cd ~/
mkdir SteamCmd
cd SteamCmd
```

### 2.2 Insurgency Installation via SteamCmd
download SteamCmd firstly:

``` shell
cd ~/SteamCMD
wget http://media.steampowered.com/installer/steamcmd_linux.tar.gz 
tar xvfz steamcmd_linux.tar.gz
```

run SteamCMD so as to download Insurgency Server file:

``` shell
./steamcmd.sh
```
``` shell
login anonymous
force_install_dir ./insServer/ 
app_update 237410 validate
......(downloading ~10GB file; better to taste a coffee)
exit
```

### 2.3. Config Setting
You, at least, need to config the server setting before we go:
``` shell
cd ~/SteamCmd/insServer/insurgency/cfg
vi server.cfg
```

Optionally, if you are going to play checkpoint, you can edit:
``` shell
(optional)
vi ~/SteamCmd/insServer/insurgency/cfg/server_checkpoint.cfg
vi ~/SteamCmd/insServer/insurgency/mapcycle_cooperative.txt
```
Optionally, the following file is the server message:
``` shell
(optional)
cd ~/SteamCmd/insServer/insurgency/
vi motd.txt
```

### 2.4. Starting Script Creation
To be convenient, we create a script before kicking the server:
``` shell
cd ~/SteamCmd/insServer/ 
touch start.sh
chmod 744 start.sh
vi start.sh
```
(please change the path, ip, port, player no. and startig map,  according to your environment)
```xml
export LD_LIBRARY_PATH=~/SteamCmd/insServer:~/SteamCmd/insServer/bin:{$LD_LIBRARY_PATH}
./srcds_linux -console +map ministry_coop +maxplayers 32 -ip <your ip> -port <your port, for example 27015>
```
### 2.5. Kick Server
To kick the server., run the following cmd:
``` shell
cd ~/SteamCmd/insServer/ 
./start.sh
```
then make sure the server is running and no error occurred.

ENJOY!:100:

