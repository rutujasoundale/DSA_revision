```java
class Solution {
    public int strStr(String haystack, String needle) {
        for(int i=0 , j=needle.length() ; j<=haystack.length();i++,j++){
            if(haystack.substring(i,j).equals(needle)){
                return i;
            }
        }
        return -1;
    }
}
```
Approach
Use a loop to iterate through the haystack string. The loop starts at index i = 0 and goes up to i = haystack.length() - needle.length(). This is done to ensure that there are enough characters left in the haystack for the needle to fit.

Within the loop, check substrings of length equal to the length of the needle starting from the current index i up to i + needle.length(). If any of these substrings matches the needle, return the current index i.

If the loop completes without finding a match, return -1.

Complexity
Time complexity: O(n * m)
Space complexity: O(1)
