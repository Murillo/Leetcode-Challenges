# Combination Sum

The backtrack technique will be used in this algorithm. At each new node, the algorithm checks whether the target has been reached or exceeded. If it has not been reached, the function calls the same function recursively, adding the same number or the next one in the list until the target is reached. If the target is reached or exceeded, the function ends by returning the combination found, or an empty value if the target has been surpassed. The previous function on the stack will continue the loop for the next number in the list of combinations and repeat this process until the numbers in the list are finished.

### Code complexity
Time complexity **O(n^(T/M))** where n is the numbers, T is the target and S is the smaller number of n.\
Space complexity: **O(T/M)** the height of the tree, the number max of the function in the stack.

### Java implementation

``` Java
public class Solution {

    public static void main(String[] args){
        Solution solution = new Solution();
        List<List<Integer>> permutations1 = solution.combinationSum(new int[]{2,3,6,7}, 7);
        for (List<Integer> permutation : permutations1){
            System.out.println(Arrays.toString(permutation.toArray()));
        }

        List<List<Integer>> permutations2 = solution.combinationSum(new int[]{2,3,5}, 8);
        for (List<Integer> permutation : permutations2){
            System.out.println(Arrays.toString(permutation.toArray()));
        }
    }
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
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
            int nextTarget = target - candidates[i];
            if (nextTarget < 0) {
                return combinationCandidates;
            }
            currentCombination.add(candidates[i]);

            List<int[]> othersCombinations = this.combinationBacktracking(candidates, new ArrayList(currentCombination), i, nextTarget);
            combinationCandidates.addAll(othersCombinations);

            currentCombination.remove(currentCombination.size() - 1);
        }
        return combinationCandidates;
    }
}
```

### References
[Leetcode](https://leetcode.com/problems/combination-sum)
