# 配列操作を行うメソッド

JavaScriptでの配列操作について、定期的に分からなくなって調べ直しているのでまとめておく。

## toString

配列をカンマ区切りの文字列に変換する。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/toString)

```javascript
arr.toString()
```

```javascript
const arr = ['a', 'b', 'c']
console.log(arr.toString()) // a,b,c
```

## join

配列を任意の区切り文字で区切った文字列に変換する。  
区切り文字を指定しなかった場合はカンマ区切りに変換される。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/join)

```javascript
arr.join(separator)
```

- `separator`
  - 配列の要素を区切る文字列。空文字を渡した場合、配列の要素が区切り文字なしで繋がれる。
  - 省略可能。
  - 省略した場合、配列の要素はカンマで区切られる。

```javascript
const arr = ['a', 'b', 'c']
console.log(arr.join()) // a,b,c
console.log(arr.join('')) // abc
console.log(arr.join('-')) // a-b-c
```

## concat

複数の配列を結合する。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)

```javascript
arr.concat([value1[, value2[, ...[, valueN]]]])
```

- `valueN`
  - 配列に連結する配列もしくは値。
  - 省略可能。
  - 省略された場合、元の配列のシャローコピーを返す。

```javascript
const arr1 = ['a', 'b', 'c']
const arr2 = ['d', 'e', 'f']
const merged = arr1.concat(arr2)
console.log(merged) // ['a', 'b', 'c', 'd', 'e', 'f']
```

## pop

配列の最後の要素を取り除き、取り除いた要素を返す。  
元の配列を**変更する**。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/pop)

```javascript
arr.pop()
```

```javascript
const arr = ['a', 'b', 'c']
const item = arr.pop()
console.log(arr) // ['a', 'b']
console.log(item) // c
```

## push

配列の最後に要素を追加する。複数の要素を追加することも可能。  
戻り値として追加後の配列の要素数を返す。  
元の配列を**変更する**。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/push)

```javascript
arr.push([element1[, element2[, ...[, elementN]]]])
```

- `elementN`
  - 配列の最後に追加する要素。

```javascript
const arr = ['a', 'b', 'c']
const count = arr.push('d')
console.log(count) // 4
console.log(arr) // ['a', 'b', 'c', 'd']
arr.push('e', 'f', 'g')
console.log(arr) // ['a', 'b', 'c', 'd', 'e', 'f', 'g']
```

## shift

配列の最初の要素を取り除き、取り除いた要素を返す。  
元の配列を**変更する**。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/shift)

```javascript
arr.shift()
```

```javascript
const arr = ['a', 'b', 'c']
const item = arr.shift()
console.log(arr) // ['b', 'c']
console.log(item) // a
```

## unshift

配列の最初に要素を追加する。複数の要素を追加することも可能。  
戻り値として追加後の配列の要素数を返す。  
元の配列を**変更する**。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift)

```javascript
arr.unshift([element1[, element2[, ...[, elementN]]]])
```

- `elementN`
  - 配列の最初に追加する要素。

```javascript
const arr = ['a', 'b', 'c']
const count = arr.unshift('z')
console.log(count) // 4
console.log(arr) // ['z', 'a', 'b', 'c']
arr.unshift('w', 'x', 'y')
console.log(arr) // ['w', 'x', 'y', 'z', 'a', 'b', 'c']
```

## splice

配列から任意の位置にある要素を取り除いたり、置き換えたり、新しい要素を追加したりする。  
戻り値として取り除いた要素を返す。  
元の配列を**変更する**。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)

```javascript
array.splice(start[, deleteCount[, item1[, item2[, ... ]]]])
```

- `start`
  - 変更の開始位置。
  - 配列の長さより大きい場合、 `start` は配列の長さに設定される。
  - 負の値を与えた場合、配列の末尾から数えた位置に設定される（ `arr.length - n` )。
- `deleteCount`
  - 開始位置から取り除く要素の数。
  - 省略可能。
  - 省略した場合、または開始位置から数えた配列の長さ以上の場合、開始位置以降全ての要素を取り除く。
  - 0または負の数の場合、どの要素も取り除かない。
- `item1, item2, ...`
  - 開始位置に追加する要素。
  - 省略可能。

```javascript
const arr = ['a', 'b', 'c']

/* 要素を追加 */
arr.splice(2, 0, 'd') // []
console.log(arr) // ['a', 'b', 'd', 'c']

/* 要素を置き換え */
arr.splice(1, 1, 'e') // ['b']
console.log(arr) // ['a', 'e', 'd', 'c']

/* 要素を削除 */
arr.splice(1, 1) // ['e']
console.log(arr) // ['a', 'd', 'c']
```

## slice

配列の任意の範囲を新しい配列としてコピーする。  
元の配列を変更しない。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)

```javascript
arr.slice([start[, end]])
```

- `start`
  - 取り出す範囲の開始位置。
  - 省略可能。
  - 省略した場合、配列の先頭から開始する。
  - 配列の長さより大きい場合、戻り値として空の配列を返す。
  - 負の値を与えた場合、配列の末尾から数えた位置に設定される。
- `end`
  - 取り出す範囲の終了位置（ `end` 自体は含まない）。
  - 省略可能。
  - 省略した場合、または配列の長さより大きい場合、配列の最後までを取り出す。
  - 負の値を与えた場合、配列の末尾から数えた位置に設定される。

```javascript
const arr = ['a', 'b', 'c', 'd', 'e']
console.log(arr.slice(2)) // ['c', 'd', 'e']
console.log(arr.slice(2, 4)) // ['c', 'd']
console.log(arr.slice(1, -1)) // ['b', 'c', 'd']
```

## indexOf

配列から引数に与えた要素を探し、同じ内容を持つ最初の要素の添字を返す。存在しない場合は `-1` を返す。  
元の配列を変更しない。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf)

```javascript
arr.indexOf(searchElement[, fromIndex])
```

- `searchElement`
  - 検索する要素。
- `fromIndex`
  - 検索を始める位置。
  - 省略可能。
  - 配列の長さ以上の値を与えた場合、 `-1` が返され検索されない。
  - 負の数を与えた場合、配列の末尾から数えた位置に設定される。ただし、検索は前から後ろへと行われる。

```javascript
const arr = ['a', 'b', 'c', 'b', 'd']
console.log(arr.indexOf('b')) // 1
console.log(arr.indexOf('b', 2)) // 3
console.log(arr.indexOf('e')) // -1
```

## lastIndexOf

配列から引数に与えた要素を探し、同じ内容を持つ最後の要素の添字を返す。存在しない場合は `-1` を返す。  
元の配列を変更しない。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf)

```javascript
arr.lastIndexOf(searchElement[, fromIndex])
```

- `searchElement`
  - 検索する要素。
- `fromIndex`
  - 検索を始める位置。
  - 省略可能。
  - 配列の長さ以上の値を与えた場合、 `-1` が返され検索されない。
  - 負の数を与えた場合、配列の末尾から数えた位置に設定される。ただし、検索は後ろから前へと行われる。

```javascript
const arr = ['a', 'b', 'c', 'b', 'd']
console.log(arr.lastIndexOf('b')) // 3
console.log(arr.lastIndexOf('b', 2)) // 1
console.log(arr.lastIndexOf('b', 0)) // -1
```

## filter

与えられた条件を満たす全ての要素からなる新しい配列を生成する。  
元の配列を変更しない。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

```javascript
arr.filter(callback(element[, index[, array]])[, thisArg])
```

- `callback`
  - 配列の各要素に対して実行される関数。
  - この関数が `true` となる値を返した要素は新しい配列の要素として残され、 `false` となる値を返した要素は取り除かれる。
- `element`
  - `arr` から取り出された要素。
  - `callback` に引数として与えられる。
- `index`
  - 元の配列での `element` の位置。
  - `callback` に引数として与えられる。
  - 省略可能。
- `array`
  - 元の配列。
  - `callback` に引数として与えられる。
  - 省略可能。
- `thisArg`
  - `callback` 内で `this` として使用する値。
  - 省略可能。

```javascript
const arr = ['a', 'b', 'c', 'b', 'd']
let result

result = arr.filter((item) => {
  /* 全ての要素でtrueを返す */
  return true
})
console.log(result) // ['a', 'b', 'c', 'b', 'd']

result = arr.filter((item) => {
  /* 全ての要素でfalseを返す */
  return false
})
console.log(result) // []

result = arr.filter((item) => {
  /* 要素の値が `b` のときだけtrueを返す */
  return item === 'b'
})
console.log(result) // ['b', 'b']
```

## map

配列のすべての要素に対して、与えられた関数を実行し、その結果から新しい配列を生成する。  
元の配列を変更しない。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

```javascript
arr.map(callback(element[, index[, array]])[, thisArg])
```

- `callback`
  - 配列の各要素に対して実行される関数。
  - この関数から返される値が新しい配列の要素として追加される。
- `element`
  - `arr` から取り出された要素。
  - `callback` に引数として与えられる。
- `index`
  - 元の配列での `element` の位置。
  - `callback` に引数として与えられる。
  - 省略可能。
- `array`
  - 元の配列。
  - `callback` に引数として与えられる。
  - 省略可能。
- `thisArg`
  - `callback` 内で `this` として使用する値。
  - 省略可能。

```javascript
const arr = ['a', 'b', 'c', 'b', 'd']
let result

result = arr.map((item) => {
  return item
})
console.log(result) // ['a', 'b', 'c', 'b', 'd']

result = arr.map((item, index) => {
  return index + 1
})
console.log(result) // [1, 2, 3, 4, 5]
```

## reduce

配列のすべての要素に対して、与えられた関数を実行し、その結果から新しい配列を生成する。  
元の配列を変更しない。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)

```javascript
arr.reduce(callback(accumulator, currentValue[, index[, array]])[, initialValue])
```

- `callback`
  - 配列の各要素に対して実行される関数。
  - この関数から返される値が次回 `callback` が実行される際に引数 `accumulator` として与えられる。
- `accumulator`
  - `callback` から返される値を蓄積する。
  - 前回の `callback` 呼び出しで返された値もしくは `initialValue` の値。
  - `callback` に引数として与えられる。
- `currentValue`
  - `arr` から取り出された要素。
  - `callback` に引数として与えられる。
- `index`
  - 元の配列での `currentValue` の位置。
  - `callback` に引数として与えられる。
  - 省略可能。
- `array`
  - 元の配列。
  - `callback` に引数として与えられる。
  - 省略可能。
- `initialValue`
  - 最初に `callback` を実行する際に `accumulator` として使用する値。
  - 省略可能。
  - 省略された場合は最初に `callback` を実行する際に `arr` の最初の要素が `accumulator` として使用され `currentValue` には `arr` の2番目の要素が使用される。

```javascript
const arr = [1, 2, 3, 4, 5]
let result

result = arr.reduce((accumulator, item) => {
  return accumulator + item
})
console.log(result) // 15

result = arr.reduce((accumulator, item) => {
  return accumulator + item
}, 10)
console.log(result) // 25
```

## reduceRight

配列のすべての要素に対して、与えられた関数を実行し、その結果から新しい配列を生成する。  
`reduce` が左から右へ適用されるのに対し、 `reduceRight` は右から左へと適用される。  
元の配列を変更しない。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/ReduceRight)

```javascript
arr.reduceRight(callback(accumulator, currentValue[, index[, array]])[, initialValue])
```

- `callback`
  - 配列の各要素に対して実行される関数
  - この関数から返される値が次回 `callback` が実行される際に引数 `accumulator` として与えられる。
- `accumulator`
  - `callback` から返される値を蓄積する。
  - 前回の `callback` 呼び出しで返された値もしくは `initialValue` の値。
  - `callback` に引数として与えられる。
- `currentValue`
  - `arr` から取り出された要素。
  - `callback` に引数として与えられる。
- `index`
  - 元の配列での `currentValue` の位置。
  - `callback` に引数として与えられる。
  - 省略可能。
- `array`
  - 元の配列。
  - `callback` に引数として与えられる。
  - 省略可能。
- `initialValue`
  - 最初に `callback` を実行する際に `accumulator` として使用する値。
  - 省略可能。
  - 省略された場合は最初に `callback` を実行する際に `arr` の最後の要素が `accumulator` として使用され `currentValue` には `arr` の最後から2番目の要素が使用される。

```javascript
const arr = [1, 2, 3, 10]
let result

result = arr.reduceRight((accumulator, item) => {
  return accumulator - item
})
console.log(result) // 4

result = arr.reduceRight((accumulator, item) => {
  return accumulator - item
}, 30) // 14
```

## forEach

配列のすべての要素に対して、与えられた関数を実行する。  
元の配列を変更しない。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

```javascript
arr.forEach(callback(element[, index[, array]])[, thisArg])
```

- `callback`
  - 配列の各要素に対して実行される関数。
- `element`
  - `arr` から取り出された要素。
  - `callback` に引数として与えられる。
- `index`
  - 元の配列での `element` の位置。
  - `callback` に引数として与えられる。
  - 省略可能。
- `array`
  - 元の配列。
  - `callback` に引数として与えられる。
  - 省略可能。
- `thisArg`
  - `callback` 内で `this` として使用する値。
  - 省略可能。

```javascript
const arr = ['a', 'b', 'c']

arr.forEach((item) => {
  console.log(item)
})

// a
// b
// c
```

## every

配列のすべての要素に対して与えられた関数を実行し、すべての要素が条件を満たすかどうかテストする。すべての要素が条件を満たす場合に `true` 、そうでない場合に `false` を返す。  
元の配列を変更しない。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/every)

```javascript
arr.every((callback(element[, index[, array]]))[, thisArg])
```

- `callback`
  - 配列の各要素に対して実行される関数。
- `element`
  - `arr` から取り出された要素。
  - `callback` に引数として与えられる。
- `index`
  - 元の配列での `element` の位置。
  - `callback` に引数として与えられる。
  - 省略可能。
- `array`
  - 元の配列。
  - `callback` に引数として与えられる。
  - 省略可能。
- `thisArg`
  - `callback` 内で `this` として使用する値。
  - 省略可能。

```javascript
const arr = [1, 2, 3, 4, 5]
let result

result = arr.every((item) => {
  return item < 10
})
console.log(result) // true

result = arr.every((item) => {
  return item < 3
})
console.log(result) // false
```

## some

配列のすべての要素に対して与えられた関数を実行し、いずれかの要素が条件を満たすかどうかテストする。条件を満たすものが1つでもある場合に `true` 、そうでない場合に `false` を返す。  
元の配列を変更しない。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/some)

```javascript
arr.some((callback(element[, index[, array]]))[, thisArg])
```

- `callback`
  - 配列の各要素に対して実行される関数。
- `element`
  - `arr` から取り出された要素。
  - `callback` に引数として与えられる。
- `index`
  - 元の配列での `element` の位置。
  - `callback` に引数として与えられる。
  - 省略可能。
- `array`
  - 元の配列。
  - `callback` に引数として与えられる。
  - 省略可能。
- `thisArg`
  - `callback` 内で `this` として使用する値。
  - 省略可能。

```javascript
const arr = [1, 2, 3, 4, 5]
let result

result = arr.some((item) => {
  return item < 3
})
console.log(result) // true

result = arr.some((item) => {
  return item > 10
})
console.log(result) // false
```

## includes

配列から引数に与えた要素を探し、存在している場合は `true` 、存在していない場合は `false` を返す。  
元の配列を変更しない。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)

```javascript
arr.includes(searchElement[, fromIndex])
```

- `searchElement`
  - 検索する要素。
- `fromIndex`
  - 検索を始める位置。
  - 省略可能。
  - 配列の長さ以上の値を与えた場合、 `false` が返され検索されない。
  - 負の数を与えた場合、配列の末尾から数えた位置に設定される。ただし、検索は前から後ろへと行われる。

```javascript
const arr = ['a', 'b', 'c', 'd', 'e']
console.log(arr.includes('a')) // true
console.log(arr.includes('f')) // false
console.log(arr.includes('a', 2)) // false
```

## copyWithin

配列の一部を同じ配列内の指定した位置にコピーする。  
元の配列を**変更する**。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/copyWithin)

```javascript
arr.copyWithin(target[, start[, end]])
```

- `target`
  - コピー先の位置。
  - 負の数を与えた場合、配列の末尾から数えた位置に設定される。
  - 配列の長さ以上の値を与えた場合、コピーは行われない。
- `start`
  - コピー元の開始位置。
  - 負の数を与えた場合、配列の末尾から数えた位置に設定される。
  - 省略可能。
  - 省略された場合、最初の要素からコピーする。
- `end`
  - コピー元の終了位置。指定した位置の要素は含まない。
  - 負の数を与えた場合、配列の末尾から数えた位置に設定される。
  - 省略可能。
  - 省略された場合、最後の要素までコピーする。

```javascript
const arr = [1, 2, 3, 4, 5]

console.log([...arr].copyWithin(2))
// [1, 2, 1, 2, 3]

console.log([...arr].copyWithin(0, 3))
// [4, 5, 3, 4, 5]

console.log([...arr].copyWithin(0, -2, -1))
// [4, 2, 3, 4, 5]
// * end の値はコピー対象に含まれない
```

## fill

配列の指定した開始位置から指定した終了位置までのすべての要素を、指定した値に変更する。  
元の配列を**変更する**。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/fill)

```javascript
arr.fill(value[, start[, end]])
```

- `value`
  - 配列に設定する値。
- `start`
  - 変更を開始する位置。
  - 負の数を与えた場合、配列の末尾から数えた位置に設定される。
  - 省略可能。
  - 省略された場合、先頭の要素から変更する。
- `end`
  - 変更を終了する位置。指定した位置の要素は含まない。
  - 負の数を与えた場合、配列の末尾から数えた位置に設定される。
  - 省略可能。
  - 省略された場合、最後の要素まで変更する。

```javascript
const arr = ['a', 'b', 'c', 'b', 'd']

console.log([...arr].fill('z'))
// ['z', 'z', 'z', 'z', 'z']

console.log([...arr].fill('z', 2, 4))
// ['a', 'b', 'z', 'z', 'd']
```

## find

与えられた条件を満たす配列内の最初の要素の値を返す。  
元の配列を変更しない。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/find)

```javascript
arr.find(callback(element[, index[, array]])[, thisArg])
```

- `callback`
  - 配列の各要素に対して実行される関数。
  - 最初に関数の実行結果が `true` となる値を `find` の結果として返す。
- `element`
  - `arr` から取り出された要素。
  - `callback` に引数として与えられる。
- `index`
  - 元の配列での `element` の位置。
  - `callback` に引数として与えられる。
  - 省略可能。
- `array`
  - 元の配列。
  - `callback` に引数として与えられる。
  - 省略可能。
- `thisArg`
  - `callback` 内で `this` として使用する値。
  - 省略可能。

```javascript
const arr = [1, 2, 3, 4, 5]

console.log([...arr].find((item) => item > 3)) // 4
```

## findIndex

与えられた条件を満たす配列内の最初の要素の位置を返す。  
元の配列を変更しない。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)

```javascript
arr.findIndex(callback(element[, index[, array]])[, thisArg])
```

- `callback`
  - 配列の各要素に対して実行される関数。
  - 最初に関数の実行結果が `true` となる要素の位置を `findIndex` の結果として返す。
- `element`
  - `arr` から取り出された要素。
  - `callback` に引数として与えられる。
- `index`
  - 元の配列での `element` の位置。
  - `callback` に引数として与えられる。
  - 省略可能。
- `array`
  - 元の配列。
  - `callback` に引数として与えられる。
  - 省略可能。
- `thisArg`
  - `callback` 内で `this` として使用する値。
  - 省略可能。

```javascript
const arr = [1, 2, 3, 4, 5]

console.log([...arr].findIndex((item) => item > 3)) // 3
```

## flat

与えられた配列を、指定した深さで再帰的に統合した新しい配列を生成する。  
元の配列を変更しない。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/flat)

```javascript
arr.flat([depth])
```

- `depth`
  - フラット化する深さ。
  - 省略可能。
  - 省略した場合、 `1` に設定される。

```javascript
const arr = [1, 2, 3, [[4, 5]], 6]
console.log(arr.flat()) // [1, 2, 3, [4, 5], 6]
console.log(arr.flat(2)) // [1, 2, 3, 4, 5, 6]
```

## flatMap

配列のすべての要素に対して与えられた関数を実行しその結果から新しい配列を生成した後、深さ `1` で再帰的に統合した新しい配列を生成する。  
[map](#map) を実行した後、深さ `1` の [flat](#flat) を実行するものと同等。  
元の配列を変更しない。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/flatMap)

```javascript
arr.flatMap(callback(element[, index[, array]])[, thisArg])
```

- `callback`
  - 配列の各要素に対して実行される関数。
  - この関数から返される値が新しい配列の要素として追加される。
- `element`
  - `arr` から取り出された要素。
  - `callback` に引数として与えられる。
- `index`
  - 元の配列での `element` の位置。
  - `callback` に引数として与えられる。
  - 省略可能。
- `array`
  - 元の配列。
  - `callback` に引数として与えられる。
  - 省略可能。
- `thisArg`
  - `callback` 内で `this` として使用する値。
  - 省略可能。

## reverse

配列の要素の順番を反転させる。最初の要素が最後の要素に、最後の要素が最初の要素となる。  
元の配列を**変更する**。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse)

```javascript
arr.reverse()
```

```javascript
const arr = ['a', 'b', 'c']
console.log(arr.reverse()) // ['c', 'b', 'a']
console.log(arr) // ['c', 'b', 'a']
```

## sort
配列の要素を指定された関数に従って並び替える。  
元の配列を**変更する**。  
[MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

```javascript
arr.sort([callback])
```

- `callback`
  - 並び替える順番を定義する関数。
  - 省略可能。
  - 省略された場合、配列の各要素を文字列に変換し、各文字の `Unicode` の番号順に従って並び替えられる。
  - 関数を指定した場合、 `callback(a, b)` が負の数を返した場合 `a` が `b` よりも前にくるように並び替える。 `callback(a, b)` が `0` を返した場合 `a` と `b` の位置は変更しない。 `callback(a, b)` が `0` より大きい値を返した場合 `b` が `a` よりも前にくるように並び替える。

```javascript
const arr = [4, 2, 1, 5, 3]
arr.sort()
console.log(arr) // [1, 2, 3, 4, 5]
```
