# Linuxツールについて

参考：<u> </u>

**目次**

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [Linuxツールについて](#linuxツールについて)
  - [vim](#vim)
  - [ctags](#ctags)
  - [tmux](#tmux)
  - [git関連](#git関連)
  - [tig](#tig)

<!-- /code_chunk_output -->

---

## vim
カスタマイズには`~/.vimrc`に下記内容を追記

[.vimrc](https://github.com/masamasagorira/VIM-Master/tree/main/LinuxTool/.vimrc)


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
    * ```CTRL-]```: 現在のウィンドウでタグジャンプ
    * ```CTRL-W]```: ウィンドウを分割してタグジャンプ

## tmux
役割：シェルを分割することで、複数の処理を同時に行いやすくできる

参考サイト：https://qiita.com/ysuzuki19/items/58cd8ac6a79849308fef

カスタマイズには`~/.tmux.conf`に下記内容を追記

[.tmux.conf](https://github.com/masamasagorira/VIM-Master/tree/main/LinuxTool/.tmux.conf)

## git関連
GitUsage/ReadMe.mdを参照

## tig
役割：gitの履歴が見れたり検索に便利

参考サイト：https://qiita.com/suino/items/b0dae7e00bd7165f79ea

色のカスタマイズには`~/.tigrc`に下記内容を追記

[.tigrc](https://github.com/masamasagorira/VIM-Master/tree/main/LinuxTool/.tigrc)

[TOPへ](#linuxツールについて)
