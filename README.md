<div align="right">
  Language:
  <a title="English" href="./README.en-US.md">🇺🇸</a>
  🇨🇳
</div>
# Termux-MTKClient
手机Termux部署MTKClient无需chroot容器！
手机有root权限就可以，完美部署！
# MTKClient 是联发科 mtk处理器的刷机工具箱!
可以包括不限于 救砖 强解 秒解bl(mtk1200以下) 刷root rec 提取分区等等功能!
今天教大家如何在手机Termux上部署MTKClient!
无需chroot容器! 只要你手机有root权限就可以!
这里以Termux 0.118.2版本演示!
# 如何部署
# 第一步换源：
sed -i 's@^\(deb.*stable main\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/termux-packages-24 stable main@' $PREFIX/etc/apt/sources.list && apt update && apt upgrade -y
# 第二步给Termux文件权限:

termux-setup-storage

没反应就手动给文件权限!
# 第三步安装必要组件依赖:

pkg install git sudo android-tools python3 libusb

# 第四步安装部署MTKClient:

git clone --branch 1.52 https://github.com/bkerler/mtkclient.git

这一步需要特殊网络环境!
克隆不了!也可以下载1.52版本解压到/data/user/0/com.termux/files/home/目录下!

克隆完成然后cd打开MTKClient目录

cd mtkclient

先安装依赖：

pip3 install setuptools

在继续部署MTKClient:

pip3 install -r requirements.txt

python3 setup.py build

python3 setup.py install

安装部署好可以输入命令测试一下

sudo python mtk

每次使用MTKClient都需要先cd mtkclient目录!
就能正常使用了!

比如给 联发科 天机 mtk 1200以下处理器解bl 命令
sudo python mtk xflash seccfg unlock

因为不是在chroot容器部署的!每次输入命令，前面必须加sudo以root环境执行命令!不然会报错!

# MTKClient https://github.com/bkerler/mtkclient/tree/1.52
