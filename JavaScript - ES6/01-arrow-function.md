# Arrow Function

tags: #ES6

縮減傳統函式寫法，更為簡潔便利。

## 兩種寫法比較

傳統函式寫法：

``` js
// html
<div class="click1">click1</div>

// js
document.querySelector('.click1').addEventListener('click', function() {
  console.log('click1')
});
```

箭頭函式寫法：

``` js
// html
<div class="click2">click2</div>

// js
document.querySelector('.click2').addEventListener('click', () => {
 console.log('click2')
});
```

可以看到，將過往`function() 改為 () =>`。

## this 指向

傳統函式中，`this`會指向`DOM`元素本身：

``` js
document.querySelector('.click1').addEventListener('click', function() {
 console.log(this) // 印出整個 a 標籤
});
```

但是箭頭函式中，`this` 指向會往上一層跑到全域環境，所以也可以理解為在`arrow function`中沒有`this`：

``` js
document.querySelector('.click2').addEventListener('click', () => {
 console.log(this); // 印出整個 window 物件
});
```

因此如果需要找到該`DOM`元素，需要透過傳值的方式：

``` js
document.querySelector('.click2').addEventListener('click', (e) => {
 console.log(e.target); // // 印出 a 標籤
});
```

## 變數指定

函式若在前方有宣告變數的情況下，可以簡寫成 arrow function：

``` js
// 但需要注意，若前方沒有變數指定，則無法改寫為 arrow function
const plus = () => {
 console.log('test');
};

plus();
```

傳值的寫法：

``` js
const plus = (val, subVal) => {
 return val + subVal;
};

console.log(plus(4, 14)); // 印出 18
```

若`return`僅一行的情況下，還可簡寫成：

``` js
const plus = (val, subVal) => val + subVal;

console.log(plus(2, 8)); // 印出 10
```
