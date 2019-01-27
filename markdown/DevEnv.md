# 環境構築

## Introduction
MacOSにはデフォルトでpythonが入っています．しかしpython2です．
```
$ which python
/usr/bin/python
$ python -V
Python 2.7.10
```

pythonにはversionが2と3があります．
基本的にこれからpythonを使い始める人は3を使っておけば問題ないでしょう．
実際公式も次のように述べています．
> Should I use Python 2 or Python 3 for my development activity? <br>
> What are the differences? <br>
> Short version: Python 2.x is legacy, Python 3.x is the present and future of the language

ということで，まずはpython3をインストールしていきます．


## Pythonの準備(簡単編)
brewを使って最新のpython3をインストールします．
```
$ brew install python3
```
インストールできたか確認します．
```
$ which python3
/usr/local/bin/python3
$ python3 -V
Python 3.7.1    # バージョン違うかもですが気にしないでください
```

### Note: バージョン管理
python3の中にも3.5, 3.6, 3.7などなど，様々なバージョンがあります．
上記のインストール方だと最新のpythonが入りますが，場合によってはこれが困ることがあります．
例えば，[TensorFlow](https://www.tensorflow.org)という深層学習などに使われる
ライブラリーは，

> Requires Python 3.4, 3.5, or 3.6

となっているため，3.7のままでは使えないです．
こういった事情から「pythonのバージョンを適宜切り替えて使いたい」という要望が出てきますが，
**pyenv** というツールを使えばこれが可能です．
詳細は [こちら](pyenv.md) にまとめているので，興味がある人は見てください．


## pythonを使ってみる
実際にpythonを使ってみましょう．

### 使い方１: 対話モード
ターミナルで`python3`と打ち込んでみましょう．
(初めの文言は多少違うかもしれませんが気にしないでください．)
```
$ python3
Python 3.7.1 (default, Nov 28 2018, 11:51:47)
[Clang 10.0.0 (clang-1000.11.45.5)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>>
```
ここに適宜数式を打ち込むと電卓のように使えたりします．
```
>>> 2 + 2
4
>>> 50 - 5*6
20
>>> (50 - 5*6) / 4
5.0
>>> 8 / 5  # division always returns a floating point number
1.6
```
このように行ごとに処理結果を返してくれます．
これを対話モード (interactive mode) といいます．

終了するには`Ctrl + D`を押すか，以下を入力してください
```
>>> exit()
$
```

### 使い方２: pythonスクリプト
対話モードのように逐次的に処理をするのではなく，`hoge.py`というようなスクリプトファイルに
処理を書いてまとめて実行することもできます．

例えば好きなエディターで，以下のような`hello.py`を作ってみましょう．
```
print("Hello, World!")
print(2 + 3)
```
これを次のように実行できます．
```
$ python3 hello.py
Hello, World!
5
```

### 使い方３: jupyter-notebook
実際に様々な作業をしていると上記二つの使い方の中間くらいの使い方ができると嬉しかったりします．
これを実現してくれるのがjupyter-notebookです．

<img src="/picture/ipynb_sample1.png" width="500">

「Mathematicaのようにセルごとに実行していけるもの」と考えてもらうと分かりやすいかもしれません．

次のページでjupyter-notebookのセットアップをしていきましょう．

[> Next: Jupter Notebook](JupyterNotebook.md)

[Topへ戻る](https://github.com/Kevinrobot34/MLwithPython)
