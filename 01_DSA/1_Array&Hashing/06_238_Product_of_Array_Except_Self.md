

https://leetcode.com/problems/product-of-array-except-self/description/

```
// basic way of doing by using /
class Solution {

    public int[] productExceptSelf(int[] nums) {

        int product = 1;

  

        for(int num : nums){

            product = product * num;

        }

  

        int numsLength = nums.length;

        int[] output = new int[numsLength];

        for(int i = 0; i < numsLength; i++){

            output[i] = product / nums[i];

        }

        return output;

    }

}
```

```
//brute force way (TLE)

class Solution {

    public int[] productExceptSelf(int[] nums) {

        int numsLength = nums.length;

        int[] result = new int[numsLength];

  

        for(int i = 0; i < numsLength; i++){

            int product = 1;

            for(int j = 0; j < numsLength; j++){

                if(j != i){

                    product = product * nums[j];

                }

            }

        result[i] = product;

        }

    return result;

    }

}
```

hint: its a prefix and suffix problem

```

```