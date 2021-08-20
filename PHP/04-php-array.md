# Array(陣列)

tags: #PHP
links: 目錄 - [[00-php-index]]

在`php`中，呈現陣列的格式寫法有下列兩種：

``` PHP
<?php
  $list = ['player', 'wow', 'apple'];
  $numberList = array(1, 2, 3);
```

而當我想要印出陣列時，不再使用`echo()`，而是改用`print_r()`：

``` PHP
<?php
  $list = ['player', 'wow', 'apple'];
  $numberList = array(1, 2, 3);
  print_r($list);
  print_r($numberList);
```

可以在終端機上看到印出的結果：

``` PHP
Array
(
    [0] => player
    [1] => wow
    [2] => apple
)
Array
(
    [0] => 1
    [1] => 2
    [2] => 3
)
```

字典陣列，我理解為類似帶有欄位屬性：

``` PHP
<?php
  $player = [
    'name' => 'Pitt',
    'defence' => 100
  ];
  print_r($player);
```

在陣列操作上，和`JS`也是相當雷同：

``` PHP
<?php
  $numberList = array(1, 2, 3);
  $player = [
    'name' => 'Pitt',
    'defence' => 100
  ];
  $numberList[0] = $player['defence'];
  print_r($numberList); // [0] => 100
  print_r($numberList[1] + $player['defence']); // 102
```

## 使用迴圈操作陣列

使用`foreach`跑迴圈：

``` PHP
<?php
  $list = ['Ragnarok', 'Black Desert', 'League of Legends', 'Lineage'];
  foreach ($list as $index => $game) {
    echo("第{$index}個遊戲：{$game}"."\r\n");
  }
```

如果陣列改為字典式陣列，則寫法調整為對應欄位：

``` PHP
<?php
  $list = [
    ['name' => 'Ragnarok'],
    ['name' => 'Black Desert'],
    ['name' => 'League of Legends'],
    ['name' => 'Lineage']
  ];
  foreach ($list as $index => $game) {
    echo("第{$index}個遊戲：{$game['name']}"."\r\n");
  }
```

### 實作

實作一，建立一組陣列，並在其中塞入五張獲利的股票，計算平均每張獲利，以及總獲利：

``` PHP
<?php
  $stocks = [
    ['profit' => 5],
    ['profit' => 10],
    ['profit' => 20],
    ['profit' => 33],
    ['profit' => 17]
  ];
  $totalProfit = 0;
  foreach ($stocks as $index => $value) {
    $totalProfit = $totalProfit + $value['profit'];
  }
  echo($totalProfit); // 總獲利：85
  $stocksLength = count($stocks);
  $perProfit = $totalProfit / $stocksLength;
  echo($perProfit); // 平均每張獲利：17
```

實作二，建立一組陣列，裡面有五位操盤手，依據每個人績效x10000，做為獎金發放，其中要有一個人無績效，並顯示對應文字，並使用substr清除字串最後一個字元，印出結果：：

``` PHP
<?php
  $people = [
    [ 'name' => 'Alice', 'performance' => '120%' ],
    [ 'name' => 'Olive', 'performance' => '150%' ],
    [ 'name' => 'Mavis', 'performance' => '67%' ],
    [ 'name' => 'Lena', 'performance' => '250%' ],
    [ 'name' => 'Alyssa', 'performance' => null ]
  ];
  foreach ($people as $index => $value) {
    $text = substr($value['performance'], 0, -1);
    $bonus = (((float) $text) / 100) * 10000;
    if ($text) {
      echo("{$value['name']}獎金：{$bonus}元"."\r\n");
    } else {
      echo("{$value['name']}：沒有績效資料");
    }
  }

// Alice獎金：12000元
// Olive獎金：15000元
// Mavis獎金：6700元
// Lena獎金：25000元
// Alyssa：沒有績效資料
```

第二個情境，假設陣列結構調整為如下：

``` PHP
<?php
  $girls = ['Alice', 'Olive', 'Mavis', 'Lena', 'Alyssa'];
  $report = [
    'Alice' => 1.2,
    'Olive' => 1.5,
    'Mavis' => 0.67,
    'Lena' => 2.5
  ];
```

那麼迴圈的寫法就需要調整如下，使用`php`的`isset()`過濾：

``` PHP
<?php
  $girls = ['Alice', 'Olive', 'Mavis', 'Lena', 'Alyssa'];
  $report = [
    'Alice' => 1.2,
    'Olive' => 1.5,
    'Mavis' => 0.67,
    'Lena' => 2.5
  ];
  foreach ($girls as $index) {
    $bonus = $report[$index] * 10000;
    if (isset($report[$index])) {
      echo("{$index}獎金：{$bonus}元\r\n");
    } else {
      echo("{$index}：沒有績效資料。");
    }
  }
```

## 關於閉合標籤

在`php`中會看到兩種寫法：

``` PHP
<?php
  echo('Hello PHP!');
```

``` PHP
<?php
  <h2>Hello PHP!</h2>
?>
```

在單純只有`php`的程式時，譬如`echo()`不建議寫閉合標籤，但倘若當中嵌有`HTML`的`tag`時，則需要添加`?>`閉合標籤。
