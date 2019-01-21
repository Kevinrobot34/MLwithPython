# Jupyter Notebook の設定


## Reference
* https://jupyter.readthedocs.io/en/latest/index.html
    * 公式ドキュメント
* http://jupyter.org/install
    * Jupyterのinstallに関して
* https://ipython.readthedocs.io/en/latest/install/kernel_install.html
    * kernelの追加に関して


## Introduction
Jupyter Notebookはブラウザ上で動作するアプリケーションで，
コードやMarkdownテキスト・図などが共存するドキュメントを簡単に作ることができるツールです．

<img src="https://github.com/Kevinrobot34/MLwithPython/blob/master/picture/ipynb_sample1.png" width="400">

## Installation
まずpipを最新のバージョンにする．
```
$ pip3 install --upgrade pip
```
そしてjupyterをインストールする．
```
$ pip3 install jupyter
```

## Usage
### Starting the Notebook Server
ターミナルで適当なディレクトリに移動し，
```
$ jupyter-notebook
```
と実行すると，コマンドを実行したディレクトリをルートとしてNotebook Dashboardが開く．

<img src="https://github.com/Kevinrobot34/MLwithPython/blob/master/picture/notebook_dashboard.png" width="500">

### Creating a Notebook
GUIを操作すれば簡単に作れる．

* GUIを操作し適当なディレクトリに移動
* 右上の**New**からNotebookの使いたいKernelを選択

でNotebookができる．

### Manipulation in Notebook
Jupyter Notebookには２つの入力モードがある
* **Edit Mode**
    * 実際にセル内のコードやテキストを編集するモード．セルの枠が緑色になる．
    * `Enter`を押すとこのモードになる．
* **Command Mode**:
    * セル間の移動やセルの挿入・削除といったセル単位の操作をするモード．セルの枠が青色になる．
    * `Esc`を押すとこのモードになる．

セル内にコードを書き，`Shift + Enter`でそのセル内の処理を実行できる．


## Kernel周り
### Kernelの確認
<pre>
$ jupyter kernelspec list
</pre>
出力は
<pre>
Available kernels:
  python3       /Users/hoge/Library/Jupyter/kernels/python3
  tensorflow    /Users/hoge/Library/Jupyter/kernels/tensorflow
</pre>
的な感じ．ここで表示されるパスの中の`kernel.json`というファイルを見ると，どこのpythonを使っているかやdisplay-nameなどの情報が書かれている．

### Kernelの追加
Kernelとして追加したいPython環境をActivateさせた状態で，
<pre>
$ python -m pip install ipykernel
$ python -m ipykernel install --user --name other-env --display-name "Python (other-env)"
</pre>
とする．`other-env`や`Python (other-env)`のところは好きに決めてOK．
* display-name : jupyter-notebookやHydrogenのKernel選択で出てくる名前
* name : `jupyter kernelspec list`をした時に出てくる名前，Kernelの削除とかするときに指定する名前

#### 注意
以上の設定で追加されるKernelのバージョンはここで使った`python`に当然依存する．
追加する前に，
<pre>
$ python -V
</pre>
でバージョンを確認したり，
<pre>
$ which python
</pre>
でどこにあるpythonなのか確認したりしよう．
必要に応じて`python`を`python3`に置き換えたりして適宜実行してください．

### Kernelの削除
<pre>
$ jupiter kernelspec uninstall [kernelname]
</pre>


## Jupyter-Notebookの環境設定
### Fontの設定
NotebookのcodeのFontは好きなように指定できる．
`~/.jupyter/custom/custom.css`を編集し以下などのようにしておけば良い．
<pre>
.CodeMirror pre, .output pre {
  font-family: Menlo, Consolas, "DejaVu Sans Mono", monospace;
  font-size: 10pt;
}
</pre>
* Atomと同じものを指定しておくのが無難かなぁ
