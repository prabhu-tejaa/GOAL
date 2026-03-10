
10-03-2026 - 03:01pm

https://leetcode.com/problems/group-anagrams/description/

```
class Solution {

    public List<List<String>> groupAnagrams(String[] strs) {

  

        // so the intution is take a specifc string, sort it and then create it as a key for hashmap and push value as the word so by that way we get all the anagrams

  

        Map<String, List<String>> map = new HashMap<>();

  

        for(String word : strs){

  

            char[] chars = word.toCharArray();

            Arrays.sort(chars);

            String key = new String(chars);

  

            if(!map.containsKey(key)){

                map.put(key, new ArrayList<>());

            }

  

            map.get(key).add(word);

        }

        return new ArrayList<>(map.values());

    }

}
```