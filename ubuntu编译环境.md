# vmtools
## vm cd 配置为自动检测
## Ubuntu 内部浏览器搜索 Ubuntu vmtools
复制命令执行
## 关闭息屏

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

# 二进制驱动
https://source.android.com/docs/setup/reference/build-numbers?hl=zh-cn#build-ids-defined

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
## 步骤
```bash
source build/envsetup.sh
export TARGET_RELEASE=trunk_staging
ap2a
bp1a（or trunk_staging）
build_build_var_cache
lunch
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







