# IGV-setup
GxD環境におけるIGVのセットアップ方法。

## Xming のインストール
　　https://sourceforge.net/projects/xming/  (ミラーサイト ※旧版) \
　　http://www.straightrunning.com/XmingNotes/ (公式サイト ※有料) 

1. ダウンロードした .exe をダブルクリックしてインストーラを起動。
2. セットアップウィザードに従い、次へを押していきます。
3. インストールディレクトリ（通常はそのままでOK）を指定。
4. 「Start Menu Folder」などのオプションを選択する。\
  （Create a desktop icon for XmingのチェックボックスをONにする。他はそのままでOK。）
6. 最後に「Install」をクリックしてインストールを完了する。

## putty のインストールと設定
　　https://www.ranvis.com/putty ※日本語版 \
　　https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html ※公式サイト

1. ダウンロードした .msi をダブルクリックしてインストーラを起動。
2. セットアップウィザードに従い、次へを押していきます。
3. インストールディレクトリ（通常はそのままでOK）を指定。
4. 最後に「Install」をクリックしてインストール。
5. デスクトップのputtyアイコンをダブルクリックして起動する。
6. ホスト名（またはIPアドレス）項目に \<username\>@192.168.9.100 を入力（usernameはサーバ管理者に聞いてください）
  <p align="center">
    <img src="https://github.com/user-attachments/assets/bb5db04f-820c-4ef3-94cd-623edebbabe7" width="300">
  </p>
  
7. 左側のカテゴリ>接続>SSH>X11 を選択し、「X11転送を有効にする」のチェックボックスをONにする。
  <p align="center">
    <img src="https://github.com/user-attachments/assets/857b5ba7-4eda-4d31-8069-0e1174574ba4" width="300">
  </p>
  
8. セッションに名前をつけて保存する。
  <p align="center">
    <img src="https://github.com/user-attachments/assets/293963f8-790f-4754-b0e8-121e518eee48" width="300">
  </p>
  
9. 作成したセッションを選択し、開くボタンを押下
10. 開かれたウィンドウでパスワードを入力する。
11. ~/bin/ の下に以下記載したテキストファイル igv を作成して保存し、実行権限を付与する。
```
singularity exec --disable-cache -B /data1 /data1/GxD_eWES/Pipeline/containers/geninus_igv.sif igv
```
12. ~/igv/genomes/ の直下に GxD.json を格納する。

## IGVの起動
1. Xmingのアイコンをダブルクリックする。（バックグランドで動作するため、デスクトップ上の変化はありません）
2. FortiClient VPN を起動し、VPN接続を開始する。
3. puttyのアイコンをダブルクリックしてputtyを起動する
4. 作成したセッションを選択し、開くボタンを押下。
5. パスワードを入力してログイン。
6. igv + Enter でIGVを起動する。
7. 上部左端のドロップダウンリストから「GxD Human（GRCh38）」を選択してリファレンスを表示する。

検体データの表示には以下のファイルを使用する。
|解析種別 | type       | 解析フォルダの相対パス                                                                |
|:-------:|:-----------|:--------------------------------------------------------------------------------------|
|eWES     |align       |*/\<sample ID\>/Preprocessing/align/\<sample ID\>.tumour.recaled.bam                                 |
|WTS      |Expression  |*/\<sample ID\>/Expression/STAR_align_exp/\<sample ID\>.Aligned.sortedByCoord.out.bam                |
|WTS      |STAR-SEQR   |*/\<sample ID\>/Fusion/STAR-SEQR/\<sample ID\>_STAR-SEQR/\<sample ID\>.Aligned.sortedByCoord.out.bam |
|WTS      |STAR-Fusion |*/\<sample ID\>/Fusion/STAR-Fusion/STAR_align_starfu/\<sample ID\>.star-fusion.Aligned.out.sam       |
|WTS      |arriba      |*/\<sample ID\>/Fusion/Arriba/STAR_align_arriba/\<sample ID\>.Aligned.out.bam                        |

　　※ WTS(Expression), WTS(STAR-SEQR) をロードする場合は *.bam.bai ファイルを作成する。\
　　※ WTS(STAR-Fusion)をロードする場合は ソートして変換したbamを作成し、 *.bam.bai ファイルを作成する。\
　　※ WTS(arriba)をロードする場合はソートしたbamを作成し、 *.bam.bai ファイルを作成する。

IGVの操作方法については以下サイトの User Guide 項目を参照 \
　　https://igv.org/doc/desktop/

## WinSCP のインストールと設定 ※必要に応じて実行
　　https://winscp.net/eng/download.php

1. ダウンロードした .exe をダブルクリックしてインストーラを起動。
2. セットアップウィザードに従い、次へを押していきます。
3. インストールディレクトリ（通常はそのままでOK）を指定。
4. 最後に「インストール」をクリックしてインストール。
5. デスクトップのWinSCPアイコンをダブルクリックして起動する。
6. ホスト名: 192.168.9.100, ユーザ名: \<username\> を入力し、セッション名をつけて保存する。
