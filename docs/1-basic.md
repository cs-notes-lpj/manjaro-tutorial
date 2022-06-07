> 推荐安装英文系统，中国时区，后续再安装中文输入法

#### 调整外设的默认参数

- 系统设置 => 硬件 => 输入设备

  - 触摸板 => 勾选反向滚动 => 指针加速0.4 => 应用

  - 鼠标 => 指针速度增加两格 => 应用

#### 3 种打开 terminal 的方式

1. konsole: 默认为 ctrl+alt+t

2. yakuake: 默认为 f12

> 首次运行打开 yakuake 会自动弹窗，此时推荐将默认的 f12 修改为 meta+space
>
> 可在系统设置中将 yakuake 设置为开机自启

3. 当聚焦于文件资源管理器 dolphin 的窗口时，默认按 f4 打开其内置 terminal

#### 软件包管理

> 官方软件包管理器：pacman

ArchLinux 以及基于其的一众发行版（比如 ManjaroLinux）采用滚动更新的系统更新方式

这意味着每隔十天半个月，官方就会发布少量的程序更新（也正是因此，从官方网站下载的 ISO 系统镜像未必最新，我们需要在刚安装好系统进入桌面后就立刻尝试接收官方的程序更新）

优点：你可以时刻使用各种程序的最新版本，体验最新特性

缺点：你需要经常使用你的电脑，你需要每隔十天半个月就使用软件包管理器尝试接收官方发布的程序更新

#### tmux

tmux 是一个极好的 terminal 复用器，为方便后续操作，我们安装他，关于其进阶配置和使用会专门编写其他文章

```bash
sudo pacman -S tmux
```

#### vim

vim 是一个上古编辑器之神，为方便后续操作，我们安装他，关于其进阶配置和使用会专门编写其他文章

```bash
sudo pacman -S vim
```

#### git

git 是 Linux 之父创造的高性能文件版本控制工具（respect ！）

可以执行命令 `git --version` 查看当前系统中 git 的版本

如果系统中未安装 git，那么

```bash
sudo pacman -S git
```

`git config` 有 3 种作用域：--local、--global、--system（具体含义请自行查询 git manual）

下面我们简单地配置一下 git（具体含义也请自行查阅 git manual）

```bash
# 必要配置项
git config --global user.name "your_english_name"
git config --global user.email "your_email"

# 推荐配置项
git config --global init.defaultBranch master
git config --global core.quotepath false
git config --global core.editor vim
```

查看 git 的配置信息，就加 `--list`，git 的进阶配置使用方式会另外编写文章介绍

> https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/
>
> **鉴于此，我决定使用 https + personalAccessToken 的方式验证 git operation in cli，官方也推荐用 https**
>
> **而之前使用的基于 ssh 的验证方式，我目前不使用**

#### 合理地配置软件源，然后更新系统并重启系统

**不要使用** ~~pacman-mirrors~~，其虽然可以自动配置你的软件源，但有时并不精准

#### AUR & yay

AUR 是由 ArchLinux 社区驱动维护的软件仓库，其中几乎拥有所有你能想到的软件

搭配一个第三方开源软件包管理器 yay

就能实现以下需求：

**当 pacman 官方无你想要安装的软件包时，很大概率 AUR 上是有的，可使用 yay 查询下载安装**

> 注意：能用 pacman 就用 pacman，毕竟官方支持，只有无计可施的时候，才谨慎考虑使用 yay & AUR

我曾经询问过 yay 的开发者：[Can I just use yay instead of pacman?](https://github.com/Jguer/yay/issues/1601)

#### 中文输入法

```bash
sudo pacman -S fcitx5-im fcitx5-chinese-addons        # 输入法框架 & 输入法引擎
sudo pacman -S fcitx5-qt fcitx5-gtk fcitx5-configtool # 依赖和配置工具
sudo pacman -S fcitx5-pinyin-zhwiki                   # 中文维基百科词库

vim ~/.pam_environment

# 写入以下配置，保存退出
GTK_IM_MODULE DEFAULT=fcitx5
QT_IM_MODULE  DEFAULT=fcitx5
XMODIFIERS    DEFAULT=\@im=fcitx5
SDL_IM_MODULE DEFAULT=fcitx5
```

注销或重启系统，应该就可以输入中文了，输入法切换的快捷键默认为：ctrl+space 或 ctrl+shift

#### 配置触摸板手势操作

- 第一步，see [FAQ](https://github.com/JoseExposito/touchegg#faq)

- 第二步，安装核心程序包 [touchegg](https://github.com/JoseExposito/touchegg#arch-linux-manjaro-and-derivatives)

- 第三步，安装图形化客户端 [touche](https://github.com/JoseExposito/touche)

![image-20220304102852504](https://aliyun-oss-lpj.oss-cn-qingdao.aliyuncs.com/images/by-picgo/image-20220304102852504.png)

![2-四指轻扫（向上多桌面平铺、向下单桌面平铺、切换桌面）](https://aliyun-oss-lpj.oss-cn-qingdao.aliyuncs.com/images/mass/2-四指轻扫（向上多桌面平铺、向下单桌面平铺、切换桌面）.png)

![3-双指捏合缩放](https://aliyun-oss-lpj.oss-cn-qingdao.aliyuncs.com/images/mass/3-双指捏合缩放.png)

![4-三指捏合显示所有应用程序](https://aliyun-oss-lpj.oss-cn-qingdao.aliyuncs.com/images/mass/4-三指捏合显示所有应用程序.png)

![5-轻敲默认](https://aliyun-oss-lpj.oss-cn-qingdao.aliyuncs.com/images/mass/5-轻敲默认.png)
