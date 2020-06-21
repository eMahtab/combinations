# Combinations
## https://leetcode.com/problems/combinations

Given two integers n and k, return all possible combinations of k numbers out of **1 ... n.**
```
Example:

Input: n = 4, k = 2
Output:
[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]
```
# Implementation : Recursive 
```java
class Solution {
    public List<List<Integer>> combine(int n, int k) {
        List<List<Integer>> result = new ArrayList<>();
	 
		if (n <= 0 || n < k)
			return result;
	 
		List<Integer> item = new ArrayList<Integer>();
		dfs(n, k, 1, item, result); // because it need to begin from 1
	 
		return result;
    }
     
	private void dfs(int n, int k, int start, List<Integer> item, List<List<Integer>> res) {
		if (item.size() == k) {
			res.add(new ArrayList<Integer>(item));
			return;
		}
	 
		for (int i = start; i <= n; i++) {
			item.add(i);
			dfs(n, k, i + 1, item, res);
			item.remove(item.size() - 1); // removing the last added element
		}
	}
}
```
