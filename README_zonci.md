
# 获取SDK

## XML 介绍
以rk356x为例子：

* rk356x_linux_release.xml SDK的 release 版本
* rk356x_linux_next.xml SDK的开发版本
* rk356x_linux_bsp_release.xml bsp的 release 版本
* rk356x_linux_bsp_next.xml bsp的开发版本


## 拉取SDK
```
mkdir ~/firefly
cd ~/firefly

## 完整 SDK
repo init --no-clone-bundle https://gitlab.com/anly8888/git-repo.git --repo-rev=v2.17 -u https://gitlab.com/zonci-firefly/manifests.git -b zonci -m poct_linux_release.xml
```

后续可以使用以下命令更新 SDK：
```
repo sync -c --no-tags
```

也可以使用以下命令切换manifests
```
repo init -b zonci -b nxtask_v1.0.xml
repo sync -c --no-tags
```
