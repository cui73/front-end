# How To CSS

## make element in the center both position

2 div, outer, inner

1. use position transform

![](../../.gitbook/assets/image%20%281%29.png)

                                            

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LgnugJ0SdX2tMAwP37V%2F-Lhh2DSijjAEVArSq9_1%2F-Lhh2LoZnQ7A1jfs54LM%2Fimage.png?alt=media&token=9782bb7e-3b6e-407c-8983-bbcb3e3f9d69)

## Make multiply divs in a line.

3.  methods

left

flex



## Hoverable Dropdown

Move the mouse over the button to open the dropdown menu.

Dropdown  Link 1 Link 2 Link 3

.dropdown-content a:hover {background-color: \#ddd;}

.dropdown:hover .dropdown-content {display: block;}

.dropdown:hover .dropbtn {background-color: \#3e8e41;}



## **Write CSS so that link &lt;a href="http://www.testdome.com"&gt;Check documentation&lt;/a&gt; and cursor looks like:**

![](https://lh6.googleusercontent.com/4oiIqyYZV5c4e6XwI93DA7buDaECfVhSicUUmbuRxq-3Ic9rVLk9h3DisHRfp-ltlz1MeY02O87VDOoSDj-4Y3Gw2c6OgtIyj-D9MFWQbPRPFtP4rp2gmQh7xxV3_qcjINe5SoXe)

```text
a {
  text-transform: uppercase;
  text-decoration: none;
  cursor: help;
}

a::before {
  content: ">";
}

a::after {
  content: "<";
}

```

\*\*\*\*

## **写一个animation，slide， fade in, 并用flexbox最普遍方法平分页面？**

## **写两个点赞 “大拇指上👆” “大拇指向下”两个按钮 要求 可以键盘左边键为点赞，右边键为不点赞**

## **在一个container 里面有很多个container 每个container有扩大 或者 关闭两个功能，如何在最里面的container关闭 所有container都关闭， 如何在最外面container扩大时 所有 container都展开应有的大小**

## **button class &lt;div class="button"&gt;Next Page&lt;/div&gt; 和 &lt;button &gt;Next page&lt;/button&gt;有区别吗？那个更好修改**

## **一个div里面 一个按钮 一句话 怎么样按下按钮 这句话改变style**

## **given 3 &lt;div&gt;s, the height of those are different based on the inner content, how can you make the height of them same by CSS?**

## **how to use flexbox to do 2\*2 grid**

## **how to make reusable UI component in CSS**

##  **How to use function change the the style of css \(document.getElementById\(id\).style.property = new style\) 或者jquery**

##  **如何用css使一个element水平垂直居中，这个一定要会，前端大概率会问**

**两种做法， 一是用position和transform， 二是用flex box，我回答了第一种**

[**https://codepen.io/YoungShaw/pen/eaoWpq**](https://codepen.io/YoungShaw/pen/eaoWpq)  ****

[**https://codepen.io/YoungShaw/pen/GaLmqy**](https://codepen.io/YoungShaw/pen/GaLmqy)

  


## 给你三个框框, 比例是1:2:1 如何做?

我就说了下我的答案, 他就问我这三个框框你是打算用div吗？ 还是别的什么？ 请把详细的所有步骤都说出来, 他要求的很细, 我干脆把代码给他写了 第二题 让一个1400px的div水平垂直居中, 同Xiao Yang的面经:

## **如何用CSS写click一个button之后让旁边的div背景颜色改变，用什么pseudo selector体如何实现**

## **how to center an element?**

