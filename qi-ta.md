# 其他

1.**how do you do your version control/share code within team**

  
2.**what is sql injection**

**3.oop questions such as difference between interface vs abstract class**

**4.how do you do your version control/share code within team**

  
5.**current project & role**

**6.How do you make your website load faster?**

**7.unit test**

8.**开始聊下我们的project，** 

**\(1\)写一个 我们上课employee project的action里面部分函数**

**\(2\) 如何实现 页面跳转 routes怎么写 exact里面怎么安排url顺序**

**\(3\) 讲下 parent componet vs same component 为什么选择same componet 时候往往选择重写parent componet**

**9.how to do project management**  


10.**how to build web services.**

**11.what packages you used in you project**

**12.**

\*\*\*\*[**https://stackoverflow.com/questions/43532755/jquery-interview-online-15-minutes-testdome**](https://stackoverflow.com/questions/43532755/jquery-interview-online-15-minutes-testdome)

**Jquery:**

**The createProductCodeForm function is used to create a new form that accepts a product code from a user. The current version of the form contains the hint: ‘The product code can be found on the label’. The hint is currently always visible to the user. Improve the form so that the hint is only rendered when the input element is the focused element.**

**13.过去半年最大挑战**

**14.. UX/UI design**

   **Given  four servers loacted in different cities, let’s say Newark, Portland, Philadephia, LA**

   **and there are multipal port of each server, and multipal url for each port.**

   **Design UX/UI to check all servers status, if they are good or down...how to design to show     the detail of the info...**  


15.**how you use webpack**  


16.**jquery and how you use it**  


17.**平时怎么工作的/scrum\(do you know scrum? how it works?**  
**\)**

**18.Jasmine grunt-jasmine**

**19. package.json file**

**20.explain how to use Enzyme**

**21.explain how shallow function work in enzyme**

**22.**

**a. png vs svg**

**b. in what situation you prefer png/svg, explain why**

**23.advantages of single page application**

**24.What’s the bundling in Angular**

**25.how to use npm**

**26.怎样用browser debug,  怎样用browser设置component的断点**

**27.Project Macanition Detail //产品逻辑，运行机制**

**28.解释ECMA Script**

**29.Agile 里面 waterfall model, 怎么接受require, 怎么提交进度**

**30.mroservice and how to use.**

**31.how to reduce the project's weight? \(size?\)**

**32.**

\*\*\*\*

1. **解释web的架构， 在白板上画diagram, 主要是前端，后端，数据库相互交流的结构。在你画图的基础上面试官会问你问题。**
2. **谈到了google oauth的结构，并在白板上画diagram。**

**33.how to reduce the project's weight? not webpack, Lazy-loading, other method**

**34. Write Async in Jquery   $.ajax; Async in React  axios.get; handle nested async call;**

35.**问了when you input url in browser and click enter, what will happen，这个题google一下，有非常详细的解释，看的时候记一下有哪些步骤并且每一步做了些啥，按着这个回答就行**

**36.Enzyme做testing**

37.**MySQL 的简单用法**  

**38.what is mongoose and why you use mongoose?**

**39.how to use search bar and find info from mongodb?\( I said “find\(\)”\)**

**40. Introduce one project which makes you proud**

**41.do you have experience of git and github**

**42.问你上一个项目的工作流程workflow**

**我固定了一个可行的答案，最近问到都这么说，基本没有interviewer质疑。**

**首先你是一个developer，写完一个feature后你上传代码到github，或许你在github上有自己的branch，那就上传到这个branch，这中间你可以有自己的测试，用jest或者jest + enzyme都可以，但是这只是你自己的测试**

**然后组里有另一个engineer会负责CI/CD，他会用jenkins或者类似的软件把你的代码从github上pull到jenkins，并结合测试工程师的代码在jenkins中build, deploy and test，也就是实际的测试**

**如果在jenkins中运行的代码有问题， jenkins会上报bug到jira这个软件，所以你或者manager就能看到这些bug，通常jira会发送邮件报告给具体的developer这个bug，这时候你就需要更新代码，消除bug，或许你需要和测试工程师一起合作解决问题**

**如果jenkins中的代码测试后没有问题， 你的代码也许会在github上merge到master branch， 这时候你就可以开始下一项工作了**

**所以github, jenkins 和 jira 是一同工作的， 它们一起形成了完整的流程。github做VC\(version control\)，jenkins负责CI/CD，jira通常用来追踪整个项目的进度以及报告bug**  


43.**为什么你喜欢用javascript, 我回答它很便捷，说到了array 可以当 stack, queue, arraylist等等**

**44.SQL 和 NoSQL database的区别，performance哪个好**

**45. if we start a new project, what is the best practice do you think that you should keep in mind**

**46.what open source library do you use?**

**47.what is dependency injection, give an example**

**48.if you were looking back, which mistake you would do differently?**

**49.**

**tell me why did you choose MongoDB over MySQL**

**follow up: generally NoSQL vs SQL database**

**tell me more about consistency\(因为上一题提到了consistency\)**

**tell me more about replica \(因为上一题提到了replica\)**

**50.CI/CD**

**51. how to reduce loading time of the webpage**

**52.what’s the minification and amplification of images?**

**53.How to load the images efficiently?**

**54.lazy loading**

**55.transcompiler**

**56.webpack**

**57.mongoose的优点**

**58.What is database cluster**

**59. mongodb能存进excel文件吗？能存进txt文件吗？**

**60.白板画自己的project的database schema**

**61.讲上个project怎么设计的，数据怎么传的，就画下MVVM 和flux Architecture**

**62.sql和nosql区别，然后写sql的什么操作**

63.**SASS， LESS写CSS**

**64.Did you write Unit test? How?**

  
65**.What is jest , shallow and mount difference**

**66.How to guarantee your code is right before you push to github**

**67.**

**Give a situation: Autocomplete feature in a website, will return an autocomplete advice each time user enter something, but this will get too much request, how do you solve the situation.**

**My answer: request every time user enter 3 characters**

**Follow up: setTimeOut\(\), setInterval\(\), Debouncing, Throttling**  


**68.**

**How to improve your website performance :** 

**Clean up HTML Document / Reduce External HTTP request / Minify CSS, JS and HTML / Increase Speed With a CDN and Caching / Compress Your File / Optimize Images**  


**69.What’s the most challenge work or problem you have met? Did you solve that?**

**70.MongoDB vs mysql**  


**71.第一个面试官，是一个白人的软件工程师，一开始问我简历上的东西，问的非常仔细。**

**他其中有问了我一个node js是否可以实现multi-thread的问题，我跟他说node js是以single thread为基础实现的，于是他告诉了我一个plugin，我不记得名字了，但是确实有许多可以在nodejs的框架之上套入一个manage plugin， 下面有一些参考资料**

[**https://stackoverflow.com/questions/40028377/is-it-possible-to-achieve-multithreading-in-nodejs**](https://stackoverflow.com/questions/40028377/is-it-possible-to-achieve-multithreading-in-nodejs)

[**https://stackoverflow.com/questions/18613023/how-to-create-threads-in-nodejs**](https://stackoverflow.com/questions/18613023/how-to-create-threads-in-nodejs)

[**https://stackoverflow.com/questions/2387724/node-js-on-multi-core-machines**](https://stackoverflow.com/questions/2387724/node-js-on-multi-core-machines)

[**https://github.com/audreyt/node-webworker-threads**](https://github.com/audreyt/node-webworker-threads)  
****

**最后他问了我LCS算法** 

[**https://www.geeksforgeeks.org/longest-common-subsequence-dp-4/**](https://www.geeksforgeeks.org/longest-common-subsequence-dp-4/)  




72.**你在之前的公司用GitHub吗？怎么用的？从头到尾给我讲讲。**  


  
73.**Node, Express:**

**1. 现场会写router！！！**

**2. 会写middleware, 了解next middleware**

**3. error handling in Express**

**Testing: Jest，Enzyme,现场会写一段unit test**

**unit test, integration test**

**Project related:**

**1. search \(additional: search 太频繁问题和怎样解决\), sort, pagination, infinite scrolling怎么实现**

**2.authentication（JWT）**

**3.validationTools and methodology: Webpack, Babel, Grunt, Gulp, Git, scrum\(sprint, standup, user story, backlog grooming, point\), project tracking tool\(e.g. JIRA\)**

**74.**

![](https://lh6.googleusercontent.com/Srl-qrtVbma0VpmliWFgD_3kY6j86poKV7BgRC5CGcfa-VvBJ_iW-Naw3bAnuxkJJVMA1-dzSvbHJxCodG5Slh_7gMKpHXgGPAaCqEog6cYozVciAU4QMEUAUHkdEaPnRFEIeD02)

**给你一个搜索界面，让你用JavaScript写一个能够测试这个界面所有功能的脚本。Automation text 就是模拟用户使用界面，来找出可能出现的错误。这个界面包含inputbox，checkbox，switch button， dropbox，**

**search button，用户填完信息，点击search button以后下面会显示符合条件的结果。**  


  
75.**开发流程scrum**

**76.hm大哥，team lead，identity team**

**介绍组，login/验证功能  
Email，pwd前端验证过了为什么后端还要验证  
Email，pwd前端验证的functions，多个conditions，每个不符合的conditions都要提示，重点不是regex**

**//hm提示要用array存不valid的各种情况，把valid的删掉即可**

**测试工具End to end testing  
webpack， package.json， package.json.lock是啥**

**77.设计一个 amazon shopping cart 的 东西 写出所有database 的表 和details 和所有表的关系 primary key forg key  在白板上**

\*\*\*\*

\*\*\*\*

  
  


