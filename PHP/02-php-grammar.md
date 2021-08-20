# 基礎語法

tags: #PHP
links: 目錄 - [[00-php-index]]

## Basic grammar

先建立一個`Demo`資料夾，然後建立一個`hello.php`的檔案，並在檔案中輸入以下內容：

``` PHP
<?php
  echo('Hello PHP!');
```

接著回到終端機，執行以下指令：

``` sh
php hello.php
```

這時候就會看到終端機印出`Hello PHP`。

## 變數與資料型別

四種資料型別：

``` PHP
string   字串    'text'
interger 整數     15
float    浮點數   10.2
bolean   布林值   true or false
```

`php`中，變數前方採用`$`符號宣告，句尾需添加`;`：

```  PHP
$people = 'pitt';
$number = 100;
$boolean = true;
$float = 12.7;
```

在我的理解中，`php`的`echo();`近似於`js`的`cosole.log();`，所以我如果想要知自己變數的值為多少，可以這樣寫：

``` PHP
<?php
  $people = 'pitt';
  $number = 100;
  $boolean = true;
  $float = 12.7;
  echo($number);
```

執行指令`php hello.php`，可以看到終端機印出`100`。

## 轉換型別

透過轉型可以將上面的變數進行型別轉換：

``` PHP
$people = (int) $people;      // 0
$number = (float) $number;    // 100.0
$boolean = (string) $boolean; // ''
$float = (integer) $float;    // 12
```

再配合`var_dump`可以印出資料的型別：

``` PHP
<?php
  $number = (string) 100;
  var_dump($number);  // 印出 string 類型，以及有幾個字元，並印出結果'100'
```

此外，也能做四則運算：

``` PHP
<?php
  $number1 = 12;
  $number2 = 4;
  $ans = $number1 + $number2;
  echo($ans."\r\n"); // 16
  $ans = $number1 - $number2;
  echo($ans."\r\n"); // 8
  $ans = $number1 * $number2;
  echo($ans."\r\n"); // 48
  $ans = $number1 / $number2;
  echo($ans."\r\n"); // 3
  $ans = $number1 % $number2;
  echo($ans."\r\n"); // 0
```

計算一組跳錶收費，並在`echo()`輸出時包含有變數和字串：

``` PHP
<?php
  $initPrice = 80; // 起跳價格
  $perKilometerPrice = 16; // 每公里價格
  $kilometer = 12; // 跑了多少公里
  $calculatePrice = $perKilometerPrice * $kilometer;
  $finalPrice = $initPrice + $calculatePrice; // 最終價格
  echo("起跳價：{$initPrice}"."\r\n");
  echo("公里數：{$kilometer}"."\r\n");
  echo("最終收費：{$finalPrice}");

  // 起跳價：80
  // 公里數：12
  // 最終收費：272
```
