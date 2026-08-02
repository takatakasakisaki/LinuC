# プログラムの実行
 - 実行権必要
   拡張子は無関係(winのexe,bat,cmdとか).強いてつけるなら、ELF形式の実行ファイルなら.out
 - インタプリタの指定
   実行ファイル(機械語のファイルELF形式)以外は、何で実行するかを先頭行`#!`で記述する。
   ```bash
   #!/bin/bash
   ```
  - PATHに設定しているディレクトリから探す
  - カレントの実行ファイルは./a.out のように`./`から始める。
    または、絶対PATHで指定する/home/user/a.out
    カレントはPATHに含まれない
    
# 環境変数   environment variables
  - 実行時のプログラム外の変数
  - シェルでは  `$`+環境変数名
    $HOME,$PWD,$PATH,$SHELL,$USER など
  - 環境変数への設定 export
    ```
    export  VAR1="abc"
    export VAR2="$VAR1/a.c"    <-- 既存の変数に連結
    ```
    `"～"`で囲うと`$VAR`は環境変数の内容に置き換えられる
    `'`(シングルクォーテーション)でくくるとそのままの文字になる
  - 環境変数一覧を確認 `env`, `printenv`
  - env, printenv 環境変数一覧表示
  - let 整数値の格納,計算
    ``` bash
    let a=10
    let b=a+1  <--- 11が入る
    let c=0x10  <-- 16が入る 16進数
    ```

# unix 便利コマンド
- echo   文字列表示
  ```
  echo "input any key"
  echo "$HOME"
  ```
- grep,egrep
  文字列をファイルの中から探す
- find
  ファイルの探索
　```bash
   find . -name '*.c'   現在のディレクトリ以下から、.cの拡張子のファイルを探索
  ```
- sed   ストリームエディタ
  ファイルの内容を自動編集して出力
   `sed -e 's/^ethtool/#ethtool'`
# パイプ
直前のコマンドの標準出力を、次のコマンドの標準入力にする
```bash
grep  define *.c | grep stdio    defineを検索し、検索結果からさらにstdioが含まれる行だけを抽出
```

# コマンド実行結果をコマンド引数にする
  ```bash
  ll `find -name *.c`   findでｃファイルを探し、ls -l で詳細を表示
  ```



#  Linuxの起動
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

# プログラム実行
実行ファイル、　共有ライブラリ
ファイル形式はELF
実行ファイル = .exe , 共有ライブラリ(shared object)= DLL  
ABSと、ダイナミックリンクタイプ
ABSは全部リンクされている。ダイナミックリンクは、soを動的にリンクする


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



