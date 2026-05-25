
# EX 3C Tug of War problem - Backtracking.
## DATE: 07.05.26
## AIM:
To write a Java program to for given constraints.
Given an integer array nums, return true if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or false otherwise.
Example 1:
Input: Enter the number of elements: 4
Enter the elements of the array:
1 5 11 5
Output: true
Explanation: The array can be partitioned as [1, 5, 5] and [11].

Constraints:

1 <= nums.length <= 200
1 <= nums[i] <= 100

## Algorithm
1. Start the program and read the number of elements n, then input n integers into the array nums.
2. Calculate the total sum of all elements in the array.
3. If the total sum is odd, print false (since it cannot be divided equally).
4. Set the target as half of the total sum and create a boolean array dp to track possible subset sums.
5. Use dynamic programming to fill the dp array and finally print true if a subset with the target sum exists, else false.

## Program:
```
/*
Program to implement Reverse a String
Developed by: SARISH VARSHAN V 
Register Number:  212223230196
*/

import java.util.Scanner;

public class Solution {
    public boolean canPartition(int[] nums) {
        int total = 0;
        for (int num : nums)
            total += num;

        // If total sum is odd, it cannot be partitioned equally
        if (total % 2 != 0)
            return false;

        int target = total / 2;
        boolean[] dp = new boolean[target + 1];
        dp[0] = true; // Base case — sum 0 is always possible

        for (int num : nums) {
            for (int j = target; j >= num; j--) {
                dp[j] = dp[j] || dp[j - num];
            }
        }

        return dp[target];
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution sol = new Solution();
        int n = scanner.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }
        boolean canBePartitioned = sol.canPartition(nums);
        System.out.println(canBePartitioned);
    }
}
```

## Output:
<img width="655" height="252" alt="image" src="https://github.com/user-attachments/assets/d813bc2d-f8b9-4397-ab27-0bd5f254dfbb" />



## Result:
The program successfully implemented and the expected output is verified.
