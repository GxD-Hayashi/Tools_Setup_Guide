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
6. 最後に「Install」をクリックしてインストール。

## putty のインストールと設定
　　https://www.ranvis.com/putty ※日本語版 \
　　https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html ※公式サイト

1. ダウンロードした .msi をダブルクリックしてインストーラを起動。
2. セットアップウィザードに従い、次へを押していきます。
3. インストールディレクトリ（通常はそのままでOK）を指定。
4. 最後に「Install」をクリックしてインストール。
5. デスクトップのputtyアイコンをダブルクリック
6. ホスト名（またはIPアドレス）項目に \<username\>@192.168.9.100 を入力（usernameはIT担当に聞いてください）
  <p align="center">
    <img src="https://github.com/user-attachments/assets/bb5db04f-820c-4ef3-94cd-623edebbabe7" width="300">
  </p>
  
7. 左側のカテゴリ>接続>SSH>X11 を選択し、「X11転送を有効にする」のチェックボックスをONにする。
  <p align="center">
    <img src="https://github.com/user-attachments/assets/a9534c83-bf7b-400f-aeac-4a51013b35de" width="300">
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

## IGVの起動
1. Xmingのアイコンをダブルクリック（バックグランドで動作するため、デスクトップ上の変化はありません）
2. FortiClient VPN を起動し、VPN接続を開始する。
3. puttyのアイコンをダブルクリック
4. 作成したセッションを選択し、開くボタンを押下。
5. パスワードを入力してログイン。
6. igv + Enter でIGVを起動する
   
リファレンスゲノムの表示には以下のファイル使用する。\
　　/data1/home/geninus1/ncbiRefSeq.txt.gz \
検体データの表示には以下のファイルを使用する。\
　　/data1/data/result/eWES/<batch>/<sample ID>/Preprocessing/align/<sample ID>.tumour.recaled.bam \
IGVの操作方法については以下サイトの User Guide 項目を参照 \
　　https://igv.org/doc/desktop/

