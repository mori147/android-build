# vmtools
## vm cd 配置为自动检测
## Ubuntu 内部浏览器搜索 Ubuntu vmtools
复制命令执行
## 关闭息屏
## 修改为英文
```bash
LANG=en_US xdg-user-dirs-gtk-update
```

# 代理
```bash
export http_proxy="http://192.168.0.100:7890"
export https_proxy="http://192.168.0.100:7890"

git config --global http.proxy http://192.168.0.100:7890
git config --global https.proxy http://192.168.0.100:7890
```

# repo 下载
```bash
sudo apt install repo
which repo
wget  https://storage.googleapis.com/git-repo-downloads/repo
mv 
```

# 查看安卓版本
https://source.android.com/docs/setup/reference/build-numbers?hl=zh-cn#build-ids-defined

# repo 初始化
```bash
repo init -u https://android.googlesource.com/platform/manifest -b android-14.0.0_r73
```

# repo 同步
```bash
repo sync -c -d -j8 --no-clone-bundle --force-sync
```
AP2A.240905.003.F1

# 二进制驱动
https://source.android.com/docs/setup/reference/build-numbers?hl=zh-cn#build-ids-defined
https://developers.google.com/android/drivers?hl=zh-cn

# 安装依赖库
```bash
sudo apt-get install git-core gnupg flex bison gperf build-essential zip curl zlib1g-dev libc6-dev-i386 libncurses5 lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z-dev libgl1-mesa-dev libxml2-utils xsltproc unzip fontconfig
```
## chatgpt补充
```bash
sudo dpkg --add-architecture i386
sudo apt update
sudo apt install git-core lib32z1-dev libncurses6 libncurses-dev lib32ncurses-dev zlib1g-dev libc6-dev-i386

sudo apt install g++-multilib gcc-multilib build-essential
```


# sload.f2fs错误
添加权限
```bash
sudo usermod -aG disk $USER
```
需要重启

## 废弃
```bash
sload.f2fs -V
wget  https://git.kernel.org/pub/scm/linux/kernel/git/jaegeuk/f2fs-tools.git/snapshot/f2fs-tools-1.14.0.tar.gz
tar -xzf f2fs-tools-1.14.0.tar.gz
cd f2fs-tools-1.14.0

sudo apt install autoconf libtool pkg-config libuuid1 uuid-dev

./autogen.sh
./configure
make
sudo make install
sudo ldconfig
sload.f2fs -V
```

## 解压到 repo根目录执行

# 编译
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
## 步骤
```bash
source build/envsetup.sh
export TARGET_RELEASE=ap2a
ap2a
bp1a（or trunk_staging）
build_build_var_cache
lunch aosp_oriole-ap2a-user
lunch aosp_oriole-ap2a-userdebug
m -j 4
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







