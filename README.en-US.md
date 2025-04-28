<div align="right">
  Language:
  🇺🇸
  <a title="Chinese" href="./README.md">🇨🇳</a>
</div>
# Termux-MTKClient  
Deploy MTKClient on Termux without chroot containers!  
Only requires root access on your phone - perfect deployment!  

# MTKClient is a Mediatek (MTK) processor flashing toolkit!  
Supports functions including but not limited to:  
Brick recovery | Forced unlock | Instant BL unlock (for MTK1200 and below) | Flash Root/Recovery | Partition extraction | etc!  
Today we'll learn how to deploy MTKClient on Termux!  
No chroot container needed! Just root access required!  
Demo using Termux 0.118.2 version!  

# How to Deploy  
# Step 1: Change Repository Mirror:  
sed -i 's@^\(deb.*stable main\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/termux-packages-24 stable main@' $PREFIX/etc/apt/sources.list && apt update && apt upgrade -y  

# Step 2: Grant Termux File Permissions:  
termux-setup-storage  

If no response, manually grant file permissions!  

# Step 3: Install Required Components:  
pkg install git sudo android-tools python3 libusb  

# Step 4: Install MTKClient:  
git clone --branch 1.52 https://github.com/bkerler/mtkclient.git  

This step requires special network environment!  
If cloning fails! Manually download v1.52 and extract to /data/user/0/com.termux/files/home/ directory!  

After cloning, cd to MTKClient directory:  
cd mtkclient  

First install dependencies:  
pip3 install setuptools  

Continue deploying MTKClient:  
pip3 install -r requirements.txt  
python3 setup.py build  
python3 setup.py install  

After installation, test with command:  
sudo python mtk  

Every time you use MTKClient, first cd to mtkclient directory!  
Then you can use it normally!  

Example command to unlock BL for Mediatek Dimensity/MTK 1200 and below:  
sudo python mtk xflash seccfg unlock  

Because it's not deployed in chroot container! You must add sudo before commands for root execution! Otherwise errors occur!  

# MTKClient https://github.com/bkerler/mtkclient/tree/1.52
