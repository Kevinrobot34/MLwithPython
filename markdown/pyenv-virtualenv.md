pyenvの賢い仮想環境管理ツール

## Reference
* https://github.com/pyenv/pyenv-virtualenv
    *  この資料は全てここに書かれている情報を和訳・要約している．


## Installation & settings
### MacOS
1. **brew**
	```
	$ brew install pyenv-virtualenv
	```
2. **`~/.bash_profile`にpyenv-vitualenvを初期化する文を追加**
	```
	$ echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bash_profile
	```
    * これにより自動で仮想環境がactivateされるようになる．
3. **仮想環境を作る**
	```
	$ pyenv virtualenv 3.6.7 venv367
	```
4. **作った仮想環境を実際に使うpythonとして設定する**

	```
	$ pyenv global venv367
	```
    or

	```
    $ cd ~/project/directory
    $ pyenv local venv367  
	```
    etc.



## Commands
* 仮想環境を作る
	```
	$ pyenv virtualenv 3.6.7 venv_name
	```
    *  `pyenv vitualenv`コマンドは，pythonのバージョン名とこれから作る仮想環境の名前を指定して使う．
    * `$(pyenv root)/versions`の下に`venv_name `というフォルダができる．
* 存在する仮想環境のリストアップ
	```
	$ pyenv virtualenv**s**
        3.6.7/envs/venv367 (created from /Users/hoge/.pyenv/versions/3.6.7)
      * venv367 (created from /Users/hoge/.pyenv/versions/3.6.7)
	```
    * 各仮想環境に対して２つずつエントリーがあるが，短い方はシンボリックリンク．
* 手動で仮想環境をactivate/deactivateする
	```
	$ pyenv activate venv_name
	```
	```
	$ pyenv deactivate
	```
* 仮想環境の消去
	```
	$ pyenv uninstall venv_name
	```



## Note
### virtualenvとvenv
python3.3以降，標準でモジュール`venv`が提供されている．
pyenv-virtualenvでは`venv`が使用可能でかつ`virtualenv`が使用不可能な場合，`python -m venv`を使うことになっている．

### `$ pip install -r requirements.txt` する時
versionとか順番によって怒られたりするので注意
* numpyは初めの方に入れる
* boto3, botocore, awscli辺りの各バージョンに注意
    * **`boto3 1.7.65 has requirement botocore<1.11.0,>=1.10.65, but you'll have botocore 1.12.71 which is incompatible.`** 的な文言が出てくるので注意
* spaCyの辞書(en-core-web-sm)やsudachiの辞書は後から入れる ( [参考](https://spacy.io/models/en) )
