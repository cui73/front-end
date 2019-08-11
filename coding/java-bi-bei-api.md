# JAVA 必备API

## priorityQueue的建立：

PriorityQueue&lt;int\[\]&gt; pq = new PriorityQueue&lt;int\[\]&gt;\(\(p1, p2\) -&gt; p2\[0\] \* p2\[0\] + p2\[1\] \* p2\[1\] - p1\[0\] \* p1\[0\] - p1\[1\] \* p1\[1\]\);

## 遍历二维数组：

```java
int[][] points;
for (int[] p : points) {
  pq.offer(p);
  if (pq.size() > K) { //priorityqueue的大小
    pq.poll();
  }
}
```

## 建立一个二维数组 和 赋值:

```java
int[][] res = new int[K][2];

while (K > 0) {
  res[--K] = pq.poll(); // 如把[2,3]放入一个生成好的二维数组
}

```

## 修改java Comparator API

对象a 和对象b 比较时， 如果返回 -1 则表示对象a 在对象b的前面

对象a 和对象b 比较时， 如果返回 0  则按照input进来的顺序排列

对象a 和对象b 比较时， 如果返回 1  则表示对象a 在对象b的后面

```java
Comparator<String> myComp = new Comparator<String>() {
  @Override
  public int compare(String s1, String s2) {
   return 0 , 1 ,-1;
  }
 };
Arrays.sort(logs, myComp); // 使用

```

## split and isDigit and  charAt 的用法

```java
String[] split2 = s2.split(" ", 2);//以空格分两段 第二个parameter 代表limits
boolean isDigit2 = Character.isDigit(split2[1].charAt(0));
```

## 判断Array是否为空 和 Array创建

```java
 if (nums == null || nums.length < 2) {
        return  new int[2];
      } //永远先判断空再判断长度
 
 int[] res = new int[2]; //建立长度为2的空数组
 return new int[] { map.get(complement), i }; //另外一种数组建立的方式
```

## Map相关操作

```java
HashMap<Integer, Integer> map = new HashMap<>();
map.put(nums[i], i);
if (map.containsKey(target - nums[i])) {
          res[0] = map.get(target - nums[i]);
          res[1] = i;
          break;
} 
```



## BFS 相关variables建立

```java
  
        boolean[][] visited = new boolean[m][n];
        Queue<int[]> queue = new LinkedList<>();
        queue.offer(new int[]{i, j});

```

