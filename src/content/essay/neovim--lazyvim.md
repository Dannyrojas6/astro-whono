---
{
  title: Neovim & LazyVim,
  description: LazyVim编辑器安装配置指南，从Scoop到WezTerm,
  date: 2026-01-06,
  updatedAt: 2026-01-22,
  tags: [ Neovim ],
  draft: false,
  archive: true,
  slug: essay-260106-q770
}
---
## 1. Getting Started

### Use Global Proxy

在Arch Linux上使用全局代理，让LazyVim自己下载依赖，然后再运行checkhealth只有少数几个包需要手动安装，其他的都装好了。

### Install Scoop+Neovim+Lazyvim

使用PowerShell安装Scoop：

```jsx
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
```

安装Git和Neovim：

```jsx
scoop install git
scoop install neovim
```

在C:\Users\**用户名**\AppData\Local目录下创建nvim文件夹：

```jsx
mkdir ~/AppData/Local/nvim
```

克隆LazyVim到nvim文件夹下：

```jsx
# 把yourname替换为用户名
git clone https://github.com/LazyVim/starter C:\Users\yourname\AppData\Local\nvim
```

### Install NerdFont

下载 **0xProto Nerd Font** 字体，解压后选中字体并安装：

[Nerd Fonts - Iconic font aggregator, glyphs/icons collection, & fonts patcher](https://www.nerdfonts.com/)

### Install Lazygit

```jsx
scoop bucket add extras
scoop install lazygit
```

### Install **tree-sitter-cli+**gcc

```jsx
scoop install tree-sitter
scoop install gcc
```

### Install curl+fzf+ripgrep+fd

```jsx
scoop install curl fzf ripgrep fd
```

### Install luarocks+magick+gs+tectonic

```jsx
scoop install luarocks imagemagick ghostscript tectonic
```

### Install WezTerm Nightly

```jsx
scoop bucket add versions
scoop install wezterm-nightly
```

安装完毕后会提示添加Windows右键上下文菜单选项，复制运行即可：

```powershell
# example
reg import "C:\Users\kk\scoop\apps\wezterm-nightly\current\install-context.reg"
```

WezTerm默认使用CMD，可以选择安装PowerShell 7替代：

```lua
scoop install pwsh
```

将文件地址复制到资源管理器打开：

```powershell
# example
C:\Users\kk\scoop\apps\pwsh\current\install-explorer-context.reg
```

### WezTerm Configuration

在C:\Users\用户名目录下创建**.wezterm.lua**文件，将下面内容写入文件：

```lua
local wezterm = require 'wezterm'

local config = wezterm.config_builder()

-- Primary Font
config.font = wezterm.font('0xProto Nerd Font Mono')  

-- Font Size
config.font_size = 12.0

-- Line Height & Cell Width
config.line_height = 1.2
config.cell_width = 1.0

-- Power Shell 7
config.default_prog = { 'pwsh', '-NoLogo' }

-- Title Bar Settings
config.window_decorations = "RESIZE" 
config.enable_tab_bar = true
config.use_fancy_tab_bar = false 
config.window_padding = { left = 0, right = 0, top = 0, bottom = 0 }

-- Initial Window Size
config.initial_cols = 120
config.initial_rows = 30
config.window_background_opacity = 1.0

return config
```

### Check Health

安装好后进入LazyVim，输入`:checkhealth`检查是否有报错。

[Getting Started | LazyVim](https://www.lazyvim.org/)

[WezTerm - Wez's Terminal Emulator](https://wezterm.org/)
