Pythonで一通り機械学習などを出来るようになるためのnotebookなどをまとめたものです．

## 目的
* 自分のPCでPythonの環境構築を完了させること．
* Pythonの文法をざっくり把握すること．
* sklearnやchainerといったライブラリーを使った簡単な機械学習のコードを動かせるようになること．
    * （またその内容の理解をすること．）


## 対象読者
以下を満たす人を想定しています．
* MacOSのユーザーでbrewなどは使える人．
    - 他のOS(特にLinux)でもある程度参考になるとは思います．
    - 簡単なコマンドライン操作はできることを想定します．
* Pythonは初めて触る人．
    - ただし，CやFortranやJavaなど何かしらの別の言語には触れたことがある人．
    - 変数や関数といった概念はざっくりと分かっていることを想定します．


## Contents
* 環境構築
    - [pythonの準備](markdown/DevEnv.md)
        - [pyenvによるpythonのインストール](markdown/pyenv.md)
        - [pyenv-virtualenvによる仮想環境の整備](markdown/pyenv-virtualenv.md)
    - [Jupyter Notebookの設定](markdown/JupyterNotebook.md)
* [pythonの文法overview](notebook/PythonGrammar.ipynb)
* [pandasによるデータ処理](notebook/pandas.ipynb) (under construction)
* [matplotlibによる可視化](notebook/matplotlib.ipynb)
* [scikit-learnによる機械学習](notebook/sklearn.ipynb) (under construction)
* [chainerによる深層学習](notebook/chainer_MNIST.ipynb)


## 追加予定な内容
* pythonの文法overview
    * file読み書き，クラスの定義・継承など，リスト内包表記
    * 自作モジュールのimport
