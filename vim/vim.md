# VIM 常用命令

## 光标移动命令 (motion command)
1. 向前翻一页(forward): ctrl-f (forward)
2. 向后翻一页(backward): ctrl-b (backward)
3. 向下翻半页(down): ctrl-d 
4. 向上翻半页(up): ctlr-u 
5. 将光标移动到文件的最后一行(go to the end of file): G
6. 将光标移动到文件的第一行(go to top of file): gg
7. 上次修改的地方(go to older position in change list): g;
8. 下次修改的地方(go to newer position in change list): g,
9. go to the beginning of current or previous word: b
10. go to the beginning of next word: w
11. go to the end of current or next word: e
12. go to the end of previous word: ge


## 错别字检查
1. 检查错别字: setlocal spell 或者 set spell
2. 指定检查的语言: setlocal spell spelllang=en\_us
3. 把字符加到字典中: zg
4. 关闭错别字检查 : set nospell

## System Clipboard 系统剪切板
1. 检测是否支持系统剪切版（access the system clipboard）: vim --version 
+clipboard: 支持访问系统剪切版 means support access to system clipboard.
-clipboard: 不支持系统剪切版

## 命令行 (command line)
1. 把命令结果读入vim : ":read!command"
2. 切换到命令行 : "Ctl+z"
3. 从命令行切换回vim : "fg"

## 显示设置
1. 显示行号：set nu
2. 取消行号的显示: set nonu
3. 显示空白字符，例如tab、行结束符等: set list
4. 取消显示空白字符: set nolist
5. 在屏幕底部显示当前光标的位置,包括行号、列号等, : set ruler
6. 取消光标位置的显示: set noruler

