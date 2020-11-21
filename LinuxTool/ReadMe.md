# Linuxツールについて

参考：<u> </u>

**目次**

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [Linuxツールについて](#linuxツールについて)
  - [vim](#vim)
    - [便利コマンド](#便利コマンド)
    - [便利なプラグイン](#便利なプラグイン)
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
    * ```:tabo```：現在のタブ以外全て閉じる
    * ```:sp ファイル名```：縦分割
    * ```:vsp ファイル名```：横分割
    * ```ctrl+w → Shift+t```：分割したファイルを新規タブへ移動
    * ```ctrl+w → c```：選択しているファイルを閉じる
    * ```ctrl+w → o```：選択しているファイル以外の分割したファイルを全て閉じる
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

### 便利なプラグイン
参考サイト：https://qiita.com/reireias/items/5364dcaada1a5b88a206<br>
特に便利だと思ったプラグインの一部を紹介する<br>
※今回は```vim-plug```をベースにインストールを行った

* nerdtree<br>
	* 概要：ディレクトリ構造を表示する
	* 参考サイト：https://qiita.com/zwirky/items/0209579a635b4f9c95ee

* winresizer<br>
	* 概要：分割したウィンドウサイズの変更を高速に行う
	* 参考サイト：https://qiita.com/simeji/items/e78cc0cf046acc937226<br>

* vim-fugitive<br>
	* 概要：vim起動中にgit操作を可能にする
	* 参考サイト：<br>
		* https://doruby.jp/users/kurita/entries/fugitive-vim%E3%81%A7vim%E4%B8%8A%E3%81%A7git%E6%93%8D%E4%BD%9C%E3%82%92%E3%81%97%E3%82%88%E3%81%86%EF%BC%81
		* https://qiita.com/hyshhryk/items/4936c4412daa866daf7d  

* vim-airline<br>
	* 概要：vim起動中に表示されるstatusバーをカスタマイズする
	* 参考サイト：<br>

* previm<br>
	* 概要：編集中のmarkdownのプレビューを表示する<br>
	※今回はWSLをベースで設定したので注意
	* 参考サイト：
		* https://coriandered.com/ja/posts/previm/<br>
		* https://blackhawk888.github.io/blog/2018/02/08/vim-markdown/

<br>.vimrcへの記述例を下記に示す
```
" #######################プラグイン機能########################## 
call plug#begin()

" ファイルをtree表示してくれる
Plug 'scrooloose/nerdtree'
" windowサイズを高速に変更
Plug 'simeji/winresizer'
" vim起動中にgit操作を可能にする
Plug 'tpope/vim-fugitive'
" statusバーの表示をカスタマイズ
Plug 'vim-airline/vim-airline'
Plug 'vim-airline/vim-airline-themes'
" markdownのプレビューを表示する
Plug 'kannokanno/previm'

call plug#end()

" #####nerdtreeに関して#####
"ctrl+aでtree表示
nnoremap <silent><C-a> :NERDTreeToggle<CR>
"treeのdir色を変更
hi Directory guifg=#FF0000 ctermfg=Cyan

" #####MarkdownPreviewに関して#####
" 表示ブラウザの設定
let g:previm_open_cmd = '/mnt/c/Program\ Files\ \(x86\)/Google/Chrome/Application/chrome.exe'
let g:previm_wsl_mode = 1
" Ctrl+pでプレビュー
nnoremap <silent> <C-p> :PrevimOpen<CR>
" 変更がリアルタイムで反映される
let g:previm_enable_realtime = 1


```

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
