---
{
  title: Emacs + Doom Emacs,
  description: Doom Emacs安装与Chemacs2多配置管理方案,
  date: 2026-03-24,
  tags: [ Emacs ],
  draft: false,
  archive: true,
  slug: essay-260324-271c
}
---
安装doom emacs后输入emacs后，启动默认Emacs而非doom，从头安装一遍再配置一下就行了。

# Fix

先更新系统，然后安装Emacs以及相关依赖工具：

```bash
sudo pacman -Syu
sudo pacman -S emacs-wayland ripgrep fd git
```

安装Chemacs2：

```bash
git clone <https://github.com/plexus/chemacs2.git> ~/.emacs.d
```

安装Doom Emacs，中途会出现“Generate an envvar file?” ，输入y回车：

```bash
git clone --depth 1 <https://github.com/doomemacs/doomemacs> ~/.config/emacs
~/.config/emacs/bin/doom install
```

安装完成后运行：

```
~/.config/emacs/bin/doom sync
~/.config/emacs/bin/doom env
```

接下来配置chemacs2，创建并编辑.emacs-profiles.el文件：

```bash
# ~/.emacs-profiles.el
(("default" . ((user-emacs-directory . "~/.config/emacs")))
 ("doom"    . ((user-emacs-directory . "~/.config/emacs")
               (env . (("DOOMDIR" . "~/.config/doom"))))))
```

编辑 fish 配置，在文件最底部添加：

```bash
nvim ~/.config/fish/config.fish
# Doom Emacs with Chemacs2
function emacs
    command emacs --with-profile doom $argv
end
```

然后重新打开终端运行Emacs，应该正常出现doom emacs：

```bash
emacs
```
