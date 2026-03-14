

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
class Solution {

    public int[] productExceptSelf(int[] nums) {

        int numsLength = nums.length;

  

        int[] left = new int[numsLength];

        left[0] = 1;

        int[] right = new int[numsLength];

        right[numsLength - 1] = 1;

  

        for(int i = 1; i < numsLength; i++){

            left[i] = left[i-1] * nums[i-1];

        }

  

        for(int i = numsLength - 2; i >= 0; i--){

            right[i] = right[i+1] * nums[i+1];

        }

  

        int[] result = new int[numsLength];

  

        for(int i = 0; i < numsLength; i++){

            result[i] = left[i] * right[i];

        }

        return result;

    }

}
```

more better optimized version with only O(1) space

```
class Solution {

    public int[] productExceptSelf(int[] nums) {

        int numsLength = nums.length;

        int[] result = new int[numsLength];

        result[0] = 1;

        int suffixProduct = 1;

  

        for(int i = 1; i < numsLength; i++){

            result[i] = result[i-1] * nums[i-1];

        }

  

        for(int i = numsLength - 1; i >= 0; i--){

            result[i] = result[i] * suffixProduct ;

            suffixProduct  = suffixProduct * nums[i];

        }

        return result;

    }

}
```