
<h2><a href="https://leetcode.com/problems/bulls-and-cows/">299. Bulls and Cows</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are playing the Bulls and Cows game with your friend.

You write down a secret number and ask your friend to guess what the number is. When your friend makes a guess, you provide a hint with the following info:

The number of "bulls", which are digits in the guess that are in the correct position.
The number of "cows", which are digits in the guess that are in your secret number but are located in the wrong position. Specifically, the non-bull digits in the guess that could be rearranged such that they become bulls.
Given the secret number secret and your friend's guess guess, return the hint for your friend's guess.

The hint should be formatted as "xAyB", where x is the number of bulls and y is the number of cows. Note that both secret and guess may contain duplicate digits.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>  secret = "1807", guess = "7810"
<strong>Output:</strong>"1A3B"
</pre>
<pre>
Explanation:  Bulls are connected with a '|' and cows are underlined:
"1807"
  |
"7810"
  </pre>
  


Constraints:
<pre>
1 <= secret.length, guess.length <= 1000
secret.length == guess.length
secret and guess consist of digits only.
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 class Solution {
public:
    string getHint(string secret, string guess) {
        unordered_map<int,int> m;
        int n=secret.size();
        int A=0,B=0;
        for(int i=0;i<n;i++)
        {
           if(secret[i]==guess[i]) A++; 
           else m[secret[i]]++;
        } 
        for(int i=0;i<n;i++)
        {
           if(secret[i]!=guess[i] && m[guess[i]]>0 ) 
           {
               m[guess[i]]--;
               B++;
           } 
        }
        return to_string(A)+ 'A'+ to_string(B) + 'B';
    }
};
 </pre>

