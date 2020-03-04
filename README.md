# Insurgency Server Setup Guide
This guild is trying to show how to setup up an Insurgency dedicated server.

## 1. Hardware Requirement
To run a private dedicated server for cooperation game with your friends (3-6), <br>
believe it or not, the following machine (Linux exclusive) is good enought:
* 1 CPU core
* 2 GB Ram
* ~10 GB hard disk

Remember in your firewall and router setting:
* open 27015 UDP/TCP
* port forward for 27015 UDP/TCP, in the router, if any

## 2. Step up on Windows Environment
To host an Insurgency dedicated server on Windows machine, please do the following step by step -

### 2.1 Software Requirments
First of all, please install Microsoft Visual C++ 2010 Redistributable Package (x86): <br>
https://www.microsoft.com/en-us/download/details.aspx?id=5555

Then download SteamCMD by clicking: <br>
http://media.steampowered.com/installer/steamcmd.zip

In here, we unzip the file to the path of `C:/SteamCMD`	(change the path by yourself)

### 2.2 Insurgency Installation via SteamCmd
clicking the following exe to run SteamCMD:

``` shell
C:/SteamCMD/steamcmd.exe
```

After that, entering the following cmd to download Insurgency:

``` shell
login anonymous
force_install_dir ./insServer/ 
app_update 237410 validate
......(downloading ~10GB file; better to taste a coffee)
exit
```

### 2.3. Config Setting
You, at least, need to config the server setting before we go:
- [x] `C:\InsServer\insurgency\cfg\server.cfg`

Optionally, you also can edit the following config:
- [x] (optional) `C:\InsServer\insurgency\cfg\server_checkpoint.cfg`
- [x] (optional) `C:\InsServer\insurgency\mapcycle_cooperative.txt`
- [x] (optional) `C:\InsServer\insurgency\motd.txt`

### 2.4. Starting Batch Creation
Create the following file: <br>
`C:\InsServer\start.bat`

Enter the follwong cmd in the file: <br>
(please change the path, ip, port, player no. and startig map, according to your environment)

``` shell
start srcds.exe -usercon +maxplayers 24 +sv_lan 0 +map " sinjar_coop" -ip xxx.xxx.xxx -port yyyyy(e.g. 27015)
```

### 2.5. Kick Server
To kick the server, simple click the batch you created perviously: <br>
`C:\InsServer\start.bat`

then make sure the server is running and no error occurred.

## 3. Step up on Linux Environment
The following steps are based on Ubuntu 18.04 LTS. <br/>
To host Insurgency server on a Linux machine, please do the following step by step -

### 3.1 Software Requirments
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

### 3.2 Insurgency Installation via SteamCmd
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

### 3.3. Config Setting
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

### 3.4. Starting Script Creation
To be convenient, we create a script before kicking the server:
``` shell
cd ~/SteamCmd/insServer/ 
touch start.sh
chmod 744 start.sh
vi start.sh
```
(please change the path, ip, port, player no. and startig map, according to your environment)
```xml
export LD_LIBRARY_PATH=~/SteamCmd/insServer:~/SteamCmd/insServer/bin:{$LD_LIBRARY_PATH}
./srcds_linux -console +map ministry_coop +maxplayers 32 -ip xxx.xxx.xxx -port yyyyy(e.g. 27015)
```
### 3.5. Kick Server
To kick the server., run the following cmd:
``` shell
cd ~/SteamCmd/insServer/ 
./start.sh
```
then make sure the server is running and no error occurred.

ENJOY!

:100:

