14-03-2026 - 05:14am

https://leetcode.com/problems/top-k-frequent-elements/description/

```
class Solution {

    public int[] topKFrequent(int[] nums, int k) {

        Map<Integer, Integer> map = new HashMap<>();

  

        for(int num : nums){

            map.put(num, map.getOrDefault(num, 0)+1);

        }

  

        int numsLength = nums.length;

        List<Integer>[] bucket = new List[numsLength + 1];

  

        for(int key : map.keySet()){

  

            int frequency = map.get(key);

  

            if(bucket[frequency] == null){

                bucket[frequency] = new ArrayList<>();

            }

  

            bucket[frequency].add(key);

        }

  

        int[] result = new int[k];

        int index = 0;

  

        for(int i = bucket.length - 1; i >= 0 && index < k;i--){

            if(bucket[i] != null){

                for(int num : bucket[i]){

                    result[index++] = num;

                    if(index == k){

                        break;

                    }

                }

            }

        }

        return result;

    }

}
```