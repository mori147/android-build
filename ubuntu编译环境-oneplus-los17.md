# vmtools
1.vm cd 配置为自动检测
2.Ubuntu 内部浏览器搜索 Ubuntu vmtools
3.复制命令执行
# 关闭息屏
设置 → 电源 → 屏幕休眠（Blank Screen） → 选择 “从不（Never）”
## 修改为英文
```bash
LANG=en_US xdg-user-dirs-gtk-update
```

# 代理
```bash
export http_proxy="http://192.168.2.100:7890"
export https_proxy="http://192.168.2.100:7890"

git config --global http.proxy http://192.168.2.100:7890
git config --global https.proxy http://192.168.2.100:7890
```
# repo 下载
```bash
sudo apt install repo
which repo
wget  https://storage.googleapis.com/git-repo-downloads/repo
mv 
```
# repo 初始化
```bash
repo init -u https://github.com/LineageOS/android.git -b lineage-17.1 --git-lfs --no-clone-bundle
```
# repo 同步
```bash
repo sync -c -d -j8 --no-clone-bundle --force-sync
```
# 安装依赖库
```bash
sudo apt-get install git-core gnupg flex bison gperf build-essential zip curl zlib1g-dev libc6-dev-i386 libncurses5 lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z-dev libgl1-mesa-dev libxml2-utils xsltproc unzip fontconfig m4 libssl-dev
```
## chatgpt补充
```bash
sudo dpkg --add-architecture i386
sudo apt update
sudo apt install git-core lib32z1-dev libncurses6 libncurses-dev lib32ncurses-dev zlib1g-dev libc6-dev-i386

sudo apt install g++-multilib gcc-multilib build-essential
```
# 编译启动
## 1. source
```bash
source build/envsetup.sh
```
## 2. croot
```bash
croot
```
## 3. 驱动镜像
```bash
breakfast enchilada
```
**第一次肯定会报错，解决办法在下面**
## 4. brunch
```bash
brunch enchilada
```
## 5. installer
There you’ll find all the files that were created. The two files of more interest are:

boot.img, which is the LineageOS recovery image.
lineage-22.2-20251210-UNOFFICIAL-enchilada.zip, which is the LineageOS installer package.
# 二进制驱动
此时需要手机刷好lineageos17，并连上虚拟机
## 步骤
1. adb安装
```bash
sudo apt update
sudo apt install android-tools-adb android-tools-fastboot
```
2. 进入目录
```bash
<lineage-17>
cd /device/oneplus/enchilada
```
**3.adb root**
4. 执行extract-files.sh
```bash
./extract-files.sh
```
**5.同步代码repo sync**
## 同步大文件
```bash
repo forall -c 'git lfs pull'
```


# 错误解决
权限/环境
## sload.f2fs错误
添加权限
```bash
sudo usermod -aG disk $USER
```
**需要重启**


## Build sandboxing disabled due to nsjail error
```bash
sudo gedit /usr/lib/sysctl.d/10-apparmor.conf
```
kernel.apparmor_restrict_unprivileged_userns = 0
把 1 改为 0
```bash
sudo sysctl -p /usr/lib/sysctl.d/10-apparmor.conf
```
### 第二种修复方法
```bash
sudo gedit /etc/sysctl.d/99-nsjail.conf
```
添加
```ini
kernel.unprivileged_userns_clone = 1
kernel.apparmor_restrict_unprivileged_userns = 0
```

## 增加交换内存
```bash
sudo swapoff /swap.img
sudo rm /swap.img
sudo fallocate -l 16G /swap.img
sudo chmod 600 /swap.img
sudo mkswap /swap.img
sudo swapon /swap.img
```
### 验证
```bash
swapon --show
```
### Ubuntu 内存查看
```bash
htop
```







