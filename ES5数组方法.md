# ES5数组方法
## 快速检索
*可以判断数组项是否存在,不存在返回-1* 
```javascript
array.indexOf()
```

```javascript
array.lastIndexOf()
```

## 递归操作

### 参数
*callback(value,index,array){}* value:数组项,index:索引值,array:调用的数组*  
*thisArg(可以省略),一个对象在callback中指向this*  
*执行策略:判断每个数组项是否和条件相符,返回true或false,每种方法通过返回值进行各自操作.*  

### 方法

##### *返回值为Boolean*

###### *关心的是通过的结果,全部通过或有通过*

```javascript
array.every(callback[,thisArg]) 
// 返回值需要接收 
// var flag = array.every()
// 如果flag = true,说明所有判断都通过.
```
*属于短路操作,只会执行满足条件的数组项,当条件不满足,返回false时立即跳出.*

```javascript
array.some(callbakc[,thisArg])
// 只要一个值通过判断,返回值true之后跳出
```

*只要有一个数组项符合判断条件,第一次返回true时即刻跳出.*

##### *返回值为Array*

###### *关心的是有哪些值通过验证,并合并成数组输出*

```javascript
array.fliter(callback[,thisArg])
// return value > 10
// 返回true的值被组成一个数组输出
// var array = arr.fliter()
```

*直接把每个数组项和判断条件进行判断,返回值true时,value被push进接收变量中.*

###### *关心的是值的操作,操作每个数组项后再返回数组项,最后返回全部处理好的数组,包含所有数组项.*

```javascript
array.map(callback[,thisArg])
function callback(value,index,array){
  var result = value + 1;
  return result;
}
// 最后会返回一个数组,对于原数组来说,数组项每个都+1,不修改原数组.
```

##### *返回值为null*

###### *只是把每个数组项遍历操作下*

```javascript
array.forEach(callback[,thisArg])
function logArrayElements(element, index, array) {
    console.log("a[" + index + "] = " + element);
}
[2, 5, 9].forEach(logArrayElements);
// logs:
// a[0] = 2
// a[1] = 5
// a[2] = 9
```

## 归并累积

###### *如静态变量一般,累积处理.*

```javascript
array.reduce(callback[, initialValue])
function callback(prev,curr,index,arr){}
var total = [0, 1, 2, 3].reduce(function(a, b) {
    return a + b;
});
// total == 6
```

```javascript
array.reduceRight(callback[, initialValue])
// 从右边开始处理数组项
```