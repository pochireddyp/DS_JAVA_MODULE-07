# Flattening a Nested List Using an Iterator
## DATE:26-11-2025
## AIM:
To design and implement a class NestedIterator that flattens a nested list of integers such that all integers can be accessed sequentially using an iterator interface (next() and hasNext()).
## Algorithm
1. Create a visited array to mark elements already used in any set.
2. For each index k, if it is not visited, start building the set S[k].
3. Keep moving to nums[current], marking each element as visited.
4. Count each step until you reach a visited element (duplicate).
5. Update the maximum count found so far and return it. 

## Program:
```PY
/*
Program to find Flattening a Nested List Using an Iterator
Developed by: pochireddy p
RegisterNumber: 212223240115
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

<img width="435" height="89" alt="image" src="https://github.com/user-attachments/assets/0df42e89-91f2-4ffe-92eb-18b06be92a93" />



## Result:
The NestedIterator class successfully flattens a nested list of integers into a single list and provides sequential access using standard iterator methods.
