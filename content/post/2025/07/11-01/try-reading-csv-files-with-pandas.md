---
title: Pandas で CSV ファイルを読む
slug: try-reading-csv-files-with-pandas
description: Python の Pandas で CSV ファイルの読み込むを試した。
date: 2025-07-11T12:23:11+09:00
categories: AI
image:
math: false
license: default
hidden: false
comments: false
draft: false
---

## 基本操作
`pandas` の導入。
```python
import pandas as pd
```

CSV ファイルを読み込む。
```python
df = pd.read_csv('example.csv')
```

> ファイルの内容が変更された場合、`pd.read_csv()` でファイルの再読み込みが必要。

CSV ファイルの内容をプリント。
```python
print(df)
```

出力結果
```python
     A  B  C  D  E  F  G  H  I   J   K   L   M   N   O   P   Q   R   S   T   U   V   W   X   Y   Z
0    1  2  3  4  5  6  7  8  9  10  11  12  13  14  15  16  17  18  19  20  21  22  23  24  25  26
1    1  2  3  4  5  6  7  8  9  10  11  12  13  14  15  16  17  18  19  20  21  22  23  24  25  26
2    1  2  3  4  5  6  7  8  9  10  11  12  13  14  15  16  17  18  19  20  21  22  23  24  25  26
3    1  2  3  4  5  6  7  8  9  10  11  12  13  14  15  16  17  18  19  20  21  22  23  24  25  26
4    1  2  3  4  5  6  7  8  9  10  11  12  13  14  15  16  17  18  19  20  21  22  23  24  25  26
..  .. .. .. .. .. .. .. .. ..  ..  ..  ..  ..  ..  ..  ..  ..  ..  ..  ..  ..  ..  ..  ..  ..  ..
195  1  2  3  4  5  6  7  8  9  10  11  12  13  14  15  16  17  18  19  20  21  22  23  24  25  26
196  1  2  3  4  5  6  7  8  9  10  11  12  13  14  15  16  17  18  19  20  21  22  23  24  25  26
197  1  2  3  4  5  6  7  8  9  10  11  12  13  14  15  16  17  18  19  20  21  22  23  24  25  26
198  1  2  3  4  5  6  7  8  9  10  11  12  13  14  15  16  17  18  19  20  21  22  23  24  25  26
199  1  2  3  4  5  6  7  8  9  10  11  12  13  14  15  16  17  18  19  20  21  22  23  24  25  26
```

## 行操作

### 先頭 `10` 行を取得
```python
print(df.head(10))
```

### 末尾 `10` 行を取得
```python
print(df.tail(10))
```

### 指定行を取得
```python
print(df[64:89])
```

### 表示行数の上限を設定
```python
pd.set_option('display.max_rows', 100)
```

または
```python
pd.set_option('display.max_rows', None)
```

> 設定を変更後、`pd.read_csv()` でファイルの再読み込みが必要。

## 列操作
### 指定列を取得
```python
print(df[["A", "P"]])
```

または
```python
print(df.iloc[:,4:6])
```

### "A" 列の値が 0 より大きい行を取得
```python
print(df[df.A > 0])
```

### 表示列数の上限を設定
```python
pd.set_option('display.max_columns', 100)
```

または
```python
pd.set_option('display.max_columns', None)
```

> 設定を変更後、`pd.read_csv()` でファイルの再読み込みが必要。