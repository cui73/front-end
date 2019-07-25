# 亚麻OA

## 1.Two sum \(songs/ truck\) （选出最大值pair的index，会有重复，return含有最大长度的那一组）

/\* Given int array of song list return a pair of song which total songs time will end exactly 30 minute before given ride duration. if 2 pairs with same duration get the longest song

For example: Ride Duration:90 Songs: \(1,10,25,35,60,20,40\)

Output: \[20,40\] as 40 has longer song \*/

```text
import java.io.*;
import java.util.*;
class Main {
  public List<Integer> getSongs(int[] songs, int ride) {
    //store the pair of song that we find
    List<Integer> res = new ArrayList<>();
    //use HashMap to store every single song's time and corresponding index in songs array 
    Map<Integer, Integer> map = new HashMap<>();
    int firstSong = -1;
    int secondSong = -1;
    int longestSong = -1; 

    // use blow method to find out matching pair  and  updating longestSong if we find a longer song's time match
    for (int i = 0; i < songs.length; i++) {
      if (map.containsKey(ride - 30 - songs[i])) {
        if (longestSong < Math.max(songs[i], ride - 30 - songs[i])) {
          //record the index for the song we want 
          firstSong = i;
          secondSong = map.get(ride - 30 - songs[i]);
          //update longestSong
          longestSong = Math.max(songs[i], ride - 30 - songs[i]);
        }
      } 
      map.put(songs[i], i);
    }
    res.add(firstSong);
    res.add(secondSong);
    return res;
  }

  public static void main(String[] args) {
    Main sol = new Main();
    int ride = 90;
    int[] songs = new int[] {1, 10, 25, 35, 60, 20, 40};
    List<Integer> res = new ArrayList<>();
    res = sol.getSongs(songs, ride);
    for (Integer k : res) {
      System.out.println(k);
    }
  }
}  
```

//description:  
// use HashMap data structure to store every single song's time as key and corresponding index from songs array as value. while on the way of putting song's time into map, we can use map.containsKey to find out if there is a match with current song's time. if there is, we can record indexes of both song's time and we can also update longestSong time should longer  song's time be found. After looping through the whole array, we can get the pair.

//Time: O\(n\) Space:O\(n\)

## 2. Shortest path, Maze \(2d array\) \(Robert / remove obstacle\) 

\[\[1, 0, 0\],

\[1, 0, 0\],

\[1, 9 ,0\]\].

output: 3 \[0, 0\] -&gt; \[1, 0\] -&gt; \[2, 0\] -&gt; \[2, 1\]

```text
import java.io.*;
import java.util.*;
import java.util.List;

class Main {
public static int removeObstacle(int numRows, int numColumns, List<List<Integer>> lot) {

  // record already visted coordinates
  boolean[][] visit = new boolean[numRows][numColumns];

  int result = 0;

  // control directions from left,right,up,down

  int[][] Directions = new int[][]{{1,0},{-1,0},{0,1},{0,-1}};

  Queue<int[]> que = new LinkedList<>();

  que.offer(new int[]{0,0});

  // main algorithm bfs
  while(!que.isEmpty()){
    int size = que.size();
    for(int i = 0; i < size; i++) {
      int[] current = que.poll();
      int x = current[0];
      int y = current[1];
      // conditions checking
      if (x < 0 || y<0 || x >= numRows || y >= numColumns || lot.get(x).get(y) == 0 || visit[x][y]){
        continue;
      }
      visit[x][y] = true;
      if (lot.get(x).get(y)  == 9) {
        return result;
      }
      // get current position's neighbors  and put them into queue
      for (int[] dir: Directions) {
        int nextX = dir[0] + x;
        int nextY = dir[1] + y;
        que.offer(new int[]{nextX,nextY});
      }
    }
    result++;
  }
  return - 1;
}


  public static void main(String[] args) {
  
    List<List<Integer>> roadsAvailable = constructList(new int[][]{{1, 0, 0}, {1, 0, 0}, {1, 9, 1}});   
    
    int res = removeObstacle(
               3,3,roadsAvailable
    );
    
    System.out.println(res);
    }
  
    private static List<List<Integer>> constructList(int[][]input) {
    List<List<Integer>> list = new LinkedList<>();
    for (int[] eles : input) {
      if (eles.length == 3) {
        List<Integer> newPair = new LinkedList<>();
        for (int ele : eles) {
          newPair.add(ele);
        }
        list.add(newPair);
      }
    }
    return list;
  }
}  


```

//description:  
// Use breadth-first search algorithm to find the shortest path. 

//Time: O\(m\*n\) Space:O\(n\)

## 3.Reorder Log\(files\)

```text
import java.io.*;
import java.util.*;
import java.util.List;

class Main {


 /***** Driver Function *****/  
 public static void main(String[] args) {
    List<String> input = constructList(new String[]{
      "a1 9 2 3 1",
      "g1 act car",
      "zo4 4 7",
      "ab1 off key dog",
      "a8 act zoo"
    });
    List<String> res = reorderLog(input);
    
    for (String str : res) {
      System.out.println(str);
    }
  }

  private static List<String> constructList(String[] arrOfStr) {
    List<String> input = new LinkedList<>();
    for (int i = 0; i < arrOfStr.length; i++) {
      input.add(arrOfStr[i]);
    }
    return input;
  }
  

  // create class Log to access log's id and log's description
  static class Log {
    String id;
    String description;
    public Log(String id, String description) {
      this.id = id;
      this.description = description;
    }
  }

  private static class LogComparator implements Comparator<Log> {
    @Override
    public int compare(Log a, Log b) {
     
        boolean isDigit1 = Character.isDigit(a.description.charAt(0));
        boolean isDigit2 = Character.isDigit(b.description.charAt(0));

        // applying custom ordering 
         if (!isDigit1 && !isDigit2) {
                int cmp = a.description.compareTo(b.description);
                if (cmp != 0) return cmp;
                return a.id.compareTo(b.id);
            }
            return isDigit1 ? (isDigit2 ? 0 : 1) : -1;
      
    }
  }

  public static List<String> reorderLog(List<String> logs) {
    // base case check
    if (logs == null || logs.size() <= 1) {
      return logs;
    }

    // variables initialization to seperate id and description
    List<Log> sortLogs = new LinkedList<>();
    for (String log : logs) {
      String[] curLog = log.split(" ", 2);
      sortLogs.add(new Log(curLog[0], curLog[1]));
    }

    //  sort algorithm comparator:
    Collections.sort(sortLogs, new LogComparator());
    
    // construct result
    List<String> result = new LinkedList<>();
    for (Log log : sortLogs) {
      String str = log.id + " " + log.description;
      result.add(str);
    }   
    return result;
  }
}  





```

//description: 

//by modifying compare function, we will sort in a custom order we specify.

Time: O\(NlogN\) space:O\(n\)

## 4. Two sum closest \(foreApp and backApp / air route\)

/\* two sum closest

* 给两个int的list，一个capacity，从两个list中各选一个item把num加和，返回所有pair里小于capacity并且最大的id，有多个就返回多个
* list是这个格式的：\[\[id1, num1\], \[id2, num2\], \[id3, num3\]\]
* 返回的格式是：\[\[id, id\], ...\] \*/

```text
    public List<List<Integer>> utilization(int[][] fore, int[][] back, int capacity) {
        // use TreeMap data structure to store id and key
        TreeMap<Integer, List<Integer>> tree = new TreeMap<>();
        //sotre capacity as key, id as value
        for (int[] pair : back) {
            // if there is the same capacity, add id to the list otherwise return new ArrayList. 
            List<Integer> list = tree.getOrDefault(pair[1], new ArrayList<>());
            list.add(pair[0]);
            tree.put(pair[1], list);
        }
        
        // use TreeMap to store the closest or exact match
        TreeMap<Integer, List<List<Integer>>> res = new TreeMap<>();
        for (int[] pair : fore) {
            Integer floorKey = tree.floorKey(capacity - pair[1]);
            if (floorKey != null) {
                int diff = capacity - pair[1] - floorKey;
                List<List<Integer>> list = res.getOrDefault(diff, new ArrayList<>());
                for (int id : tree.get(floorKey)) {
                    List<Integer> match = new ArrayList<>();
                    match.add(pair[0]);
                    match.add(id);
                    list.add(match);
                }
                res.put(diff, list);
            }
        }
        return res.get(res.firstKey());
	}
    
    public static void main(String[] args) {
        Main sol = new Main();
		int capacity = 10000;
        int[][] fore = new int[][] {{1,7000}, {2,5000}, {3,3000}, {4,10000}};
        int[][] back = new int[][] {{1,2000}, {2,4000}, {3,3000}, {4,5000}};
        List<List<Integer>> res = new ArrayList<>();
        res = sol.utilization(fore, back, capacity);
        for (List<Integer> li : res) {
            System.out.println(li);
        }
    }

```

//description:  
// use TreeMap to store  back id and capacity, then we can loop through fore and use floorKey method to find if there is an exact match or closest match. If we find the result, we can store it into another TreeMap use the difference as key and store ids as value.

Time:O\(N\*logN\) Space:O\(N\)

## 5.零件组装题

题目意思就是有一堆零件，每个零件的尺寸和组装需要的时间是一样的。输入各个零件的尺寸的list，要求输出最短的总的 accumulated 组装时间。这么说估计也很难描述清楚，直接上例子： 比如输入的list是 {8， 4， 6， 12}。 1. 先选 4 和 6组装到一起，形成 size 为 10 的新零件。目前为止耗时为10。零件的 list 变为 {8， 10， 12} 2. 再选 8 和 10 组装到一起，形成 size 为 18 的新零件。目前为止耗时为 10 + 18 = 28。零件的 list 变为 {12， 18} 3. 最后 把 12 和 18 组装到一起，形成 size 为 30 的新零件。目前为止耗时为 10 + 18 + 30 = 58。 最后输出 58 就可以了。

```text
 public static void main(String[] args) {
    List<Integer> input = constructList(new int[]{8, 4, 6, 12});
    System.out.println(minimumAccumulatedTime(input));
  }
  
  private static List<Integer> constructList(int[] arrOfInt) {
    List<Integer> input = new LinkedList<>();
    for (int i = 0; i < arrOfInt.length; i++) {
      input.add(arrOfInt[i]);
    }
    return input;
  }
  
  public static int minimumAccumulatedTime(List<Integer> sizes) {
    // base case check
    if (sizes == null || sizes.size() == 0) {
      return 0;
    }

    // variable initialization
    int totalTime = 0;
    PriorityQueue<Integer> minHeap = new PriorityQueue<>();
    for (int element : sizes) {
      minHeap.offer(element);
    }

    // main algorithm
    while (minHeap.size() > 1) {
      int smallest = minHeap.poll();
      int secondSmallest = minHeap.poll();
      // merge two smallest and put it back into pq
      int newSize = smallest + secondSmallest;
      totalTime += newSize;
      minHeap.offer(newSize);
    }
    
    return totalTime;
  }
```

//description:  
// put all size the parts into  min-heap and then poll smallest and second smallest part and add them up. Then put it back to min-head until there is only one part in min-heap. we need to record the accumulative time during this process.

Time: O\(NlogK\) space:O\(n\)

## 6. 城市建路题MST

题目意思是有一定数量的城市，城市之间已经有了一些道路。还有一些可以供选择的道路来建设。每个新建的道路有 cost。问如果要连接所有的城市，新建路的最小的 cost 是多少。举个栗子： Input 如下： numTotalAvailableCities = 6 numTotalAvailableRoads = 3 roadsAvailable = \[\[1, 4\], \[4, 5\], \[2, 3\]\] numNewRoadsConstruct = 4 costNewRoadsConstruct = \[\[1, 2, 5\], \[1, 3, 10\], \[1, 6, 2\], \[5, 6, 5\]\] Output 应该是： 7 解释：numTotalAvailableCities = 6 意思是城市的编号从 1 到 6。基于提供的 roadsAvailable list, 这 6 个城市中 已经形成了三个岛， 分别为 \[1, 4, 6\], \[2, 3\] 和 \[6\]。 现在要从 costNewRoadsConstruct list 中选一些路来建使得所有的城市都被连接。这个例子中，显然要选择\[1, 2, 5\] 和 \[1, 6, 2\] 这两条路。总的 cost 就是 5 + 2 = 7。

```text
public static int getMinimumCostToRepair(int numTotalAvailableCities, 
               int numTotalAvailableRoads,
               List<List<Integer>> roadsAvailable,
               int numNewRoadsConstruct,
               List<List<Integer>> costNewRoadsConstruct
  ) {
    // base case check
    if (numTotalAvailableCities < 2 
      || numTotalAvailableRoads >= numTotalAvailableCities - 1) {
      return 0;
    }

    // Initialization 
    UnionFind ufind = new UnionFind(numTotalAvailableCities);
    // int existingRoadCount = 0;
    
    // Step #1: connect exsting roads 
    for (List<Integer> pair : roadsAvailable) {
      int cityA = pair.get(0);
      int cityB = pair.get(1);
      if (!ufind.find(cityA, cityB)) {
        ufind.union(cityA, cityB);
        // numTotalAvailableRoads++;
      }
    }
    
    // sort the priority queue based on cost: small cost to large cost and put road objects into the queue.
    PriorityQueue<RoadConnection> pq = new PriorityQueue<>(
      numNewRoadsConstruct, 
      (a, b) -> (a.cost - b.cost)
    );
    for (List<Integer> newRoad : costNewRoadsConstruct) {
      RoadConnection road = new RoadConnection(
                    newRoad.get(0), 
                    newRoad.get(1),
                    newRoad.get(2)
                  );
      pq.offer(road);
    }
    
    // create results which store smallest cost NewRoads
    List<RoadConnection> result = new LinkedList<>();
    
    // mst.size() + existingRoadCount == numTotalAvailableCities - 1 meaning all cities are connected
    while (pq.size() > 0 
      && result.size() + numTotalAvailableRoads < numTotalAvailableCities - 1) {
      RoadConnection tmpRoad = pq.poll();
      int city1 = tmpRoad.cityA;
      int city2 = tmpRoad.cityB;
      if (!ufind.find(city1, city2)) {
        ufind.union(city1, city2);
        result.add(tmpRoad);
      }
    }

    // mst doesn't exist
    if (result.size() + numTotalAvailableRoads < numTotalAvailableCities - 1) {
      return -1;
    }

    //distract the cost and compute
    int sum = 0;
    for (RoadConnection road : result) {
      sum += road.cost;
    }

    return sum;
  }

  /***** Driver Function *****/  
  public static void main(String[] args) {
    
    int numTotalAvailableCities = 6;
    int numTotalAvailableRoads = 3;
    List<List<Integer>> roadsAvailable = constructList(new int[][]{{1, 4}, {4, 5}, {2, 3}});
    int numNewRoadsConstruct = 4;
    List<List<Integer>> costNewRoadsConstruct = constructList(new int[][]{{1, 2, 5}, {1, 3, 10}, {1, 6, 2}, {5, 6, 5}});
    
    int res = getMinimumCostToRepair(
               numTotalAvailableCities, 
               numTotalAvailableRoads,
               roadsAvailable,
               numNewRoadsConstruct, 
               costNewRoadsConstruct
    );
    
    System.out.println(res);
  }
  
  private static List<List<Integer>> constructList(int[][] input) {
    List<List<Integer>> list = new LinkedList<>();
    for (int[] eles : input) {
      if (eles.length == 2) {
        List<Integer> newPair = new LinkedList<>();
        for (int ele : eles) {
          newPair.add(ele);
        }
        list.add(newPair);
      } else { // ele.length == 3
        List<Integer> newTriple = new LinkedList<>();
        for (int ele : eles) {
          newTriple.add(ele);
        }
        list.add(newTriple);
      }
    }
    return list;
  }
  
}

class RoadConnection {
  int cityA;
  int cityB;
  int cost;
  public RoadConnection(int cityA, int cityB, int cost) {
    this.cityA = cityA;
    this.cityB = cityB;
    this.cost = cost;
  }
}

class UnionFind {
  private int[] ids;
  public UnionFind(int size) {
    this.ids = new int[size + 1];
    for (int i = 0; i < size + 1; i++) {
      this.ids[i] = i;
    }
  }

  private int root (int a) {
    while (ids[a] != a) {
      a = ids[a];
    }
    return a;
  }
  
  /**
   * @return - a and b are not yet connected, return false
   *           a and b are already connected, return true
   **/
  public boolean find(int a, int b) {
    return root(a) == root(b);
  }

  public void union(int a, int b) {
    int rootA = root(a);
    int rootB = root(b);
    ids[rootA] = rootB;
  }
```

//description:

这是个最小生成树（MST）问题。但要注意整个图中已经有一些边了，不是从0开始的最小生成树。具体来说，可以先Union-Find所有已经有的路 in roadsAvailable list，然后把所有可以建的路 in costNewRoadsConstruct list 按照 cost 排序放入 min-heap。然后每次从 min-heap 中拿出最小 cost 的路来接着 Union-Find整个图。每次需要Union的时候，累积目前为止的 cost。当总的 edges 数目等于总的 vertices 数目减 1 时，整个图就被构建成了一颗树。这时输入累积的cost作为输出。  
//  use mst to get the result

 Time:O\(N\*logN\) Space:O\(N\)

## 7. Partition label



/\*

* Input: S = "ababcbacadefegdehijhklij"
* Output: \[9,7,8\]
* Explanation:
* The partition is "ababcbaca", "defegde", "hijhklij".
* This is a partition so that each letter appears in at most one part.
  * A partition like "ababcbacadefegde", "hijhklij" is incorrect, because it splits S into less parts. \*/

```text
public List<Integer> partitionLabels(String S) {
        List<Integer> res = new ArrayList<>();
        int[] last = new int[26];
        for (int i = 0; i < S.length(); i++) {
            last[S.charAt(i) - 'a'] = i;
        }
        
        int start = 0;
        int end = 0;
        for (int i = 0; i < S.length(); i++) {
            end = Math.max(end, last[S.charAt(i) - 'a']);
            if (i == end) {
                res.add(end - start + 1);
                start = i + 1;
            }
        }
        return res;
}

```

//description:  
// Looping through input string and store each character’s rightest index into an array. Looping the string again and use variables left and right to be the left boundary and right boundary each time we need to check we reach the end of right boundary. When we loop through the end of right boundary, we can get the number of characters of this substring. Then, we can set new boundaries for both variables left and right.

Time: O\(n\) Space:O\(1\)

## 8.Amazon Fresh送货\(k closest points to origin\)

```text
import java.io.*;
import java.util.*;
import java.util.List;

class Main {


 public static void main(String[] args) {
    List<List<Integer>> input = new LinkedList<>();
    input.add(generateCoord(new int[]{1, 2}));
    input.add(generateCoord(new int[]{3, 4}));
    input.add(generateCoord(new int[]{1, -1}));
    // input.add(generateCoord(new int[]{4, 5}));
    // input.add(generateCoord(new int[]{2, 1}));
    List<List<Integer>> result = kNearestPoint(3, input, 2);
    for (List<Integer> res : result) {
      System.out.println(res);
    }
  }
  
  private static List<Integer> generateCoord(int[] coord) {
    List<Integer> newCoord = new LinkedList<>();
    newCoord.add(coord[0]);
    newCoord.add(coord[1]);
    return newCoord;
  }
  
  public static List<List<Integer>> kNearestPoint(int numDestinations, List<List<Integer>> allLocations, int numDeliveries) {
    // base case check
    if (numDestinations == numDeliveries) {
      return allLocations;
    }

    if (numDeliveries == 0) {
      return new LinkedList<>();
    }

    // variable initialization
    PriorityQueue<List<Integer>> maxHeap = new PriorityQueue<>(numDeliveries, (a, b) -> (getDistance(b) - getDistance(a)));
    for (List<Integer> coord : allLocations) {
      maxHeap.offer(coord);      
      if (maxHeap.size() > numDeliveries) {
        maxHeap.poll();
      }
    } 
    List<List<Integer>> res = new LinkedList<>();
    while (!maxHeap.isEmpty()) {
      res.add(maxHeap.poll());
    }
    return res;
  }
  // compute distance between origin and different locations
  private static int getDistance(List<Integer> coord) {
    return coord.get(0) * coord.get(0) + coord.get(1) * coord.get(1);
  }
}




```

//description:  
// we first need to compute distances between origin and other locations. Then we can store those locations from the farthest to the nearest into max heap. if the max heap's size larger than the size of numDeliveries, we  need to poll out them until the max heap size is equal to numDeliveries. in the max heap, we got the nearest locations for delivery.

Time: O\(NlogK\) space:O\(n\)

