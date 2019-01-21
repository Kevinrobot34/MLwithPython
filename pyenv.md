# PyenvによるPythonの準備
pyenvを用いてpythonの開発環境を構築する．

## Installation & Setting
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

### usage

## Reference
* [pyenv-Github](https://github.com/pyenv/pyenv)
    * かなり丁寧にREADMEが書かれている．これを落ち着いて読むべし．
* [pyenv-Github-Commands](https://github.com/pyenv/pyenv/blob/master/COMMANDS.md)
    * 便利なコマンド一覧．具体的な使い方を知りたいときはこれを見るのが一番．
