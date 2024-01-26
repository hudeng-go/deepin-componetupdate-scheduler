# deepin-componetupdate-scheduler



## 项目名称

实现Deepin系统组件更新调度算法,更新操作包括组件增加、删除以及版本更新

## **项目描述**

deepin系统层的组件存在复杂的依赖关系，因此组件任何的变更都需要做很多相关依赖组件的准备工作，而这些准备工作需要尽可能的分析依赖组件带来的影响，该算法就是为了帮助做这些准备工作，让系统组件更新的问题尽可能的在源码更新阶段解决，并对接到开发流程中，做规范的自动化操作，提供开发效率。

实现Deepin系统组件更新调度算法（更新操作包括组件增加、删除以及版本更新），该算法有如下要求：
1. 计算组件新增或者版本更新需要进行更新的依赖组件的列表以及顺序
2. 计算组件新增或者版本更新需要进行rebuild的组件列表以及顺序
3. 上述计算过程需要支持递归

计算输入数据为Deepin和Debian软件包仓库中系统软件包的元数据以及组件更新信息（包含名称、版本以及更新操作），软件包的元数据示例如下：

        Package: alacritty
        Source: rust-alacritty
        Version: 0.12.2-2
        Architecture: amd64
        Maintainer: Debian Rust Maintainers <pkg-rust-maintainers@alioth-lists.debian.net>
        Installed-Size: 7429
        Depends: libc6 (>= 2.35), libfontconfig1 (>= 2.12.6), libfreetype6 (>= 2.8), libgcc-s1 (>= 4.2), libxcb1 (>= 1.11.1)
        Provides: x-terminal-emulator
        Built-Using: rust-expat-sys (= 2.1.6-3), rust-nix (= 0.26.2-1), rust-option-ext (= 0.2.0-1), rust-sctk-adwaita (= 0.5.3-2), rust-servo-fontconfig-sys (= 5.1.0-2), rust-wayland-protocols-0.29 (= 0.29.5-2), rustc (= 1.71.1+dfsg0ubuntu1-0ubuntu2)
        Filename: amd64/alacritty_0.12.2-2_amd64.deb
        Size: 1983940
        MD5sum: 23d2bca2bf3c5e281a3cd1b2b80630d3
        SHA1: 4c76a3420ba41f084ab67149b0e229f9eb0771e8
        SHA256: dd050b93fbbce00541e5412b639ad298c05d873dbdb8e9a9ba93a769c009e3ac
        SHA512: dbefdbe026f08adf1d8c928b2adbd4cdb5ccb9f6d38d3d65d894fb6f353e2cc40ec25212ddb9d8a0e2a99fe92748826626a5fb48638cb5998a5d05bea5c5adbc
        Section: x11
        Priority: optional
        Multi-Arch: allowed
        Homepage: https://github.com/alacritty/alacritty
        Description: Fast, cross-platform, OpenGL terminal emulator
        Alacritty is a modern terminal emulator that comes with sensible defaults, but
        allows for extensive configuration. By integrating with other applications,
        rather than reimplementing their functionality, it manages to provide a
        flexible set of features with high performance.

## **所属赛道:**

2024全国大学生操作系统比赛的“OS功能设计”赛道

## **参赛要求**


## **项目导师**

Name: 胡登

Github：[hudeng-go](https://github.com/hudeng-go)

Mail: hudeng@deepin.org

## **难度**

中等

## 特征

1. perl/shel/python/golang编程
2. 系统开发
3. linux下的包管理机制

## 参考文档

- https://www.debian.org/doc/manuals/debian-faq/pkgtools.zh-cn.html

- https://wiki.deepin.org/zh/03_%E6%8A%80%E6%9C%AF%E8%A7%84%E8%8C%83/00_%E8%BD%AF%E4%BB%B6%E5%8C%85%E4%B8%8E%E4%BB%93%E5%BA%93%E7%AE%A1%E7%90%86%E8%A7%84%E8%8C%83/%E8%BD%AF%E4%BB%B6%E5%BC%80%E5%8F%91%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F%E7%AE%A1%E7%90%86


# License

GPL-v2

## 预期目标

**注意：选择本项目的同学也可与导师联系，提出自己的新想法，如导师认可，可加入预期目标。**

计算输出结果用列表的形式展现，例如：

- 依赖组件更新

    依赖组件a：需要版本更新到1.0.1版本

    依赖组件b：新增组件，来源debian sid

    依赖组件c：标记删除，参考Debian sid

    依赖组件d：未知风险...

- Rebuild列表

    依赖组件a,依赖组件b,依赖组件c...

Idea：通过web页面展示计算输入和结果,然后页面配置或者API接口输入上述数据，计算过程的状态也可以同步到页面；计算输出的结果应该是一个持续性的过程，中间结果可以以事件的方式转发到消息中间件，然后对接到Deepin系统开发的自动化流程中，帮助Deepin系统的开发。

备注：实现算法的核心需要用到linux操作系统包管理和维护相关的知识。
