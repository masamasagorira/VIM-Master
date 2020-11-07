# Linuxツールについて

参考：<u> </u>

**目次**

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [Linuxツールについて](#linuxツールについて)
  - [vim](#vim)
    - [便利コマンド](#便利コマンド)
  - [ctags](#ctags)
  - [tmux](#tmux)
    - [小技](#小技)
  - [git関連](#git関連)
  - [tig](#tig)

<!-- /code_chunk_output -->

---

## vim
カスタマイズには`~/.vimrc`に下記内容を追記

[.vimrc](https://github.com/masamasagorira/VIM-Master/tree/main/LinuxTool/.vimrc)

### 便利コマンド
* ファイル、ウィンドウ操作
参考サイト：https://qiita.com/ykyk1218/items/ab1c89c4eb6a2f90333a
    * ```:tabe ファイル名```：新規タブ作成
    * ```:sp ファイル名```：縦分割
    * ```:vsp ファイル名```：横分割
    * ```:数値 → ctrl+w → < ```：分割ウィンドウを指定した分リサイズ
    * ```u```：アンドゥ(直前の編集取り消し)
    * ```ctrl+r```：リドゥ(アンドゥの逆)
<br>

* 選択系
    * ```v```：選択モード
    * ```ctrl+v```：矩形選択モード
    * ```Shift+i → 入力文字 → esc```：複数行入力
    ※矩形選択モード中に実行可能
<br>

* 移動系
参考サイト：https://qiita.com/takeharu/items/9d1c3577f8868f7b07b5
    * ```ctrl+i```：一つ次の画面へ進む 
    * ```ctrl+o```：一つ前の画面へ進む 
<br>

* 検索系
    * ```:vim 検索ワード ** | cw```：カレントディレクトリから検索
<br>

* 自動補完
    * ```:ctrl+p```or```:ctrl+n```：単語の自動補完
    ※挿入モード中に実行可能
<br>

* 中断、再開
    * ```ctrl+z```：vim中断
    * ```fg 番号```：指定した番号のvim再開
    ※ターミナルコマンドにて実行可能
    * ```jobs```：中断中のジョブを確認
    ※ターミナルコマンドにて実行可能
<br>

## ctags
役割：ソースコード内の任意の関数の定義にジャンプする

参考サイト：https://maku77.github.io/vim/advanced/tags.html

* ctagsのインストール
    下記コマンド実行
    >sudo apt install exuberant-ctags
* tagsファイルの作成
    下記コマンド実行
    >ctags -R

* Vim に tags ファイルの検索パスを設定する
    ~/**.vimrc**に下記内容を追記
    ```
    #####.tmux.conf#####
    "親ディレクトリを上って tags ファイルを検索
    set tags=./tags;,tags;
    ```

* 定義位置にジャンプする
    * ```ctrl+]```: 現在のウィンドウでタグジャンプ
    * ```ctrl+W+]```: ウィンドウを分割してタグジャンプ

## tmux
役割：シェルを分割することで、複数の処理を同時に行いやすくできる

参考サイト：https://qiita.com/ysuzuki19/items/58cd8ac6a79849308fef

カスタマイズには`~/.tmux.conf`に下記内容を追記

[.tmux.conf](https://github.com/masamasagorira/VIM-Master/tree/main/LinuxTool/.tmux.conf)

### 小技
* WSL+tmux⇔ホストOS間(Windows)でコピペ
参考サイト：https://qiita.com/s4kr4/items/91e5de920ae1e09bf667
    * ```Shift+右クリック```or```Shift+insertキー```：ペースト
    


## git関連
GitUsage/ReadMe.mdを参照

## tig
役割：gitの履歴が見れたり検索に便利

参考サイト：https://qiita.com/suino/items/b0dae7e00bd7165f79ea

色のカスタマイズには`~/.tigrc`に下記内容を追記

[.tigrc](https://github.com/masamasagorira/VIM-Master/tree/main/LinuxTool/.tigrc)

[TOPへ](#linuxツールについて)
