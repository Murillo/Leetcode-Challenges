# Combination Sum III

This problem is similar to [Combination Sum I](https://github.com/Murillo/Leetcode-Challenges/blob/main/algorithms/CombinationSum.md), with the difference that each number can only be used once, and the largest number available is 9. Additionally, the combination must have a certain pre-defined size, so the recursive function will check if the target sum has been reached and if the size of the combination matches the pre-defined size.

``` Java
if (currentCombination.size() == size && target == 0) {
    return Arrays.asList(currentCombination.stream().mapToInt(i -> i).toArray());
}
```


### Code complexity
Time complexity **O(n!)** For each number, the algorithm will call the next numbers recursively.  \
Space complexity: **O(n)** n is the height of the tree, being the total number of times the recursive function is stored on the stack.

### Java implementation

``` Java
public class Solution {

    public static void main(String[] args) {
        Solution solution = new Solution();
        List<List<Integer>> permutations1 = solution.combinationSum3(3, 7);
        for (List<Integer> permutation : permutations1){
            System.out.println(Arrays.toString(permutation.toArray()));
        }

        List<List<Integer>> permutations2 = solution.combinationSum3(3, 9);
        for (List<Integer> permutation : permutations2){
            System.out.println(Arrays.toString(permutation.toArray()));
        }
    }

    public List<List<Integer>> combinationSum3(int size, int target) {
        List<int[]> combinationsSum = this.combinationBacktracking(new ArrayList<Integer>(), 1, size, target);
        return combinationsSum.stream().map(item -> Arrays.stream(item).boxed().toList()).toList();
    }

    private List<int[]> combinationBacktracking(List<Integer> currentCombination, int start, int size, int target){
        if (currentCombination.size() == size && target == 0) {
            return Arrays.asList(currentCombination.stream().mapToInt(i -> i).toArray());
        }

        List<int[]> combinationCandidates = new ArrayList<>();
        for (int i = start; i <= 9; i++) {
            int nextTarget = target - i;
            if (nextTarget < 0) {
                return combinationCandidates;
            }

            currentCombination.add(i);
            combinationCandidates.addAll(this.combinationBacktracking(currentCombination, i + 1, size, nextTarget));
            currentCombination.remove(currentCombination.size() - 1);
        }
        return combinationCandidates;
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/combination-sum-iii)
