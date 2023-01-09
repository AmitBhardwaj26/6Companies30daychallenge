
<h2><a href="https://leetcode.com/problems/number-of-substrings-containing-all-three-characters/description/">1358. Number of Substrings Containing All Three Characters</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
 Given a string s consisting only of characters a, b and c.

Return the number of substrings containing at least one occurrence of all these characters a, b and c.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  s = "abcabc"
<strong>Output:</strong> 10
</pre>
<pre>
Explanation: The substrings containing at least one occurrence of the characters a, b and c are "abc", "abca", "abcab", "abcabc", "bca", "bcab", "bcabc", "cab", "cabc" and "abc" (again). 
  </pre>


Constraints:
<pre>
The substrings containing at least one occurrence of the characters a, b and c are "abc", "abca", "abcab", "abcabc", "bca", "bcab", "bcabc", "cab", "cabc" and "abc" (again). 
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
      class Solution {
        public:
            int numberOfSubstrings(string s) {
                int a[3]={0},i=0,j=0,n=s.size(),ans=0;
                while(j<n)
                {
                    while(j<n && (a[0]==0 || a[1]==0 || a[2]==0 )) { a[s[j]-'a']++; j++; }
                    if(a[0]>0 && a[1]>0 && a[2]>0) ans+=n-j+1;
                    a[s[i]-'a']--;
                    i++;
                    //cout<<ans<<" ";
                }
                while(i<j)
                {
                    if(a[0]>0 && a[1]>0 && a[2]>0) ans+=n-j+1;
                    a[s[i]-'a']--;
                    i++;
                }
                return ans;
            }
        };
          
 </pre>

