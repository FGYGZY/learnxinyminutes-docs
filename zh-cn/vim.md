---
contributors:
    - ["RadhikaG", "https://github.com/RadhikaG"]
    - ["kaymmm", "https://github.com/kaymmm"]
translator:
    - ["FGYGZY", "https://github.com/FGYGZY"]
---

[Vim](http://www.vim.org)
(Vi IMproved) 是 Unix 上广受欢迎的 vi 编辑器的一个克隆。它是一款专为提高速度和生产力而设计的文本编辑器，在大多数基于 Unix 的系统中都可以找到。它提供了大量快捷键，以便用户快速导航到文件中的特定位置，并进行高效编辑。

`vimtutor` 是一个优秀的应用程序，专门用来教你如何使用 `Vim` 。它会随 `vim` 一同下载。你只需在命令行中运行 `"vimtutor"`，即可打开该教学工具。`vimtutor` 将引导你学习 `Vim` 的所有主要功能，帮助你快速上手并掌握基本操作。

## Basics of navigating Vim

```
        vim <filename>    # 在vim中打开 <filename> 文件
        :help <topic>     # 打开 <topic> 相关的内置帮助文档 (如果存在的话)
        :q                # 退出 vim
        :w                # 保存当前文件
        :wq               # 保存并退出 vim
        ZZ                # 保存并退出 vim
        :q!               # 不保存并退出 vim
                          # ! 表示强制执行，因此会直接退出而不保存 
        ZQ                # 不保存退出 vim
        :x                # 保存文件(仅当文件有所修改时)并退出 vim

        u                 # 撤销
        CTRL+R            # 重做

        h                 # 光标左移一个字符
        j                 # 下移一行
        k                 # 上移一行
        l                 # 右移一个字符

        Ctrl+B            # 向后移动一个完整屏幕
        Ctrl+F            # 向前移动一个完整屏幕
        Ctrl+D            # 向前移动半个屏幕
        Ctrl+U            # 向后移动半个屏幕

        # 行内移动

        0                 # 移到行首
        $                 # 移到行末
        ^                 # 移动到行中的第一个非空字符

        /word             # 高亮光标后所有单词
        ?word             # 高亮光标前所有单词
        n                 # 移动到下一个搜索结果
        N                 # 移动到上一个搜索结果

        :%s/foo/bar/g     # 将文件中的所有 'foo' 替换为 'bar'
        :s/foo/bar/g      # 将当前行中的所有 'foo' 替换为 'bar'
        :%s/\n/\r/g       # 将换行符替换为回车符
        :'<,'>s/foo/bar/g # 将当前选中区域中的所有 'foo' 替换为 'bar'

        # 跳转到字符

        f<character>      # 向前跳转并停在 <character> 上
        t<character>      # 向前跳转并停在 <character> 前

        # 例如，
        f<                # 向前跳转并停在 <
        t<                # 向前跳转并停在 < 前

        # 按词移动

        w                 # 向前移动一个词
        b                 # 向后移动一个词
        e                 # 移动到当前词的末尾

        # 其他移动方式

        gg                # 移动到文件顶部
        G                 # 移动到文件底部
        :NUM              # 跳转到第 NUM 行 (NUM 为数字)
        H                 # 移动到屏幕顶部
        M                 # 移动到屏幕中间
        L                 # 移动到屏幕底部
    ```
```

## 帮助文档

Vim 内置了帮助文档，可以使用 `:help <topic>` 访问。  
例如，输入 `:help navigation` 将打开关于如何在工作区中导航的文档。

`:help` 也可以单独使用，而不带任何选项。这将打开默认的帮助对话框，旨在使 Vim 的入门更加简单易懂！

## 模式

Vim 基于 **模式** 的概念。

- 普通模式 - vim 启动时的默认模式，用于导航和执行命令
- 插入模式 - 用于在文件中进行修改
- 可视模式 - 用于高亮文本(即选择文本)并对其进行操作
- 命令模式 - 用于在底部输入 `:` 提示符后的命令

```
    i                 # 将 vim 切换到插入模式，光标位置前插入
    a                 # 将 vim 切换到插入模式，光标位置后插入
    v                 # 将 vim 切换到可视模式
    :                 # 将 vim 切换到命令模式
    <esc>             # 从当前模式切换到普通模式

    # 复制和粘贴文本
                      # 操作默认使用 vim 寄存器
                      # 可以将其视为 vim 的私有剪贴板

                      # y代表Yank ~ 复制文本到 vim 寄存器
    y                 # 复制选中的内容
    yy                # 复制当前行

                      # d即Delete ~ 复制文本并从文件中删除
    d                 # 删除选中的内容
    dd                # 删除当前行

    p                 # 在光标位置后粘贴 vim 寄存器中的文本
    P                 # 在光标位置前粘贴 vim 寄存器中的文本

    x                 # 删除光标位置的字符
```

## vim 的"语法"

Vim 可以被认为是一组以“动词-修饰符-名词”格式的命令，其中：

- 动词 - 你的动作
- 修饰符 - 你如何执行动作
- 名词 - 动作作用的对象

一些关于“动词”、“修饰符”和“名词”的重要例子：

```
    # '动词'

    d                 # 删除
    c                 # 更改
    y                 # 复制
    v                 # 可视选择

    # '修饰符'

    i                 # 内部
    a                 # 周围
    NUM               # 数字 (NUM 是任何数字)
    f                 # 搜索某物并停在其上
    t                 # 搜索某物并停在其前
    /                 # 从光标开始查找字符串
    ?                 # 从光标前查找字符串

    # '名词'

    w                 # 单词
    s                 # 句子
    p                 # 段落
    b                 # 块

    # 示例“句子”或命令

    d2w               # 删除两个单词
    cis               # 更改句子内部
    yip               # 复制段落内部 (复制你所在的段落)
    ct<               # 更改到下一个 <
                      # 更改从当前位置到下一个 < 的文本
    d$                # 删除到行尾
```

## 一些简写和技巧

```
    >                 # 将选中的内容缩进一段
    <                 # 将选中的内容减少一段缩进
    :earlier 15m      # 将文档恢复到15分钟前的状态
    :later 15m        # 撤销上述命令
    ddp               # 交换连续两行的位置，先 dd 然后 p
    .                 # 重复上一个操作
    :w !sudo tee %    # 以 root 身份保存当前文件
    :set syntax=c     # 将语法高亮设置为 'c'
    :sort             # 对所有行进行排序
    :sort!            # 反向排序所有行
    :sort u           # 排序所有行并删除重复项
    ~                 # 切换选中文本的大小写
    u                 # 将选中文本转换为小写
    U                 # 将选中文本转换为大写
    J                 # 将当前行与下一行合并

    # 折叠文本
    zf                # 从选中文本创建折叠
    zd                # 删除当前行的折叠
    zD                # 递归删除嵌套的或选择的折叠
    zE                # 消除窗口中的所有折叠
    zo                # 展开当前折叠
    zO                # 递归打开嵌套的或选择的折叠
    zc                # 折叠当前折叠
    zC                # 递归关闭嵌套的或选择的折叠
    zR                # 展开所有折叠
    zM                # 折叠所有折叠
    za                # 切换当前折叠的展开/折叠状态
    zA                # 递归切换嵌套折叠的展开/折叠状态
    [z                # 移动到当前折叠的开始
    ]z                # 移动到当前折叠的结束
    zj                # 移动到下一个折叠的开始
    zk                # 移动到上一个折叠的结束
```

## 宏

宏本质上是可记录的操作。
当你开始录制一个宏时，它会记录你使用的**每一个**操作和命令，直到你停止录制为止。
调用宏时，它会在选择的文本上再次应用完全相同的操作和命令序列。

```
    qa                # 开始录制名为 'a' 的宏
    q                 # 停止录制
    @a                # 播放宏
```

### 配置 ~/.vimrc

`.vimrc` 文件可以用来在启动时配置 Vim。

以下是一个示例的 `~/.vimrc` 文件：

```vim
" ~/.vimrc 示例
" 2015.10

" 让 vim 以非兼容 vi 的模式运行(否则有些功能会有问题)
set nocompatible

" 根据文件名确定文件类型，以允许智能自动缩进等功能
filetype indent plugin on

" 启用语法高亮
syntax on

" 更好的命令行补全
set wildmenu

" 使用不区分大小写的搜索，除非使用大写字母
set ignorecase
set smartcase

" 当换行后没有启用特定文件的缩进时，
" 保持与当前行相同的缩进
set autoindent

" 在左侧显示行号
set number

" 缩进选项，根据个人喜好进行更改

" 每个 TAB 的视觉空格数
set tabstop=4

" 编辑时 TAB 的空格数
set softtabstop=4

" 使用重新缩进操作 (>> 和 <<) 时缩进的空格数
set shiftwidth=4

" 将 TAB 转换为空格
set expandtab

" 启用智能缩进和对齐的 TAB 与空格
set smarttab
```

### 参考

[Vim官网](http://www.vim.org/index.php)

`$ vimtutor`

[A vim Tutorial and Primer](https://danielmiessler.com/study/vim/)

[What are the dark corners of Vim your mom never told you about? (Stack Overflow thread)](http://stackoverflow.com/questions/726894/what-are-the-dark-corners-of-vim-your-mom-never-told-you-about)

[Arch Linux Wiki](https://wiki.archlinux.org/index.php/Vim)
