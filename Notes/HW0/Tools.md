# Tmux
<http://cenalulu.github.io/linux/tmux/>
tmux的主要元素分为三层：
- Session 一组窗口的集合，通常用来概括同一个任务。session可以有自己的名字便于任务之间的切换。
- Window 单个可见窗口。Windows有自己的编号，也可以认为和ITerm2中的Tab类似。
- Pane 窗格，被划分成小块的窗口，类似于Vim中 C-w +v 后的效果。


1. tmux默认的前置操作是CTRL+b
2. tmux new -s myNewSession 创建一个名为 myNewSession 的新的session