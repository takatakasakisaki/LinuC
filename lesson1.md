# OSとカーネル
- カーネル Kernel(核)  ちなみに同じ発音でcolonel(大佐)があるが意味が違う
  複数のタスクを動かすための機構
  - メモリの管理
    物理メモリと仮想アドレス。メモリの使用、空きの管理
  - プログラム実行の管理
    - スケジューリング、タスク(プロセス、スレッド)切り替え 
      どの順番でCPUに実行させるか割り振る。
    - スレッドは昔は**LWP**(*L*ight *W*eight *P*rocess) と呼ばれていた
  - 割り込み
  - タイマー 
    タイムシェアリング、周期処理
  
  
- OS(*O*perating *S*ystem)
  - カーネル
  - ハードウェア資源の管理
    - デバイスドライバ等
  - サービス
    - ネットワーク
    - ストレージ、ファイルシステム
    - 端末
    - サウンド
    ｰ 描画
  - ユーザランドサービス
    - デーモン類
      http,ssh,ntp,login, ...
    
- Linuxの起動
  - bootloader
    grub(pc),uboot(組み込み機器),その他、pmon,yamon...
    pcはBIOS,EFIがストレージからメモリにbootloaderを転送して実行
    組み込み機器は、SoC毎に手順が異なるが、メモリに転送されて実行
  - カーネルをメモリへロード  
    grub: vmlinux,vmlinuz,  uboot: uImage,zImage,bzImage,   
  - カーネル起動 Starting Kernel
  - VFSマウント ファイルシステムのマウント
  - <ユーザランド側起動>
  - initの起動 
    - サービス起動

# ファイル
  - UNIX/Linuxのユーザランドからの操作はファイルを通して行う
  - ファイルの種類
      - 通常ファイル
      - ディレクトリ
      - リンク
      - デバイス character , block device
        - character device:  /dev/tty*XX* など、
        - block device  : /dev/sdaなどストレージ
      - パイプ
      - ソケット
   - パーミッション アクセス権
      - 所有者 ,グループ,その他の３つの分類でアクセス制御を行う
   -  setuid
   -  スティッキー

# UNIX/Linuxのコマンド操作
  - ls  : file *l*i*s*t
    fileの情報を表示
    lsだけだと、カレントディレクトリ(.)にあるファイルリストを表示
    - -l
      ファイルの詳細　ファイルタイプ、パーミッション、所有者、サイズを表示
    - -i  iノード表示
      ファイルのIDみたいな番号
    - -F  ファイル名の後ろにファイルタイプ、パーミッションの記号が表示される
        `*` 実行可能 `/`ディレクトリ  `@`シンボリックリンク `|`パイプ
     
  - mkdir  : ディレクトリ作成 make directory
    - -p : 再帰的に作成   `mkdir -p a/b/c` とやると、a/b/cの階層ができる。
  - rmdir  : ディレクトリ削除  remove directory
    空ディレクトリであれば削除
  - rm :ファイル削除 remove
    - -f 強制的に
    - -i 削除してよいか問い合わせてくる
    - -r ディレクトリを再帰的(recursively) に削除する
  - mv  : ファイルの移動、名前の変更  move
  - ln  : ファイル、ディレクトリのリンク
    - -s シンボリックリンク
  - chmod  : ファイルのパーミッションを変更 change mode
    `chmod +r file` 読み込み可能
    `chmod +w file` 書き込み可能
    `chmod +x file` 実行可能
    `chmod 644 file` 所有者は読み書き可能、その他は、読み込みのみ
  - chown : 所有者変更  change owner
     `chown kawamoto:users file` 所有者をkawamotoにする
  - pwd :  現在のカレントディレクトリを表示
  - cd : 現在のカレントディレクトリを変更  chage current directory
  - cat ファイルの内容表示   con*cat*inate コンカチ 結合
  - wc  : ファイルの中の、行数、単語数、文字数を表示  word count
  - mount マウント
    ブロックデバイス(ストレージ)をファイルシステムのどこかに配置してアクセスできるようにする。
  - umount
    マウントの解除
  - findmnt マウントの状態を表示

# 標準入出力
- stdin=0
標準入力　キー入力 or リダイレクト
- stdout=1
標準出力　画面表示 or リダイレクト
- stderr=2
標準エラー 画面表示 or リダイレクト
# リダイレクト
標準出力、標準エラーをファイルに保存
`a.out > file`, `a.out 2>file`
標準入力をプログラムの入力にする
`cat < file`
- `>>` ファイルへの追加
- `<<` 入力の終わりを文字列で示す エディタを使わずにファイルを作ったりできる
```bash
cat <<_EOF >file.txt
abc
def
ghk
_EOF
```
# パイプ
直前のコマンドの標準出力を、次のコマンドの標準入力にする
# コマンド入力
### コマンドの履歴
```bash
ls -l test.txt
!!
gcc a.c b.c
!g
echo $*
cat !$
!g
cat !:1
```
`!!`：直前のコマンドの再実行
`!g`: ヒストリをさかのぼってgで始まる行を探して実行  
`!*` 直前のコマンドの全引数
`!$` 直前のコマンドの最後(右端)の引数
`!:1` 直前のコマンド引数の１番目   :2は２番目...
ctrl+R, ctrl+S ヒストリの検索


# 練習
## vi の操作
hjkl : カーソル
:w ファイル保存

## hello worldのC言語プログラムを作成
```C
#include <stdio.h>
int main(int argc, char * argv[])
{
puts("hello world");
return 0;
}
```
