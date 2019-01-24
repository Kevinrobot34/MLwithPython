# Python Tutorial

## Interactive Mode
まずターミナルを立ち上げて，pythonを使ってみましょう．
```
$ python
Python 3.7.1 (default, Nov 28 2018, 11:51:47)
[Clang 10.0.0 (clang-1000.11.45.5)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

### 各種演算
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

```
>>> 17 / 3     # classic division returns a float
5.666666666666667
>>> 17 // 3    # floor division discards the fractional part
5
>>> 17 % 3     # the % operator returns the remainder of the division
2
>>> 5 * 3 + 2  # result * divisor + remainder
17
```

```
>>> 5 ** 2  # 5 squared
25
>>> 2 ** 7  # 2 to the power of 7
128
```

変数も使えます．
ただし，C言語などのように型を明記したりはしません．
```
>>> weight = 55
>>> height = 1.7
>>> bmi = weight / (height ** 2)
>>> bmi
19.031141868512112
```
これは数なら数で良しなに計算してくれます．
これは気軽にかける反面，複雑なプログラム中だと変数がどのような型のものなのか分かりにくいという側面もあります．
`type()`で変数の「型」を確認できます．
```
>>> type(weight)
<class 'int'>
>>> type(height)
<class 'float'>
>>> type(bmi)
<class 'float'>
```


以上のような使い方を対話モード (interactive mode) と言います．
これをやめるには
```
>>> exit()
```
とするか，`Ctrl + D`を押してください．



## terminalから
`test.py`というようなファイルを作り，ターミナルから
```
$ python test.py
```
としても，`test.py`の中身を上から順に実行してくれます．

### 例１
```hello.py
language:filename
print("Hello World!")
```
という内容の`hello.py`というファイルを作り，ターミナルから以下を実行してみましょう．
```
$ python hello.py
Hello World!
```


- comment
- string
    - print
- if
- for
- while
- List
- Dict
- 関数
-

## Reference
* https://docs.python.jp/3/tutorial/index.html
    - 公式のチュートリアル
    - 3,
