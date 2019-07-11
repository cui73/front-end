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

**console.log\(100/”apple”\)**

**console.log\(true === “appke”\)**

**35.**

 **alert prompt javascript**

**Can you change the Alert? Answer is no, chrome default.**  


![](https://lh5.googleusercontent.com/xFdOPJ5zSqlSDnYAFaPfzcbglblofubINPJsfZlCfvjom-O_h-_CkjUsqx_E8WF9pTnsBCBxWja7sLOesHC4JmBIbfxn4lAMBLlEyqt90mlWEXMDCrid8Dhdz4NYzXlr51nLjQFi)



**36. store is not duplicate**

 **output is one string:**

![](https://lh3.googleusercontent.com/DwJZVDHc_IvE6hfCYWJQmX8YnGBpsBdR3vToYTFSEY6tp_Nq0G7AsTOdE0q9zvzD5FD31dh9_yVGpuYSJ4Ed8j2_D-Zmto-yQOHk9do0SLaDpW2i-tkWQ3wsJRwhGLgOrM2mJGWC)

**37.**

**常见的for loop问题**

**for \(var i =  0; i &lt; 5; i++\) {**

 **setTimeout\(........\)**

**}**

**问打印的i是啥，怎么拿closure改成0,1,2,3,4**  


**console.log\(0.1 + 0.2\);**

**console.log\(0.1 + 0.2 == 0.3\);**

**console.log\(0.1 + 0.2 === 0.3\);**

**打印结果是什么**  


**38.**

**写个function sum**

**支持两种call**

**sum\(2, 3\); //5**

**sum\(2\)\(3\); //5**

**用arguments不用arguments**  


**let sum = \(a, b\) =&gt; {**

 **if \(b === undefined\) {**

 **return \(c\) =&gt; a + c;**

**}**

**return a + b;**

**}**  


**let sum = function\(\) {**

**if \(arguments.length === 2\) {**

**return arguments\[0\] + arguments\[1\];**

   **}**

**let cur = arguments\[0\];**

**return function\(c\) {**

   **return cur + c;**

**}**

**}**  


**39.coding: find number of character in string. ex : input = ‘java’ -&gt; return j - 1, a-2, v-1;**

**40.**

```text
(function(){
  var a = b = 3;
	
})();

console.log("a defined? " + (typeof a !== 'undefined'));
console.log("b defined? " + (typeof b !== 'undefined'));

```

  
**41.**

```text
19.
var y = 1;
  if (function f(){}) {
    y += typeof f;
  }
  console.log(y);

```

**42.reverse “the sky is blue” to “blue is sky the”**

**43.How to check an object is an array or not? Array.isArray\(\).**

**44.write fnLimiter, to limit the callback numbers.**

**write a function fnLimiter\(limit, callback\){**

**}**

**that call back can only run “limit” times. after this return false;**

  




![](https://lh6.googleusercontent.com/he5KspvDTXMdNkDyxHJUys7X0eF9sOtV_G-2c79iSw4d1wk3hFMF1sVs0Gg5RdPCly0hRCWMqiQEhF1Y-ISgIPgeesrGbAk4IoNKpfggWoc-nO9j3t1FbiJ1AP17YAtHlu-psbq6)



![](https://lh3.googleusercontent.com/vGQPwDQwvAPySASRhei9YL2xwN5WGrMF4gqIk-Qc_VRtKGyHmNtiQR3mpw31dUg_mE2qkSC8Uc7fKOQ2v_zkFHsEbStPUUKhFNwzNG4U5mx1zqxC0qgy1-wQYu3nbroLQ9Zt9mGZ)

**45.下面getData加括号getData\(\);**

**interviewer给的答案：**

**function getData\(\) {**

        **return "Success";**

**}**

 **getData\(\).then\(\(res\) =&gt; {**

        **document.querySelector\(".result"\).textContent = res;**

 **}\);**  


46.**4. fetch\(“url”\).then\(\(\)=&gt;{“success”}\).catch\(\(\)=&gt;{error}\)**

**输出error** 

**url和server都好 问为什么**

**答 cors 问题**

**如何解决**  


47.

**async function getData\(\) {**

        **return "Success";**

      **}**

      **document.querySelector\(".result"\).textContent = getData;**  
  


**answer:**

**function getData\(\) {**

        **return "Success";**

**}**

 **getData\(\).then\(\(res\) =&gt; {**

        **document.querySelector\(".result"\).textContent = res;**

      **}\);**  


48.

**algo:** 

**add\(1\)\(2\) = 3**

**add\(1\)\(2\)\(3\) = 6**

**我觉得这个题少了括号应该是**

**add\(1\)\(2\)\(\) = 3**

**但是如果后面要无限个括号参数并且没有这个空括号的话就完全不同**  


49.

**let a = { b: { c: 'd' } }**  


**let interview = \(obj, path, defaultValue\) =&gt; {**

    **let paths = path.split\("."\);**

    **let currentResult = obj;**

    **for \(name in paths\) {**

      **currentResult = currentResult\[name\] ? currentResult\[name\] : defaultValue;** 

    **}**

    **return currentResult;**

**}**  


**//interview\(a, 'b.c', 'defaultValue'\)**

**//interview\(a, 'c', 'defaultValue'\)**

**//interview\(a, 'b', 'defaultValue'\)**

**console.log\(interview\(a, 'b.c', 'defaultValue'\)\)**

**console.log\(interview\(a, 'c', 'defaultValue'\)\)**

**console.log\(interview\(a, 'b', 'defaultValue'\)\)**  


50.

**Stu1: \[48, 47, 46\]**

**Stu2: \[44, 50, 49\]**

**find topper student who have most higher scores**

**\[5, 8, -3, 1, -7\]**

**find all subsets who has the sum of 0**

**51.**

![](https://lh6.googleusercontent.com/VVkWI6ugqc-5S0AtFD4pesmDw3ZnkHQUjkAXKaVXWPUmbvRtk87TVN4kvxg9CPZJdKAsIsvHStUuVHdi98TjEKfQnYB4UyE3f1cm5yUlnq_UrLVYhq0g3WG__fqqKBkrT35eKll0)

**52.return lowest positive two numbers sum in an array**

**53.**

```text
flatten an array, two way 
var arr1 = [[10,[18,45,79]],20,[30,33],40];
[10,18,45,79,20,30,33,40]

const flatten = arr => {
  return arr.reduce((acc, cur) => {}
    return !Array.isArray(cur) ? [...acc, cur] : [...acc, ...flatten(cur)];
  }, []);



use clouse to implement a limit time function
function abc(name) {
  console.log(name);
}

function fnLimiter(limit, callback) {
  return function (arg){
    if(limit > 0){
      callback(arg);
      limit--;
    }
  }
}

const fn = fnLimiter(3, abc);
fn("1")    1
fn("2")    2
fn("3")    3
fn(“4”)      return nothing

different between these two functions
function foo1()
{
  return {
      bar: "hello"
  };
}

function foo2()
{
  return
  {
      bar: "hello"
  };
}



how to init a state in react
constructor(props)[
  super(props);
  this.state = {};
]

let state = {};
how to change state
this.setState({
  
})
differrent between null and undefined
what is type of null and undefined
what is pure component, where to update pure component
explain about react lifecycle, talk about some example
talk about redux, 

```

54.

**Return keys of the object**

**Use reduce to merge 3 objects：use spread&rest**

**Write a class es5/es6 : use \`${ }\` for output**

**How to add ele in the end of arr**

**How to delete the first ele in an arr**

**55.for \(var i = 0; i &lt; 10; i++\) {**

 **setTimeout\(\(\) =&gt; arr\[i\] = i, 0\);**

**}**

**就这种之类的，问你arr\[6\]是多少。**

**怎么改成arr\[6\] = 6;**

**用let或者closure。**  


56.

**基本二分查找。**

**给一个string array，长度不一。**

**\[aaa, vvv, ccc, 4dsvv, dvsdv, sk3, 32fv\]**

**返回所有最长string。**  
  
**57.Coding: write custom reduce function that have same functionality as system defined reduce function**

**58..Given an array of string and a checking string, return an array which element contains checking string.**

 **Ex \[‘abc’, ‘Abd’, ‘bc’, ‘jabdf’\], ‘ab’ =&gt; \[‘abc’, ‘Abd’, ‘jabdf’\]**  


59.**.\[{name: “a”,**

     **editable: true**

    **},**

    **{name: “b”,**

     **editable: true**

    **},**

    **{name: “c”,**

     **editable: false**

    **}**

   **\]**

   **Return an array of object that editable is true.**  


60.

**function a\(\){**

    **console.log\(a\);**

    **console.log\(test\(\)\);**  


    **var a = 1;**

    **function test\(\){**

        **return 2;**

    **}**

**}**  


**var car = "Honda";**  


**var garage = {**

    **car: "BMW",**

    **getCar : function\(\) {**

        **return this.car;**

    **}**

**}**

**// var myCar = garage.getCar.bind\(garage\);**

**var myCar = garage.getCar;**  


**console.log\(myCar\(\)\); // undefind**

**// =&gt; correct:  var myCar = garage.getCar.bind\(garage\);**

**console.log\(myCar\); // print function \(\) {...}**  


**3. Flatten array**

**4. log\(‘test’, ‘is’, ‘happy’\) =&gt; “test is happy”**  


61.

 **find largest number in array**

**Var arr = \[10, 1, 17, 5, 7, 6, 12, 3, 11\]**

 **Var arr = \[10, 1, 17, 5, 7, 6, 12, 3, 11\]**

**Filter element bigger than 10**

**62.Give a string and a integer k. Find the minimal substring that need to remove, so that the remain string has exactly k uniquick char.**

**Example:** 

**S=”abaacbca”, k=2, then return 3.  Reason: remove “cbc”, string will only contain “a” and “b”.**

**S=”aabcabc”, k=1, then return 5. Reson: remove “bcabc”, string will only contain “a”.**  


63.

```text
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

64.**Given an array and chunk size, divide the array into many subarrays where each subarray is of length size**

**// --- Examples**

**// chunk\(\[1, 2, 3, 4\], 2\) --&gt; \[\[ 1, 2\], \[3, 4\]\]**

**// chunk\(\[1, 2, 3, 4, 5\], 2\) --&gt; \[\[ 1, 2\], \[3, 4\], \[5\]\]  用array.slice做的**  


65.

```text
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

  
66.  


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

67.

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

68.

1. **Given an array of numbers with no duplicates, find all pairs of the sum equal to the target**

**follow up: Given an array with duplicates**

      **3.  Replace a string with substring ‘abc’ with ‘xxx’.**

**eg. input “cdabcdefabcd” =&gt; output: “cdxxxdefxxxd”**  


69.

1. **Given a array of 0 and 1, move all 0s at the front and 1s at the end**

**follow up: do it with only one loop**  


70.

```text
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

71.**输入: an  array of strings and a word, 从每个string里取一个字母，最后拼出这个单词find all combinations** 

**72.字符转换**

**ab-cd-ef 变成 abCdEf**

```text
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

**Subsets**  


```text
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



