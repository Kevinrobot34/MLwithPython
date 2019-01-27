# PyenvによるPythonの準備
pyenvを用いてpythonの開発環境を構築する．

## Installation & Setting for MacOS Users
1. pyenvのインストール
    <pre>
    $ brew update
    $ brew install pyenv </pre>

2. pyenvの機能や自動補完を使えるように`~/.bash_profile`を編集する
    <pre>
    $ echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.bash_profile </pre>

3. ターミナルを再起動する

4. [pyenv wiki](https://github.com/pyenv/pyenv/wiki)を読んで必要そうなものをインストールする
    <pre>
    $ xcode-select --install
    $ brew install openssl readline sqlite3 xz zlib
    </pre>
    Mojave以降のOSを使っている場合は以下も必要．
    <pre>
    $ sudo installer -pkg /Library/Developer/CommandLineTools/Packages/macOS_SDK_headers_for_macOS_10.14.pkg -target /
    </pre>

5. 好きなpythonをインストールする(今回は3.6.7)
   <pre>$ pyenv install 3.6.7</pre>

6. インストールしたバージョンを実際に設定する
   <pre>$ pyenv global 3.6.7</pre>


## Commands
基本的には [pyenv-Github-Commands](https://github.com/pyenv/pyenv/blob/master/COMMANDS.md) を見れば解決するはず．
* `$(pyenv root)`の確認
    <pre> $ pyenv root</pre>
    * defaultでは`~/.pyenv/`

* pyenvで利用可能なpythonのバージョンを列挙
    <pre>$ pyenv install --list</pre>
    * or <code>$ pyenv install --list | grep 3.6</code> and so on.

*  特定のバージョンのpythonをpyenvで使えるようにインストールする
   <pre>$ pyenv install 3.6.7</pre>
    * `$(pyenv root)/versions/3.6.7/`にpython3.6.7が入る．

* pyenvにインストールされているバージョンを確認する
  <pre>$ pyenv versions
  system
  * 3.6.7 (set by /Users/hoge/.pyenv/version)</pre>
    * 現在アクティブになっているバージョンの横に*がつく

* `python`や`python3`などのコマンドのフルパスを表示する
  <pre>$ pyenv which python3.6
  /Users/hoge/.pyenv/versions/3.6.7/bin/python3.6</pre>
    * `$which python3.6`だと，`/Users/hoge/.pyenv/shims/python3.6`などとなってしまう．

* グローバルなpythonのバージョンの設定をする．<pre>$ pyenv global 3.6.7</pre>
    * `$(pyenv root)/version`にバージョン名を書き込んでいる．
    * `$ pyenv global {version name}`は実はかなり賢い！詳細は[ここ](https://github.com/pyenv/pyenv/blob/master/COMMANDS.md#pyenv-global)

* ローカルなpythonのバージョンを設定する(あるディレクトリ以下のpythonのバージョンを指定する)．<pre>$ pyenv local 3.6.7</pre>

## How pyenv works
### directory structure
```
$(pyenv root)
├── shims
│   ├── pip
│   ├── pip3
│   ├── pip3.6
│   ├── python
│   ├── python3
│   ├── python3.6
│   ...
├── version
└── versions
    ├── 3.6.7
    ├── 3.4.5
    ...
```
* `$(pyenv root)`
    * pyenvのもろもろが入ってる．デフォルトでは`~/.pyenv`．
* `$(pyenv root)/shims/`
    * 環境変数`PATH` の最上位に設定されるディレクトリ．
* `$(pyenv root)/version`
    * `$ pyenv global {version_name}`で設定されたバージョン名が記載された**ファイル**
* `$(pyenv root)/versions/`
    * `$ pyenv install {version_name}`でインストールされたpythonたちが入ってるディレクトリ．

### Understanding shims
プログラムのバージョンや環境間の差異を埋める緩衝材のような役割をするライブラリーのことを **shims(=詰め木)** と呼んだりする．
まさにpyenvのことやん．

* https://en.wikipedia.org/wiki/Shim_(computing)

pyenvは`$(pyenv root)/shims/`内に以下の **Choosing the Python Version** に従って特定のバージョンのパスを渡すような各種実行ファイル(`pip`, `python`, `python3` etc.)を置いている．
この`$(pyenv root)/shims`を`$PATH`の最上位に追加することで，shimとしての役割を実現している．具体的には，例えば`pip`をコマンドラインで実行すると，
* `$PATH`内の各パスに`pip`がないか探す．
* `$(pyenv root)/shims/pip`を見つける．
* `$(pyenv root)/shims/pip`が実行され，**Choosing the Python Version** に従って特定のバージョンの`pip`実行ファイルを探し実行される．

となる．


### Choosing the Python Version
shimの中の`python`といった実行ファイルが実行されると，pyenvはどのバージョンを使うのかを以下の優先度で決定する．
1. 環境変数`PYENV_VERSION`で指定されているバージョン
    * [$ pyenv shell](https://github.com/pyenv/pyenv/blob/master/COMMANDS.md#pyenv-shell) で設定できる．
2. カレントディレクトリにある`.python-version`ファイル内で指定されているバージョン
    * [$ pyenv local](https://github.com/pyenv/pyenv/blob/master/COMMANDS.md#pyenv-local) で設定できる．
3. 最も近くの親ディレクトリにある`.python-version`ファイル内で指定されているバージョン
4. `$(pyenv root)/version`ファイル内で指定されているバージョン
    * [$ pyenv global](https://github.com/pyenv/pyenv/blob/master/COMMANDS.md#pyenv-global) で設定できる．
5. 上記どれも指定されていなければ，"system"のpythonが使われる．

2.と3.によって，特定のプロジェクトのrootで`$ pyenv local {version name}`をしておくと，そのプロジェクトフォルダ内ではどこでも指定したバージョンのpythonが使えるようになっている．

## Reference
* [pyenv-Github](https://github.com/pyenv/pyenv)
    * かなり丁寧にREADMEが書かれている．これを落ち着いて読むべし．
* [pyenv-Github-Commands](https://github.com/pyenv/pyenv/blob/master/COMMANDS.md)
    * 便利なコマンド一覧．具体的な使い方を知りたいときはこれを見るのが一番．
* [How to manage multiple Python versions and virtual environments](https://medium.freecodecamp.org/manage-multiple-python-versions-and-virtual-environments-venv-pyenv-pyvenv-a29fb00c296f)
    * pythonのバージョン管理や仮想環境についてまとめてくれてるブログ

[Topへ戻る](../README.md)
