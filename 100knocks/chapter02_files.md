# Linux コマンド練習 100 本ノック (Q1〜Q13)

> 実行環境: Ubuntu on WSL2
>
> ※ ユーザー名・ホスト名は `user` / `host` に置き換えています。

---

## ファイル・ディレクトリの操作

### Q1. `test.txt` を作成する

**コマンド**

```bash
touch test.txt
```

**結果**

```
user@host:~/dev/linux-practice$ ls
100knocks  README.md  test.txt
```

**解説**

`touch` は新規ファイルの作成と、既存ファイルのタイムスタンプ更新ができる。

既にファイルが存在する場合、中身は消えずに更新日時だけが現在時刻になる。

---

### Q2. `mydir` というディレクトリを作成する

**コマンド**

```bash
mkdir mydir
```

**結果**

```
user@host:~/dev/linux-practice$ ls
100knocks  README.md  mydir  test.txt
```

**解説**

`mkdir` は make directory の略。

Linux のコマンド名・ファイル名は**大文字小文字を区別する**ため、`MKDIR` や `Mydir` は別物として扱われる。`MKDIR` は「そんなコマンドはない」というエラーになる。

階層をまとめて作りたい場合は `mkdir -p a/b/c` のように `-p` を使う。

---

### Q3. `test.txt` を `backup.txt` という名前でコピーする

**コマンド**

```bash
cp test.txt backup.txt
```

**結果**

```
user@host:~/dev/linux-practice$ ls
100knocks  README.md  backup.txt  mydir  test.txt
```

**解説**

`cp` は copy の略で、`cp コピー元 コピー先` の順で指定する。

ディレクトリごとコピーしたい場合は `cp -r` を使う。

---

### Q4. `backup.txt` を `renamed.txt` にリネームする

**コマンド**

```bash
mv backup.txt renamed.txt
```

**結果**

```
user@host:~/dev/linux-practice$ ls
100knocks  README.md  mydir  renamed.txt  test.txt
```

**解説**

`mv` は move の略で、移動とリネームの両方ができる。

- 移動: `mv ファイル名 移動先ディレクトリ`
- リネーム: `mv 変更前 変更後`

移動先が「存在するディレクトリ」なら移動、そうでなければリネームとして解釈される、と覚えると分かりやすい。

---

### Q5. `renamed.txt` を `mydir/` へ移動する

**コマンド**

```bash
mv renamed.txt mydir
```

**結果**

```
user@host:~/dev/linux-practice/mydir$ ls
renamed.txt
```

**解説**

Q4 と同じ `mv` だが、移動先に既存のディレクトリ `mydir` を指定しているため、リネームではなく移動になる。

---

### Q6. `test.txt` を削除する

**コマンド**

```bash
rm test.txt
```

**結果**

```
user@host:~/dev/linux-practice$ ls
100knocks  README.md  mydir
```

**解説**

`rm` は remove の略。

⚠️ `rm` で消したファイルはゴミ箱を経由せず即座に消える。復元は基本的にできない。

---

### Q7. `mydir/` を中身ごと削除する

**コマンド**

```bash
rm -r mydir
```

**結果**

```
user@host:~/dev/linux-practice$ ls
100knocks  README.md
```

**解説**

`-r` は再帰的に、つまりディレクトリと中身をまとめて削除する。

`-d` は「空のディレクトリのみ削除」なので、中身が入っていると失敗する(`rmdir` と同じ挙動)。

⚠️ `rm -rf` はパスのタイプミスが致命傷になる。不安なうちは `-i`(削除前に確認を求める)を付けるか、先に `ls` で対象を確認する癖をつけるとよい。

---

## ファイル内容の確認

### Q8. `/etc/hostname` の内容を表示する

**コマンド**

```bash
cat /etc/hostname
```

**結果**

```
user@host:~$ cat /etc/hostname
host
```

**解説**

`cat` は concatenate(連結)の略で、ファイルの内容を標準出力に出す。

複数ファイルを指定すると、その名の通り連結して出力される。

---

### Q9. `/etc/hosts` の内容を行番号付きで表示する

**コマンド**

```bash
cat -n /etc/hosts
```

**結果**

```
(ここに実行結果を貼る)
```

**解説**

`-n` で全行に行番号を付けて表示する。

空行には番号を振りたくない場合は `-b` を使う。

---

### Q10. `/var/log/syslog` の先頭 10 行を表示する

**コマンド**

```bash
head /var/log/syslog
```

**結果**

```
(ここに実行結果を貼る)
```

**解説**

`head` はデフォルトで先頭 10 行を表示する。

行数を明示したい場合は `head -n 10`、20 行なら `head -n 20` のように指定する。

`cat` には行数を制限するオプションがないため、この用途では `head` を使う。

---

### Q11. `/var/log/syslog` の末尾 10 行を表示する

**コマンド**

```bash
tail /var/log/syslog
```

**結果**

```
(ここに実行結果を貼る)
```

**解説**

`tail` はデフォルトで末尾 10 行を表示する。

`tail -f` を付けると、ログが追記されるたびにリアルタイムで表示し続ける(トラブルシューティングで多用)。

---

### Q12. `/var/log/syslog` の行数を数える

**コマンド**

```bash
wc -l /var/log/syslog
```

**結果**

```
6370 /var/log/syslog
```

**解説**

`wc` は word count の略。`-l` で行数、`-w` で単語数、`-c` でバイト数を表示する。

オプションなしだと「行数 単語数 バイト数」がまとめて出るので、行数だけ欲しいときは `-l` を忘れずに。

---

### Q13. `/var/log/syslog` から `error` を含む行を検索する

**コマンド**

```bash
grep error /var/log/syslog
```

**結果**

該当行が大量に出力されたため、件数だけを数え直した。

```
(ここに grep -ci error /var/log/syslog の実行結果を貼る)
```

**解説**

`grep` は指定した文字列を含む行を抽出する。

- `-i` … 大文字小文字を区別しない(`Error` / `ERROR` も拾える)
- `-c` … マッチした行数のみ表示
- `-n` … 行番号を表示
- `-v` … マッチ**しない**行を表示
- `-r` … ディレクトリを再帰的に検索

出力が多いときは `grep error /var/log/syslog | head` のようにパイプで絞ると読みやすい。