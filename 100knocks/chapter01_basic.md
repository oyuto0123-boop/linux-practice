# 基本操作

## Q1.現在いるディレクトリパスを表示
コマンド：pwd
結　　果：/home/ohta/dev/linux-practice
解　　説：pwd(print working directory) 現在地を表示するコマンド。

## Q2.ホームディレクトリへ移動
コマンド：ohta@NX:~/dev/linux-practice$ cd ~
結　　果：ohta@NX:~$ 
解　　説：~(ホームディレクトリを表す記号)。cdだけも可。

## Q3.カレントディレクトリのファイルとディレクトリ一覧の表示
コマンド：ls
結　　果：dev
解　　説：ls(list)はファイルとディレクトリを一覧表示する。devはディレクトリ。○.txtはテキストファイル。

## Q4.隠しファイルを含めて表示
コマンド：ls -a
結　　果：.   .bash_history  .bashrc  .config   .gitconfig  .motd_shown  .python_history  .vscode-server
　　　　　..  .bash_logout   .cache   .copilot  .local      .profile     .ssh             dev
解　　説：オプション-aはallの意味。隠しファイルも表示される。

## Q5.権限・所有者・サイズ・更新日時を含む詳細一覧の表示
コマンド：ls -l
結　　果：total 4
　　　　　drwxr-xr-x 3 ohta ohta 4096 Jul  5 23:20 dev
解　　説：オプション-lはlong formatの意味。詳細一覧が表示される。

