# 基本操作

## Q1.現在いるディレクトリパスを表示
コマンド：pwd<br>
結　　果：/home/ohta/dev/linux-practice<br>
解　　説：pwd(print working directory) 現在地を表示するコマンド。<br>

## Q2.ホームディレクトリへ移動
コマンド：ohta@NX:～/dev/linux-practice$ cd ～<br>
結　　果：ohta@NX:～$<br> 
解　　説：～(ホームディレクトリを表す記号)。cdだけも可。<br>

## Q3.カレントディレクトリのファイルとディレクトリ一覧の表示
コマンド：ls<br>
結　　果：dev<br>
解　　説：ls(list)はファイルとディレクトリを一覧表示する。devはディレクトリ。○.txtはテキストファイル。<br>

## Q4.隠しファイルを含めて表示
コマンド：ls -a<br>
結　　果：.   .bash_history  .bashrc  .config   .gitconfig  .motd_shown  .python_history  .vscode-server<br>
　　　　　..  .bash_logout   .cache   .copilot  .local      .profile     .ssh             dev<br>
解　　説：オプション-aはallの意味。隠しファイルも表示される。<br>

## Q5.権限・所有者・サイズ・更新日時を含む詳細一覧の表示
コマンド：ls -l<br>
結　　果：total 4<br>
　　　　　drwxr-xr-x 3 ohta ohta 4096 Jul  5 23:20 dev<br>
解　　説：オプション-lはlong formatの意味。詳細一覧が表示される。<br>

## Q6.隠しファイルの詳細まで表示
コマンド：ls -al<br>
結　　果：<br>
total 60<br>
drwxr-x--- 9 ohta ohta 4096 Jul  5 23:26 .<br>
drwxr-xr-x 3 root root 4096 Jun 21 15:53 ..<br>
-rw------- 1 ohta ohta 1965 Jul  5 23:25 .bash_history<br>
-rw-r--r-- 1 ohta ohta  220 Jun 21 15:53 .bash_logout<br>
-rw-r--r-- 1 ohta ohta 3771 Jun 21 15:53 .bashrc<br>
drwxr-x--- 6 ohta ohta 4096 Jul  5 23:26 .cache<br>
drwxr-x--- 3 ohta ohta 4096 Jun 21 15:54 .config<br>
drwx------ 3 ohta ohta 4096 Jul  5 23:26 .copilot<br>
-rw-r--r-- 1 ohta ohta   59 Jun 29 23:43 .gitconfig<br>
drwx------ 3 ohta ohta 4096 Jun 29 23:29 .local<br>
-rw-rw-r-- 1 ohta ohta    0 Jul  5 22:55 .motd_shown<br>
-rw-r--r-- 1 ohta ohta  807 Jun 21 15:53 .profile<br>
-rw-r--r-- 1 ohta ohta    7 Jun 26 14:34 .python_history<br>
drwx------ 3 ohta ohta 4096 Jul  5 23:20 .ssh<br>
drwxr-xr-x 5 ohta ohta 4096 Jul  5 23:26 .vscode-server<br>
drwxr-xr-x 3 ohta ohta 4096 Jul  5 23:20 dev<br>
解　　説：オプションは組み合わせ可能。-alでも-laでも可<br>

## Q7.画面をクリアにする
コマンド：clear<br>
結　　果：<br>
解　　説：画面出力が多く、見えにくいときに使用。画面はきれいになるが、↑で過去のコマンドは引用可能。ctrl+Lも同じ効果。<br>

## Q8.過去に実行したコマンドの履歴の表示
コマンド：history<br>
結　　果：<br>
    1  exit<br>
    2  ifconfig<br>
    3  sudo ifconfig<br>
    4  which is<br>
    5  which ls<br>
    6  ls<br>
    7  ls -l<br>
    8  ls<br>
    9  which python<br>
   10  sudo which python<br>
   ・・・・・・略・・・・・・<br>
解　　説：過去のコマンドが番号付きで表示。!コマンド番号で再実行可能。ctrl+Rで検索可。<br>

## Q9.ターミナルにHello,Linuxと表示
コマンド：echo "Hello,Linux"<br>
結　　果：Hello,Linux<br>
解　　説：echoは文字列を表示するコマンド。<br>

## Q10.lsコマンドのマニュアル表示
コマンド：man ls<br>
結　　果：色々表示される。<br>
解　　説：man(manual)は、コマンドの使い方、オプション一覧などを確認でき、Qを押すと終了できる。<br>