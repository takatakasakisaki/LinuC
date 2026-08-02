LInux コマンド 10選

# ファイル操作
ls
cd, pwd
cp, mv, rm, mkdir , rmdir
ln
chmod
mkfifo
mknod
find 

# ファイル内容の確認
cat
head
tail
diff
less, more
# 検索
grep, fgrep egrep

# アーカイバ
tar, cpio,
## 圧縮
gzip, bzip2,xz, zstd,lzo,lz4
# システム
ps 
pstree
top
uname   hostname
ip   ifconfig
systemctl


# Linuxコマンドの使い方
パイプ　pipe
プロセス間通信　を標準入出力で行う
cmd1 | cmd2    cmd1のstdout をcmd2のstdinに
シェルはpipeをstdout//stdinに割り当てる
/proc*pid/fdを見る
sleep 1000|cat
sleepの1(stdout)はpipeになっている
catの0(stdin)はpipeになっている

cmc1  && cmd2     成功したらcmd2を実行
cmd1 || cmd2   失敗したらcmd2を実行

# シェルプログラム
構文
for, while, if
比較 test, -lt, -gt, -le, -ge -eq

 



