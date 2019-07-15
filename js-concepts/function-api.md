# Function API

## Array  <a id="array"></a>

InPlace:push\(\)/pop\(\), shift\(\)/unshift\(\), **splice\(\),** copyWithin\(\), fill\(\), reverse\(\), sort\(\)

ReturnNew: concat\(\), slice\(\) `***`**splice\(\), splice\(startIndex, deleteNumber, input new to here\);**

```text
array.splice(start[, deleteCount[, item1[, item2[, ...]]]])
```

Matching: indexOf\(\), lastIndexOf\(\), find\(\), findIndex\(\), some\(\), every\(\), join\(\)

​

**traverse forEach** executes the provided callback once for each element present in the array in ascending order.

```text
fruits.forEach(function (item, index, array) {    console.log(item, index);});
```

•Does not make a copy of the array before iterating.

```text
splitvar myArray = myData.split(',');var myNewString = myArray.join(',');myNewString;
```

 push\(\): add to last.

pop\(\): delete last and return this one.

​

​[`toString()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/toString)​

1. ```text
   var dogNames = ["Rocket","Flash","Bella","Slugger"];dogNames.toString(); //Rocket,Flash,Bella,Slugger
   ```

​

```text
var myArray = ['Manchester', 'Leeds', 'Carlisle'];myArray.push('Cardiff');myArray.pop();pop() delete last onevar removedItem = myArray.pop();
```

​[`unshift()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift) [`shift()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/shift) `100% like push and pop, only on the begining`

`unshift(): add to head.`

```text
myArray.unshift('Edinburgh');var removedItem = myArray.shift();
```

​

```text
.indexOf(element) return the index
```

Splice: delete some elements:

```text
array.splice(start[, deleteCount[, item1[, item2[, ...]]]])start position, delete number, items to add.from startreturn the [] that deleted.
```

```text
var removedItem = fruits.splice(pos, 1); 
```

.fill\(\) fill all indexes.

​[`.concat()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)

​[`Array.prototype.includes()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)​

​[`Array.prototype.join()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/join) `concat and return a new String`

​[`Array.prototype.slice()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/slice) `get some return a new array`

```text
arr.slice(begin, end);// [begin, end)
```

​[`Array.prototype.toString()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/toString)​

​[`Array.prototype.lastIndexOf()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf) `return the last index..`

​

Traverse:

​[`Array.prototype.forEach()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)​

​[`Array.prototype.map()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/map)​![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LgnugJ0SdX2tMAwP37V%2F-Li6lCc1yK8BklAkdxk2%2F-Li6lDIjLkob_ZyGL7MN%2Fimage.png?alt=media&token=0113e6cb-2266-4de0-9504-eb8b5d0b0148)

​[`Array.prototype.reduce()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)​

let finalVal = oldArray.reduce\(\(accumulator, currentValue, currentIndex, array\) =&gt; { ... }\), initalValue;![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LgnugJ0SdX2tMAwP37V%2F-Li6lCc1yK8BklAkdxk2%2F-Li6l_4PSuL5t8x5vTMJ%2Fimage.png?alt=media&token=a4684f5a-dfbb-4233-bd49-4852e98dd7bc)

​

​[`Array.prototype.some()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/some) `as least one or return false;`

​[`Array.prototype.filter()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/some)`​`![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LgnugJ0SdX2tMAwP37V%2F-Li6lCc1yK8BklAkdxk2%2F-Li6lNmp7bnfIEJ82q6P%2Fimage.png?alt=media&token=3b00c2c1-bcf3-4194-ac9b-94068b49424d)

​

## Object <a id="object"></a>

​

•**map** transforms the elements in the array

•Based on a function you give

•Return a copy and doesn’t modify the input array

•When the function you provide gets called, it gets called for each element with three arguments: the element itself, the index of the element, and the array itself \(which is seldom useful\).

•**filter** removes unwanted things from an input array.

•Based on a function you give

•Return a copy and doesn’t modify the input array

•map and filter often are used together

​[`Object.assign()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)Copies the values of all enumerable own properties from one or more source objects to a target object.

​[`Object.keys()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys)Returns an array containing the names of all of the given object's **own** enumerable string properties.

​[`Object.values()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/values)Returns an array containing the values that correspond to all of a given object's **own** enumerable string properties.

### Reduce\(\) <a id="reduce"></a>

array.reduce\(\(accumulator, currentValue, currentIndex, sourceArray\) =&gt; { }\)

```text
arr.reduce(callback(accumulator, currentValue[, index[, array]])[, initialValue])
```

​

## String <a id="string"></a>

Strings can also be created using the `String` global object directly:

```text
String(thing)new String(thing)
```

#### ​[Character acces](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#Character_access)s <a id="Character_access"></a>

 string.[`charAt()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/charAt)​

```text
return 'cat'[1];
```

### ​[`String` instance](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#String_instances)​ <a id="String_instances"></a>

`String.prototype.constructor`Specifies the function that creates an object's prototype.[`String.prototype.length`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/length)Reflects the length of the string.

### ​[`String.prototype.concat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/concat)Combines the text of two strings and returns a new string. <a id="string-prototype-concat-combines-the-text-of-two-strings-and-returns-a-new-string"></a>

### ​[`String.prototype.includes()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/includes)Determines whether one string may be found within another string. <a id="string-prototype-includes-determines-whether-one-string-may-be-found-within-another-string"></a>

​[`String.prototype.indexOf()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/indexOf)Returns the index within the calling [`String`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) object of the first occurrence of the specified value, or -1 if not found.

​[`String.prototype.lastIndexOf()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/lastIndexOf)Returns the index within the calling [`String`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) object of the last occurrence of the specified value, or -1 if not found.

​[`String.prototype.match()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/match)Used to match a regular expression against a string.[`String.prototype.matchAll()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/matchAll)Returns an iterator of all matches.[`String.prototype.normalize()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/normalize)Returns the Unicode Normalization Form of the calling string value.

​[`String.prototype.repeat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/repeat)Returns a string consisting of the elements of the object repeated the given times.

### ​[`String.prototype.replace()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace)Used to find a match between a regular expression and a string, and to replace the matched substring with a new substring. <a id="string-prototype-replace-used-to-find-a-match-between-a-regular-expression-and-a-string-and-to-replace-the-matched-substring-with-a-new-substring"></a>

​[`String.prototype.search()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/search)Executes the search for a match between a regular expression and a specified string.

### ​[`String.prototype.slice()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/slice)Extracts a section of a string and returns a new string. <a id="string-prototype-slice-extracts-a-section-of-a-string-and-returns-a-new-string"></a>

```text
str.slice(beginIndex[, endIndex])
```

### ​[`String.prototype.split()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split)Splits a [`String`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) object into an array of strings by separating the string into substrings. <a id="string-prototype-split-splits-a-string-object-into-an-array-of-strings-by-separating-the-string-into-substrings"></a>

```text
str.split([separator[, limit]])
```

### ​[`String.prototype.substring()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/substring)Returns the characters in a string between two indexes into the string. <a id="string-prototype-substring-returns-the-characters-in-a-string-between-two-indexes-into-the-string"></a>

​[`String.prototype.toLowerCase()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase)Returns the calling string value converted to lower case.

​[`String.prototype.toUpperCase()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toUpperCase)Returns the calling string value converted to uppercase.

###  [`String.prototype.toString()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toString)Returns a string representing the specified object. Overrides the [`Object.prototype.toString()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/toString) method. <a id="string-prototype-tostring-returns-a-string-representing-the-specified-object-overrides-the-object-prototype-tostring-method"></a>

​

### Methods[Section](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#Methods)​ <a id="Methods"></a>

​[`String.fromCharCode()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/fromCharCode)Returns a string created by using the specified sequence of Unicode values.[`String.fromCodePoint()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/fromCodePoint)Returns a string created by using the specified sequence of code points.[`String.raw()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/raw) Returns a string created from a raw template string.

## typeof <a id="typeof"></a>

**typeof null = objec**

| **Type** | result |
| :--- | :--- |
| Null | `"object"`（见下文） |
| Boolean | `"boolean"` |
| Number | `"number"` |
| String | `"string"` |
| Symbol （ECMAScript 6 新增） | `"symbol"` |
| 宿主对象（由JS环境提供） | _Implementation-dependent_ |
| 函数对象（\[\[Call\]\] 在ECMA-262条款中实现了） | `"function"` |
| 任何其他对象 | `"object"` |

New

```text
var str = new String('String');var num = new Number(100);typeof str; // It will return 'object'typeof num; // It will return 'object'
```

[  
](https://gzqsjtu.gitbook.io/workspace/javascript/special-function)

