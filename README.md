# Insurgency Server Setup Guide
This guild is trying to show how to setup up a Insurgency dedicated server.

## 1. Step up on Linux Environment
The following steps are based on Ubuntu 18.04 LTS. <br/>
To host Insurgency server on a Linux machine, please do the following step by step -

### 1.1 Software requirments
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

### 1.2 Insurgency Installation via SteamCmd
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

### 1.3. Config Setting
You, at least, need to config the server setting before we go:
``` shell
cd /SteamCmd/insServer/insurgency/cfg
vi server.cfg
```



