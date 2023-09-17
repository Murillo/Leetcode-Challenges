# Permutation

The permutation of an array is a rearrangement of its elements. Backtracking is a recursive technique used to rearrange positions efficiently.

### Code complexity
Time complexity **O(n!)**\
Space complexity: **O(n!)**

### Java implementation

``` Java
public class Solution {
    public static void main(String[] args){
        Solution solution = new Solution();
        List<List<Integer>> permutations = solution.permute(new int[]{1,2,3});
        for (List<Integer> permutation : permutations){
            System.out.println(Arrays.toString(permutation.toArray()));
        }
    }
    public List<List<Integer>> permute(int[] nums) {
        List<int[]> permutations = this.permuteBacktracking(0, nums.length, nums);
        return permutations.stream().map(item -> Arrays.stream(item).boxed().toList()).toList();
    }

    private List<int[]> permuteBacktracking(int start, int total ,int[] permutation) {
        if (start == total - 1){
            return Arrays.asList(Arrays.copyOf(permutation, total));
        }

        List<int[]> permutations = new ArrayList<>();
        for (int i = start; i < total; i ++) {
            // swipe items
            this.swap(start, i, permutation);

            // Backtrack
            List<int[]> othersPermutations = this.permuteBacktracking(start + 1, total, permutation);
            permutations.addAll(othersPermutations);

            // swipe items back
            this.swap(start, i, permutation);
        }
        return permutations;
    }

    private void swap(int start, int current, int[] nums){
        int temp = nums[start];
        nums[start] = nums[current];
        nums[current] = temp;
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/permutations/)
