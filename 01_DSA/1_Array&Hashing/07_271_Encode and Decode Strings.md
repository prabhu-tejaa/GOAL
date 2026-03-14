	15-03-2026 - 1:00am

https://github.com/prabhu-tejaa/dsa-mastery/blob/main/leetcode-premium/lc_271.md

```
import java.util.*;

  

class lc_271 {

    public String encode(List<String> strs) {

        String encoder = "";

        for(String word : strs){

            encoder += word.length() + "#" + word;

        }

        return encoder;

    }

  

    public List<String> decode(String s) {

        List<String> result = new ArrayList<>();

        int i = 0;

        while(i < s.length()) {

            int j = i;

            while(s.charAt(j) != '#') {

                j++;

            }

            int len = Integer.parseInt(s.substring(i, j));

            result.add(s.substring(j + 1, j + 1 + len));

            i = j + 1 + len;

        }

        return result;

    }

  

    public static void main(String[] args) {

        lc_271 sol = new lc_271();

        List<String> input = Arrays.asList("hello", "world");

        String encoded = sol.encode(input);

        System.out.println("Encoded: " + encoded);

        System.out.println("Decoded: " + sol.decode(encoded));

    }

}

  

// The symbol # is just called a delimiter — it's just any character you choose to separate the length from the string.

  

/*

in terminal:

javac lc_271.java

java Solution

*/
```