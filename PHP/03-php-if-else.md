# 條件判斷與迴圈

tags: #PHP
links: 目錄 - [[00-php-index]]

``` PHP
// if / else
<?php
  $number = 9;
  if ($number > 10) {
    echo('大於');
  } elseif ($number === 10) {
    echo('等於');
  } else {
    echo('小於');
  }
```

``` PHP
// 增加判斷條件
<?php
  $number = 8;
  if ($number > 10 && $number > 12) {
    echo('大於');
  } elseif ($number === 10 || $number === 8) {
    echo('等於');
  } else {
    echo('小於');
  }
```

``` PHP
// 四季判斷
<?php
  $month = 9;
  if ($month > 2 && $month <= 5) {
    echo('台灣春季');
  } elseif ($month > 5 && $month <= 10) {
    echo('台灣夏季');
  } elseif ($month === 11) {
    echo('台灣秋季');
  } else {
    echo('台灣冬季');
  }
```

## 迴圈

### while

印出數字`0 ~ 8`：

``` PHP
<?php
  $count = 0;
  while ($count < 10) {
    echo($count."\r\n");
    $count ++;
  }
```

### for

印出數字`1 ~ 12`：

``` PHP
<?php
  for ($count = 1; $count < 13; $count++) {
    echo($count."\r\n");
  }
```

將指定數字內，奇數加總總和：

``` PHP
<?php
  $totalNumber = 0;
  for ($number = 1; $number < 151; $number ++) {
    if ($number % 2 !== 0) {
      $totalNumber = $totalNumber + $number;
    }
  }
  echo($totalNumber); // 5625
```
