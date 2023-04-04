Given a non-negative integer c, decide whether there're two integers a and b such that a2 + b2 = c.

 

Example 1:

Input: c = 5
Output: true
Explanation: 1 * 1 + 2 * 2 = 5
Example 2:

Input: c = 3
Output: false
 

Constraints:

0 <= c <= 2^31 - 1


```cpp
class Solution {
public:
    bool judgeSquareSum(int c) {
        int start=0;
        int end=sqrt(c);
        // use binary search with a twist!
        while(start<=end){
            long long sum=pow(start,2) + pow(end,2);
            if(sum==c){
                return true;
            }
            if(sum>c){
                end--;
            }
            else{
                start++;
            }
        }
        return false;
    }
};
```
