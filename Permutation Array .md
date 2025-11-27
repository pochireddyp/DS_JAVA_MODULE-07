# Ex9 Finding the Longest Length of Nested Set in a Permutation Array
## DATE: 26-11-2025
## AIM:
To write a program that finds the length of the longest set s[k] defined as s[k] = { nums[k], nums[nums[k]], nums[nums[nums[k]]], … },where the iteration stops before a duplicate element occurs.

The task is to return the maximum size among all such sets.
## Algorithm
1. Create a visited array to mark elements already used in any set.
2. For each index k, if it is not visited, start building the set S[k].
3. Keep moving to nums[current], marking each element as visited.
4. Count each step until you reach a visited element (duplicate).
5. Update the maximum count found so far and return it.
  

## Program:
```PY
/*
Program to find the Longest Length of Nested Set in a Permutation Array
Developed by: pochireddy p
RegisterNumber:  212223240115
*/
import java.util.Scanner;

class LongestSet {

    public static int longestSetLength(int[] nums) {
        boolean[] visited = new boolean[nums.length];
        int maxLength = 0;

        for (int i = 0; i < nums.length; i++) {
            if (!visited[i]) {
                int count = 0;
                int current = i;

                while (!visited[current]) {
                    visited[current] = true;
                    current = nums[current];
                    count++;
                }

                maxLength = Math.max(maxLength, count);
            }
        }

        return maxLength;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter the array size: ");
        int n = sc.nextInt();

        int[] nums = new int[n];

      
        System.out.println("Enter " + n + " elements:");
        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }

        int result = longestSetLength(nums);
        System.out.println("Maximum size of S[k] = " + result);

        sc.close();
    }
}

```

## Output:

<img width="435" height="89" alt="image" src="https://github.com/user-attachments/assets/25857bb4-9e4a-4be1-8590-3799f0ff8081" />



## Result:
The program successfully computes the longest length of the nested set s[k] for the given permutation array.
