# JS特殊

## 1.compare two objects\(Amazon\)

```javascript
input: 
let a = {
  tagName: 'parent',
  textContent: 'haha',
  children: [
    {
      tagName: 'chilren',
      textContent: 'haha',
      children: null,
      className: 'nihaoa',
      id: '456'
    }
  ],
  className: 'nihao',
  id: '123'
};
let c = {
  tagName: 'parent',
  textContent: 'haha',
  children: [
    {
      tagName: 'chilren',
      textContent: 'haha',
      children: null,
      className: 'nihaoa',
      id: '456'
    }
  ],
  className: 'nihao',
  id: '123'
};

//answer
const compare = (a, b) => {
  for (const key in a) {
    if (Array.isArray(a[key]) && Array.isArray(b[key])) {
      for (let i = 0; i < a[key].length; i++) {
        if (compare(a[key][i], b[key][i]) === false) return false;
      }
    } else {
      if (a[key] !== b[key]) return false;
    }
  }
  return true;
};
```

version2

```javascript
 //判断是否是对象或者是数组
  function isObject(obj) {
    return typeof obj === 'object' && obj !== null
  }

  //全相等
  function isEqual(obj1, obj2) {
    if (!isObject(obj1) || !isObject(obj2)) {
      //值类型(参与equal的一般不会是函数)
      return obj1 === obj2;
    }
    //传入的两个object都是一样的引用地址值
    if (obj1 === obj2) {
      return true;
    }
    //两个都是对象或者数组，而且不相等
    //先取出obj1 和obj2的keys，比较个数
    const obj1keys = Object.keys(obj1);
    const obj2keys = Object.keys(obj2);
    if (obj1keys.length !== obj2keys.length) {
      return false;
    }
    //以obj1为基准 对obj2 一次递归遍历
    for (let key in obj1) {
      const res = isEqual(obj1[key], obj2[key]);
      if (!res) {
        return false;
      }
    }
    return true;
  }
```



## 2.flatten objects to certain ways

```javascript
let d = {
  a: 5,
  b: 6,
  c: {
    f: 9,
    g: {
      m: 17,
      n: 3
    }
  }
};


//answer
const convert = a => {
  let result = {};
  for (let key0 in a) {
    if (typeof a[key0] === 'object') {
      let b = convert(a[key0]);
      if (Object.keys(b).length !== 0) {
        for (let key1 in b) {
          result[`${key0}.${key1}`] = b[key1];
        }
      }
    } else {
      result[key0] = a[key0];
    }
  }
  return result;
};
```

## 3.**Use Array.reduce to calculate the sum of array**

```javascript
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue;

// 1 + 2 + 3 + 4
console.log(array1.reduce(reducer));
// expected output: 10
```

## **4. remove the duplicate element in array**

```javascript
Array.from(new Set(array));

// return first index of occurrence
array.filter((item, index) =>{
  return array.indexOf(item) === index
});

//retrive duplicated values

array.filter((item, index) =>{
  return array.indexOf(item) !== index
});

array.reduce((unique, item) => {
  return unique.includes(item) ? unique : [...unique, item]
}, []);

```

\*\*\*\*

## **5. manipulate objects inside of an array**

```javascript
//return cost < 5 array
//return cost  5 && type === ‘retail’ array

const items = [
  { id: 1, type: ‘retail’, cost: 1 },
  { id: 2, type: ‘retail’, cost: 2 },
  { id: 3, type: ‘retail’, cost: 5 },
  { id: 4, type: ‘retail’, cost: 10 },
  { id: 5, type: ‘inventory’, cost: 1 },
  { id: 6, type: ‘inventory’, cost: 2 },
  { id: 7, type: ‘inventory’, cost: 5 },
  { id: 8, type: ‘inventory’, cost: 10 },
];

array.filter((item, index) =>{
  return item.cost < 5 && item.type === "retail"
});


```

## **6. Implement the ensure function so that it throws an error if called without arguments or the argument is undefined. Otherwise it should return the given value.**

```javascript
function ensure => (value) {
  if (arguments[0] || value === undefined) {
    throw new Error();
  }
  return value;
}
```

## 7.**Write a function that converts user entered date formatted as M/D/YYYY to a format required by an API \(YYYYMMDD\). The parameter "userDate" and the return values are strings.**

```javascript
//f or example, it should convert user entered date "12/31/2014" to "20141231" suitable for the API.
function formatDate => (userDate) {
  // format from M/D/YYYY to YYYYMMDD
  const words = userDate.split(“/“);
  const year = words[2];
  let month = words[0];
  month = month.length >= 2 ? month : “0” + month;
  let day = words[1];
  day = day.length >=2 ? day : “0” + day;
  return year + month + day;
}

console.log(formatDate("12/31/2014"));
```

  


## 8. **Implement the removeProperty function which takes an object and property name, and does the following:If the object obj has a property prop, the function removes the property from the object and returns true; in all other cases it returns false.**

```javascript
function removeProperty(obj, prop) {
   if(obj.hasOwnProperty(prop)) {
       delete obj[prop];
       return true;
   }
   return false;
}

```



## **9. manipulate objects inside of an array**

```javascript
input: 
obj [
{k:"a",v:2},
{k:"b",v:3},
{k:"c",v:7}
]
output: 
out = [{a:4},{b:6},{c:14}]
在输入函数的时候 一定要检查 k的值 有个testcase是他当场写的，k有重复的值
当出现了重复值 变成直接加法
obj [
{k:”a”,v:2},
{k:”b”,v:3},
{k:”c”,v:7},
{k:”c”,v:5}
]
output: 
out = [{a:4},{b:6},{c:19}]
follow up 是用array.reduce 写完这个函数 不可以用for loop
var multi_reduce = (arr) => {
    return arr.reduce((res, element) => {
        var index = res.findIndex(item => item[element.k]);
        if(index >= 0) {
            res[index][element.k] += element.v;
        }
        else{
            let obj = {};
            obj[element.k] = element.v * 2;
            res.push(obj);
        }
        return res;
    }, []);
}
```

## **10. Using bind and apply**

```javascript

//写下这个bind function， apply function， 或者call function 都行, 要求检测两个函数的最后输出
//并且在jest里面describe 一下那个 expect (function a.b)toBe(“.....”)


//jest question：
//const hello= function(name){
 //return `hello, this is ${ this.name} 
//}

//const Person = function(name){
    //this.name = name;
//}
//var t = New Person(“Chris”)
//is t.(hello() work ? how to fix that?
//expect t.hello(.....). toBe(“hello, this is Chris”)




// bind
const hello= function(name){
  return `hello, this is ${ this.name}`
 }

const Person = function(name){
  this.name = name;
}

let t = new Person("Chris");
let result = hello.bind(t);
result();

//apply

const hello= function(name){
  return `hello, this is ${ this.name}`
 }

const Person = function(name){
  this.name = name;
}

let t = new Person("Chris");
hello.apply(t); // run directly


```

\*\*\*\*

\*\*\*\*

## **11.Flatten an array, give \[1,2,3,\[4,5\],\[6,\[7,8,\[9,10\]\]\],  whiteboard**

```javascript
//let arr1 = [1,2,3,[4,5],[6,[7,8,[9,10]]]];
function flatten1(arr) {
  while(arr.some(ele => Array.isArray(ele))) {
      arr = [].concat(...arr);
  }
  return arr;
}
console.log(flatten1(arr1));

```

## **12. combined two objects with certain conditions**

\*\*\*\*

```javascript
let obj1 =[
  {name:"chris", age:26},
  {name:"peter", age:21},
  {name:"Tom"}]
  
let obj2 =[
  {name:"chris", company:"SIS",age:27},
  {name:"peter", company:"Apple"},
  {name:"Tom", company:"walmart"}]

let result =[
  {name:"chris", age:27, company:"SIS"},
  {name:"peter", age: 21,company:"Apple"},
  {name:"Tom", company:"walmart"}]
// hard way
const combine = (obj1, obj2) => {
  let result = [];
  for (let i =0; i < obj1.length; i++) {
    let temp = {};
    for (let key0 in obj1[i]) {
      temp[key0] = obj1[i][key0];  
    }
    for (let key1 in obj2[i]) {
      if (temp[key1] === obj2[i][key1]) {
        continue;
      } else {
        temp[key1] = obj2[i][key1];  
      }
    }
    result.push(temp);
  }
  return result;
}

//easiest way
[...obj1,...obj2];
```

## **13. Node manipulation**

[![](https://lh3.googleusercontent.com/OQpIFyhn6nR4MT6HhDXIN8Mv6R3krgicN-V54HAPL1Ca8jvkBhgnwSfqi88Ne5XvgWGcmwKPiXBBRECvt-vkBvcMMRb79zvKP6PI_ju5CQSf1IpaCLSETR0sGa7TMcbSnjdL3wAD)](https://www.testdome.com/questions/javascript/image-gallery/18215?questionIds=14188,18215,17429,13919&generatorId=16&type=fromtest&testDifficulty=Easy)

## 14. return all object's keys

```javascript
//1:返回 object的所有key值
//recevie object
const process = function(obj){
  let key= Object.keys(obj)
  return key;
}


const process = function(obj){
  let res= [];
  for(let item in obj){
    res.push(item)
  }
  return res;
}
```

## 15.return array's product

```javascript
//2: 返回array的乘积
array.reduce( (sum,cur)=>{
  return sum*cur*cur;
},1)
```

## **16.  return a promise and combine into a new object and add it into promise**

```javascript



//写一个函数 输入是f1 f2 两个函数
//返回promise 的object要求 合并成一个新的object 然后加入进promise
// f1 f2
// call some library
// return promise response is object
// return promise response is object
const  wait = async ()=>{
   let promise1 =new Promise((resolve,reject)=>{
       setTimeout(()=>resolve({a:1},0))
   })
   let promise2 =new Promise((resolve,reject)=>{
       setTimeout(()=>resolve({b:2},0))
   })
   let res1 = await promise1
   let res2 = await promise2;
   let promise3 = new Promise((resolve, reject)=>{
       setTimeout(()=>resolve({...res1,...res2}),0)
   })
   let res3 = await promise3
   console.log(res3)
}

Better version: 
 const promise = (obj) => {
   return new Promise((resolve => {
     setTimeout(() => {
       resolve(obj);
     }, 0);
   }))
 }

 const wait = async () => {
   const val1 = await promise({a: 1});
   const val2 = await promise({b: 2});
   return await promise({...val1, ...val2});
 }

 wait().then((data) => {
   console.log(data);
 }) // {a: 1, b: 2}
```

## 17.finish callback after certain amount of time

```text

// function two parameter
// delay  //one is call back function
// 给一个数组 和 一个函数 要求 间隔index[i]数组里面时间后 完成callback函数
// 确定完成callback函数后 再隔 index[i+1] 再次调用callback函数 循环


const arr = [200,300,500]

const test = function(){
   Axios.get("ur1").then(...arguments);
}
(async function soltion(arr, test){
   for(let i = 0; i < arr.length; i++){
       await new Promise(resolve =>setTimeout(resolve,arr[i]))
       await test();
   } 
})(arr,test);

Better version: 

 const arr = [2000, 5000, 3000];

 const wait = (time) => {
   return new Promise((resolve) => {
     setTimeout(() => {
       resolve("test");
     }, time);
   })
 }

 const solution = async () => {
   for (let i = 0; i < arr.length; i++) {
     await wait(arr[i]);
   }
 }
```

  


## 18. **query string: input an object**

```javascript
//{name: ‘michael’, company: ‘walmart’}    
//return “?name=michael&company=walmart”
 const query = (obj) => {
  let query = "?";
  for (let key in obj) {
    query +=`${key}=${obj[key]}&`
  }
   return query.slice(0,query.length -1 );
 }

```

## **19. filter negative number**

```javascript
numbers = [-1,-2,-3,5,6]
const result = numbers.filter(number => number >= 0);

```

## 20. check code and predict output

```javascript
var x = 21; 
var girl = function () { 
console.log(x); 
var x = 20; 
}; girl();
// return undeified due to variable hoist
```

**21. deep clone of an object???**

```javascript
// method 1 

let arr = {test:[{name:"123", id:"456"}]};
first I write a deep clone
function clone(arr) {
 if(arr === null) return arr;
    const copy = arr.constructor();
    for(let a in arr) {
     if(arr.hasOwnProperty(a)) copy[at] = arr[at];
    }
 return copy;
}


// method 2 very effective
var arr = JSON.parse(JSON.stringify(arr));

```

\*\*\*\*

## **22. mutate array with reduce function**

```javascript
//arr=[1,2,3,4]
//get [2,3,4,5]
//use other methods, for loop, for each, map

arr.reduce((res, element) => {
  element += 1;
  res.push(element);
  return res;
},[])

arr.map(element => element + 1);

array1.forEach(element => element + 1);





```

##  23.implement **memoize**

```javascript
const add = (...input) => (input.reduce((res,num) => res + num, 0));
const memoized = (callback) => {
    let cache = {};
    return (...parameter) => {
        if(parameter in cache) {console.log("cached"); return cache[parameter];}
        else {
            console.log(parameter)
            const res = callback(...parameter);
            cache[parameter] = res;
            console.log("callback")
            return res;
        }
    }
}
const memoizedAdd = memoized(add);
console.log(memoizedAdd(1,2,3,4));
console.log(memoizedAdd(1,2,3,4));
```

##  24.fnLimiter

**write fnLimiter, to limit the callback numbers.**

**write a function fnLimiter\(limit, callback\){}**

**that call back can only run “limit” times. after this return false;**

```javascript
function fnLimiter(limit, callback {
	return function(arg){
    if(limit > 0) {
      limit--;
      callback(arg);
    } 
  }
});

var callback = (abc) => {
  console.log(abc);
  
}

var fn = fnLimiter(5, callback);
fn(45);
fn(50);
fn(11)
fn(12)
fn(100);
fn(33);




```

## 25.flatten array

```javascript
var arr = [[10,[18,45,79]],20,[30,33],40];
[10,18,45,79,20,30,33,40]



function flattern(arr) {
   var arr1 = [];
   const reducer = (arr1,curElement) => {
    	if(Array.isArray(curElement)){
   			 arr1.concat(flattern(curElement));
  		} else {
         arr1 = [...arr1].concat(curElement);
      }
 	 }
   arr.reduce(reducer, arr1);
  return arr1;
```

## 26.debounce

a debounce function will wait until the last time the function is called and then fire after a predetermined amount of time or once the event firing becomes inactive.

scenarios: Debouncing a resize event handler Debouncing a scroll event handler Debouncing a save function in an autosave feature

```javascript
const debounce = (fn, time) => {
  let timeout;

  return function (...args) { // <-- not an arrow function
    const functionCall = () => fn.apply(this, args);

    clearTimeout(timeout);
    timeout = setTimeout(functionCall, time);
  }
}

const obj = {
  name: 'foo',
  sayMyName() {
    console.log('My name is', this.name)
  }
}

obj.sayMyName() //-> My name is foo
obj.sayMyName = debounce(obj.sayMyName, 1000)
obj.sayMyName() //-> My name is foo <-- allows correct this binding

// <input name="my-input" />
input.addEventListener('keyup', debounce(function (e) { // <-- allows handler element binding
  console.log('Element name is', this.name); //-> Element name is my-input
}, 1000));
```

// second version

```javascript
const input = document.getElementById("inpu1");
function debounce(fn, delay = 500) {
  let timer = null;
  return function (){
    if (timer) {
      clearTimeout(timer);
    }
    timer = setTimeout(() => {
      console.log(this) //input here
      fn.apply(this, arguments);
      timer = null;
    }, delay)
  }
}

input.addEventListener('keyup', debounce(function () {
  console.log(input.value);
}));
```



## 27.throttle

scenarios:throttling a button click so we can’t spam click Throttling an API call Throttling a mousemove/touchmove event handler

```javascript
// functions can only run after certain amount of time
function throttle(cb, time) {
  let ignore = false;
    return function(...args) {
        let context = this;
        if (!ignore) {
            ignore = true;
            cb.apply(context, args);
            setTimeout(function() {
            ignore = false;
            }, time);
        }
    }
}
```

version 2

```javascript
const input = document.getElementById("inpu1");
function throttle(fn, delay = 500) {
  let timer = null;
  return function (){
    if (timer) {
      return;
    }
    timer = setTimeout(() => {
      console.log(this) //input here
      fn.apply(this, arguments);
      timer = null;
    }, delay)
  }
}

input.addEventListener('keyup', throttle(function () {
  console.log(input.value);
}));
```



## 28.retry **??**

```javascript
const retry = async (assertion, remainingAttempts, retryInterval = 0) => {
 if (remainingAttempts <= 1) {
  return assertion();
 } else {
  try {
   assertion();
  } catch (e) {
   await delay(retryInterval);
   await retry(assertion, remainingAttempts - 1, retryInterval);
  }
 }
}
```



## 29. curry

\*\*\*\*

```javascript
add(1)(2)(3) = 6
add(1)(2) = 3
add(1) = 1

function add(x){
    let sum = x;
    return function resultFn(y){
        if(arguments.length){ //not relying on falsy value
            sum += y;
            return resultFn;
        }
        return sum;
    }
}


> add(2)(3)() //output: 5
> var t = add(3)(4)(5)
> t() //output: 12

function add(){
    let args = [].slice.apply(arguments);
    function resultFn(){
        args = args.concat([].slice.apply(arguments));
        if(args.length>=3){
            return args.slice(0,3).reduce(function(acc,next){ return acc+next},0); //will only sum first 3 arguments
        }
        return resultFn;
    }
    return resultFn();
}

> add(2)(3)(4) //output: 9
> add(2,3,4) //output: 9
> add(2)(3,4) //output: 9
> add(2,3)(4) //output: 9


//写个function sum 支持两种call
//sum(2, 3); //5
//sum(2)(3); //5
//用arguments不用arguments

let sum = (a, b) => {
 if (b === undefined) {
   return (c) => a + c;
  }
  return a + b;
}

let sum = function() {
  if (arguments.length === 2) {
    return arguments[0] + arguments[1];
  } 
  let cur = arguments[0];
  return function(c) {
    return cur + c;
  }
}
```

\*\*\*\*

## 30.**converse input to output const input = \[{**

    **"title": "Spending or sending money",**

    **"rows": \[{**

      **"title": "International transaction \(sending money to accounts outside the U.S.\)",**

      **"fee": "5% \(minimum $1 and maximum $2\)",**

      **"description": "There's a fee when you send personal payments to friends and family in countries outside of Canada and Europe using your Cash balance.&lt;br/&gt;&lt;br/&gt;If you're sending in a foreign currency, the fee is a comparable amount in that currency."**

    **}\]**

  **},**

  **{**

    **"title": "Transferring money from your balance",**

    **"rows": \[{**

        **"title": "Electronic withdrawal \(Instant Transfer\)",**

        **"fee": "1.00%  \(maximum $3 fee\)",**

        **"description": "There's a fee to transfer money from your Cash account to your eligible linked bank account or debit card with the Instant Transfer option. The money is typically available in minutes."**

      **},**

      **{**

        **"title": "checks",**

        **"fee": "$5",**

        **"description": "There's a fee to have a paper check mailed to you."**

      **}**

    **\]**

  **}**

**\]**  
  


**/\* output \*/**  


**/\* title1="Spending or sending money”**

**title2="International transaction \(sending money to accounts outside the U.S.\)”**

**fee1="5% \(minimum $1 and maximum $2\)”**

**description1="There's a fee when you send personal payments to friends and family in countries outside of Canada and Europe using your Cash balance.&lt;br/&gt;&lt;br/&gt;If you're sending in a foreign currency, the fee is a comparable amount in that currency.”**

**title3="Transferring money from your balance"**

**title4="Electronic withdrawal \(Instant Transfer\)"**

**fee2="1.00%  \(maximum $3 fee\)”**

**descripton2="There's a fee to transfer money from your Cash account to your eligible linked bank account or debit card with the Instant Transfer option. The money is typically available in minutes." \*/**  


```javascript

var map = {}
const flattenObject = (input) => {
    flatten = (obj) => {
        return [].concat(
            ...Object.keys(obj).map(key => {
                if(typeof obj[key] === "object"){
                    return flatten(obj[key]);
                } else {
                    let num = 1;
                    if(map[key]){
                        num = map[key];
                        map[key]++;
                                    }  else {
                        map[key] = 2;
                    }
                    return `${key}${num} = ${obj[key]}`;
                }
            })
        )
    }
    return flatten(input).join(' ');
}
```

## 30.**coding question\(split,map\)**

```javascript
//coding question，输入是一个string, 相当于一个文章的段落，统计所有词出现的频率，在console中打印结果，要求去掉所有的标点符号，类似于comma, full stop and dash，这些要去掉。
//所以首先我们可以用str.replace(/[^a-zA-Z ]/g, “”) 来去掉所有的标点，注意regex里面最后要包含空格在内，然后用split(“ ”)方法得到单词，然后用map统计频率，不难
```

  


## 31.**simple promise**

```javascript
var promise1 = new Promise(function(resolve, reject) {
  setTimeout(function() {
    resolve('foo');
  }, 300);
});

promise1.then(function(value) {
  console.log(value);
  // expected output: "foo"
});

console.log(promise1);
// expected output: [object Promise]

//类似于new Promise((resolve, reject) => resolve(“hi”))

```

\*\*\*\*

## 32. print **&lt;li&gt;&lt;a&gt;some number&lt;/a&gt;&lt;/li&gt; number**

[**https://codepen.io/YoungShaw/pen/QRPveW**](https://codepen.io/YoungShaw/pen/QRPveW)  


## 33.**randomize two arrays**

```javascript
//coding question: 给两个数组，要求输出两个数组， 但是数组中的数字要randomize
//例如input是两个数组[1, 2, 3], [4, 5, 6]，
//output可能是[2, 5, 4] [6 1 3]
//我们可以首先concat这两个数组，然后开始randomize
//核心就是这一小段，然后可以根据长度slice()出两个数组


for (let i = temp.length - 1; i >= 0; i--) {
    let j = Math.floor(Math.random() * (i + 1));
    [temp[i], temp[j]] = [temp[j], temp[i]];
}

```

##  **** 34. Object manipulation 

![](https://lh5.googleusercontent.com/xFdOPJ5zSqlSDnYAFaPfzcbglblofubINPJsfZlCfvjom-O_h-_CkjUsqx_E8WF9pTnsBCBxWja7sLOesHC4JmBIbfxn4lAMBLlEyqt90mlWEXMDCrid8Dhdz4NYzXlr51nLjQFi)

![](https://lh3.googleusercontent.com/DwJZVDHc_IvE6hfCYWJQmX8YnGBpsBdR3vToYTFSEY6tp_Nq0G7AsTOdE0q9zvzD5FD31dh9_yVGpuYSJ4Ed8j2_D-Zmto-yQOHk9do0SLaDpW2i-tkWQ3wsJRwhGLgOrM2mJGWC)

```javascript
const input = [
  { store: 'sunnyvale', item: 'bike' },
  { store: 'mtv', item: 'chocolate' },
  { store: 'milpitas', item: 'bike' },
  { store: 'fremont', item: 'football' },
  { store: 'san francisco', item: 'football' },
  { store: 'newark', item: 'milk' }
];

const b = obj => {
  let result = {};
  obj.forEach(function(item, index) {
    if (result[item.item]) {
      result[item.item].push(item.store);
    } else {
      result[item.item] = [];
      result[item.item].push(item.store);
    }
  });
  let s = '';
  for (let key in result) {
    let temp = result[key].toString();
    s += `${key} at ${temp} `;
  }
  return s;
};

```

## **35.coding: find number of character in string.** 

```javascript
const count = s => {
  let result = {};
  for (let i = 0; i < s.length; i++) {
    if (result[s[i]]) {
      result[s[i]] += 1;
    } else {
      result[s[i]] = 1;
    }
  }
  let rs = "";
  for (let key in result) {
    rs += `${key}${result[key]}`;
  }
  return rs;
};

```



\*\*\*\*

## **36. check code**

```javascript
(function(){
  var a = b = 3;
	
})();

console.log("a defined? " + (typeof a !== 'undefined'));
console.log("b defined? " + (typeof b !== 'undefined'));

//a === 'undefined' b ==3

var y = 1;
  if (function f(){}) {
    y += typeof f;
  }
  console.log(y);
//1undefined


```

##  37.**reverse “the sky is blue” to “blue is sky the”**

```javascript
const reverse1 = (s) => {
  let res = s.split(" ").reverse().join(" ");
}
```

##  **38.下面getData加括号getData\(\);**

```javascript
function getData() {
        return "Success";
}
 getData().then((res) => {
        document.querySelector(".result").textContent = res;
 });
```



## **39.object manipulation**

```javascript
let a = { b: { c: 'd' } }

let interview = (obj, path, defaultValue) => {
    let paths = path.split(".");
    let currentResult = obj;
    for (name in paths) {
      currentResult = currentResult[name] ? currentResult[name] : defaultValue; 
    }
    return currentResult;
}

//interview(a, 'b.c', 'defaultValue')
//interview(a, 'c', 'defaultValue')
//interview(a, 'b', 'defaultValue')
console.log(interview(a, 'b.c', 'defaultValue'))
console.log(interview(a, 'c', 'defaultValue'))
console.log(interview(a, 'b', 'defaultValue'))
```

\*\*\*\*

## **40.code checking**

![](https://lh6.googleusercontent.com/VVkWI6ugqc-5S0AtFD4pesmDw3ZnkHQUjkAXKaVXWPUmbvRtk87TVN4kvxg9CPZJdKAsIsvHStUuVHdi98TjEKfQnYB4UyE3f1cm5yUlnq_UrLVYhq0g3WG__fqqKBkrT35eKll0)

## **41. Use reduce to merge 3 objects：use spread&rest**

```javascript

let a = {a : "a"};
let b = {b: "b"};
let c = {c: "c"};

const merge1 = (...arg) => {
  console.log(arg); //[{…}, {…}, {…}]
  console.log(...arg); //{a: "a"} {b: "b"} {c: "c"}
}


const merge2 = (arg) => {
  console.log(arg); //{a: "a"}
  console.log(...arg); //Uncaught TypeError: Found non-callable @@iterator
}

// correct method
const merge = (...arg) => {
  let result = {...arg[0],...arg[1],...arg[2]};
  console.log(result);
}

```



##  **43. write custom reduce function that have same functionality as system defined reduce function**



## 44.  **Return an array of object that editable is true.** 

```javascript
[{name: “a”,
     editable: true
    },
    {name: “b”,
     editable: true
    },
    {name: “c”,
     editable: false
    }
   ]
   Return an array of object that editable is true.
   
 const editable = (arg) => {
  let res = arg.filter(elment => elment.editable == true);
  console.log(res);
}
```

  


## **45**. code checking

```javascript
function a(){
    console.log(a);
    console.log(test());

    var a = 1;
    function test(){
        return 2;
    }
}
// undefined and 2



var car = "Honda";
var garage = {
    car: "BMW",
    getCar : function() {
        return this.car;
    }
}

var myCar = garage.getCar;

console.log(myCar()); // Honda

var myCar = garage.getCar.bind(garage);
console.log(myCar()); // BMW
```

\*\*\*\*

## **46. log\(‘test’, ‘is’, ‘happy’\) =&gt; “test is happy”**

```javascript
const log = (...arg) => {
  let res = arg.join(" ");
  console.log(res);
}

// in es6, arguments got replaced by ...

```

## 47.getElementByClassName

```javascript
How to implement getElementByClassName?
Write the function.
ex,
<html>
<div  ref = ‘root’>
	<span></span>
</div>
<ol>
	<li></li>
	<li></li>
	<li></li>
	<li></li>
</ol>
</html>
How to get all elements? Write the function.
( You don’t have any API, only have getChildren(), getNextSibling(), getParent() )

  function walkDOM(main) {
 var arr = []; 
 var loop = function(main) { 
   do { arr.push(main);
     if(main.hasChildNodes()) 
        loop(main.firstChild); } 
   while (main = main.nextSibling); 
} 
loop(main); 
return arr; } 
walkDOM(document.body);

const walkDOM= function(main) {              // 不一定对

   let arr = [];
   if (!main) {
       return arr;
   }
   const dfs = function(main) {
     arr.push(main);
     if (main.hasChildNodes()){
       let childrens=main.getChildren();  
       for (let i = 0; i < childrens.size(); i++) {
         let n=childrens[i];
         if(n!=null){
           dfs(n);
         }
       }
     }
   }
   dfs(main);
   return arr;
}
walkDOM(document.body);
```

## 48.**Given an array and chunk size, divide the array into many subarrays where each subarray is of length size**

**// --- Examples**

**// chunk\(\[1, 2, 3, 4\], 2\) --&gt; \[\[ 1, 2\], \[3, 4\]\]**

**// chunk\(\[1, 2, 3, 4, 5\], 2\) --&gt; \[\[ 1, 2\], \[3, 4\], \[5\]\]  用array.slice做的**  


## 49. Object Manipulation

```javascript
   var obj = {
       name: "Tom",
       age: 20
        }

       var dup = obj;
       obj.age = 45;

       console.log(dup.age);
       console.log(obj.age);
	各种记不清楚的改来改去问print的结果是什么
（2）
test();
var n = 9;;

function test(){
 console.log(n);
}
console.log(n);
问result


6.
// A AND (B OR C)

var root = {
  type: 'operator',
  value: 'AND',
  children: [{
    type: 'operand',
    value: 'A'
  }, {
    type: 'operator',
    value: 'OR',
    children: [{
      type: 'operand',
      value: 'B'
    }, {
      type: 'operand',
      value: 'C'
    }]
  }]
};

描述一下有什么方法可以把这个json object变成 A AND (B OR C);(DFS)

```

##  50. 

```text
Given a 7*3 grid of characters output a decoded message. The  message for the following would be IROCKED.
            var message = [
       ['I', 'B', 'C', 'A', 'K', 'E', 'A'],
       ['D', 'R', 'F', 'C', 'A', 'E', 'A'],
        ['G', 'H', 'O', 'E', 'L', 'A', 'D']];
var decode = function(messages) {
let m = messages.length;
let n = messages[0].length;

let down = -1;
let j = 0;
let res = [];
for (let i = 0; i < n; i++) {
  
   res.push(messages[j][i]);
   if (j === 0 || j === m-1) {
       down = -down;
   }
   j+= down;
  
}
return res;
}            // Emily提供
```

## 51.give you data, ask you to return array of salary inorder

```text
// give you data, aske you to return array of salary inorder
const data = [
[1, "FTE", 75000],
[2, "FTE", 100000],
[3, "Manager", "4,5"],
[4, "Manager", "1,2"],
[5, "FTE", 80000]
];

```

  


## 52. 2d array

```javascript
 Given a 2d array like this, which is the start and the destination, find the longest path
[[“SFO”, “LA”],
[“Beijing”, “SFO”],
[“LA”, “Beijing”],
[“NY”, “LA”],
[“STL”, “SFO”]
]

The longest path is [“NY”, “LA”, “Beijing”, “SFO”]

Hint: using 2 maps: 
convert 2d array to map
all destinations in a map, this case:
{LA: true, SFO: true, Beijing: true, SFO: true}
start point is the starting point without destination

```

## 53.**输入: an  array of strings and a word, 从每个string里取一个字母，最后拼出这个单词find all combinations** 



## **54..字符转换 ab-cd-ef 变成 abCdEf**

```javascript
let str1 = "ab-cd-ef";
let str2 = "abCdEf";
 
let res = "";
let arr = str1.split("-");
res = arr[0];
for(let i = 1; i< arr.length; i++){
   let s = arr[i];
   s = s[0].toUpperCase() + s.substr(1);
   res += s;
}
 
console.log(res);
```

## **55. Subsets** 

```javascript
nums = [1,2,3];
function subsets(nums){
   var res = [];
   for(let i = 0; i< nums.length; i++){
       var num = nums[i];
       var max = res.slice().length;
       res.push([num]);
       for(let j = 0 ; j < max; j++){
           var list = res[j].slice();
           list.push(num);
           res.push(list);
       }
 
   }
   res.push([]);
 
   return res;
}
var test = subsets(nums);
for(let i = 0; i< test.length; i++){
   console.log(test[i]);
}

```

## 56.Observable

```javascript
class Observable {
    constructor(functionThatTakesObserver){
      this._functionThatTakesObserver = functionThatTakesObserver;
    }

    subscribe(observer) {
      return this._functionThatTakesObserver(observer)
    }
}

let myObservable = new Observable(observer => {
  setTimeout(() => {
    observer.next("got data!")
    observer.complete()
  }, 1000)
})

let myObserver = {
  next(data) {
    console.log(data)
  },
  error(e) {
    console.log(e)
  },
  complete() {
    console.log("request complete")
  }
}

myObservable.subscribe(myObserver)
// (1 second) got data!
// (1 second) request complete

//https://www.stackchief.com/tutorials/JavaScript%20Observables%20in%205%20Minutes
```



## 57. EvenEmitter

```javascript
// we'll omit error handling and complex stuff for simplicity
const EventEmitter = {
  events: {}, // dictionary with our events
  on(event, listener) { // add event listeners
    if (!this.events[event]) { this.events[event] = { listeners: [] } }
    this.events[event].listeners.push(listener);
  },
  off(event) { // remove listeners
    delete this.events[event]
  },
  emit(name, ...payload) { // trigger events
    for (const listener of this.events[name].listeners) {
      listener.apply(this, payload)
    }
  }
};

EventEmitter.on('dog', () => console.log('dog'));
EventEmitter.on('dog', (name, color, race) => console.log('dog', name, color, race));

EventEmitter.emit('dog');
// dog
// dog undefined undefined undefined

EventEmitter.emit('dog', 'Fig', 'brown', 'chihuahua');
// dog
// dog Fig brown chihuahua

EventEmitter.off('dog')

EventEmitter.emit('dog');
// TypeError: Cannot read property 'listeners' of undefined

//https://dev.to/tunaxor/the-beautiful-thing-called-eventemitter-23ei
```

## 58.querySelector

```javascript
/**
 * Run a callback over all children of a given element using depth-first
 * traversal.
 *
 * @param {HTMLElement} element
 * @param {Function}    callback
 */
function iterateDOM(element, callback) {
    const nodes = [];

    nodes.push(element);

    do {
        element = nodes.shift();

        callback(element);

        nodes.unshift(element.children);
    } while (nodes.length > 0);
}

/**
 * Determine if an element matches a given string query.
 *
 * @param {HTMLElement} element
 * @param {string}      query
 *
 * @return {bool}
 */
function matchElement(element, query) {
    return element.tagName === query.toUpperCase() ||
        element.classList.contains(query);
}

/**
 * Return the first element matching the given query.
 *
 * @param {string} query
 *
 * @return {HTMLElement}
 */
function querySelector(query) {
    return querySelectorAll(query)[0];
}

/**
 * Return all elements matching the given query.
 *
 * @param {string} query
 *
 * @return {HTMLElement[]}
 */
function querySelectorAll(query) {
    const elements = [];

    iterateDOM(this, function(element) {
        if (matchElement(element, query)) {
            elements.push(element);
        }
    });

    return elements;
}
```



## 59.Promise.all and promise final

[https://medium.com/@muralikv/implementing-promise-all-in-javascript-732076497946](https://medium.com/@muralikv/implementing-promise-all-in-javascript-732076497946)



## 60.Promise with limit



## 61.Promise

```javascript
// 三种状态
const PENDING = "pending";
const RESOLVED = "resolved";
const REJECTED = "rejected";
// promise 接收一个函数参数，该函数会立即执行
function MyPromise(fn) {
  let _this = this;
  _this.currentState = PENDING;
  _this.value = undefined;
  // 用于保存 then 中的回调，只有当 promise
  // 状态为 pending 时才会缓存，并且每个实例至多缓存一个
  _this.resolvedCallbacks = [];
  _this.rejectedCallbacks = [];

  _this.resolve = function (value) {
    if (value instanceof MyPromise) {
      // 如果 value 是个 Promise，递归执行
      return value.then(_this.resolve, _this.reject)
    }
    setTimeout(() => { // 异步执行，保证执行顺序
      if (_this.currentState === PENDING) {
        _this.currentState = RESOLVED;
        _this.value = value;
        _this.resolvedCallbacks.forEach(cb => cb());
      }
    })
  };

  _this.reject = function (reason) {
    setTimeout(() => { // 异步执行，保证执行顺序
      if (_this.currentState === PENDING) {
        _this.currentState = REJECTED;
        _this.value = reason;
        _this.rejectedCallbacks.forEach(cb => cb());
      }
    })
  }
  // 用于解决以下问题
  // new Promise(() => throw Error('error))
  try {
    fn(_this.resolve, _this.reject);
  } catch (e) {
    _this.reject(e);
  }
}

MyPromise.prototype.then = function (onResolved, onRejected) {
  var self = this;
  // 规范 2.2.7，then 必须返回一个新的 promise
  var promise2;
  // 规范 2.2.onResolved 和 onRejected 都为可选参数
  // 如果类型不是函数需要忽略，同时也实现了透传
  // Promise.resolve(4).then().then((value) => console.log(value))
  onResolved = typeof onResolved === 'function' ? onResolved : v => v;
  onRejected = typeof onRejected === 'function' ? onRejected : r => throw r;

  if (self.currentState === RESOLVED) {
    return (promise2 = new MyPromise(function (resolve, reject) {
      // 规范 2.2.4，保证 onFulfilled，onRjected 异步执行
      // 所以用了 setTimeout 包裹下
      setTimeout(function () {
        try {
          var x = onResolved(self.value);
          resolutionProcedure(promise2, x, resolve, reject);
        } catch (reason) {
          reject(reason);
        }
      });
    }));
  }

  if (self.currentState === REJECTED) {
    return (promise2 = new MyPromise(function (resolve, reject) {
      setTimeout(function () {
        // 异步执行onRejected
        try {
          var x = onRejected(self.value);
          resolutionProcedure(promise2, x, resolve, reject);
        } catch (reason) {
          reject(reason);
        }
      });
    }));
  }

  if (self.currentState === PENDING) {
    return (promise2 = new MyPromise(function (resolve, reject) {
      self.resolvedCallbacks.push(function () {
        // 考虑到可能会有报错，所以使用 try/catch 包裹
        try {
          var x = onResolved(self.value);
          resolutionProcedure(promise2, x, resolve, reject);
        } catch (r) {
          reject(r);
        }
      });

      self.rejectedCallbacks.push(function () {
        try {
          var x = onRejected(self.value);
          resolutionProcedure(promise2, x, resolve, reject);
        } catch (r) {
          reject(r);
        }
      });
    }));
  }
};
// 规范 2.3
function resolutionProcedure(promise2, x, resolve, reject) {
  // 规范 2.3.1，x 不能和 promise2 相同，避免循环引用
  if (promise2 === x) {
    return reject(new TypeError("Error"));
  }
  // 规范 2.3.2
  // 如果 x 为 Promise，状态为 pending 需要继续等待否则执行
  if (x instanceof MyPromise) {
    if (x.currentState === PENDING) {
      x.then(function (value) {
        // 再次调用该函数是为了确认 x resolve 的
        // 参数是什么类型，如果是基本类型就再次 resolve
        // 把值传给下个 then
        resolutionProcedure(promise2, value, resolve, reject);
      }, reject);
    } else {
      x.then(resolve, reject);
    }
    return;
  }
  // 规范 2.3.3.3.3
  // reject 或者 resolve 其中一个执行过得话，忽略其他的
  let called = false;
  // 规范 2.3.3，判断 x 是否为对象或者函数
  if (x !== null && (typeof x === "object" || typeof x === "function")) {
    // 规范 2.3.3.2，如果不能取出 then，就 reject
    try {
      // 规范 2.3.3.1
      let then = x.then;
      // 如果 then 是函数，调用 x.then
      if (typeof then === "function") {
        // 规范 2.3.3.3
        then.call(
          x,
          y => {
            if (called) return;
            called = true;
            // 规范 2.3.3.3.1
            resolutionProcedure(promise2, y, resolve, reject);
          },
          e => {
            if (called) return;
            called = true;
            reject(e);
          }
        );
      } else {
        // 规范 2.3.3.4
        resolve(x);
      }
    } catch (e) {
      if (called) return;
      called = true;
      reject(e);
    }
  } else {
    // 规范 2.3.4，x 为基本类型
    resolve(x);
  }
}

```



## 62.getElementsByAttribute

```javascript
function getElementsByAttribute(attribute){
  var allElements = document.getElementsByTagName('*'), 
      elm,
      found=[];
  for (var i = 0; i < allElements.length; i++)
   {
    elm = allElements[i];
    if (elm.getAttribute(attribute))
    {
      found.push(elm);
    }
  }
  return found;
}
```

## 63.array methods

The **`Array.from()`** method creates a new, shallow-copied `Array` instance from an array-like or iterable object. \(new\)

```javascript
console.log(Array.from('foo'));
// expected output: Array ["f", "o", "o"]

console.log(Array.from([1, 2, 3], x => x + x));
// expected output: Array [2, 4, 6]


```

The **`Array.isArray()`** method determines whether the passed value is an [`Array`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array).

```javascript
Array.isArray([1, 2, 3]);  // true
Array.isArray({foo: 123}); // false
Array.isArray('foobar');   // false
Array.isArray(undefined);  // false
```

**`Array.of()`** method creates a new `Array` instance from a variable number of arguments, regardless of number or type of the arguments.The difference between **`Array.of()`** and the **`Array`** constructor is in the handling of integer arguments: **`Array.of(7)`** creates an array with a single element, `7`, whereas **`Array(7)`** creates an empty array with a `length` property of 7 \(new\)

```javascript
Array.of(7);       // [7] 
Array.of(1, 2, 3); // [1, 2, 3]

Array(7);          // array of 7 empty slots
Array(1, 2, 3);    // [1, 2, 3]
```

The **`concat()`** method is used to merge two or more arrays. This method does not change the existing arrays, but instead returns a new array.\(new\)

```javascript
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];

console.log(array1.concat(array2));
// expected output: Array ["a", "b", "c", "d", "e", "f"]

```

The **`entries()`** method returns a new **`Array Iterator`** object that contains the key/value pairs for each index in the array.  


```javascript
const array1 = ['a', 'b', 'c'];

const iterator1 = array1.entries();

console.log(iterator1.next().value);
// expected output: Array [0, "a"]

console.log(iterator1.next().value);
// expected output: Array [1, "b"]

```

The **`fill()`** method fills \(modifies\) all the elements of an array from a start index \(default zero\) to an end index \(default array length\) with a static value. It returns the modified array.\(modified\)

```javascript
const array1 = [1, 2, 3, 4];

// fill with 0 from position 2 until position 4
console.log(array1.fill(0, 2, 4));
// expected output: [1, 2, 0, 0]

// fill with 5 from position 1
console.log(array1.fill(5, 1));
// expected output: [1, 5, 5, 5]

console.log(array1.fill(6));
// expected output: [6, 6, 6, 6]
```

The **`filter()`** method **creates a new array** with all elements that pass the test implemented by the provided function.\(new\)

```javascript
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter(word => word.length > 6);

console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]

```

The **`find()`** method returns the **value** of the **first element** in the provided array that satisfies the provided testing function.

```javascript
const array1 = [5, 12, 8, 130, 44];

const found = array1.find(element => element > 10);

console.log(found);
// expected output: 12

```

The **`findIndex()`** method returns the **index** of the first element in the array **that satisfies the provided testing function**. Otherwise, it returns -1, indicating that no element passed the test.

```javascript
const array1 = [5, 12, 8, 130, 44];

const isLargeNumber = (element) => element > 13;

console.log(array1.findIndex(isLargeNumber));
// expected output: 3

```

The **`flat()`** method creates a new array with all sub-array elements concatenated into it recursively up to the specified depth.\(new\)

```javascript
var arr1 = [1, 2, [3, 4]];
arr1.flat(); 
// [1, 2, 3, 4]

var arr2 = [1, 2, [3, 4, [5, 6]]];
arr2.flat();
// [1, 2, 3, 4, [5, 6]]

var arr3 = [1, 2, [3, 4, [5, 6]]];
arr3.flat(2);
// [1, 2, 3, 4, 5, 6]

var arr4 = [1, 2, [3, 4, [5, 6, [7, 8, [9, 10]]]]];
arr4.flat(Infinity);
// [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

The **`forEach()`** method executes a provided function once for each array element.

```javascript
const array1 = ['a', 'b', 'c'];

array1.forEach(element => console.log(element));

// expected output: "a"
// expected output: "b"
// expected output: "c"

```

The **`includes()`** method determines whether an array includes a certain value among its entries, returning `true` or `false` as appropriate.

```javascript
const array1 = [1, 2, 3];

console.log(array1.includes(2));
// expected output: true

const pets = ['cat', 'dog', 'bat'];

console.log(pets.includes('cat'));
// expected output: true

console.log(pets.includes('at'));
// expected output: false

```

The **`indexOf()`** method returns the first index at which a given element can be found in the array, or -1 if it is not present.

```javascript
const beasts = ['ant', 'bison', 'camel', 'duck', 'bison'];

console.log(beasts.indexOf('bison'));
// expected output: 1

// start from index 2
console.log(beasts.indexOf('bison', 2));
// expected output: 4

console.log(beasts.indexOf('giraffe'));
// expected output: -1

```

The **`join()`** method creates and returns a new string by concatenating all of the elements in an array \(or an [array-like object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Indexed_collections#Working_with_array-like_objects)\), separated by commas or a specified separator string. If the array has only one item, then that item will be returned without using the separator.\(new\)

```javascript
const elements = ['Fire', 'Air', 'Water'];

console.log(elements.join());
// expected output: "Fire,Air,Water"

console.log(elements.join(''));
// expected output: "FireAirWater"

console.log(elements.join('-'));
// expected output: "Fire-Air-Water"

```

The **`keys()`** method returns a new **`Array Iterator`** object that contains the keys for each index in the array.

```javascript
const array1 = ['a', 'b', 'c'];
const iterator = array1.keys();

for (const key of iterator) {
  console.log(key);
}

// expected output: 0
// expected output: 1
// expected output: 2

```

The **`lastIndexOf()`** method returns the last index at which a given element can be found in the array, or -1 if it is not present. The array is searched backwards, starting at `fromIndex`.

```javascript
const animals = ['Dodo', 'Tiger', 'Penguin', 'Dodo'];

console.log(animals.lastIndexOf('Dodo'));
// expected output: 3

console.log(animals.lastIndexOf('Tiger'));
// expected output: 1

```

The **`map()`** method **creates a new array** with the results of calling a provided function on every element in the calling array.\(new\)

```javascript
const array1 = [1, 4, 9, 16];

// pass a function to map
const map1 = array1.map(x => x * 2);

console.log(map1);
// expected output: Array [2, 8, 18, 32]

```

The **`pop()`** method removes the **last** element from an array and returns that element. This method changes the length of the array.\(modified\)

```javascript
const plants = ['broccoli', 'cauliflower', 'cabbage', 'kale', 'tomato'];

console.log(plants.pop());
// expected output: "tomato"

console.log(plants);
// expected output: Array ["broccoli", "cauliflower", "cabbage", "kale"]

plants.pop();

console.log(plants);
// expected output: Array ["broccoli", "cauliflower", "cabbage"]

```

  
The **`push()`** method adds one or more elements to the end of an array and returns the new length of the array.\(modified\)

```javascript
const animals = ['pigs', 'goats', 'sheep'];

const count = animals.push('cows');
console.log(count);
// expected output: 4
console.log(animals);
// expected output: Array ["pigs", "goats", "sheep", "cows"]

animals.push('chickens', 'cats', 'dogs');
console.log(animals);
// expected output: Array ["pigs", "goats", "sheep", "cows", "chickens", "cats", "dogs"]

```

  
The **`reduce()`** method executes a **reducer** function \(that you provide\) on each element of the array, resulting in a single output value.\(new\)

```javascript
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue;

// 1 + 2 + 3 + 4
console.log(array1.reduce(reducer));
// expected output: 10

// 5 + 1 + 2 + 3 + 4
console.log(array1.reduce(reducer, 5));
// expected output: 15

```

The **`reverse()`** method reverses an array [_in place_](https://en.wikipedia.org/wiki/In-place_algorithm). The first array element becomes the last, and the last array element becomes the first.\(modified\)

```javascript
const array1 = ['one', 'two', 'three'];
console.log('array1:', array1);
// expected output: "array1:" Array ["one", "two", "three"]

const reversed = array1.reverse();
console.log('reversed:', reversed);
// expected output: "reversed:" Array ["three", "two", "one"]

/* Careful: reverse is destructive. It also changes
the original array */
console.log('array1:', array1);
// expected output: "array1:" Array ["three", "two", "one"]

```

The **`shift()`** method removes the **first** element from an array and returns that removed element. This method changes the length of the array.\(modified\)

```javascript
const array1 = [1, 2, 3];

const firstElement = array1.shift();

console.log(array1);
// expected output: Array [2, 3]

console.log(firstElement);
// expected output: 1

```

The **`slice()`** method returns a shallow copy of a portion of an array into a new array object selected from `begin` to `end` \(`end` not included\) where `begin` and `end` represent the index of items in that array. The original array will not be modified.（是object的时候只能是shallow\)

```javascript
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(2));
// expected output: Array ["camel", "duck", "elephant"]

console.log(animals.slice(2, 4));
// expected output: Array ["camel", "duck"]

console.log(animals.slice(1, 5));
// expected output: Array ["bison", "camel", "duck", "elephant"]

```

The **`some()`** method tests whether at least one element in the array passes the test implemented by the provided function. It returns a Boolean value. 

```javascript
const array = [1, 2, 3, 4, 5];

// checks whether an element is even
const even = (element) => element % 2 === 0;

console.log(array.some(even));
// expected output: true

```

The **`sort()`** method sorts the elements of an array [_in place_](https://en.wikipedia.org/wiki/In-place_algorithm) and returns the sorted array. The default sort order is ascending, built upon converting the elements into strings, then comparing their sequences of UTF-16 code units values.

The time and space complexity of the sort cannot be guaranteed as it depends on the implementation.

```javascript
const months = ['March', 'Jan', 'Feb', 'Dec'];
months.sort();
console.log(months);
// expected output: Array ["Dec", "Feb", "Jan", "March"]

const array1 = [1, 30, 4, 21, 100000];
array1.sort();
console.log(array1);
// expected output: Array [1, 100000, 21, 30, 4]

```

  
The **`splice()`** method changes the contents of an array by removing or replacing existing elements and/or adding new elements [in place](https://en.wikipedia.org/wiki/In-place_algorithm).

```javascript
const months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 0, 'Feb');
// inserts at index 1
console.log(months);
// expected output: Array ["Jan", "Feb", "March", "April", "June"]

months.splice(4, 1, 'May');
// replaces 1 element at index 4
console.log(months);
// expected output: Array ["Jan", "Feb", "March", "April", "May"]

```

The **`toString()`** method returns a string representing the specified array and its elements.

```javascript
const array1 = [1, 2, 'a', '1a'];

console.log(array1.toString());
// expected output: "1,2,a,1a"

```

The **`unshift()`** method adds one or more elements to the beginning of an array and returns the new length of the array.

```javascript
const array1 = [1, 2, 3];

console.log(array1.unshift(4, 5));
// expected output: 5

console.log(array1);
// expected output: Array [4, 5, 1, 2, 3]

```

The **`values()`** method returns a new **`Array Iterator`** object that contains the values for each index in the array.\(new\)

```javascript
const array1 = ['a', 'b', 'c'];
const iterator = array1.values();

for (const value of iterator) {
  console.log(value);
}

// expected output: "b"
// expected output: "c"


```



## 64.string methods

The [`String`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) object's **`charAt()`** method returns a new string consisting of the single UTF-16 code unit located at the specified offset into the string.\(new\)

```javascript
var sentence = 'The quick brown fox jumps over the lazy dog.';

var index = 4;

console.log('The character at index ' + index + ' is ' + sentence.charAt(index));
// expected output: "The character at index 4 is q"

```

The **`concat()`** method concatenates the string arguments to the calling string and returns a new string.\(new\)

```javascript
var str1 = 'Hello';
var str2 = 'World';

console.log(str1.concat(' ', str2));
// expected output: "Hello World"

console.log(str2.concat(', ', str1));
// expected output: "World, Hello"

```



The **`endsWith()`** method determines whether a string ends with the characters of a specified string, returning `true` or `false` as appropriate.

```javascript
const str1 = 'Cats are the best!';

console.log(str1.endsWith('best', 17));
// expected output: true

const str2 = 'Is this a question';

console.log(str2.endsWith('?'));
// expected output: false

```

The **`includes()`** method determines whether one string may be found within another string, returning `true` or `false` as appropriate.

```javascript
var sentence = 'The quick brown fox jumps over the lazy dog.';

var word = 'fox';

console.log(`The word "${word}" ${sentence.includes(word)? 'is' : 'is not'} in the sentence`);
// expected output: "The word "fox" is in the sentence"

```

The **`indexOf()`** method returns the index within the calling [`String`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) object of the first occurrence of the specified value, starting the search at `fromIndex`. Returns -1 if the value is not found.

```javascript
var paragraph = 'The quick brown fox jumps over the lazy dog. If the dog barked, was it really lazy?';

var searchTerm = 'dog';
var indexOfFirst = paragraph.indexOf(searchTerm);

console.log('The index of the first "' + searchTerm + '" from the beginning is ' + indexOfFirst);
// expected output: "The index of the first "dog" from the beginning is 40"

console.log('The index of the 2nd "' + searchTerm + '" is ' + paragraph.indexOf(searchTerm, (indexOfFirst + 1)));
// expected output: "The index of the 2nd "dog" is 52"

```

The **`lastIndexOf()`** method returns the index within the calling [`String`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) object of the last occurrence of the specified value, searching backwards from `fromIndex`. Returns -1 if the value is not found.

```javascript
var paragraph = 'The quick brown fox jumps over the lazy dog. If the dog barked, was it really lazy?';

var searchTerm = 'dog';

console.log('The index of the first "' + searchTerm + '" from the end is ' + paragraph.lastIndexOf(searchTerm));
// expected output: "The index of the first "dog" from the end is 52"

```

The **`match()`** method retrieves the result of matching a _string_ against a _regular expression_.

```javascript
var paragraph = 'The quick brown fox jumps over the lazy dog. It barked.';
var regex = /[A-Z]/g;
var found = paragraph.match(regex);

console.log(found);
// expected output: Array ["T", "I"]
```

The **`repeat()`** method constructs and returns a new string which contains the specified number of copies of the string on which it was called, concatenated together.

```javascript
var chorus = 'Because I\'m happy. ';

console.log('Chorus lyrics for "Happy": ' + chorus.repeat(27));

// expected output: "Chorus lyrics for "Happy": Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. Because I'm happy. "
```

The **`replace()`** method returns a new string with some or all matches of a `pattern` replaced by a `replacement`. The `pattern` can be a string or a [`RegExp`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp), and the `replacement` can be a string or a function to be called for each match. If `pattern` is a string, only the first occurrence will be replaced.

```javascript

var p = 'The quick brown fox jumps over the lazy dog. If the dog reacted, was it really lazy?';

var regex = /dog/gi;

console.log(p.replace(regex, 'ferret'));
// expected output: "The quick brown fox jumps over the lazy ferret. If the ferret reacted, was it really lazy?"

console.log(p.replace('dog', 'monkey'));
// expected output: "The quick brown fox jumps over the lazy monkey. If the dog reacted, was it really lazy?"

```

The **`search()`** method executes a search for a match between a regular expression and this [`String`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) object.

```javascript
var paragraph = 'The quick brown fox jumps over the lazy dog. If the dog barked, was it really lazy?';

// any character that is not a word character or whitespace
var regex = /[^\w\s]/g;

console.log(paragraph.search(regex));
// expected output: 43

console.log(paragraph[paragraph.search(regex)]);
// expected output: "."

```

The **`slice()`** method extracts a section of a string and returns it as a new string, without modifying the original string.\(new\)

```javascript
var str = 'The quick brown fox jumps over the lazy dog.';

console.log(str.slice(31));
// expected output: "the lazy dog."

console.log(str.slice(4, 19));
// expected output: "quick brown fox"

console.log(str.slice(-4));
// expected output: "dog."

console.log(str.slice(-9, -5));
// expected output: "lazy"

```

The **`split()`** method turns a [`String`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) into an array of strings, by separating the string at each instance of a specified separator string.

```javascript
var str = 'The quick brown fox jumps over the lazy dog.';

var words = str.split(' ');
console.log(words[3]);
// expected output: "fox"

var chars = str.split('');
console.log(chars[8]);
// expected output: "k"

var strCopy = str.split();
console.log(strCopy);
// expected output: Array ["The quick brown fox jumps over the lazy dog."]

```

The **`startsWith()`** method determines whether a string begins with the characters of a specified string, returning `true` or `false` as appropriate.

```javascript
const str1 = 'Saturday night plans';

console.log(str1.startsWith('Sat'));
// expected output: true

console.log(str1.startsWith('Sat', 3));
// expected output: false

```

The **`substring()`** method returns the part of the `string` between the start and end indexes, or to the end of the string.

```javascript
var str = 'Mozilla';

console.log(str.substring(1, 3));
// expected output: "oz"

console.log(str.substring(2));
// expected output: "zilla"


```

The **`toLowerCase()`** method returns the calling string value converted to lower case.

```javascript
var sentence = 'The quick brown fox jumps over the lazy dog.';

console.log(sentence.toLowerCase());
// expected output: "the quick brown fox jumps over the lazy dog."

```

The **`toString()`** method returns a string representing the specified object.

```javascript
var stringObj = new String("foo");

console.log(stringObj);
// expected output: String { "foo" }

console.log(stringObj.toString());
// expected output: "foo"

```

The **`toUpperCase()`** method returns the calling string value converted to uppercase \(the value will be converted to a string if it isn't one\).

```javascript
var sentence = 'The quick brown fox jumps over the lazy dog.';

console.log(sentence.toUpperCase());
// expected output: "THE QUICK BROWN FOX JUMPS OVER THE LAZY DOG."

```

The **`trim()`** method removes whitespace from both ends of a string. Whitespace in this context is all the whitespace characters \(space, tab, no-break space, etc.\) and all the line terminator characters \(LF, CR, etc.\).

```javascript
var greeting = '   Hello world!   ';

console.log(greeting);
// expected output: "   Hello world!   ";

console.log(greeting.trim());
// expected output: "Hello world!";


```

The **`valueOf()`** method returns the primitive value of a [`String`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) object.

```javascript
var stringObj = new String("foo");

console.log(stringObj);
// expected output: String { "foo" }

console.log(stringObj.valueOf());
// expected output: "foo"

```



## 65.object methods

The **`Object.assign()`** method is used to copy the values of all enumerable own properties from one or more source objects to a target object. It will return the target object.\(modified\)

```javascript
const target = { a: 1, b: 2 };
const source = { b: 4, c: 5 };

const returnedTarget = Object.assign(target, source);

console.log(target);
// expected output: Object { a: 1, b: 4, c: 5 }

console.log(returnedTarget);
// expected output: Object { a: 1, b: 4, c: 5 }

```

The **`Object.create()`** method creates a new object, using an existing object as the prototype of the newly created object.\(new\)

```javascript
const person = {
  isHuman: false,
  printIntroduction: function () {
    console.log(`My name is ${this.name}. Am I human? ${this.isHuman}`);
  }
};

const me = Object.create(person);

me.name = "Matthew"; // "name" is a property set on "me", but not on "person"
me.isHuman = true; // inherited properties can be overwritten

me.printIntroduction();
// expected output: "My name is Matthew. Am I human? true"

```

The **`Object.entries()`** method returns an array of a given object's own enumerable string-keyed property `[key, value]` pairs, in the same order as that provided by a [`for...in`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in) loop \(the difference being that a for-in loop enumerates properties in the prototype chain as well\). The order of the array returned by **Object.entries\(\)** does not depend on how an object is defined. If there is a need for certain ordering then the array should be sorted first like `Object.entries(obj).sort((a, b) => b[0].localeCompare(a[0]));`.

```javascript
const object1 = {
  a: 'somestring',
  b: 42
};

for (let [key, value] of Object.entries(object1)) {
  console.log(`${key}: ${value}`);
}

// expected output:
// "a: somestring"
// "b: 42"
// order is not guaranteed

```

  
The **`Object.freeze()`** method **freezes** an object. A frozen object can no longer be changed; freezing an object prevents new properties from being added to it, existing properties from being removed, prevents changing the enumerability, configurability, or writability of existing properties, and prevents the values of existing properties from being changed. In addition, freezing an object also prevents its prototype from being changed. `freeze()` returns the same object that was passed in.

```javascript
const obj = {
  prop: 42
};

Object.freeze(obj);

obj.prop = 33;
// Throws an error in strict mode

console.log(obj.prop);
// expected output: 42

```

The **`Object.fromEntries()`** method transforms a list of key-value pairs into an object.

```javascript
const entries = new Map([
  ['foo', 'bar'],
  ['baz', 42]
]);

const obj = Object.fromEntries(entries);

console.log(obj);
// expected output: Object { foo: "bar", baz: 42 }

```

The **`Object.getPrototypeOf()`** method returns the prototype \(i.e. the value of the internal `[[Prototype]]` property\) of the specified object.

```javascript
const prototype1 = {};
const object1 = Object.create(prototype1);

console.log(Object.getPrototypeOf(object1) === prototype1);
// expected output: true

```

The **`Object.keys()`** method returns an array of a given object's own enumerable property **names**, in the same order as we get with a normal loop.

```javascript
const object1 = {
  a: 'somestring',
  b: 42,
  c: false
};

console.log(Object.keys(object1));
// expected output: Array ["a", "b", "c"]

```

  
The **`hasOwnProperty()`** method returns a boolean indicating whether the object has the specified property as its own property \(as opposed to inheriting it\).

```javascript
const object1 = new Object();
object1.property1 = 42;

console.log(object1.hasOwnProperty('property1'));
// expected output: true

console.log(object1.hasOwnProperty('toString'));
// expected output: false

console.log(object1.hasOwnProperty('hasOwnProperty'));
// expected output: false

```

The **`isPrototypeOf()`** method checks if an object exists in another object's prototype chain.

```javascript
function object1() {}
function object2() {}

object1.prototype = Object.create(object2.prototype);

const object3 = new object1();

console.log(object1.prototype.isPrototypeOf(object3));
// expected output: true

console.log(object2.prototype.isPrototypeOf(object3));
// expected output: true

```

The **`toString()`** method returns a string representing the object.

```javascript
function Dog(name) {
  this.name = name;
}

var dog1 = new Dog('Gabby');

Dog.prototype.toString = function dogToString() {
  return '' + this.name;
}

console.log(dog1.toString());
// expected output: "Gabby"

```

  


The **`valueOf()`** method returns the primitive value of the specified object.

JavaScript calls the `valueOf` method to convert an object to a primitive value. You rarely need to invoke the `valueOf` method yourself; JavaScript automatically invokes it when encountering an object where a primitive value is expected.

```javascript
function MyNumberType(n) {
  this.number = n;
}

MyNumberType.prototype.valueOf = function() {
  return this.number;
};

const object1 = new MyNumberType(4);

console.log(object1 + 3);
// expected output: 7

```

  
  
  
  
  
  
  
  




## 66.implement apply

```javascript
Function.prototype.myApply = function (context) {
  var context = context || window
  context.fn = this;
  var result;
  // 需要判断是否存储第二个参数
  // 如果存在，就将第二个参数展开
  if (arguments[1]) {
    result = context.fn(...arguments[1])
  } else {
    result = context.fn()
  }
  delete context.fn
  return result
}

作者：yck
链接：https://juejin.im/post/5ba34e54e51d450e5162789b
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

## 67.implement bind

对于实现以下几个函数，可以从几个方面思考

* 不传入第一个参数，那么默认为 `window`
* 改变了 this 指向，让新的对象可以执行该函数。那么思路是否可以变成给新的对象添加一个函数，然后在执行完以后删除？

```javascript
Function.prototype.myBind = function (context) {
  if (typeof this !== 'function') {
    throw new TypeError('Error')
  }
  var _this = this // function that calls bind
  var args = [...arguments].slice(1)
  // 返回一个函数
  return function F() {
    // 因为返回了一个函数，我们可以 new F()，所以需要判断
    if (this instanceof F) {
      return new _this(...args, ...arguments)
    }
    return _this.apply(context, args.concat(...arguments))
  }
}

作者：yck
链接：https://juejin.im/post/5ba34e54e51d450e5162789b
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

## 68.implement  call

```javascript
Function.prototype.myCall = function (context) {
  var context = context || window
  // 给 context 添加一个属性
  // getValue.call(a, 'yck', '24') => a.fn = getValue
  context.fn = this
  // 将 context 后面的参数取出来
  var args = [...arguments].slice(1)
  // getValue.call(a, 'yck', '24') => a.fn('yck', '24')
  var result = context.fn(...args)
  // 删除 fn
  delete context.fn
  return result
}

作者：yck
链接：https://juejin.im/post/5ba34e54e51d450e5162789b
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

## 69.Oracal Object Manipulation 

```javascript


var obj2 = [
  {
    "id" : "978-0641723445",
    "cat" : ["ebook","hardcover"],
    "name" : "The Lightning Thief",
    "author" : "Rick Riordan",
    "series_t" : "Percy Jackson and the Olympians",
    "sequence_i" : 1,
    "genre_s" : "fantasy",
    "inStock" : true,
    "price" : 12.50,
    "pages_i" : 384
  }
,
  {
    "id" : "978-1423103349",
    "cat" : ["book","paperback"],
    "name" : "The Sea of Monsters",
    "author" : "Rick Riordan",
    "series_t" : "Percy Jackson and the Olympians",
    "sequence_i" : 2,
    "genre_s" : "fantasy",
    "inStock" : true,
    "price" : 6.49,
    "pages_i" : 304
  }
,
  {
    "id" : "978-1857995879",
    "cat" : ["book","paperback"],
    "name" : "Sophie's World : The Greek Philosophers",
    "author" : "Jostein Gaarder",
    "sequence_i" : 1,
    "genre_s" : "fantasy",
    "inStock" : true,
    "price" : 3.07,
    "pages_i" : 64
  }
,
  {
    "id" : "978-1933988177",
    "cat" : ["ebook","paperback", "hardcover"],
    "name" : "Lucene in Action, Second Edition",
    "author" : "Michael McCandless",
    "sequence_i" : 1,
    "genre_s" : "IT",
    "inStock" : true,
    "price" : 30.50,
    "pages_i" : 475
  }
];

//output:


[ { cat: 'ebook',
    books:
     [ 'The Lightning Thief', 'Lucene in Action, Second Edition' ] },
  { cat: 'hardcover',
    books:
     [ 'The Lightning Thief', 'Lucene in Action, Second Edition' ] },
  { cat: 'book',
    books:
     [ 'The Sea of Monsters',
       'Sophie\'s World : The Greek Philosophers' ] },
  { cat: 'paperback',
    books:
     [ 'The Sea of Monsters',
       'Sophie\'s World : The Greek Philosophers',
       'Lucene in Action, Second Edition' ] } ]





const merge2 = (obj) => {
  let catogories = new Set();
  let result = [];
  let temp =  {};
  for(let i = 0; i < obj.length; i++) {
      for (let j =0; j < obj[i]["cat"].length; j++) {
        catogories.add(obj[i]["cat"][j]);
      }
  }
  catogories = Array.from(catogories);
  for (let i = 0; i < catogories.length; i++) {
    temp["cat"] = catogories[i];
    temp["books"] = [];
    for (let j = 0; j < obj.length; j++) {
      if (obj[j]["cat"].includes(temp["cat"])) {
        if (temp["books"].includes(obj[j]["name"])) {
          continue;
        } else {
          temp["books"].push(obj[j]["name"]);
        }
      }
    }
    result.push(temp);
    temp = {};
  }
  return result;  
  
}

function bookList(obj2) {
  let res = [];
  obj2.forEach(ele => {
    for (let i = 0; i < ele.cat.length; i++) {
      let curIndex = res.findIndex(items => items.cat === ele.cat[i]);
      if (curIndex != -1) {
        res[curIndex].books.push(ele.name);
      } else {
        let newCatagory = {
          cat: ele.cat[i],
          books: [ele.name]
        };
        res.push(newCatagory);
      }
    }
  });
  return res;
}
console.log(JSON.stringify(bookList(obj2)));
```

## 70.classic for loop

```javascript
for (var i = 1; i < 5; i++) {
    setTimeout(() => console.log(i), 1000)  // 5 5 5 5
}
for (let i = 1; i < 5; i++) {
    setTimeout(() => console.log(i), 1000)  // 1 2 3 4
}
```

ith **var** you have a function scope, and only one shared binding for all of your loop iterations - i.e. the i in every setTimeout callback means **the same** variable that **finally** is equal to 6 after the loop iteration ends.

With **let** you have a block scope and when used in the for loop you get a new binding for each iteration - i.e. the i in every setTimeout callback means **a different** variable, each of which has a different value: the first one is 0, the next one is 1 etc.

ps：

A block scope is the area within **if**, **switch** conditions or **for** and **while** loops. Generally speaking, whenever you see **{curly brackets}**,



## 71.implement new

```javascript
function Student(name, age) {
  this.name = name;
  this.age = age;
}

function myNew() {
  const obj = new Object();
  let Constructor = Array.prototype.shift.call(arguments);//get this
  obj.__proto__ = Constructor.prototype;
  let ret = Constructor.apply(obj, arguments);
  return typeof ret === 'object'?ret : obj;
}

let newPerson = myNew(Student, 'hanson', 18);
console.log(newPerson.name);


```

## 72.prototype chain

```javascript
创建对象的几种方法
  // 字面量
  let o1 ={name: "01"};
  let o2= new Object({name: "o2"});
  //通过构造函数 函数才有prototype和__proto__ (__proto__ === Function.prototype)对象则有 __proto__
  let M = function(name){this.name = name;}; //构造函数是函数object的实例
  let o3 = new M("o3");  // M connects to empty object   构造函数的对象是 Function.prototype
 // M.prototype.constructor 是原型对象和函数寄建立连接的方式    
//M.prototype初始化一个空的对象（原型对象） ,这个原型对象是一个空的object, 它是Object （Object.prototype）创造出来的一个原型对象(Object)（非空）的实例. Object.prototype === M.prototype.__proto__

//M.prototype.__proto__ 指向 Object （方法）创造出来的一个原型对象 . 

//M.prototype.__proto__.__proto__ ===Object.prototype.__proto__ 为 null

   //Xxx instanceof M(构造函数)   Xxx instanceof Object //true指向原型对象
   //查找实例属于哪个构造函数的时候用 o3.__proto__.constructor ===X 更为准确
  //创建实例的时候，实例可以引用函数原本的值以及在prototype上新建立的值
  //Object.create
  let p = {name:’p’};//原型对象p 
  let o4 = Object.create(p); //只是连接了原型对象p o4本身是空的null
```

## 73. Implement shallow copy

```javascript
//slice浅拷贝
let arr = [1, 2, {val: 4}];
let newArr = arr.slice();
newArr[2].val = 1000;

console.log(arr);//[ 1, 2, { val: 1000 } ]
//这就是浅拷贝的限制所在了。它只能拷贝一层对象。如果有对象的嵌套，那么浅拷贝将无能为力


//手动实现
const shallowClone = (target) => {
  if (typeof target === 'object' && target !== null) {
    const cloneTarget = Array.isArray(target) ? []: {};
    for (let prop in target) {
      if (target.hasOwnProperty(prop)) {
          cloneTarget[prop] = target[prop];
      }
    }
    return cloneTarget;
  } else {
    return target;
  }
}

//Object.assign
let obj = { name: 'sy', age: 18 };
const obj2 = Object.assign({}, obj, {name: 'sss'});
console.log(obj2);//{ name: 'sss', age: 18 }

//..展开运算符
let arr = [1, 2, 3];
let newArr = [...arr];//跟arr.slice()是一样的效果

```

## 74. implement instanceof

```javascript
function myInstanceof(left, right) {
    //基本数据类型直接返回false
    if(typeof left !== 'object' || left === null) return false;
    //getProtypeOf是Object对象自带的一个方法，能够拿到参数的原型对象
    let proto = Object.getPrototypeOf(left);
    while(true) {
        //查找到尽头，还没找到
        if(proto == null) return false;
        //找到相同的原型对象
        if(proto == right.prototype) return true;
        proto = Object.getPrototypeOf(proto);
    }
}

console.log(myInstanceof("111", String)); //false
console.log(myInstanceof(new String("111"), String));//true
```



## 75.inheritance

```javascript
 function Parent5 () {
    this.name = 'parent5';
    this.play = [1, 2, 3];
  }
  function Child5() {
    Parent5.call(this);
    this.type = 'child5';
  }
  Child5.prototype = Object.create(Parent5.prototype); //这里创建的是Parent5.prototype的实例
  Child5.prototype.constructor = Child5;

作者：神三元
链接：https://juejin.im/post/5dac5d82e51d45249850cd20
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

## 76. implement native functions

```javascript
'use strict';

/*****************NATIVE forEACH*********************/

Array.prototype.myEach = function(callback) {
    for (var i = 0; i < this.length; i++)
        callback(this[i], i, this);
};

//tests
var arr = ['biggy smalls', 'bif tannin', 'boo radley', 'hans gruber'];
arr.myEach(function(word) {
    console.log(word);
});
//biggy smalls
//bif tannin
//boo radley
//hans gruber

/*****************NATIVE MAP*************************/

Array.prototype.myMap = function(callback) {
    arr = [];
    for (var i = 0; i < this.length; i++)
        arr.push(callback(this[i], i, this));
    return arr;
};

//tests
var arrs = ['dic tanin', 'boo radley', 'hans gruber'];
var numbers2 = [1, 4, 9];

var goodT = arrs.myMap(function(n) {
    return n;
});

var squareRoot = numbers2.myMap(function(num) {
    return Math.sqrt(num);
});

console.log(goodT); // [ 'dic tanin', 'boo radley', 'hans gruber' ]
console.log(squareRoot); // [ 1, 2, 3 ]

/*****************NATIVE FILTER*************************/

Array.prototype.myFilter = function(callback, context) {
    arr = [];
    for (var i = 0; i < this.length; i++) {
        if (callback.call(context, this[i], i, this))
            arr.push(this[i]);
    }
    return arr;
};

//tests
var numbers = [1, 20, 30, 80, 2, 9, 3];
var newNum = numbers.myFilter(function(n) {
    return n >= 10;
});
console.log(newNum); // [ 20, 30, 80 ]

/*****************NATIVE REDUCE*************************/


Array.prototype.myReduce = function(callback, initialVal) {
    var accumulator = (initialVal === undefined) ? undefined : initialVal;
    for (var i = 0; i < this.length; i++) {
        if (accumulator !== undefined)
            accumulator = callback.call(undefined, accumulator, this[i], i, this);
        else
            accumulator = this[i];
    }
    return accumulator;
};

//tests
var numbers3 = [20, 20, 2, 3];
var total = numbers3.myReduce(function(a, b) {
    return a + b;
}, 10);
console.log(total); // 55

var flattened = [
    [0, 1],
    [2, 3],
    [4, 5]
].reduce(function(a, b) {
    return a.concat(b);
});
console.log(flattened); //[ 0, 1, 2, 3, 4, 5 ]


/*****************NATIVE EVERY*************************/

Array.prototype.myEvery = function(callback, context) {
    for (var i = 0; i < this.length; i++) {
        if (!callback.call(context, this[i], i, this))
            return false;
    }
    return true;
};

//tests
var passed = [12, 5, 8, 130, 44].myEvery(function(element) {
    return (element >= 10);
});
console.log(passed); // false
passed = [12, 54, 18, 130, 44].myEvery(function(element) {
    return (element >= 10);
});
console.log(passed); // true

passed = [12, 54, 18, 130, 44].myEvery(function(element) {
    return (element >= 13);
});
console.log(passed); // false



/*****************NATIVE SOME*************************/

Array.prototype.mySome = function(callback, context) {
    for (var i = 0; i < this.length; i++) {
        if (callback.call(context, this[i], i, this))
            return true;
    }
    return false;
};

//tests
var passed = [12, 5, 8, 130, 44].mySome(function(element) {
    return (element >= 200);
});
console.log('some: ' + passed); //some: false

var passed = [12, 5, 8, 130, 44].mySome(function(element) {
    return (element >= 100);
});
console.log('some: ' + passed); //some: true
```



