# Jupyter Notebook の設定

## Introduction
Jupyter Notebookはブラウザ上で動作するアプリケーションで，
コードやMarkdownテキスト・図などが共存するドキュメントを簡単に作ることができるツールです．

<img src="/picture/ipynb_sample1.png" width="400">

## Installation
まずpipを最新のバージョンにします．
```
$ pip3 install --upgrade pip
```
そしてjupyterをインストールしましょう．
```
$ pip3 install jupyter
```

## Usage
### Starting the Notebook Server
ターミナルで適当なディレクトリに移動し，
```
$ jupyter-notebook
```
と実行すると，コマンドを実行したディレクトリをルートとしてNotebook Dashboardが開きます．

<img src="/picture/notebook_dashboard.png" width="500">

### Creating a Notebook
GUIを操作すれば簡単に作れます．

* GUIを操作し適当なディレクトリに移動
* 右上の**New**からNotebookの使いたいKernelを選択

でNotebookができます．
$ \alpha $

### Manipulation in Notebook
Jupyter Notebookには２つの入力モードがあります．
* **Edit Mode**
    * 実際にセル内のコードやテキストを編集するモード．セルの枠が **緑色** になる．
    * `Enter`を押すとこのモードになる．
* **Command Mode**:
    * セル間の移動やセルの挿入・削除といったセル単位の操作をするモード．セルの枠が **青色** になる．
    * `Esc`を押すとこのモードになる．


基本的な使い方を以下に列挙しておきます．
* セル内のコードの実行
    - `Shift + Enter` in Edit Mode or 上部リボンのRunボタン
* セルの追加
    - `A`, `B` in Command Mode or 上部リボンのプラスボタン
* セルの削除
    - `D`+`D` in Command Mode or 上部リボンのハサミボタン

<img src="/picture/ipynb_sample2.png" width="500">

続いて，実際にNotebookを使いながらPythonの文法について確認しましょう．

[> Next: Python Grammar](../notebook/PythonGrammar.ipynb)

[Topへ戻る](https://github.com/Kevinrobot34/MLwithPython)


## Reference
* https://jupyter.readthedocs.io/en/latest/index.html
    * 公式ドキュメント
* http://jupyter.org/install
    * Jupyterのinstallに関して
* https://ipython.readthedocs.io/en/latest/install/kernel_install.html
    * kernelの追加に関して





## Kernel周り
### Kernelの確認
```
$ jupyter kernelspec list
```
出力は
```
Available kernels:
  python3       /Users/hoge/Library/Jupyter/kernels/python3
  tensorflow    /Users/hoge/Library/Jupyter/kernels/tensorflow
```
的な感じ．ここで表示されるパスの中の`kernel.json`というファイルを見ると，どこのpythonを使っているかやdisplay-nameなどの情報が書かれている．

### Kernelの追加
Kernelとして追加したいPython環境をActivateさせた状態で，
```
$ python -m pip install ipykernel
$ python -m ipykernel install --user --name other-env --display-name "Python (other-env)"
```
とする．`other-env`や`Python (other-env)`のところは好きに決めてOK．
* display-name : jupyter-notebookやHydrogenのKernel選択で出てくる名前
* name : `jupyter kernelspec list`をした時に出てくる名前，Kernelの削除とかするときに指定する名前

#### 注意
以上の設定で追加されるKernelのバージョンはここで使った`python`に当然依存する．
追加する前に，
```
$ python -V
```
でバージョンを確認したり，
```
$ which python
```
でどこにあるpythonなのか確認したりしよう．
必要に応じて`python`を`python3`に置き換えたりして適宜実行してください．

### Kernelの削除
```
$ jupiter kernelspec uninstall [kernelname]
```


## Jupyter-Notebookの環境設定
### Fontの設定
NotebookのcodeのFontは好きなように指定できる．
`~/.jupyter/custom/custom.css`を編集し以下などのようにしておけば良い．
```
.CodeMirror pre, .output pre {
  font-family: Menlo, Consolas, "DejaVu Sans Mono", monospace;
  font-size: 10pt;
}
```
* Atomと同じものを指定しておくのが無難かなぁ
