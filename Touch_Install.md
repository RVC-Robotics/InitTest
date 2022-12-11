# 3D Systems Geomagic Touch ROS Drivers and Applications
ROS Packages for **3D Systems** **Geomagic Touch** haptic device.

Then we will explore some interesting applications with UR3 robot which is to be continued.

___

## 1. Installation (Touch Driver and OpenHaptics)

*Environment*: Ubuntu 18.04

1. Download Touch Driver [here](https://s3.amazonaws.com/dl.3dsystems.com/binaries/Sensable/Linux/TouchDriver2019_2_15_Linux.tar.xz) . 

   Problem: the newest driver provided by the official is based on ubuntu 20.0, and It requires higher version **GLIBC_2.29** of `/lib/x86_64-linux-gnu/libm.so.6`. 

   see the version your system support`strings /lib/x86_64-linux-gnu/libm.so.6 | grep GLIBC_`

```bash
# extract file 
x TouchDriver2019_2_15_Linux.tar.xz
# copy two executable file to /usr/local/bin 
sudo cp bin/Touch* /usr/local/bin 
# copy driver lib to the default /usr/lib
sudo cp usr/lib/libPhantomIOLib42.so /usr/lib
# Create and configure shared directory for configuration files
sudo mkdir -p /usr/share/3DSystems/config
sudo chmod 777 config
# Create profile.d configurationfile
echo "export GTDD_HOME=/usr/share/3DSystems" > 3ds-touch-drivers.sh
sudo cp 3ds-touch-drivers.sh /etc/profile.d/3ds-touch-drivers.sh
# Removing temporary files
rm -rf TouchDriver2019_2_15_Linux*
# Then you can run Touch_Setup and Touch_Diagnostic
Touch_Setup or Touch_Diagnostic

# Set permission for each com port
sudo chmod 777 /dev/ttyACM0
# or add yourself to the "dialout" permission group 
sudo adduser carrot dialout
```

2. Download OpenHaptics v3.4 from [3D System Support Center.](https://support.3dsystems.com/s/article/OpenHaptics-for-Linux-Developer-Edition-v34?language=en_US)

```bash
# install OpenHaptics SDK 
tar zxvf openhaptics_3.4-0-developer-edition-amd64.tar.gz
# run install bash
sudo ./install
# destination folder: /opt/OpenHaptics/Developer/3.4-0/
# Dependencies to compile/run OpenHaptics applications
sudo apt install libncurses5-dev freeglut3-dev zlib1g-dev

# SETTING ENVIRONMENT VARIABLES by default
echo "export OH_SDK_BASE=/opt/OpenHaptics/Developer/3.4-0" > /etc/profile.d/openhaptics.sh
```

### Ref Link

1. [3ds-touch-openhaptics-Github (how to install driver)](https://github.com/jhu-cisst-external/3ds-touch-openhaptics)
2. [ubuntu18.04 update GLIBC_2.29](https://www.cnblogs.com/chenyirong/p/16342370.html)

##  2. ROS Driver

The Touch ROS driver is originally forked from Francisco Suárez Ruiz [phantom_omni](https://github.com/fsuarez6/phantom_omni). 



## 3. Applications with UR3

### 3.1 Tele-operation

to be continued...





