
<h2><a href="https://leetcode.com/problems/rotate-function/description/">396. Rotate Function</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given an integer array nums of length n.

Assume arrk to be an array obtained by rotating nums by k positions clock-wise. We define the rotation function F on nums as follow:

F(k) = 0 * arrk[0] + 1 * arrk[1] + ... + (n - 1) * arrk[n - 1].
Return the maximum value of F(0), F(1), ..., F(n-1).

The test cases are generated so that the answer fits in a 32-bit integer.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>    nums = [4,3,2,6]
<strong>Output:</strong>  26
</pre>
<pre>
F(0) = (0 * 4) + (1 * 3) + (2 * 2) + (3 * 6) = 0 + 3 + 4 + 18 = 25
F(1) = (0 * 6) + (1 * 4) + (2 * 3) + (3 * 2) = 0 + 4 + 6 + 6 = 16
F(2) = (0 * 2) + (1 * 6) + (2 * 4) + (3 * 3) = 0 + 6 + 8 + 9 = 23
F(3) = (0 * 3) + (1 * 2) + (2 * 6) + (3 * 4) = 0 + 2 + 12 + 12 = 26
So the maximum value of F(0), F(1), F(2), F(3) is F(3) = 26.
  </pre>
  
 

Constraints:
<pre>
n == nums.length
1 <= n <= 105
-100 <= nums[i] <= 100
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
        // concept is that take noraml mul=0*num[0]+1*nums[1]....
//then take the sum of all elements 
//at each rotation we remove last word n*nums[n-1-i] and add sum to it 
//at any time mul contains n-1 occurance of last element after adding sum we ///have to substrat n occurence
//take the minimum print the answer.

class Solution {
public:
    int maxRotateFunction(vector<int>& nums) {
        long long sum=0,ans=-1*1e10,mul=0,n=nums.size();
        for(int i=0;i<n;i++)
        {
            sum+=nums[i];
            mul+=i*nums[i];
        } 
       // cout<<mul<<" ";
        for(int i=0;i<n;i++)
        {
            mul=mul-n*nums[n-i-1]+sum;
            ans=max(ans,mul);
           // cout<<ans<<" ";
        }
        return ans;
    }
};
 </pre>

