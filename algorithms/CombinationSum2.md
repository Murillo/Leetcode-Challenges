# Combination Sum II
 
The implementation is similar to [Combination Sum I](https://github.com/Murillo/Leetcode-Challenges/blob/main/algorithms/CombinationSum.md). However, two more procedures are added in this solution.
When the function `combinationBacktracking` is called, the start parameter will be the next number in the original collection. So, this way the algorith can avoid call the same number many times.
``` Java        
this.combinationBacktracking(candidates, new ArrayList(currentCombination), i + 1, nextTarget);
```

Once the algorithm reaches a non-initial index, it has either successfully found the target or surpassed it, requiring a recursive function to be returned to the stack in order to move to the next index. However, if the next number is identical to the previous one, the result of the upcoming recursive functions will be identical as well. In order to prevent repeated calls, the following code is incorporated within the `for`.

``` Java        
if(i > start && candidates[i] == candidates[i - 1]) {
    continue;
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
        List<List<Integer>> permutations1 = solution.combinationSum2(new int[]{10,1,2,7,6,1,5}, 8);
        for (List<Integer> permutation : permutations1){
            System.out.println(Arrays.toString(permutation.toArray()));
        }

        List<List<Integer>> permutations2 = solution.combinationSum2(new int[]{2,5,2,1,2}, 5);
        for (List<Integer> permutation : permutations2){
            System.out.println(Arrays.toString(permutation.toArray()));
        }
    }

    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        Arrays.sort(candidates);
        List<int[]> combinationsSum = this.combinationBacktracking(candidates, new ArrayList<Integer>(), 0, target);
        return combinationsSum.stream().map(item -> Arrays.stream(item).boxed().toList()).toList();
    }

    private List<int[]> combinationBacktracking(int[] candidates, List<Integer> currentCombination, int start, int target){
        if (target == 0) {
            return Arrays.asList(currentCombination.stream().mapToInt(i -> i).toArray());
        }

        List<int[]> combinationCandidates = new ArrayList<>();
        for (int i = start; i < candidates.length; i++) {
            if(i > start && candidates[i] == candidates[i - 1]) {
                continue;
            }

            int nextTarget = target - candidates[i];
            if (nextTarget < 0) {
                return combinationCandidates;
            }
            currentCombination.add(candidates[i]);
            List<int[]> othersCombinations = this.combinationBacktracking(candidates, new ArrayList(currentCombination), i + 1, nextTarget);
            combinationCandidates.addAll(othersCombinations);
            currentCombination.remove(currentCombination.size() - 1);
        }
        return combinationCandidates;
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/combination-sum-ii)
