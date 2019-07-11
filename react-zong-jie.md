# React 总结

**1.The pros of React and difference with Angular**

**2.what is hoc and when to use**

**3.react render function**

**4.**reactDomServer

5.**what is state, setState**

**6.life cycle methods**

**7.componentwillmount-》 render-》componentdidmount 还有child component之间怎么传props**

**8.Why react has good performance**

**9. Difference between framework and libraries**

**10.props and state**

**11.end-to-end test tool and unit test tool**

**12.What is advantage of react?**

  
**13.Can react work with angular.js? What’s the problem of doing that?**

**14.What’s render\(\) ?**

  
**15.What is component?**

**16.What is props?  
17.How to handle event in react\(2 kinds?\)?**

**18.what life cycle to do async calls**  
19.**what is ref, give a scenario using ref**

**20.how to communicate between parent and child component?**  
21.**how to change the parent component in child component?**  
22.**forceUpdate? when to use that?**

**23.ask difference between library & framework, when to choose library/framework & why?**  
24.**react play as view, what is mvc structure?**  
25.**what’s virtual dom?how it works?**

**26.pass data between components**   
**27.react 优缺点**

**28.angular优缺点**

**29.What part of the MVC pattern does ReactJS implement?** 

30.**What frameworks have you used in conjunction with ReactJS for routing, AJAX calls, and other Model and Controller functionality that is not provided by ReactJS?**

**31. Explain what a Component is and how it is created.**

**32.which function  would you write when you wanna get data from server?**

**33.what is the data binding advantage for ReactJS and AngularJs**

**34.http request with different method\(put, get, delete,\) and status**

**300?400?500?200?都什么意思 其中server反应时间怎么看呢？多长时间返回数据从后端**  


35.**React, Redux 的关系图是什么样子的，白板给我画一下**

**36.react+redux怎么传data，props怎么往上传，怎么跨页面传东西  
    如果不用redux怎么传    如果还不能用react怎么传  
    react router用法**

**37.如果不用react，怎么储存传进来的一大堆数据 //dom，localStorege**

**38.what is:**

**react.lazy\(\)**

**react state**

**AJAX**

**mapstatetopros**

**mapdispatchtopros**

**redux-saga**

**innerHTML**

**39.what is high-order component? and give an example**

**40.              how to design the high order component**

**41if I have a large json data response, what would you do to store in front end,**

                        **I said I will use offset in url like infinite scroll API**  
42.**what is the react works in FLUX?**

**43.what is the render method for**

**44.what is JSX**

**45.element vs component**

**46.React.createElement\(\)**

**47.write simple function and class component**

**48.state vs props**

**49.how to maintain state for your project**

**50.second parameter in setState\(\)**

**51.how to output array in react**

**52.what test method you use for React**

**53.how to prevent a component from rendering**

**54.how to do auth in React**

**55.explain different data binding methods for React and Angular**

**56. react state vs redux state, when do you use redux**

**57.write a router to route different componet.**

**58.can you explain what’s the meaning of below of code and what’s the ReactDom for?**

**ReactDOM.render\(**

    **&lt;Hello message="Welcome" /&gt;,** 

    **document.getElementById\("root"\)**

**\);**  


59.

**shouldComponentupdate.**

**when to use it.** 

**how to use it.**

**is this function check this state or next state.**

**how to check state changes.**  


60. **how to access dom tree node, when to use Refs**

**61.前端怎么通过URL拿取json数据**

**62. controlled components/ uncontrolled components.**

**63.**

**解释这段**

**class App extends React.Component {**

  **render\(\) {**

 **return\(**

  **&lt;div&gt;**

        **&lt;h1&gt;{'Welcome to ReacT!'}&lt;/h1&gt;**

      **&lt;/div&gt;**

 **\)**

  **}**

**}**

**64.Prevent default**

**65. html element vs react component**

**66.  解释call back function**

**67.virtual dom and real dom**

**68.写arrow function in event handle**

**69. Forward refs**

**70. Error boundaries**

**71.class component vs function component，使用环境**

**72.怎么提升react效率**

**73.为什么要用redux，为什么不用context api**

**74.eject 用过吗**

**npm run eject上面提到，脚手架为了"优雅",隐藏了所有的webpack相关配置文件，如果我们想要基于原来的基础再次增加一些自己的东西，首先就要找到这些隐藏文件并且进行修改。**

**有的开发者直接到node\_modules中去搜索webpack.config...等文件，然后进行修改，修改后发现生效了，但是当修改后，我们又安装了一些其它项目模块，重新编译的时候，又回到了原有的配置信息\(很头疼的问题，总不能每一次安装新模块后，都重新改一次需要修改的配置吧...\)**

**基于create-react-app创建完成项目后，会提供一个eject命令\($ yarn eject\)，基于这个命令，可以把隐藏的webpack文件展示出来，方便我们二次进行配置。**

**$yarn eject或者npm run eject 此命令执行完成不可逆转\(慎重使用\)**

**执行完成后，我们可以看到原有的结构目录发生了一些变化\(新增两个文件夹,package.json中的内容也跟着发生改变\)**  


75.**用哪个版本的react，新版本的新特性有哪些**

**76.Why virtual DOM is faster than real DOM?**

77.**sometime, response json file has empty field. how to do?**  

**hard to handle from front end**  


78.

**问我, 听说你之前用过reusable Component, 能具体说说都是怎么用的吗? 我说用过的reusable Component里面,  button类型的用过的最多, 看她貌似不太满意, 我就又说form我也用过reusable Component, 并解释说reusable Component就类似一个Component的基本框架, 想要用的时候就添加新的feature或者function就行了, 如果想要使用的话, 任何8一个Component都可以是reusable Component, 看她貌似满意, 我就没再继续BB了**

**79.然后问我Component, reducer和actionCreator之前怎么联系在一块的**

**80.**

**解释React Hooks,解释React Context API,解释React Context API 和 Redux的区别，更喜欢哪个**

**81.**

**how many ways to create a react component?**

**follow up: what is the difference between functional component and class component.**

**which one has better performance do you think?**

**what is react hook? give an example （让我在白板上写react hook example代码, 因为上个问题回答答到了hook）**

**82.**

**写个React Component去request一个list, 按她想要的做个mapping，很基本的东西。**

**state改变了，如何阻止render, shouldComponentUpdate\(\) { return false}**  


**83.what is synthetic event?**

**84.如何clean up event handler**

**85.什么引起了react update?**

**86.flux vs react**

**87.if you cannot render correctly, what will you do?**

**I talked about redux state check and the value of the states, Unit test ,and system test.**  


88.**props  vs state can we directly change state**

**89.why we use root in React**

**90.do you know react fibre**

91.**react fragment**

**92.tree shaking of react**

**93.do you know something new about react like react pwa?**

**94. authorization besides JWT**

**95.what is the difference between react and mvc**

**96.how to prevent re-render**

**97.react native vs react**

**98. what is container layer  in the redux? Container layer?**

**99. flux flow vs redux**

**100.What is the purpose of render function?**

101.**What method will trigger in re-render page**

**Component should update**  


102.**what is curry**

**103.Event driven model**

**104.Difference between reactjs and jquery**

**105. Pure function,**   


106.**how to persist your data\(大概意思是说如何不让信息暴露给所有人**

**107.What will happen if you do this.setState in render function**

**108.proptypes this is used validate the props that is fetched from the parent**

          **proptypes is a package**

  
109.**React router**

**110. arguments of createStore\(\) ? \(reducer, \[preloadedState\], \[enhancer\]\)**

**111.同时有2个Async calls，你怎么handle？一个接一个，or同时？**

**112.How a button works from user Click to updates rendering on the page?**

**113.Write an easy helloWorld Component \(using codesandbox\)**

  
  


\*\*\*\*

  
  


  


  


\*\*\*\*

  


\*\*\*\*

\*\*\*\*

  




