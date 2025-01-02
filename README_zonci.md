
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
repo init \
    --no-clone-bundle https://gitlab.com/anly8888/git-repo.git \
    --repo-rev=v2.17 \
    -u https://gitlab.com/zonci-firefly/manifests.git \
    -b zonci \
    -m poct_linux_release.xml
```

后续可以使用以下命令更新 SDK：
```
repo sync -c --no-tags
```

也可以使用以下命令切换manifests
```
repo init -b zonci -m nxtask_v1.0.xml
repo sync -c --no-tags
```

## 编译poct

poct 默认源代码目录为``~/projects/nx/poct/px``.
如果是其它目录, 需要更改buildroot配置文件.

1. 更新源代码
```
repo init -b zonci -m poct_linux_release.xml
repo sync -c --no-tags
```

2. 设置系统登录密码
```
export PASSWORD=<password>
```
对于fish, 则使用
```
set -x PASSWORD <password>
```

3. 编译
```
./build.sh poct-mipi-buildroot.mk
./build.sh
```

## 配置Buildroot

### 建立buildroot编译环境

通过poct-mipi-buildroot.mk文件我们了解到,
buildroot使用的配置文件为rockchip_rk3566.
```
# Buildroot config
export RK_CFG_BUILDROOT=rockchip_rk3566
```

在bash下, 我们也可以通过下面指令来显示buildroot配置文件.
```
source device/rockchip/.BoardConfig.mk
echo $RK_CFG_BUILDROOT
```

最后通过下面指令建立编译环境:
```
source envsetup.sh rockchip_rk3566
```

### 配置

```
cd buildroot

# 显示配置菜单
make menuconfig

# 保存默认配置
make savedefconfig
```
