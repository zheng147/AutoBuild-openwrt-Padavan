# AutoBuild-OpenWrt-Padavan

- 定制.config文件：
- 进入工作目录输入：./scripts/diffconfig.sh > diffconfig分离出定制的插件配置，
- 输入：nano diffconfig后会列出分离后的内容
- [[StartBuild](https://github.com/zheng147/AutoBuild-openwrt-Padavan/actions?query=workflow%3A%22AutoBuild-openwrt-Padavan%22)] 

## 本地编译基本操作
- 首次编译
- cd openwrt
- ./scripts/feeds update -a
- ./scripts/feeds install -a
- make menuconfig
- 下载 dl 库，编译固件 （-j 后面是线程数，第一次编译推荐用单线程）

- make download -j8
- make V=s -j1

- 二次编译：
- cd lede
- git pull
- ./scripts/feeds update -a
- ./scripts/feeds install -a
- make defconfig
- make download -j8
- make V=s -j$(nproc)

- 如果需要重新配置：
- rm -rf ./tmp && rm -rf .config
- make menuconfig
- make V=s -j$(nproc)
- 编译完成后输出路径：bin/targets
