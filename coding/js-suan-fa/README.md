# JS算法

 **leetcode coinchange**

  **leetcode pascals triangle**

**English number to normal number and explain it**

**Binary tree level order traversal**

  
**Given a sorted array, find the target's first and last index**

**eg. \[1, 2, 2, 3, 3, 4, 4, 5, 6, 7\] target = 2**

**return \[1, 2\]**

**follow up: no while \(left + 1 &lt; right\) template**



**3. Given a string with char a, b, c**

**ab ba =&gt; c**

**ac ca =&gt; b**

**bc cb =&gt; a**

**return the final string after replacement**

**eg. str = "ccabc" =&gt; "cbbc" =&gt; "abc" =&gt; "cc"**  


**Given two BST. How to merge it into one balanced BST?**

**what about one BST is much smaller than the other?**  


**level order of tree to traverse in js code.**



[**https://leetcode.com/problems/delete-node-in-a-linked-list/**](https://leetcode.com/problems/delete-node-in-a-linked-list/)\*\*\*\*

**find 2 top occurances of a string when the string is too long**  


![](https://lh3.googleusercontent.com/kBAtLGIcW1F3KYdaLS-iP4CYZOjcSx6aYg1fMxxd4171WTRyMMrhof__hg7KHvesOy651CRh5hMAZW3q88vvV8UYJPM86jVY-xsxb532ruPFPO2lYWALaQQySbNui0fdP4nDytZU)

![](https://lh5.googleusercontent.com/lWMFOlyDs7n9GTGbASRXzipss2xpOxpSe6EULtnpLMi_tfgn3ySEKWI0is4oaAGk8Dh4LGBbR5re0kghWftPI4nRQnMl6-GX6SXJXCDaP6Ffsxbbxqvo7KF-g2ltfFn5lRARRDb1)

**一个人初始有1chip去赌博,两种方式 1.一次赌1个chip  2.一次all in所有的钱**

**写一个函数f\(N,K\)**

**N 代表最后从赌场赢的钱 ,K代表最多 可以all in  K 次。返回 赢N块钱所用的最少次数。**  


**.leetcode 287. Find the Duplicate Number  
  array不是默认sort的，先随便写一个，然后会有下面三个follow up，主要是我写不出来他放宽了条件，一步步引导你  
  如果时间复杂度要linear，可以用更多空间  
  如果时间复杂度要linear，constant space  
  如果时间复杂度要linear，constant space，还要保留原本array**



**Tree traverse**

**\(a\) Inorder \(Left, Root, Right\)** 

**\(b\) Preorder \(Root, Left, Right\)**

**\(c\) Postorder \(Left, Right, Root\)**  


![](https://lh4.googleusercontent.com/4sME8zAJWclcA9C4hNhEDkdDYwIYQ4y98jRmgo1zvhCJ5i_pDju0AH3mfl-kgs-QuC47AdTOeHaoDx0I3NGbPgEBmK81D9BAtJskDEofy_ZVBNcEx_bbh6n_DvGfZ5H3RqeQzzBN)





![](https://lh3.googleusercontent.com/z-gU-9yEIJwel9_Ioyuc6dacYqe1_gh0M4NdXeGI_87gmNYeW6pIqvtsCKuCjWJdX0MfVcN7efmLjSn7WIXi74jzvrJlQ9DEkKWp3HvxPkrsmfap6spN5qPoYp5HgR45X3K7Uv1e)

**quick sort（mid）**

**sort singlely linked list （merge，mid，快慢指针）**

 **valid palindrom leetcode 680, follow up delete at most 2 character**

**write a function to return a list that contains the characters and the frequency of the characters**

**2sum, 3sum,4sum**



**1 like  101 \#1.**

    **give a matrix with some 0 and 1. find the max area of connected 1.** 

  **solution. for loop find matrix of value 1. then do dfs to calculate the area. return the max area.**  


 **ZigZag Conversion:** [**https://leetcode.com/problems/zigzag-conversion/**](https://leetcode.com/problems/zigzag-conversion/)  


\*\*\*\*

**given a dependency object like this:**

 **input = {**

 **A : \[B,C\],**

 **B:  \[C, D\],**

 **C:  \[E\],**

 **E:  \[F\]**

**}**

**means A needs dependencies B, C  before install A.**

**\(A,B,C...here is module\)**

**write a function, take input above and return a installing order sequence:**

**F,E,C,D,B,A**   


 **This question is similar to Leetcode Course Schedule.** 

 **I give a topological sort solution first, and the interviewer asked me to write down every step and every detail about this solution on the whiteboard.** 

 **然后面试官让给一个更快的方法,   我说这题最优解就是拓扑排序, 她说要我想一想real-life denpendency tree, 然后把她的这个例子画出来。 画出来后这个例子就是一棵树, 也就是所有的denpendency有一个统一的root, 我说这个例子的话, 其实可以直接用post-order traverse就可以了, 她说这就是她想要的, 我写完代码后她表示满意。\(但我后来想了想她这个例子是不成立的, 因为一旦由多个root就相当于依然是一个graph, 我没和她争论, 就按照他的意思写完了。 \)**  
  
  


![](https://lh5.googleusercontent.com/55_OJxIhooQ3sEL-mrUdwGpAtEE8BNWlysu3wh46PekYaqGz6vUgmzbVdq6ld7iOYY7HXpW_WB17j9OBKpGigcl96caJHP10V64pK1dM0B-zrBqfPHaDNPniVdTABfIyuffytVZJ)

\*\*\*\*

**Coding: Leetcode House Robber I**

**isValidBST**

**Leetcode 805**

**coding: check prime number**

**coding: best time to buy and sell stock**

**Leetcode 20 valid parentheses**

**Leetcode 32 longest valid parentheses** 

**java算法 用O\(n\) time， O\(1\) space 去输出所有的重复元素的index: 在未排序，有正有负，且有多个重复元素的情况下譬如 \[2,1,1,2,3,-3,5,7\]**

**我觉得条件太苛刻了 我能写出四种方法：set，sort, 双指针追逐，数组记录下标，但是做不到这么时间空间的严格。。。**  


**写一段代码打印斐波那契数列 0 到 13。**

**leetcode 560**  
**palindrome check**

\*\*\*\*

**一个无序的array， 找到其中最大的subarray和**

**1，2，-4，2，5，-1，3**

**最大和是9**



**无序两数组取出重复数字**

\*\*\*\*

**做题， flight ticket 简单版，直接在他电脑上做题，做完啥都没说直接走人，我也不知道我做的对不对**

**const ticket = {**

 **{start: SJC, end: LAX},**

 **{start: LAX, end: SEA},**

 **{start: SEA, end: JFK}**

**}**

**要求return a valid order of city names, time complexity in O\(1\)**

**思路： save all cities in a map to count the appearence, and start city in startSet, end city in endSet, also save a map to keep a map relationship by the key in terms of start city and the value of end city.**  


**leetcode数独那道题**

\*\*\*\*

 **给一个string\[\] list, 和一个string,根据string的每一个char去排序这个list**

**example：**

**input :String s = “word”**

**String \[\] list = \[“wait”, “rain”, “dead”. “oh” \]** 

**output: list = \[“wait”, “oh”, “rain”, “dead”\];**  


**复杂的case有：1.给的string 里面有重复的char 2. string list 里面的string 可能有多个char 符合string s, 要根据哪个定位？**

```text

Solution by Ian:
const alienSort = (str, arr) => {
 const map = {};
 for(let i = 0; i < str.length; i++) {
   //corner case 1: if duplicate, skip it (or throw error)
   if(map[str[i]) continue;
   map[str[i]] = i;
 }
 arr.sort((a,b) => {
   const min = a.length < b.length ? a.length : b.length;
   for(let i = 0; i < min; i++){
     if(a[i] !== b[i]) return map[a[i]] - map[b[i]];
     else continue;
   }
   return 0;
 })
 return arr;
}

```

  




![](https://lh4.googleusercontent.com/bz2HxBcWqVosYAZMBCWkWXWjbP-7Yy9_TpNNUQglINy4D-SUdpuZbu7sKP271IbT0N64BSN4ek9wryKudQU5kU0qYkkyjrQ4PjyNbEmm25-4piFHn02yQxNndqFUpuWUNIRr0VZO)

  
  
**leetcode 654**

**simple concept question,**[**Tribonacci Numbers - GeeksforGeeks**](https://www.geeksforgeeks.org/tribonacci-numbers/) **, do it in O\(1 space\), O\(n\).**  


**System design 惊呆看到system design**

**We have a tinyURL, like in twitter, design a server to handle user use this url.**

**Like twitter, we have** [**https://t.co/**](https://t.co/) **, can redirect to real url.**

**We only have function encode\(\), no decode\(\), design from server, database, what’s the data flow.** 

**co**

**She wants to use database to do this.**  
**Can not use decode function. only has encode function. design by detail.**

**I think need a unique domine.**

**Check** [**https://help.twitter.com/en/using-twitter/how-to-tweet-a-link**](https://help.twitter.com/en/using-twitter/how-to-tweet-a-link)**.Answer:** [**https://www.youtube.com/watch?v=JQDHz72OA3c**](https://www.youtube.com/watch?v=JQDHz72OA3c)



**leetcode 1094**

**算法，输出出现次数是基数的数，一个arr = \[9,2,3,9,8,8,8,6,5\]，return\[2,3,8,6,5\], 要求一个loop不能用map**

**当时我用的mark取负数的方法，但是没法handle出现3次，4次，比较僵硬，感觉位运算，用^好像也不行 ,不是很确定**  


 **java coding: aaabbbccccaa= &gt; a3b3c4a2**

\*\*\*\*

 **java coding: reverse string .  ‘ I love apple’ = &gt; ‘apple love I ’**

**coding: str =  ‘11122333444’ , each number appear 3 times , only one appear twice , find that number,  improve performance ,\(hashmap, one for loop, binary search\)**

\*\*\*\*

**give an input =  3\[b2\[ca\]\], should return output = bcacabcacabcaca**

**test , explain code, time complexity.**  


**1 find common element in two sorted array,** 

**Follow up :** 

**1.  o\(n\) time complexity, O\(1\) space ,no hashmap**

**2. If num1 is too small , is there any optimization or other method**  


**2.min stack O\(1\) time complexity**  






1. **given array \[4, 5, 5, 2, 6\] indicate a piece of chocolate, each element represent the sweetness\(1 - 10\) of chocolate, you want to share the chocolate with two other friends\(divide array into three subarrays\), you want to make sure that your two friends get sweetest\(你得到的是这三个subarray中sum最小的\), how to divide the array so that you can get sweetest among all those division ways\(在所有的solution中你又拿到最大的\)**

**4 \| 5 \| 5  2 6 -&gt; 4**

**4 \| 5  5 \| 2 6   -&gt; 4**

**4 \| 5  5 2 \| 6   -&gt; 4**

**4  5 \| 5 \| 2  6 -&gt; 5**

**4  5 \| 5  2 \| 6 -&gt;  6**

**4  5 5 \| 2 \| 6   -&gt; 2 answer: 6**

**有点懵，刚开始我说用brute force找所有permutations然后遍历更新global，小哥说能不能优化，我表示想不出来，他就又给我了一个function，function isSweetest\(array, n\)返回boolean是否n &gt;= resulting sweet\(好像是这样脑子转不动了\)，说可以调用这个，我说可以for loop从10到1遍历更新global，又问我时间复杂度，O\(n\)\(sweet level 1- n\), 能不能优化到O\(lgn\)，我说用二分，然后写了一下二分😮，感觉完全跑偏。。最后他说其实就看一下遇到题目解决问题的能力，不要求你做出来。总之还是挺轻松的，小哥一直也在帮着做，除了介绍project全程米有问和前端相关的**



**Find minimum depth of a binary tree, time complexity**  


[**https://www.geeksforgeeks.org/split-array-two-equal-sum-subarrays/**](https://www.geeksforgeeks.org/split-array-two-equal-sum-subarrays/)  


1. **Split array into 2 equal sub array Time: O\(n \* n\)**
2. **再用O\(n\)的方法**

\*\*\*\*

**Find the longest contiguous ascending subarray.**

**Ex: \[2,4,1,3,6,7,8,5,9\] -&gt; \[1,3,6,7,8\]**



**在一个二维数组里， 输入一个坐标，从这个坐标开始，从外向内进行螺旋线打印，横坐标优先，长度每次减一，直到你不能再继续**

```text
const sp = (matrix, x, y) => {
 let res = [];
 if (x > matrix[0].length || x < 0 || y > matrix.length || y < 0) return res;
 let cur = x;
 while (cur < matrix[0].length) {
   res.push(matrix[y][cur++]);
 }
 let startcol = 0;
 let endcol = matrix[0].length - 1;
 let startrow = y + 1;
 let endrow = matrix.length - 1;
 while (startcol <= endcol && startrow <= endrow) {
   for (let i = startrow; i <= endrow; i++) {
     res.push(matrix[i][endcol]);
   }
   endcol--;
   for (let i = endcol; i >= startcol; i--) {
     res.push(matrix[endrow][i]);
   }
   endrow--;
   for (let i = endrow; i >= startrow; i--) {
     res.push(matrix[i][startcol]);
   }
   startcol++;
   for (let i = startcol; i <= endcol; i++) {
     res.push(matrix[startrow][i]);
   }
   startrow++;
 }
 return res;
};

```

**leetcode139**

**leetcode 647. Palindromic Substrings**  


  


