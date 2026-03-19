20-03-2026 - 1:28:am

https://leetcode.com/problems/valid-palindrome/description/

```
class Solution {

    public boolean isPalindrome(String s) {

        int stringLen = s.length();

        int left = 0;

        int right = stringLen-1;

  

        while(left<right){

            if(!Character.isLetterOrDigit(s.charAt(left))){

                left++;

            } else if(!Character.isLetterOrDigit(s.charAt(right))){

                right--;

            } else {

                if(Character.toLowerCase(s.charAt(left)) != Character.toLowerCase(s.charAt(right))){

                    break;

                    return false;

                }

        left++;

        right--;

            }

        }

    return true;

    }

}
```