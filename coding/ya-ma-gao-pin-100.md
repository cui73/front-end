# 亚麻高频100

## 973. K Closest Points to Origin

思路：点到原点的距离。根据公式求两点的距离，因为是原点，这个点还是它们自己本身。所以只要用点B-点A建立一个最大堆就可以得到离原点最近（最小值）。

time complexity: Nlog\(k\) space: O\(N\)

```java
class Solution {
    public int[][] kClosest(int[][] points, int K) {
        PriorityQueue<int[]> pq = new PriorityQueue<int[]>((p1, p2) -> p2[0] * p2[0] + p2[1] * p2[1] - p1[0] * p1[0] - p1[1] * p1[1]);
        for (int[] p : points) {
            pq.offer(p);
            if (pq.size() > K) {
                pq.poll();
            }
        }
        int[][] res = new int[K][2];
        while (K > 0) {
            res[--K] = pq.poll();
        }
        return res;
    }
}
```

##  973. Reorder Log Files

思路：改写comparefunction 注意 返回0 按照input顺序， 返回1 表示 比较物a 在比较物b 后面，-1则表示 比较物a 在比较物b 前面。time complexity: O\(NlogN\) space: O\(1\)

```java
class Solution {
    public String[] reorderLogFiles(String[] logs) {
      Comparator<String> myCmp = new Comparator<String> () {
        @Override 
        public int compare (String string1, String string2) {
          String[] s1 = string1.split(" ", 2);
          String[] s2 = string2.split(" ", 2);
          boolean isDigit1 = Character.isDigit(s1[1].charAt(0));
          boolean isDigit2 = Character.isDigit(s2[1].charAt(0));
          if (!isDigit1 && !isDigit2) {
            int cmp = s1[1].compareTo(s2[1]);
            if (cmp != 0) return cmp;
            return s1[0].compareTo(s2[0]);
          }
          return isDigit1 ? (isDigit2 ? 0 : 1) : -1;
        }
      };
      Arrays.sort(logs, myCmp);
      return logs;
    }
}
```

## 1. 2 SUM

思路：创建一个map和一个存result的二维数组，紧接着遍历整个数组，如果map中存了target - nums\[i\] 则立即返回key以及当前的i

time complexity: O\(N\) Space: O\(N\); 

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
      if (nums == null || nums.length < 2) {
        return new int[2];
      }
      HashMap<Integer, Integer> map = new HashMap<>();
      int[] res = new int[2];
      for (int i = 0; i < nums.length; i++) {
        if (map.containsKey(target - nums[i])) {
          res[0] = map.get(target - nums[i]);
          res[1] = i;
          break;
        }
        map.put(nums[i], i);
      }
      return res;
        
    }
}
```



## 5. Longest Palindromic Substring

思路：一个字母是palindromic, 两个相同的字母是，完全重复的无限个字母也是palindrome，还有aba abba. 先判断自身的字母，然后再判断右边相邻的字母，如果是相同的左边减，右边加。注意要用两个loop进行判断，第二个loop j &lt; 2 ，当j == 0时判断字母本身， j==1时判断与之相邻的是否是一样。right - left - 1记录获得panlindrome的长度，只有找到时这个才会有变化。res = s.substring\(left + 1, right\); 因为找到后left往左走1， 右往右边走1.

```java
class Solution {
    public String longestPalindrome(String s) {
      String res = "";
      for (int i = 0; i < s.length(); i++) {
        for (int j = 0; j < 2; j++) {
          int left = i;
          int right = i + j;
          
          while (left >=0 && right < s.length() && s.charAt(left) == s.charAt(right)){
            left--;
            right++;
          }
          
          if (right - left - 1 > res.length()) {
            res = s.substring(left+1, right);
          }
        }
      }
      return res;
    }
}
```

## 146. LRU Cache

## 200. Number of islands

BFS: 查看上下左右四个方向的查找

```java
class Solution {
    public int numIslands(char[][] grid) {
        if (grid.length == 0) {
            return 0;
        }
        
        int m = grid.length, n = grid[0].length;
        
        boolean[][] visited = new boolean[m][n];
        Queue<int[]> queue = new LinkedList<>();
        int count = 0;
        for(int i=0; i<m; i++) {
            for(int j=0; j<n; j++) {
                if(grid[i][j] == '1' && !visited[i][j]) {
                    queue.offer(new int[]{i, j});
                    visited[i][j] = true;
                    bfs(grid, queue, visited);
                    count++;
                }
            }
        }
        
        return count;
    }
    
    private void bfs(char[][] grid, Queue<int[]> queue, boolean[][] visited) {
        int[][] dirs = {{0,1}, {1,0}, {0, -1}, {-1, 0}};
        int m = grid.length;
        int n = grid[0].length;
        
        while(!queue.isEmpty()) {
            int[] curr = queue.poll();
            for (int[] dir : dirs) {
                int x = curr[0] + dir[0];
                int y = curr[1] + dir[1];
                
                if (x < 0 || x >= m || y < 0 || y >=n || visited[x][y] || grid[x][y] == '0') 
                    continue;
                
                visited[x][y] = true;
                queue.offer(new int[]{x, y});
            }
        }
    }
}
```

DFS：深入查找

```java
class Solution {
    private int m;
    private int n;
    public int numIslands(char[][] grid) {
      int res = 0;
      m = grid.length;
      if (m == 0) return 0;
      n = grid[0].length;
      for (int i = 0; i < m; i++) {
        for (int j = 0; j < n; j++) {
          if (grid[i][j] == '1') {
            dfs(grid, i, j);
            res++;
          }
        }
      }
      return res;  
    }
    
    public void dfs(char[][] grid, int i, int j) {
      if (i < 0 || j < 0 || i >= m || j >= n || grid[i][j] == '0') return;
      grid[i][j] = '0';
      dfs(grid, i, j - 1);
      dfs(grid, i, j +1);
      dfs(grid, i + 1, j);
      dfs(grid, i - 1, j);
    }
}
```

