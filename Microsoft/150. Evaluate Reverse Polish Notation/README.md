
<h2><a href="https://leetcode.com/problems/evaluate-reverse-polish-notation/">150. Evaluate Reverse Polish Notation</a></h2>
<h3>Medium</h3>
<hr>
<div><p>
You are given an array of strings tokens that represents an arithmetic expression in a Reverse Polish Notation.

Evaluate the expression. Return an integer that represents the value of the expression.

Note that:

The valid operators are '+', '-', '*', and '/'.
Each operand may be an integer or another expression.
The division between two integers always truncates toward zero.
There will not be any division by zero.
The input represents a valid arithmetic expression in a reverse polish notation.
The answer and all the intermediate calculations can be represented in a 32-bit integer.
</p>


<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong>     tokens = ["2","1","+","3","*"]
<strong>Output:</strong> 9
</pre>
<pre>
((2 + 1) * 3) = 9

  </pre>

 

Constraints:
<pre>
1 <= tokens.length <= 104
tokens[i] is either an operator: "+", "-", "*", or "/", or an integer in the range [-200, 200].
</pre>
<hr>
 <h2><strong><b>Solution</b></strong></h2>
 <br>
 <pre>
 
      class Solution {
public:
    int evalRPN(vector<string>& tokens) {
        ios::sync_with_stdio(0); cin.tie(0);cout.tie(0);
        stack<long> st; 
        
        for(int i=0;i<tokens.size();i++)
        {
            if(tokens[i]=="+" || //check token[i]== +, - ,/ ,*
               tokens[i]=="-" || 
               tokens[i]=="*" || 
               tokens[i]=="/")  
            { 
                char c=tokens[i][0];
                long a=st.top(); st.pop();
                long b=st.top(); st.pop();
                switch(c)
                {
                    case '+': st.push(b+a); break;
                    case '-': st.push(b-a); break;
                    case '*': st.push(b*a); break;
                    case '/': st.push(b/a); break;
                }
            }
            else  st.push(stoi(tokens[i]));  
            
        }
        return st.top();
    }
};
          
 </pre>

