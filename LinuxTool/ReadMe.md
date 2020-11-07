#Linuxツールについて

参考：<u> </u>

**目次**

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [Linuxツールについて](#linuxツールについて)
  - [vim](#vim)
    - [便利コマンド](#便利コマンド)
  - [ctags](#ctags)
  - [tmux](#tmux)
  - [git関連](#git関連)
  - [tig](#tig)

<!-- /code_chunk_output -->

---

## vim
カスタマイズには~/**.vimrc**に下記内容を追記
```
#####.vimrc#####
"vim起動時に行番号を表示する
set number

" vim起動中のコメントの色を設定
hi Comment ctermfg=DarkCyan

" 検索結果をハイライト
set hlsearch

"vim起動時に編集中のファイル名を表示
set laststatus=2

"フルパス表示
set statusline=%F

```
### 便利コマンド
* ファイル、ウィンドウ操作
参考サイト：https://qiita.com/ykyk1218/items/ab1c89c4eb6a2f90333a
    * ```:tabe ファイル名```：新規タブ作成
    * ```:sp ファイル名```：縦分割
    * ```:vsp ファイル名```：横分割
    * ```u```：アンドゥ
    * ```ctrl+r```：リドゥ
<br>

* 矩形選択
ctrl+v
//複数行入力
Shift+i
esc
<br>

* 移動系
参考サイト：https://qiita.com/takeharu/items/9d1c3577f8868f7b07b5
    * ```ctrl+i```：一つ次の画面へ進む 
    * ```ctrl+o```：一つ前の画面へ進む 
<br>

* 検索系
    * ```:vim 検索ワード ** | cw```：カレントディレクトリから検索
<br>

* 中断、再開
    * ```ctrl+z```：vim中断
    * ```fg 番号```：指定した番号のvim再開
    ※ターミナルコマンドに実行可能
    * ```$jobs```：中断中のジョブを確認
    ※ターミナルコマンドに実行可能
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
    * ```CTRL-]```: 現在のウィンドウでタグジャンプ
    * ```CTRL-W]```: ウィンドウを分割してタグジャンプ

## tmux
役割：シェルを分割することで、複数の処理を同時に行いやすくできる
参考サイト：https://qiita.com/ysuzuki19/items/58cd8ac6a79849308fef

カスタマイズには~/**.tmux.conf**に下記内容を追記
```
#####.tmux.conf#####
#ペイン選択用
set display-panes-time 3000

#prefixキーをC-fに設定
set -g prefix C-j

# マウス操作を有効にする
set-option -g mouse on

# ウィンドウのインデックスを１から始める
set -g base-index 1

# ペインのインデックスを１から始める
setw -g pane-base-index 1


# \でペインを縦分割
bind \ split-window -h

# -でペインを横分割
bind - split-window -v

# Vimのキーバインドでペインを移動する
bind h select-pane -L
bind j select-pane -D
bind k select-pane -U
bind l select-pane -R
bind -r C-h select-window -t :-
bind -r C-l select-window -t :+

# Vimのキーバインドでペインをリサイズする
bind -r H resize-pane -L 5
bind -r J resize-pane -D 5
bind -r K resize-pane -U 5
bind -r L resize-pane -R 5

#ステータスバーをトップに配置する
set-option -g status-position top

#左右のステータスバーの長さを決定する
set-option -g status-left-length 90
set-option -g status-right-length 90

# コピーモードの設定（Vim風にする）
setw -g mode-keys vi

#256 color terminal
set -g default-terminal "screen-256color"
```

## git関連
GitUsage/ReadMe.mdを参照

## tig
役割：gitの履歴が見れたり検索に便利
参考サイト：https://qiita.com/suino/items/b0dae7e00bd7165f79ea

色のカスタマイズには~/**.tigrc**に下記内容を追記
```
#####.tigrc#####
# color Settings
color default white black
color cursor default magenta
color status white green bold
color date cyan default
color delimiter cyan default
color line-number yellow default
color diff-header yellow default
color diff-index cyan default
color diff-chunk magenta default
color diff-stat cyan default
color "Reported-by:" green default
color graph-commit cyan default
color grep.file cyan default
```

[TOPへ](#linuxツールについて)
