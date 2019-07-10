# React实现



**1.写一个component 实现从后端读取employee  info 设计json data 动态生成navigation bar \[{“id”:”1”,”name”:”tom”}, {“id”:”2”,”name”:”Jack”}\]**

**navigation bar就是home menu 常见的那种**

**我的理解是他们想做前端数据分离 后端读来的json data 你需要自己设计 ，就是proj里面常见的那种 比如**  


| **{** |  |  |
| :--- | :--- | :--- |
|  | **"Employees" : \[** |  |
|  | **{** |  |
|  | **"userId":"rirani",** |  |
|  | **"jobTitleName":"Developer",** |  |
|  | **"firstName":"Romin",** |  |
|  | **"lastName":"Irani",** |  |
|  | **"preferredFullName":"Romin Irani",** |  |
|  | **"employeeCode":"E1",** |  |
|  | **"region":"CA",** |  |
|  | **"phoneNumber":"408-1234567",** |  |
|  | **"emailAddress":"romin.k.irani@gmail.com"** |  |
|  | **{** |  |
|  |  | **"userId":"thanks",** |
|  |  | **"jobTitleName":"Program Directory",** |
|  |  | **"firstName":"Tom",** |
|  |  | **"lastName":"Hanks",** |
|  |  | **"preferredFullName":"Tom Hanks",** |
|  |  | **"employeeCode":"E3",** |
|  |  | **"region":"CA",** |
|  |  | **"phoneNumber":"408-2222222",** |
|  |  | **"emailAddress":"tomhanks@gmail.com"** |
|  |  | **}** |
|  |  | **\]** |

2.[**https://anatesan-stream.github.io/angularJS-restaurant-menu-app/module4\_solution/\#!/categories/items/NL**](https://anatesan-stream.github.io/angularJS-restaurant-menu-app/module4_solution/#!/categories/items/NL) **写一个简单的react app，两个components，类似于menu -- detail**  


3.**React component**

**写一个点赞button 点一下赞数+1,样式改变，再点一下变成原样**

4.**用react写component  lists of comments with like button**

**5.**

**purchase-summary**

**来自第五期的**  
  


**Millie:** [**https://codesandbox.io/s/llm5w9qp8z**](https://codesandbox.io/s/llm5w9qp8z)

**Sean:** [**https://codesandbox.io/s/0qqwjkryq0**](https://codesandbox.io/s/0qqwjkryq0)**Owen:** [**https://codesandbox.io/embed/nwyq1ropmm**](https://codesandbox.io/embed/nwyq1ropmm)



**6.一道react题，见本期100那里Yang的面经里那道react题，一样的先用react写加减器，然后用localStorage**

**7.由于a我知道面经，写的可能太快了？然后面试官觉得时间太多了，又让我写了一道react题。。。让我写一个button，原本是绿的，点了以后变成蓝色的**

8.

![](https://lh5.googleusercontent.com/5u0_FXHXA2h1x-YFOl769t2ISoOSCSWIX11sbNAvpIrUCd5R7Fa50vuoqVb0NkT0wdykYzABhb_SAC47Gx5IHSvy79La3JBbHQEVX6RzznvwsdLzdF5iLV36sZ2URlg_H8z5q8Gy)**如图所示，把1中的左边的list改成input**

1. **做一个pagination给他看。。**
2. **做个responsive design**

**如图所示，两个dropdown list，左边是美国的州，右边的是州里的城市，必须先选state，cities那个list会自动根据左边的state进行改变**

1. ![](https://lh6.googleusercontent.com/GUkCliggix4biLSR7dBbgxQIsukvyzpkMRjrCrxwyH2b9q-5seqhxGwgdgRKpZLIf_z1_pn8GY7LEBuNiY18-KVbI-h677CLU9mhKONQUSFpAVWc4yPZAFB42V0AVUnXvZnPmmjL)

**onsite这天结束了以后，第二天突然又联系我要加面，一个三小时先用react完成四道题：**

\*\*\*\*

**9.简单的React设计, 一个div里面上面text input, 下面button, 点击button则console.login出text input里的内容**

**10.write a react component:**

**//Ability to choose a gender M/F**

**//Per the gender you will query for first 10 names from an api**

**//and then you can choose from the 10 names or type a few characters for some other name that might not be in the 10...but in the database**  


**11.**

1. **react: 以亚麻为例，你搜索物品以后下面会有若干推荐 你怎么设计这个推荐panel？**

**超级抽象的说法，我就说我只设计一个component作为模板 里面有价格啊什么的**

**他说在jquery中会XXX用Ajax blabala，但是react devide and conqure 很多小compoennt 可以分开test**

**我说我整个页面是大component下面很多小component 大小component用state 和 props沟通**

1. **你下面有个recommendation panel 里面若干component 上面有个like按钮，你点一下那个like按钮，整个recommendation panel 会刷新 你怎么设计这个动作**

**我说点一下以后 clickhandler 会记录这个like的物品 我们用axios 给后端put一个 url 或者httpbody 里面包含你like的信息， 后端会记住你like的物品并存在后端的liked list里面。后端算法根据你的liked信息重新计算出recommendation 物品并且传给前端的推荐物品components 刷新这些componennts的state**  


12.

 **写一个简单的react component，有一个输入框和一个按钮，点击按钮console里打印出输入框的内容，直接用class component定义state保存input的内容， 然后点击按钮console.log\(\)就可以**

**13.**

**写react，有一个ul，里面有三个li, 每个li都有content, 但是要求初始content是隐藏的，点击其中任何一个li, 这个li的content就在下方显示出来，其他两个li就要collpase**

**我用react写了一段，但是发现要在render\(\) jsx template里选择li似乎有些问题，可能要用ref**  
  


  


