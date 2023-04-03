Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.

The overall run time complexity should be O(log (m+n)).

 

Example 1:

Input: nums1 = [1,3], nums2 = [2]
Output: 2.00000
Explanation: merged array = [1,2,3] and median is 2.
Example 2:

Input: nums1 = [1,2], nums2 = [3,4]
Output: 2.50000
Explanation: merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.
 

Constraints:

nums1.length == m
nums2.length == n
0 <= m <= 1000
0 <= n <= 1000
1 <= m + n <= 2000
-106 <= nums1[i], nums2[i] <= 106


```cpp
class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        int i,m=nums1.size(), n=nums2.size();
        //  pushing elements of second vector into first
        for(i=0; i<n; i++){
            nums1.push_back(nums2[i]);
        }
        // sorting the vector
        sort(nums1.begin(),nums1.end());
        int a=nums1.size();
        double ans;
        // applying median condition - keep in mind the indices!
        if(a%2==0){
            // here dividing by 2.0 matters a lot instead of just 2, becuase we neet to get that one decimal place too!
            ans = (nums1[(a/2)-1] + nums1[(a/2)])/2.0;
        }
        else{
            ans=nums1[(a+1)/2 -1];
        }
        return ans;
    }
};
```

INSIGHTS - I just solved this question using naive brute force approach. I have to come up with O(n+m) time complexity algo..
