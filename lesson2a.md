UNIXでなくLInux
PC、組み込みで動く
UNIXは、商用、高価なマシンでのみ動く
オープンソースのBSDは、PC,組み込み両方使えるが、対象が限られる。

LInux コマンド 10選

# ファイルシステム
ext*X*   2,3,4
raiser,xfs,
ntfs, fat
大文字、小文字の区別あり、Linuxのファイルシステム
# ファイル操作
ls
cd, pwd
cp, mv, rm, mkdir , rmdir
ln
chmod
chgrp
mkfifo
mknod
touch
find 
pushd, popd
dd
## 特殊ファイル
/dev/null, /dev/zero, /dev/random, /dev/urandom

# ファイル内容の確認
cat
head
tail
diff
less, more
od, hexdump, xxd  (vimの一部)
wc
file

# 検索
grep, fgrep egrep
# 編集
vi
ed
sed
cut
sort
uniq

# スクリプト
awk

# アーカイバ
tar, cpio

## 圧縮
gzip, bzip2,xz, zstd,lzo,lz4
# システム
ps 
pstree
top
w
kill, killall
tty
stty
uname   hostname
systemctl
whoami,id
dmesg   dmesg -T dmesg -l
date, hwclock
free
who
last
/etc/services
/etc/exports
/etc/passwd
/etc/groups
/etc/shadow
su
sudo
useradd, adduser
addgroup, groupadd
passwd
## samba
smbpasswd


## ストレージ
fdisk,
gparted,parted
mkfs.ext4, mkfs.*XXX*
mount, fstab
findmnt
lsblk
losetup
guestmount
exportfs NFS
df
du




## ネットワーク
ip   ifconfig
who
ssh
ping
netstat, ss 
nslookup
/etc/hostname, h/etc/hosts, /etc/resolv.conf
/etc/nsswitch.conf
traceroute, 
route
host



# パイプ　pipe
プロセス間通信　を標準入出力で行う
cmd1 | cmd2    cmd1のstdout をcmd2のstdinに
シェルはpipeをstdout//stdinに割り当てる
/proc*pid/fdを見る
sleep 1000|cat
sleepの1(stdout)はpipeになっている
catの0(stdin)はpipeになっている

cmc1  && cmd2     成功したらcmd2を実行
cmd1 || cmd2   失敗したらcmd2を実行

## xargs

# シェル機能
history
キー操作
ctr+A, ctrl+B  , +K, +D,   +E, +F, +L  esc+w     EMACS　bind
alias
引用符   シングル、ダブル
バックスラッシュ `\`
echo 
which 

## 変数
シェル変数
環境変数  $    export
数値 let
置換
特殊な変数 
$?, $$,$*, $#, $@ ,$1,$2,$0, $P1,$PS2, $PS3, $PS4
$PATH, $CDPATH, $PWD,$USER, $GROUP, ,$TERM, $SHELL, $PS0,PS1, PS2$HOME,$OLDPWD
env
set
printenv
## 設定ファイル
.bashrc, .profile, .bash_profile, .logout
source

## history
history, !aa, !! , !*, !$ `!:1`
ctrl+R,ctrl+S
 
## 関数

## 実行
sleep
バックグラウンド  `&`
nohup
ctrl+Z,  bg, fg, jobs




# シェルプログラム
構文
for, while, if
比較 test, -lt, -gt, -le, -ge -eq

 



