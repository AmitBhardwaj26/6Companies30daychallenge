
<h2><a href="https://leetcode.com/problems/combination-sum-iii/">216. Combination Sum III</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 Find all valid combinations of k numbers that sum up to n such that the following conditions are true:

Only numbers 1 through 9 are used.
Each number is used at most once.
Return a list of all possible valid combinations. The list must not contain the same combination twice, and the combinations may be returned in any order.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>   k = 3, n = 7
<strong>Output:</strong> [[1,2,4]]
</pre>
<pre>
Explanation: 1 + 2 + 4 = 7
There are no other valid combinations.
  </pre>
  


Constraints:
<pre>
2 <= k <= 9
1 <= n <= 60
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
   public:
       vector<vector<int>> ans; 
       int a[10]={0};
       void solve(int k,int n, vector<int>& v,int j )
       {
           if(n==0 && k==0) {ans.push_back(v); return; }
           else if(n<=0 || k<=0 || j>9) return ;

           // choice diagram
          solve(k,n,v,j+1);
               v.push_back(j);
           solve(k-1,n-j,v,j+1);
           v.pop_back();
       }

       vector<vector<int>> combinationSum3(int k, int n) {
         int x=(k*(k+1))/2;

           if(x>n) return ans;
           vector<int> v; 
           solve(k,n,v,1);
           return ans;
       }
   };
          
 </pre>

