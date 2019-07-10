# JS特殊

1.**Use Array.reduce to calculate the sum of array**

**2.Use Array.filter to remove the duplicate element in array**

**3.const items = \[**

##   **{ id: 1, type: ‘retail’, cost: 1 },**

##   **{ id: 2, type: ‘retail’, cost: 2 },**

##   **{ id: 3, type: ‘retail’, cost: 5 },**

##   **{ id: 4, type: ‘retail’, cost: 10 },**

##   **{ id: 5, type: ‘inventory’, cost: 1 },**

##   **{ id: 6, type: ‘inventory’, cost: 2 },**

##   **{ id: 7, type: ‘inventory’, cost: 5 },**

##   **{ id: 8, type: ‘inventory’, cost: 10 },**

## **\];**

**return cost &lt; 5 array**

**return cost  5 && type === ‘retail’ array**  


4.**1. Implement the ensure function so that it throws an error if called without arguments or the argument is undefined. Otherwise it should return the given value.**  
**function ensure\(value\) {**

  **if \(value === undefined\) {**

    **throw new Error\(\);**

  **}**

  **return value;**

**}**  


5.**Write a function that converts user entered date formatted as M/D/YYYY to a format required by an API \(YYYYMMDD\). The parameter "userDate" and the return values are strings.**

**For example, it should convert user entered date "12/31/2014" to "20141231" suitable for the API.**  
**function formatDate\(userDate\) {**

  **// format from M/D/YYYY to YYYYMMDD**

  **const words = userDate.split\(“/“\);**

  **const year = words\[2\];**

  **let month = words\[0\];**

  **month = month.length &gt;= 2 ? month : “0” + month;**

  **let day = words\[1\];**

  **day = day.length &gt;=2 ? day : “0” + day;**

  **return year + month + day;**

**}**  


**console.log\(formatDate\("12/31/2014"\)\);**  


6. **Implement the removeProperty function which takes an object and property name, and does the following:If the object obj has a property prop, the function removes the property from the object and returns true; in all other cases it returns false.**

```text
function removeProperty(obj, prop) {
   if(obj.hasOwnProperty(prop)) {
       delete obj[prop];
       return true;
   }
   return false;
}

```



**7. hackrank\(1 个小时\) :**

**no more introduction, let’s write code!**

**Write a function like this** 

**input:** 

**obj \[**

**{k:”a”,v:2},**

**{k:”b”,v:3},**

**{k:”c”,v:7}**

**\]**

**output:** 

**out = \[{a:4},{b:6},{c:14}\]**

**在输入函数的时候 一定要检查 k的值 有个testcase是他当场写的，k有重复的值**

**当出现了重复值 变成直接加法**

**obj \[**

**{k:”a”,v:2},**

**{k:”b”,v:3},**

**{k:”c”,v:7},**

**{k:”c”,v:5}**

**\]**

**output:** 

**out = \[{a:4},{b:6},{c:19}\]**

**follow up 是用array.reduce 写完这个函数 不可以用for loop**

| **var multi\_reduce = \(arr\) =&gt; {     return arr.reduce\(\(res, element\) =&gt; {         var index = res.findIndex\(item =&gt; item\[element.k\]\);         if\(index &gt; 0\) {             res\[index\]\[element.k\] += element.v;         }         else{             let obj = {};             obj\[element.k\] = element.v \* 2;             res.push\(obj\);         }         return res;     }, \[\]\); }  var input = \[{k:"a",v:2},{k:"b",v:3},{k:"c",v:7}, {k:"c",v:5}\]; console.log\(multi\_reduce\(input\)\);** |
| :--- |


**第二题：**

**jest question：**

**const hello= function\(name\){  
 return “hello, this is ${ this.name} ”**

**}**  


**const Person = function\(name\){**

    **this.name = name;**  


**}**

**var t = New Person\(“Chris”\)**

**is t.\(hello\(\) work ? how to fix that?**

**expect t.hello\(.....\). toBe\(“hello, this is Chris”\)**

**写下这个bind function， apply function， 或者call function 都行, 要求检测两个函数的最后输出**

**并且在jest里面describe 一下那个 expect \(function a.b\)toBe\(“.....”\)**

**8.Flatten an array, give \[1,2,3,\[4,5\],\[6,\[7,8,\[9,10\]\]\],  whiteboard**

```text
/*let arr1 = [1,2,3,[4,5],[6,[7,8,[9,10]]]];
function flatten1(arr) {
  while(arr.some(ele => Array.isArray(ele))) {
      arr = [].concat(...arr);
  }
  return arr;
}
console.log(flatten1(arr1));*/

```

**9.filter the duplicate number**

**10. obj1 =\[**

**{name:”chris”, age:26},**

**{name:”peter”, age:21},**

**{name:”Tom”}**

**\]**

**obj2 =\[**

**{name:”chris”, company:”SIS”},**

**{name:”peter”, company:”Apple”},**

**{name:”Tom”, company:”walmart”}**

**\]**

**生成：obj3=\[{**

**{name:”chris”, company:”SIS”,age:26},**

**{name:”peter”, company:”Apple”,age:21},**

**{name:”Tom”, company:”walmart”}**

**}\]**

**11.**

[![](https://lh3.googleusercontent.com/OQpIFyhn6nR4MT6HhDXIN8Mv6R3krgicN-V54HAPL1Ca8jvkBhgnwSfqi88Ne5XvgWGcmwKPiXBBRECvt-vkBvcMMRb79zvKP6PI_ju5CQSf1IpaCLSETR0sGa7TMcbSnjdL3wAD)](https://www.testdome.com/questions/javascript/image-gallery/18215?questionIds=14188,18215,17429,13919&generatorId=16&type=fromtest&testDifficulty=Easy)

12.

```text
这个组做的是Nodejs 后端， 四道js题目， 我把题目和代码写上了
// var obj
//1:返回 object的所有key值
// // recevie object
// const process = function(obj){
//     let key= Object.keys(obj)
//     return key;
// }


// const process = function(obj){
//     let res= [];
//     for(let item in obj){
//         res.push(item)
//     }
//     return res;
// }



// var array = [1,2,3,4,5]
// const process = function(array){
//     let sum = 1;
//     for(let i=0;i<array.length;i++){
//         sum= sum*array[i]*array[i]
//     }
//     return sum
// }


//2: 返回array的乘积
// array.reduce( (sum,cur)=>{
//    return sum*cur*cur;
// },1)


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

13.

**algorithm question:**

  **a.reverse linkedlist**

  **b.swap a,b  without temp**

**14. give 2 strings like**

  **String s1 = “abefccdaebef”**

  **String s2 = “ef”**

  **return first index postion of s2 in s1**

 **output \[2,10\];  //fist index of first “ef” is at position 2 of s1, first index of second “ef” is at   position 10 of s1.**

**Follow up: How to do it in O\(n\)**  


15.

**a.query string: input an object, {name: ‘michael’, company: ‘walmart’}     return “?name=michael&company=walmart”**

**b. Click a button, do deduplication**

            **&lt;ul&gt;**

 **&lt;li&gt;Cats&lt;/li&gt;**

 **&lt;li&gt;Dogs&lt;/li&gt;**

 **&lt;li&gt;Cats&lt;/li&gt;**

 **&lt;/ul&gt;**

 **&lt;button&gt;Click&lt;/button&gt;**

**c. Stopwatch**



**16.**

**algorithm design: 实现类似String.indexOf的功能, 输入string和subString, 输出第一个subString的位置, 我用了两个for循环的brutal force的, 她说时间复杂度高, 并且给我提示说可以用双指针\(但是我感觉并不会work\), 但是她并没让我具体写**

**17.\(function\(x\) { delete x; return x; }\)\(0\); 的结果**

**18.**

**ƒcoding test: find the first index of substring in one string**

**example:**

**string: abcd substring: ab result: 0**

**string: abcd substring: c result: -1**

**\(I completed by O\(n^2\), then the interviewer asked me how to improve the time complexity by O\(n\)\)**  


19.**write a Javascript function that take two arrays as arguments, output an object, {add: includes value in a but not in b, delete: includes value in b but not in a}**

**20.**

 **a. filter duplicate number \(Set, filter\)**

  **b .filter negative number**

**21.**

**var x = 21;** 

**var girl = function \(\) {** 

**console.log\(x\);** 

**var x = 20;** 

**}; girl\(\);**

**output what and why**

  
22.

**write a clone**

**let arr = {test:\[{name:"123", id:"456"}\]};**

**first I write a deep clone**

**function clone\(arr\) {**

 **if\(arr === null\) return arr;**

    **const copy = arr.constructor\(\);**

    **for\(let a in arr\) {**

     **if\(arr.hasOwnProperty\(a\)\) copy\[at\] = arr\[at\];**

    **}**

 **return copy;**

**}**

**then ask me use JSON** 

**then I use** 

**var arr = JSON.parse\(JSON.stringify\(arr\)\);**  


**23.**

**coding: give you arr=\[1,2,3,4\]**

**by using arr.reduce\(\)**

**get \[2,3,4,5\]**  


24.

**Interviewer: WalmartLab Manager - Sandeep Mandada**

**只有一个问题: type-ahead dropdown autocomplete:** 

**在text input里逐个输入letter过程中弹出datalist, 以显示前5个从REST API得到的包含text input内容的选项, 询问了我的思路,** 

**我回答: 前端axios make XMLHtmlRequest, 后端REST API接收后用Regex\(现在想想我回答错了, 应该是直接在mongoosel的Model.find里面写一个函数返回前5个满足条件的document\)**

**然后就开始用React写前端App.js的代码, 写了个能实现基本功能的Component之后, 他问我每输入一个字母都要send一次XMLHttpRequest吗? 我说当然不, 肯定要用debounce. 我说debounce的代码太复杂了, 可以用现成的module吗, 他说ok, 然后我就往里面加debounce, 还剩一行代码没加完的时候他就说ok ok我满意了**

**中间有一些小插曲, Webex的网页是需要刷新的, 不然JoinMeeting的button一直是Disable的, 一开始不知情的我就这样望着网页傻等了快10分钟, 直到Vendor给我打电话问我咋还不进去开会, 就这样耽误了10分钟,  之后面试官给我发了个JsFiddle链接, 准备看我写代码, 试了一下不好使, 然后就问我Share Screen, 结果网页版Webex不能Share Scree, 我下载Desktop版下了半天没下完, 我想凉凉都看不到我写代码不可能有下一轮了, 我就马上找了一个Shared Online Code Editor, 弄了个链接发给他, 才算能写上代码**  


25.

1. **coding: give you arr=\[1,2,3,4\]**

**by using arr.reduce\(\)**

**get \[2,3,4,5\]**

**use other methods, for loop, for each, map**

  
26.实现**memoize**

```text
const add = (...input) => (input.reduce((res,num) => res + num, 0));
const memoized = (callback) => {
    let cache = {};
    return (...parameter) => {
        if(parameter in cache) {console.log("cached"); return cache[parameter];}
        else {
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

  
27.

```text
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

28.



1. **add\(1\)\(2\)\(3\) = 6**

**add\(1\)\(2\) = 3**

**add\(1\) = 1**

**write one function to show the result**  


29.

**converse input to output**  


**const input = \[{**

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


```text

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

30.

**coding question，输入是一个string, 相当于一个文章的段落，统计所有词出现的频率，在console中打印结果，要求去掉所有的标点符号，类似于comma, full stop and dash，这些要去掉。**

**所以首先我们可以用str.replace\(/\[^a-zA-Z \]/g, “”\) 来去掉所有的标点，注意regex里面最后要包含空格在内，然后用split\(“ ”\)方法得到单词，然后用map统计频率，不难**  


31.**问用不用promise，写一个简单的promise**

**类似于new Promise\(\(resolve, reject\) =&gt; resolve\(“hi”\)\)**  


32.**有一个ul，里面的每个li是这样的结构：&lt;li&gt;&lt;a&gt;some number&lt;/a&gt;&lt;/li&gt; 每个a tag 包含的数字不同，请问如何用javascript 在console里打印出所有这些数字**

[**https://codepen.io/YoungShaw/pen/QRPveW**](https://codepen.io/YoungShaw/pen/QRPveW)  


33.

 **coding question: 给两个数组，要求输出两个数组， 但是数组中的数字要randomize**

**例如input是两个数组\[1, 2, 3\], \[4, 5, 6\]，**

**output可能是\[2, 5, 4\] \[6 1 3\]**

**我们可以首先concat这两个数组，然后开始randomize**  


**for \(let i = temp.length - 1; i &gt;= 0; i--\) {**

    **let j = Math.floor\(Math.random\(\) \* \(i + 1\)\);**

    **\[temp\[i\], temp\[j\]\] = \[temp\[j\], temp\[i\]\];**

**}**

**核心就是这一小段，然后可以根据长度slice\(\)出两个数组**  


34.

