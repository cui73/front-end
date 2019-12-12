# Oracle

## 1.Reorganize Array

```java
// arranging 
1. Count each number appearance and store it into a map with key as number, appearances as value.
2. Build a priorityqueue and sort those number with descending order. The format with this going to be an int array with {number, appearances}
3. Build a list and poll the element from priority queue with order highest appearance to be the first position, then place the number with second highest appearances  second and so on and so forth. By doing this, all of number would’t be adjacent with each other.
4. Turn a list into a array and return it.

import java.util.*;
class Main {
  public int[] reorganizeString(int[] S) {
      Map<Integer, Integer> map = new HashMap<>();
      for (int c : S) {
        int count = map.getOrDefault(c, 0) + 1;
        if (count > (S.length + 1) / 2) return new int[] {};
        map.put(c, count);
      }
      PriorityQueue<int[]> pq = new PriorityQueue<> ((a,b) -> b[1] - a[1]);
      for (int c : map.keySet()) {
        pq.add(new int[] {c, map.get(c)});
      }
      List<Integer> sb = new ArrayList<>();
      while (!pq.isEmpty()) {
        int[] first = pq.poll();
        if (sb.size() == 0 || sb.get((sb.size() - 1)) != first[0]) {
          sb.add(first[0]);
          if (--first[1] > 0) {
            pq.add(first);
          }
        } else {
          int[] second = pq.poll();
          sb.add(second[0]);
          if (--second[1] > 0) {
            pq.add(second);
          }
          pq.add(first);
        }
      }
    int[] arr = new int[sb.size()];
    for(int i = 0; i < sb.size(); i++) {
      arr[i] = sb.get(i);
    }
      return arr;  
    }
  public static void main(String[] args) {
    Main a = new Main();
    int[] b = {1,1,2,3};
    int[] s = a.reorganizeString(b);
    for (int i =0; i < s.length; i++) {
       System.out.println(s[i]);
    }
  }
}
```

## 2. level order traversal 

```java
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
 
 // O(n) O(n)
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> res = new ArrayList<>();
        if (root == null) return res;
        Queue<TreeNode> queue = new LinkedList();
        queue.offer(root);
        while (!queue.isEmpty()) {
          int size = queue.size();
          List<Integer> list = new ArrayList<>();
          for (int i = 0; i < size; i++) {
            TreeNode cur = queue.poll();
            if (cur.left != null) queue.offer(cur.left);
            if (cur.right != null) queue.offer(cur.right);
            list.add(cur.val);
          }
          res.add(list);
        }
      return res;
    }
}




class Solution {
    List<List<Integer>> levels = new ArrayList<List<Integer>>();

    public void helper(TreeNode node, int level) {
        // start the current level
        if (levels.size() == level)
            levels.add(new ArrayList<Integer>());

         // fulfil the current level
         levels.get(level).add(node.val);

         // process child nodes for the next level
         if (node.left != null)
            helper(node.left, level + 1);
         if (node.right != null)
            helper(node.right, level + 1);
    }
    
    public List<List<Integer>> levelOrder(TreeNode root) {
        if (root == null) return levels;
        helper(root, 0);
        return levels;
    }
}
```

## 3. object

```java
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

## 4. passing chilren

```java
import React, { Component } from 'react';
class App extends Component {
  render() {
    const greeting = 'Welcome to React';
    return (
      <div>
        <Greeting greeting={greeting} />
      </div>
    );
  }
}
class Greeting extends Component {
  render() {
    return <h1>{this.props.greeting}</h1>;
  }
}
export default App;
```

