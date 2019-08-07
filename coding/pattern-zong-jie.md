# Pattern 总结

## Sliding Window Pattern

1.Given an array of positive numbers and a positive number ‘k’, find the maximum sum of any contiguous subarray of size ‘k’.

Example 1:

Input: \[2, 1, 5, 1, 3, 2\], k=3 Output: 9 Explanation: Subarray with maximum sum is \[5, 1, 3\] 

Example 2:

Input: \[2, 3, 4, 1, 5\], k=2 Output: 7 Explanation: Subarray with maximum sum is \[3, 4\]. Input: \[2, 3, 4, 1, 5\], k=2 Output: 7 

Explanation: Subarray with maximum sum is \[3, 4\].

```java
class MaxSumSubArrayOfSizeK {
  public static int findMaxSumSubArray(int k, int[] arr) {
    int windowSum = 0, maxSum = 0;
    int windowStart = 0;
    for (int windowEnd = 0; windowEnd < arr.length; windowEnd++) {
      windowSum += arr[windowEnd]; // add the next element
      // slide the window, we don't need to slide if we've not hit the required window size of 'k'
      if (windowEnd >= k - 1) {
        maxSum = Math.max(maxSum, windowSum);
        windowSum -= arr[windowStart]; // subtract the element going out
        windowStart++; // slide the window ahead
      }
    }

    return maxSum;
  }

  public static void main(String[] args) {
    System.out.println("Maximum sum of a subarray of size K: "
        + MaxSumSubArrayOfSizeK.findMaxSumSubArray(3, new int[] { 2, 1, 5, 1, 3, 2 }));
    System.out.println("Maximum sum of a subarray of size K: "
        + MaxSumSubArrayOfSizeK.findMaxSumSubArray(2, new int[] { 2, 3, 4, 1, 5 }));
  }
}
```

思路： 使用sliding window 设置 start和end都是0 end的往前面走，如果window里面有K个数，开始比较maxSum的大小，再开始减去window里面element的个数，然后start往前走，保持一个window。

Time: O\(n\) spaceO\(1\)

2. Smallest Subarray with a given sum \(easy\)

Input: \[2, 1, 5, 2, 3, 2\], S=7 Output: 2 Explanation: The smallest subarray with a sum great than or equal to '7' is \[5, 2\].

Input: \[2, 1, 5, 2, 8\], S=7 Output: 1 Explanation: The smallest subarray with a sum greater than or equal to '7' is \[8\].

Input: \[3, 4, 1, 1, 6\], S=8 Output: 3 Explanation: Smallest subarrays with a sum greater than or equal to '8' are \[3, 4, 1\] or \[1, 1, 6\].

```java
class MinSizeSubArraySum {
  public static int findMinSubArray(int S, int[] arr) {
    int windowSum = 0, minLength = Integer.MAX_VALUE;
    int windowStart = 0;
    for (int windowEnd = 0; windowEnd < arr.length; windowEnd++) {
      windowSum += arr[windowEnd]; // add the next element
      // shrink the window as small as possible until the 'windowSum' is smaller than 'S'
      while (windowSum >= S) {
        minLength = Math.min(minLength, windowEnd - windowStart + 1);
        windowSum -= arr[windowStart]; // subtract the element going out
        windowStart++; // slide the window ahead
      }
    }

    return minLength == Integer.MAX_VALUE ? 0 : minLength;
  }

  public static void main(String[] args) {
    int result = MinSizeSubArraySum.findMinSubArray(7, new int[] { 2, 1, 5, 2, 3, 2 });
    System.out.println("Smallest subarray length: " + result);
    result = MinSizeSubArraySum.findMinSubArray(7, new int[] { 2, 1, 5, 2, 8 });
    System.out.println("Smallest subarray length: " + result);
    result = MinSizeSubArraySum.findMinSubArray(8, new int[] { 3, 4, 1, 1, 6 });
    System.out.println("Smallest subarray length: " + result);
  }
}

```

思路：还是sliding window 求minLength

3. Longest Substring with K Distinct Characters \(medium\)

Input: String="araaci", K=2 Output: 4 Explanation: The longest substring with no more than '2' distinct characters is "araa".

Input: String="araaci", K=1 Output: 2 Explanation: The longest substring with no more than '1' distinct characters is "aa".

Input: String="cbbebi", K=3 Output: 5 Explanation: The longest substrings with no more than '3' distinct characters are "cbbeb" & "bbebi".

```java
import java.util.*;

class LongestSubstringKDistinct {
  public static int findLength(String str, int k) {
    if (str == null || str.length() == 0 || str.length() < k)
      throw new IllegalArgumentException();

    int windowStart = 0, maxLength = 0;
    Map<Character, Integer> charFrequencyMap = new HashMap<>();
    // in the following loop we'll try to extend the range [windowStart, windowEnd]
    for (int windowEnd = 0; windowEnd < str.length(); windowEnd++) {
      char rightChar = str.charAt(windowEnd);
      charFrequencyMap.put(rightChar, charFrequencyMap.getOrDefault(rightChar, 0) + 1);
      // shrink the sliding window, until we are left with 'k' distinct characters in the frequency map
      while (charFrequencyMap.size() > k) {
        char leftChar = str.charAt(windowStart);
        charFrequencyMap.put(leftChar, charFrequencyMap.get(leftChar) - 1);
        if (charFrequencyMap.get(leftChar) == 0) {
          charFrequencyMap.remove(leftChar);
        }
        windowStart++; // shrink the window
      }
      maxLength = Math.max(maxLength, windowEnd - windowStart + 1); // remember the maximum length so far
    }

    return maxLength;
  }

  public static void main(String[] args) {
    System.out.println("Length of the longest substring: " + LongestSubstringKDistinct.findLength("araaci", 2));
    System.out.println("Length of the longest substring: " + LongestSubstringKDistinct.findLength("araaci", 1));
    System.out.println("Length of the longest substring: " + LongestSubstringKDistinct.findLength("cbbebi", 3));
  }
}

```

思路： 用map记录每个字母的频率。当存的字母个数不超出K时，我们不断去记录这个window里面的最大长度。当存的字母个数超出K时，那么要去移动这个window，移动完后接着继续验证是不是最长的长度。

O\(N\),O\(K\)

4.

