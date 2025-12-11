
# 救砖
https://pan.baidu.com/s/1p4hHpt5w7ljB2mVLY6pBLQ?dp-logid=97939000464486240002&pwd=dxam#/home/%2F/%2F
## 步骤
1.拔掉数据，确定关机
2.同时按住音量+-键，插上数据线
3.启动线刷工具

# 解锁
1.打开usb调试
2.开启oem远程
3.执行命令
```bash
adb reboot bootloader
fastboot oem unlock
```
4.同意


# 低版本刷机
### lineageos刷机包下载
https://lineage-archive.timschumi.net/
## 代号
```
enchilada
```
## 镜像提取
残芯专用TWRPRecovery入工具Win版V2.3.exe

## 刷入
1.boot
```
fastboot boot boot.img
```
2.重启到rec模式
在设备上，点选 “Apply Update”，然后点选 “Apply from ADB” 以开始 sideload 。
**3.刷入copy**
```
adb -d sideload copy-partitions-20210323_1922.zip
```
4.现在通过点按 “Advanced” 重启至 recovery 模式，然后点按 “Reboot to recovery”
5.刷机
选择usb apply
```
adb -d sideload lineageos.zip
```
6.格式化

