
# EX 3E Generate Permutations using Backtracking  Approach.
## DATE: 07.05.26
## AIM:
To write a Java program to for given constraints.
Given an array nums of distinct integers, return all the possible Permutation. You can return the answer in any order.
Example 1:
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
For example:
## Algorithm
1. Start the program and read the input array of integers from the user.
2. Initialize an empty list ans to store all possible permutations.
3. Use the recursive backtrack() method to build permutations by adding unused elements one by one.
4. When the current permutation length equals the array length, add it to the result list.
5. After recursion completes, print the list of all generated permutations.


## Program:
```
/*
Program to implement Reverse a String
Developed by: SARISH VARSHAN V
Register Number:  212223230196
*/

import java.util.*;

public class Permutations {

    // Backtracking function to generate all permutations
    static void backtrack(int[] nums, boolean[] used, List<Integer> current, List<List<Integer>> result) {
        if (current.size() == nums.length) {
            result.add(new ArrayList<>(current));
            return;
        }

        for (int i = 0; i < nums.length; i++) {
            if (used[i]) continue;
            used[i] = true;
            current.add(nums[i]);

            backtrack(nums, used, current, result);

            current.remove(current.size() - 1);
            used[i] = false;
        }
    }

    // Function to return all permutations
    public static List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        backtrack(nums, new boolean[nums.length], new ArrayList<>(), result);
        return result;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input format: [1,2,3]
        String input = sc.nextLine().trim();
        input = input.replaceAll("\\[|\\]", "");
        String[] parts = input.split(",");
        int[] nums;

        if (input.isEmpty()) {
            nums = new int[0];
        } else {
            nums = new int[parts.length];
            for (int i = 0; i < parts.length; i++) {
                nums[i] = Integer.parseInt(parts[i].trim());
            }
        }

        List<List<Integer>> result = permute(nums);
        System.out.println(result);
        sc.close();
    }
}
```

## Output:
<img width="1222" height="164" alt="image" src="https://github.com/user-attachments/assets/4334a933-d747-4d77-bcbc-0a022df4eff2" />



## Result:
The program successfully implemented and the expected output is verified.
