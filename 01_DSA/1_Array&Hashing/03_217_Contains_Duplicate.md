10-03-2026 - 01:32pm

https://leetcode.com/problems/contains-duplicate/description/

```
class Solution {

    public boolean containsDuplicate(int[] nums) {

        Set<Integer> set = new HashSet<>();

  

        for(int num : nums){

            if(set.contains(num)){

                return true;

            }

            set.add(num);

        }

        return false;

    }

}
```