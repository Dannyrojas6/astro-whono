---
{
  title: Fcitx5 & Rime-ice,
  description: Linux上Fcitx5输入法框架与雾凇拼音词库安装配置,
  date: 2026-01-10,
  updatedAt: 2026-03-24,
  tags: [ Fcitx5 ],
  draft: false,
  archive: true,
  slug: essay-260110-1bvi
}
---
# Getting Started

## Quick Start

直接用王总最新的一键安装脚本即可，然后再进行简单设置：

```bash
paru -S rime-ice-installer
rime-ice-installer
```

## Fcitx5 Configure

安装Fcitx5软件包：

```bash
pacman -S fcitx5 fcitx5-gtk fcitx5-qt fcitx5-configtool fcitx5-rime librime
```

打开Fcitx5配置工具：

```bash
fcitx5-configtool
```

搜索Rime，将其添加至左侧Input Method，建议只保留Rime和默认英文键盘。

点击上方Addons，配置Classic User Interface，这里面可以快速更改外观设置，当然手动修改**~/.config/fcitx5/conf/classicui.conf**也一样。

## Rime-ice Configure

清空旧的用户配置，然或用git clone雾凇拼音：

```bash
rm -rf ~/.local/share/fcitx5/rime
git clone --depth=1 https://github.com/iDvel/rime-ice.git ~/.local/share/fcitx5/rime
```

重新打开Fcitx5配置工具，再次将Rime添加，然后重新部署，如果部署失败可以直接重启系统：

```bash
fcitx5-configtool
```

## Environment Variable Configure

Omarchy可以不进行配置，会自动识别，设置的话通过菜单进入default即可，其他桌面环境没试过，但是基本都类似：

```bash
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS="@im=fcitx"
```

# References

[Fcitx 最佳配置实践 2026-03-17](https://manateelazycat.github.io/2026/03/17/fcitx-best-config/)
