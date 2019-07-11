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
  


14.

**given an api,  show data \(solution by Ian\)** 

  **class Homepage extends React.Component {**

  **constructor\(props\){**

  **super\(props\);**

 **this.state = {**  

   **user : {}**

 **}**

  **}**

  **componentDidMount\(\) {**

            **axios.get\("https://api.github.com/users/octocat"\)**

  **.then\(res =&gt; {**

            **this.setState\({**

       **user : res.data**

 **}\)**

  **}**

  **\)**

            **}**

            **render\(\) {**

            **const user = this.state.user;**

            **return &lt;div&gt;**

 **&lt;UserInfo**

       **login={user.login}**

       **company={user.company}**

        **location={user.location}**

        **email={user.email}**

        **blog={user.blog}**

     **avatar\_url={user.avatar\_url}**

 **/&gt;**

 **&lt;NaviBar**

       **repositories={user.public\_repos}**

      **project={user.project}**

      **follower={user.followers}**

      **following={user.following}**

 **/&gt;**

 **&lt;/div&gt;**

  **}**

**}**

**const NaviBar = props =&gt; {**

                           **return &lt;div&gt;**

            **&lt;ul&gt;**

    **&lt;li&gt;overview&lt;/li&gt;**

      **&lt;li&gt;repositories{props.repositories}&lt;/li&gt;**

       **&lt;li&gt;project{props.project}&lt;/li&gt;**          

      **&lt;li&gt;stars{props.stars}&lt;/li&gt;**

       **&lt;li&gt;follower{props.follower}&lt;/li&gt;**

        **&lt;li&gt;following{props.following}&lt;/li&gt;**

 **&lt;/ul&gt;**

  **&lt;/div&gt;**

**}**

**const UserInfo = props =&gt; {**

            **return &lt;div className="container"&gt;**

            **&lt;img src={props.avatar\_url}&gt;&lt;/img&gt;**

            **&lt;ul&gt;**

       **&lt;li&gt;{props.login}&lt;/li&gt;**  

      **&lt;li&gt;{props.company}&lt;/li&gt;**

       **&lt;li&gt;{props.email}&lt;/li&gt;**

      **&lt;li&gt;{props.location}&lt;/li&gt;**

 **&lt;/ul&gt;**

  **&lt;/div&gt;**

**}**  
  


**const root = document.querySelector\("\#root"\);**

**ReactDOM.render\(&lt;Homepage /&gt;, root\);**

**15.写一个react class component，实现click一个button之后显示一个popup的窗口。**

**16.写一个react class component，实现点击最上面的CheckBox，下面的所有的都改成checked或者如果下面4个checkbox都是checked的状态就uncheck。然后当下面4个都checked时候，最上面的checkbox也变成checked。**

**17.**

```text
互相介绍完就直接打开链接
题目:console.log(getUsersFromTag("MongoDB"));
output is [1,2]
console.log(getUsersFromTag("MySQL"));
output is [1]

Data:
const users = [
 {
   id: 1,
   name: "A",
   email: "A@gmail.com",
   tags: ["MySQL", "MongoDB", "Java", "Python"]
 },
 {
   id: 2,
   name: "B",
   email: "B@gmail.com",
   tags: ["，，，", "MongoDB", "Java", "C++"]
 }
 // …. 1000 more use
rs
];

console.log(getUsersFromTag("MongoDB"));


const getUsersFromTag = tag => {
 return users.reduce((acc, cur) => {
   if (cur.tags.includes(tag)) {
     acc.push(cur["id"]);
   }
   return acc;
 }, []);
};


follow up 1 : 如果search好多次，怎么办
用cache存起来，用一个map， key存tag, val 存数组
一开始
var map = new Map();
 const getUsersFromTag = tag => {
 if (map.has(tag)) {
   return map.get(tag);
 }
 const res =  users.reduce((acc, cur) => {
   if (cur.tags.includes(tag)) {
     acc.push(cur["id"]);
   }
   return acc;
 }, []);
 return res;
};
后来他说还能优化么，就是一开始就loop，然后把每个tag存在map里面
var map = new Map();
const help = users => {
 for (let i = 0; i < users.length; i++) {
   for (let j = 0; j < users[i].length; j++) {
     if (!map.has(users[i].tags[j])) {
       map.set(users[i].tags[j], []);
     }
     map.get(users[i].tags[j]).push(users[i].id);
   }
 }
};
help();
const getUsersFromTag = tag => {
 return map.get(tag);
};
follow up 2:
如果这样
console.log(getUsersFromTag("MongoDB", “email”));
console.log(getUsersFromTag("MySQL", “name”));
代码：

var map = new Map();
const help = users => 
 for (let i = 0; i < users.length; i++) {
   for (let j = 0; j < users[i].length; j++) {
     if (!map.has(users[i].tags[j])) {
       map.set(users[i].tags[j], []);
     }
     map.get(users[i].tags[j]).push(users[i]);
   }
 }
};
help();
const getUsersFromTag = (tag, property) => {
 return map.get(tag).map(ele => ele[property]);
};



```

  
**18.**

```text
18. parent component and child component and show the child’s list in the parent component(use callback)
https://stackoverflow.com/questions/35537229/how-to-update-parents-state-in-react


	//ChildB component
	class ChildB extends React.Component {

		render() {
			
			var	handleToUpdate	=	this.props.handleToUpdate;
			return (<div><button onClick={() => handleToUpdate('someVar')}>Push me</button></div>
			)
		}
	}

	//ParentA component
	class ParentA extends React.Component {	
	    constructor(props) {
			super(props);
		}

		handleToUpdate = (someArg) => {
				alert('We pass argument from Child to Parent: ' + someArg);
		}

		render() {
			return (<div>
				<ChildB handleToUpdate = {this.handleToUpdate} /></div>)
		}
	}

	if(document.querySelector("#demo")){
		ReactDOM.render(
			<ParentA />,
			document.querySelector("#demo")
		);
	}


```

19.

```text
what is this means 
class User extends React.Component {
static propTypes = {
name: PropTypes.string.isRequired,
age: PropTypes.number.isRequired
}

render() {
return (
<>
<h1>{`Welcome, ${this.props.name}`}</h1>
<h2>{`Age, ${this.props.age}`}</h2>
</>
)
}
}

```

20.**Given a react component which shows userlist, write a search bar**   


21.**写一个component，完成点击button 然后div里面的内容消失\(javascript 和react render 两种方法document.getElementById\("demo"\).style.display = "none";\)**

**22.write a todolist**

**23.refactoring your code in the online assessment: menu  \(with redux\)**

**24.**

 **toggle design**

**click on the button and change the color of button**

**toggle design 2**

**click on the button and the color of the label in another component changed**

**25.**

**第三轮 manager面：**

**让写一个component各种table都能重复使用，每个table要显示的不一样**

**比如第一个的table 是**

**ID， Name\(firstName secondName\),  Email, Address**

**第二个的table是**

**Name,  ID, courses, num**

**有好几种这样的table，如何实现，类似写一个接口的东西感觉**

**我的想法是用把object作为props传入children componet里面。这个objext里面是个map，有key 和 value， key是table header的attribute， value是inital data里面的attribute，这样就可以找到了**

**面试官给的解法key是table header的attribute， value是一个getvalue的fuction，然后每次调用就可以用相应的function，时间不是很多。。。**  


**26.**

**做一个购物卡片。**

**第一栏图片，第二栏描述，第三栏价格，第四栏，加入购物车 button。**

**用css调成需要的样子，需要自适应屏幕，还是用float left。**

**再写一个购物车功能，点击对应button，就会把那个项目加入购物车。**

**已经存在就 + 1.**  


**给mock data，让你做map，很简单。**

**购物车实现可以在state里面写个类，每次点了对应按钮就往对应的property里面塞。**

**然后对类做mapping**

**Object.keys\(this.state.myCart\).map\(\(a, index\) =&gt; {**

 **&lt;xxx&gt;{this.state.myCart\[a\]}&lt;xxx&gt;**

 **/\* do something with your key value pair \*/**

**}\)**  


**做完以后，面试官很纠结我的style，让我继续改css，把文字全部改成responsive对齐的。。**

**说可以在网上查着写。**

**最后没搞定。多练习css。**  


**27.**

**Coding: 3 data, customer\(firstname last name, ssn, balance \), loans\(ssn, balance\) , bank\(ssn, account\), design the action part and reducer part.**

**28.Give you api and build a** [**website**](https://anatesan-stream.github.io/angularJS-restaurant-menu-app/module4_solution/#!/categories/items/SP)**. \(1 hr\) with react redux**  


29.

**然后对这个function 写各种test case**

**给你一个用react写的网页， 如何测试这个网页的performance**  


30.

**backend api design with todolist**

**让你写出API 的 get put post delete 怎么设计 post 的body 怎么写 JSON 怎么设计**

**他在白板上写会不断添加细节。你根据细节写出API CALL**

**工作流程 用什么 TOOL meeting 的内容 怎么知道产品的requirement 是和PM 交流的嘛**

**application 代码怎么分工合作的 怎么测试 问的比较细节**  
  


