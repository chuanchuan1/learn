### 通用说明

> 例		: **count ( mixed $array_or_countable [, int $mode = COUNT_NORMAL ] ) : int**
>
> **mixed**	: 说明一个参数可以接受多种不同的（但不一定是所有的）类型。
>
> **[ ]**		: 说明参数可选
>
> **: int**    	: 说明返回值是 `int` 类型

*******

### 1. count

#### 定义

> count ( mixed $array_or_countable [, int $mode = COUNT_NORMAL ] ) : int

#### 作用

> 计算数组中的单元数目，或对象中的属性个数

#### 参数

|        参数        | 必选  |                             说明                             |
| :----------------: | :---: | :----------------------------------------------------------: |
| array_or_countable | true  | 数组或者 [Countable](http://php.net/manual/zh/class.countable.php) 对象。 |
|        mode        | false | 如果可选的 `mode` 参数设为 **COUNT_RECURSIVE**（或 1），**count()** 将递归> 地对数组计数。对计算多维数组的所有单元尤其有用。 |

#### 返回值

> 返回 `array_or_countable` 中的单元数目。 如果参数既不是数组，也不是实现 *Countable* 接口的对象，将返回 *1*。 有个例外：如果`array_or_countable` 是 **NULL** 则结果是 *0*。

#### 范例

##### 1、无 mode 参数

~~~
<?php

$a[0] = 1;				
$a[1] = 3;
$a[2] = 5;
var_dump(count($a));		// int(3)

var_dump(count(null));		// 会出现 Warning  // PHP 7.2起 int(0)
var_dump(count(false));		// 会出现 Warning  // PHP 7.2起 int(0)

~~~

##### 2、有 mode 参数

```
<?php

$food = array('fruits' => array('orange', 'banana', 'apple'),
              'veggie' => array('carrot', 'collard', 'pea'));

// recursive count
echo count($food, COUNT_RECURSIVE); // output 8

// normal count
echo count($food); // output 2
```



***

### 2、is_array

#### 定义

> is_array ( [mixed](http://php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$var` ) : bool

#### 作用

> 如果 `var` 是 [array](http://php.net/manual/zh/language.types.array.php)，则返回 **TRUE**，否则返回 **FALSE**。



***

### 3、substr

#### 定义

```
substr ( string `$string` , int `$start` [, int `$length` ] ) : string
```

#### 作用

> 函数返回字符串的一部分。
>
> 返回字符串 `string` 由 `start` 和 `length` 参数指定的子字符串。

#### 参数

 > * **string**
 >
 >   输入字符串。必须至少有一个字符。
 >
 >   
 >
 > * **strat**
 >
 >   如果 start 是非负数，返回的字符串将从 string 的 start 位置开始，从 0 开始计算。例如，在字符串 “abcdef” 中，在位置 0 的字符是 “a”，位置 2 的字符串是 “c” 等等。
 >
 >   如果 start 是负数，返回的字符串将从 string 结尾处向前数第 start 个字符开始。
 >
 >   如果 string 的长度小于 start，将返回 FALSE。
 >
 >   
 >
 > * **length**
 >
 >   如果提供了正数的 `length`，返回的字符串将从 `start` 处开始最多包括 `length` 个字符（取决于 `string` 的长度）。
 >
 >   如果提供了负数的 `length`，那么 `string` 末尾处的 `length` 个字符将会被省略（若 `start` 是负数则从字符串尾部算起）。如果 `start` 不在这段文本中，那么将返回 **FALSE**。
 >
 >   如果提供了值为 *0*，**FALSE** 或 **NULL** 的 `length`，那么将返回一个空字符串。
 >
 >   如果没有提供 `length`，返回的子字符串将从 `start` 位置开始直到字符串结尾。

#### 返回值

> 返回提取的子字符串， 或者在失败时返回 FALSE。

#### 更新日志

> 如果 string 的字符串长度与 start 相同时将返回一个空字符串。在之前的版本中，这种情况将返回 FALSE 。

#### 范例

```
<?php
echo substr('abcdef', 1);     // bcdef
echo substr('abcdef', 1, 3);  // bcd
echo substr('abcdef', 0, 4);  // abcd
echo substr('abcdef', 0, 8);  // abcdef
echo substr('abcdef', -1, 1); // f

// 访问字符串中的单个字符
// 也可以使用中括号
$string = 'abcdef';
echo $string[0];                 // a
echo $string[3];                 // d
echo $string[strlen($string)-1]; // f

```
