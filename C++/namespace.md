# Namespace
C++標準ライブラリの全ての関数、オブジェクト等が定義された名前空間(namespace)。
## :rabbit: Namespaceを省略
* namespaceに入っている特定の関数のみ使用
```C++
#include "header1.h"
#include "header2.h"

using header1::foo;
int main() {
    foo(); //header1の関数
}
```
* namespaceに入っている全てを使用
```C++
#include "header1.h"
#include "header2.h"

using namespace header1;
int main() {
    foo(); //header1の関数
    bar(); //header1の関数
}
```
## :rabbit: 名前なしのnamespace
namespaceの名前を設定しなかった場合、当namespaceに定義されたものは、ファイル内部でしか使えない。<br>
`static`のような効果

***
参考書籍<br>
초보자를 위한 C++ 씹어먹는 C++