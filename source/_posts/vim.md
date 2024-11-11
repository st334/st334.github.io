---
title: vim
categories: 技术
date: 2024-10-17 17:17:24
updated: 2024-10-20 04:31:47
tags:
  - linux
  - 配置文件
cover: https://download.logo.wine/logo/Vim_(text_editor)/Vim_(text_editor)-Logo.wine.png
---

## 配置文件
`~/.vimrc`

```vim
source $VIMRUNTIME/defaults.vim

set tabstop=4           " 一个tab显示多长
set softtabstop=4    " 在编辑模式按退格键时退的长度
set shiftwidth=4       " 每一级缩进的长度
set expandtab          " 缩进用空格表示
set hlsearch   " 高亮搜索
set incsearch  " 随着输入字符查找
" set nowrapscan  " 文件尾时结束查找
set number   " 显示行号
set showmatch " 显示匹配括号
set ignorecase  " 忽略大小写
set smartcase   " 智能匹配大小写

nnoremap E ge " 替换E为跳转为上一单词尾

" 符号成对出现
inoremap " ""<esc>i
inoremap ' ''<esc>i
inoremap ( ()<esc>i
inoremap < <><esc>i
inoremap [ []<esc>i
inoremap { {}<esc>i

" 选择多行时按 Tab 进行缩进
vnoremap <Tab> >gv
vnoremap <S-Tab> <gv

" 单行缩进和反向缩进的映射
nnoremap <Tab> >>
nnoremap <S-Tab> <<
```
## 介绍

### .1 基本

- 进入：`vi 文件.txt`
- 退出不保存：`:q!<CR>`。`<CR>`为回车键，后续不再列出，输完命令后自己回车。

### .2 几个界面

- 普通界面：`vi 文件.txt` 默认进入普通界面

  - `hjkl`移动光标，`3j`向下移动3行，`3↓`向下移动3行
  - `b`/`w`上/下一个单词头
  - `ge`/`e`上/下一个单词尾
  - `x`删一个字符
  - `r`替换光标字符，`R`持续替换，按esc退出替换模式
  - `cw`修改到单词尾，`ciw`修改整个单词，`ci"`修改引号间的内容，同理`ci<`、`ci>`、`ci{`等，参考`:h v_a`
  - `yy`复制当前行，`y3y`复制3行，`p`粘贴，`"yy`复制到系统剪贴板，`"p`
  - `/findstr`搜索字符串
  - `v`选择字符，`V`选择整行

- 编辑界面：普通界面下按`i`或其他进入

  - `i`为光标处编辑，`I`行首编辑
  - `a`光标后编辑，`A`行尾编辑
  - `o`下面新开一行编辑，`O`上面新开一行编辑
  - `<ESC>`退出编辑界面，进入普通界面

- 命令界面：普通界面下按`:`进入，同样`<ESC>`退出到普通界面

  - `:wq`保存并退出
  - `:q`退出
  - `:h`帮助。会新开一个窗口，如何关闭请参考下面的多窗口界面
  - `:%s/old/new/g`全局替换字符串

- 多窗口界面

  - `<C-w-q>`退出当前窗口，该按键组合为 `Ctrl + w + q`
  - `<C-w-w>`窗口间切换

## 其他

- [Vim 从入门到精通](https://github.com/wsdjeg/vim-galore-zh_cn)：没看过，按需看