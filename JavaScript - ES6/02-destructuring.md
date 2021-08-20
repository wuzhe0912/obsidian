# Destructuring

tags: #ES6

一種更容易取值的方式。

## 傳統取值的方法

``` js
const data = {
 player: 'Pitt',
 str: 20,
 agi: 30
};

console.log(data.str); // 印出 20
```

## 解構的做法

透過 key 將物件中的資料解構出來：

``` js
const data = {
 player: 'Pitt',
 str: 20,
 agi: 30
};

const { player, str, agi } = data;

console.log(player, str, agi); // 印出 Pitt 20 30
```

## 將物件嵌進物件

若有 a 物件，希望放入 b 物件中，也可透過解構的方式：

``` js
const data = {
 player: 'Pitt',
 str: 20,
 agi: 30,
};

const playerData = {
 data,
 newPlayer: 'Numi',
};

console.log(playerData);
```

### 印出以下展開結果

``` js
{
 data: { player: 'Pitt', str: 20, agi: 30, },
 newPlayer: 'Numi',
}
```

## 陣列的解構賦值

從陣列中進行解構取值時，會採用依序的方式：

``` js
const list = ['德芙', '77乳加', '特趣', '健達', '明治'];
const [ first, second ] = list;

console.log(first); // 德芙
console.log(second); // 77乳加
```
