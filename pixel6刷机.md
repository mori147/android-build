
# 最最最重要的：一定一定要确保先把 bootloader 分区的两个 slot 都刷到最新的 bootloader，
且一样的。这里重启到 bootloader 下，
执行这条命令 
```base
fastboot --slot all flash bootloader bootloader-oriole-slider-16.2-13291547.img
```

# 降级
接着，将 image-oriole-xxxx.xxxxxxxx.xxx.zip 解压，修改其中的 android-info.txt
删除其中的以下两行：

require version-baseband=g5123b-130914-240205-B-11405587

require version-bootloader=slider-1.x-xxxxxxxx





