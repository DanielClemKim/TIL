# 1. 大数の法則
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
## :rabbit: 回答 1
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

## :rabbit: 回答 2
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
<br><br>

# 2. 数字カードゲーム
## :rabbit: 問題
1. 数字が書いてあるカードが **N X M**の形で置かれている。この時、**N**は行の数を意味し、**M**は列の数を意味する。
2. 引こうとするカードの行を選択する。
3. 選択した行に含まれているカードの中で、一番低い数字のカードを引く。
4. したがって、最終的に一番大きい数字のカードが引けるように戦略を立てなければならない。

* 入力例
```
3 3
3 1 2
4 1 4
2 2 2
```

* 出力例
```
2
```

## :rabbit: 回答 1
```python
n, m = map(int, input().split())

result = 0

for i in range(n):
    data = list(map(int, input().split()))
    min_value = min(data)
    result = max(result, min_value)

print(result)
```

## :rabbit: 回答 2
```python
n, m = map(int, input().split())

result = 0

for i in range(n):
    data = list(map(int, input().split()))
    min_value = 10001
    for a in data:
        min_value = min(a, min_value)
    result = max(result, min_value)

print(result)
```
<br><br>
# 3. "1"になるまで
## :rabbit: 問題
ある数字 **N**が 1になるまで、次の過程の中の1つを繰り返し行う。ただし、2つ目の演算は **N**が **K**で割り切れる時のみ選択できる。
1. **N**から 1を引く
2. **N**を **K**で割る

* 入力例
```
25 5
```

* 出力例
```
2
```
## :rabbit: 回答
```python
n, k = map(int, input().split())

count = 0

while True:
    if n < k:
        break
    elif n % k == 0:
        n = n // k
        count += 1
    else:
        tmp = n % k
        n -= n % k
        count += tmp

count += (n-1)

print(count)
```
***
参考書籍<br>
1. 이것이 취업을 위한 코딩 테스트다 with 파이썬