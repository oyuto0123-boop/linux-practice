# Linux コマンド練習 100 本ノック — 基本操作 (Q1〜Q10)

> 実行環境: Ubuntu on WSL2
>
> ※ ユーザー名・ホスト名は `user` / `host` に置き換えています。

---

## Q1. 現在いるディレクトリのパスを表示する

**コマンド**

```bash
pwd
```

**結果**

```
/home/user/dev/linux-practice
```

**解説**

`pwd` は print working directory の略で、現在いるディレクトリの絶対パスを表示する。

---

## Q2. ホームディレクトリへ移動する

**コマンド**

```bash
cd ~
```

**結果**

```
user@host:~/dev/linux-practice$ cd ~
user@host:~$
```

**解説**

`~`(チルダ)はホームディレクトリを表す記号。

`cd` を引数なしで実行しても同じくホームディレクトリに移動する。

⚠️ ここで使うのは**半角の** `~` (ASCII の tilde)。全角の `～`(波ダッシュ)では別の文字として扱われ、コマンドは失敗する。

補足として、`cd -` で直前にいたディレクトリに戻れる。

---

## Q3. カレントディレクトリのファイルとディレクトリ一覧を表示する

**コマンド**

```bash
ls
```

**結果**

```
dev
```

**解説**

`ls` は list の略で、ファイルとディレクトリを一覧表示する。

デフォルトでは名前が並ぶだけなので、ファイルかディレクトリかを見分けたい場合は `ls -F` を使う。ディレクトリには `/`、実行可能ファイルには `*` が末尾に付く。

---

## Q4. 隠しファイルを含めて表示する

**コマンド**

```bash
ls -a
```

**結果**

```
.   .bash_history  .bashrc  .config   .gitconfig  .motd_shown  .python_history  .vscode-server
..  .bash_logout   .cache   .copilot  .local      .profile     .ssh             dev
```

**解説**

`-a` は all の意味。`.` から始まる隠しファイルも表示される。

`.` はカレントディレクトリ、`..` は一つ上の親ディレクトリを指す。この2つを除いて表示したい場合は `-A` を使う。

---

## Q5. 権限・所有者・サイズ・更新日時を含む詳細一覧を表示する

**コマンド**

```bash
ls -l
```

**結果**

```
total 4
drwxr-xr-x 3 user user 4096 Jul  5 23:20 dev
```

**解説**

`-l` は long format の意味。左から順に次の情報が並ぶ。

| 項目 | 例 | 意味 |
| --- | --- | --- |
| ファイル種別＋パーミッション | `drwxr-xr-x` | 先頭 `d` はディレクトリ、`-` は通常ファイル。以降3文字ずつで所有者・グループ・その他の読み(`r`)/書き(`w`)/実行(`x`)権限 |
| ハードリンク数 | `3` | ディレクトリの場合はサブディレクトリ数に関係する |
| 所有者 | `user` | |
| グループ | `user` | |
| サイズ | `4096` | バイト単位。`-h` を付けると `4.0K` のように読みやすくなる |
| 更新日時 | `Jul 5 23:20` | |
| 名前 | `dev` | |

---

## Q6. 隠しファイルの詳細まで表示する

**コマンド**

```bash
ls -al
```

**結果**

```
total 60
drwxr-x--- 9 user user 4096 Jul  5 23:26 .
drwxr-xr-x 3 root root 4096 Jun 21 15:53 ..
-rw------- 1 user user 1965 Jul  5 23:25 .bash_history
-rw-r--r-- 1 user user  220 Jun 21 15:53 .bash_logout
-rw-r--r-- 1 user user 3771 Jun 21 15:53 .bashrc
drwxr-x--- 6 user user 4096 Jul  5 23:26 .cache
drwxr-x--- 3 user user 4096 Jun 21 15:54 .config
drwx------ 3 user user 4096 Jul  5 23:26 .copilot
-rw-r--r-- 1 user user   59 Jun 29 23:43 .gitconfig
drwx------ 3 user user 4096 Jun 29 23:29 .local
-rw-rw-r-- 1 user user    0 Jul  5 22:55 .motd_shown
-rw-r--r-- 1 user user  807 Jun 21 15:53 .profile
-rw-r--r-- 1 user user    7 Jun 26 14:34 .python_history
drwx------ 3 user user 4096 Jul  5 23:20 .ssh
drwxr-xr-x 5 user user 4096 Jul  5 23:26 .vscode-server
drwxr-xr-x 3 user user 4096 Jul  5 23:20 dev
```

**解説**

オプションは組み合わせて指定できる。`-al` でも `-la` でも結果は同じ。

`.bash_history` や `.ssh` が `-rw-------` / `drwx------`(所有者のみアクセス可)になっている点に注目したい。認証情報を含むファイルは、他のユーザーから読めない権限に設定されている。

---

## Q7. 画面をクリアにする

**コマンド**

```bash
clear
```

**結果**

画面の出力が消え、プロンプトが最上部に移動する。

**解説**

出力が多くて見づらくなったときに使う。

画面上は消えるが履歴が失われるわけではなく、`↑` キーで過去のコマンドを呼び出せる。`Ctrl + L` でも同じ効果が得られる。

---

## Q8. 過去に実行したコマンドの履歴を表示する

**コマンド**

```bash
history
```

**結果**

```
    1  exit
    2  ifconfig
    3  sudo ifconfig
    4  which is
    5  which ls
    6  ls
    7  ls -l
    8  ls
    9  which python
   10  sudo which python
   ・・・・・・略・・・・・・
```

**解説**

過去に実行したコマンドが番号付きで表示される。

- `!5` のように `!番号` で、その番号のコマンドを再実行できる
- `Ctrl + R` でインクリメンタル検索ができ、途中まで打つと該当するコマンドが候補に出る

---

## Q9. ターミナルに Hello,Linux と表示する

**コマンド**

```bash
echo "Hello,Linux"
```

**結果**

```
Hello,Linux
```

**解説**

`echo` は指定した文字列を標準出力に表示するコマンド。

この例では引用符がなくても同じ結果になるが、スペースや `*`、`$` などを含む文字列ではシェルが解釈してしまうため、引用符で囲むのが安全。

---

## Q10. ls コマンドのマニュアルを表示する

**コマンド**

```bash
man ls
```

**結果**

`ls` のマニュアルがページャで開き、NAME(概要)、SYNOPSIS(書式)、DESCRIPTION(オプション一覧)といったセクションが順に表示される。

**解説**

`man` は manual の略で、コマンドの使い方やオプションを確認できる。

表示は `less` というページャで行われるため、以下の操作が使える。

- `q` … 終了
- `↑` `↓` / `Space` … スクロール
- `/文字列` … ページ内検索

GNU 版のコマンドでは `ls --help` のほうが簡潔で読みやすいことも多い。

