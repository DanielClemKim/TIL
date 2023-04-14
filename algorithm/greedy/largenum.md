# 大数の法則
色々な数字でできている配列がある時、与えられた数字を**M**回足し、一番大きい数字を作る。ただし、配列の特定インデックスの数字は繰り返し**K**回まで足される。
## :rabbit: 問題
配列のサイズ**N**、数字が足される回数**M**、そして**K**が与えられた時、大数の法則に従った結果を出力しなさい。<br>
* 入力例
```
5 8 3
2 4 5 4 6
```
* 出力例
```
46
```
## :rabbit: 回答１
```python
n, m, k = map(int, input().split())
data = list(map(int, input().split()))

data.sort()
first = data[n-1]
second = data[n-2]

result = 0

while True:
    for i in range(k):
        if m == 0:
            break
        result += first
        m -= 1
    if m == 0:
        break
    result += second
    m -= 1

print(result)
```

## :rabbit: 回答２
```python
n, m, k = map(int, input().split())
data = list(map(int, input().split()))

data.sort()
first = data[n-1]
second = data[n-2]

result = 0

count = m // (k+1) * k
count +=  m % (k+1)

result += count * first
result += (m-count) * second

print(result)
```
***
参考書籍<br>
1. 이것이 취업을 위한 코딩 테스트다 with 파이썬