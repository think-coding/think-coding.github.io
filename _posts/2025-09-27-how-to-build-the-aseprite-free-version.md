---
layout: post
title: 如何编译像素画制作软件 Aseprite 的 MacOS 免费版本
tags: [aseprite, Markdown]
feature-img: "assets/img/feature-img/aseprite-banner.png"
thumbnail: "assets/thumbnails/feature-img/aseprite-banner.png"
author: think-coding
categories: Document
---
aseprite 是一款好评如潮的像素画制作软件，它代码开源，在官网($20)和Steam($15)平台有商业版在售。
它同时支持用户编译源码，作为免费版本使用，但是由于编译过程繁琐、复杂劝退了很多人，如果你在找macOS上的编译方法，这篇笔记可作为参考。

# 1. 说明
- 编译 aseprite 版本需要 skia 库
- 编译后 aseprite 是可执行程序，开发版
- 使用个人编译的 aseprite 制作的像素图，可以用于免费商业用途：）

# 2. 编译平台
- MacOS

# 3. 编译流程
1. 编译 skia 库
2. 编译 aseprite 库

# 4. 编译skia库
## 4.1. 仓库地址
[https://github.com/aseprite/skia](https://github.com/aseprite/skia)


## 4.2. 下载 & 编译
```bash
mkdir $HOME/deps
cd $HOME/deps
git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git
git clone -b aseprite-m124 https://github.com/aseprite/skia.git
export PATH="${PWD}/depot_tools:${PATH}"  # 确保 depot_tools 中的工具优先使用
cd skia
python3 tools/git-sync-deps  # 同步依赖（关键步骤，确保第三方库完整）
# 生成 arm64 架构的 Release 配置（适配 M 系列芯片）
gn gen out/Release-arm64 --args="
  is_debug=false 
  is_official_build=true 
  skia_use_system_expat=false 
  skia_use_system_icu=false 
  skia_use_system_libjpeg_turbo=false 
  skia_use_system_libpng=false 
  skia_use_system_libwebp=false 
  skia_use_system_zlib=false 
  skia_use_freetype=true 
  skia_use_harfbuzz=true 
  skia_pdf_subset_harfbuzz=true 
  skia_use_system_freetype2=false 
  skia_use_system_harfbuzz=false 
  target_cpu=\"arm64\"  # 匹配 M 系列芯片架构
  extra_cflags=[\"-stdlib=libc++\", \"-mmacosx-version-min=11.0\"]  # 提升最低版本
  extra_cflags_cc=[\"-frtti\"]
"
# 编译 Skia（-j 后接 CPU 核心数加速编译，如 8 或 12）
ninja -C out/Release-arm64 skia modules -j 8
```

# 5. 编译 aseprite
## 5.1. 仓库地址
[https://github.com/aseprite/aseprite.git](https://github.com/aseprite/aseprite.git)

## 5.2. 下载 & 编译
```bash
git clone https://github.com/aseprite/aseprite.git
cd aseprite
mkdir build
cd build
cmake \
    -DCMAKE_BUILD_TYPE=RelWithDebInfo \
    -DCMAKE_OSX_ARCHITECTURES=arm64 \
    -DCMAKE_OSX_DEPLOYMENT_TARGET=11.0 \
    -DCMAKE_OSX_SYSROOT=/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX.sdk \
    -DLAF_BACKEND=skia \
    -DSKIA_DIR=$HOME/deps/skia \
    -DSKIA_LIBRARY_DIR=$HOME/deps/skia/out/Release-arm64 \
    -DSKIA_LIBRARY=$HOME/deps/skia/out/Release-arm64/libskia.a \
    -DPNG_ARM_NEON:STRING=on \
    -G Ninja \
    ..
ninja aseprite
```

## 5.3. 移动程序目录并启动
### 5.3.1. 程序目录位置及文件
```bash
[~/Downloads/Aseprite-v1.3.15.3-Source/build/bin] 
└─[$]> tree --dirsfirst -L 1

├── data
├── aseprite
├── gen
└── icudtl.dat
```

### 5.3.2. 移动文件到程序目录
```bash
cd ~
mkdir aseprite-1.3.15.3-dev
cp -r ~/Downloads/Aseprite-v1.3.15.3-Source/build/bin/* ~/aseprite-1.3.15.3-dev/
```

### 5.3.3. 替换图标
- 此时 aseprite 的图标是可执行文件，非常不友好
- 选中 `/Aseprite-v1.3.15.3-Source/data/icons/ase256.png`
- 【command + C】复制
- 选中 `~/aseprite-1.3.15.3-dev/aseprite`
- 【command + i】显示简介
- 选中简介中左上角图标，【command + v】粘贴

### 5.3.4. 制作替身（创建快捷方式）并修改图标，放到桌面等位置

### 5.3.5. 运行 aseprite 文件启动
此时语言是英文，且设置中无其他语言可选

# 6. 翻译程序
## 6.1. 翻译文本仓库地址
https://github.com/aseprite/strings

## 6.2. 导入本地化文化
```bash
git clone https://github.com/aseprite/strings.git
cp -r strings/* ~/aseprite-1.3.15.3-dev/data/strings
```

# 7. 重新运行就是完美的汉化版了
{% include aligner.html images="screenshot/aseprite-1.3.15.3-dev.png" column=1 caption="汉化完成啦！" %}