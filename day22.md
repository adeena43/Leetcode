```cpp
class Solution {
public:
    bool isValid(string s) {
        stack<char> st;

        for (char c : s) {
            // If it's an opening bracket, push it onto the stack
            if (c == '(' || c == '{' || c == '[') {
                st.push(c);
            } 
            // If it's a closing bracket
            else {
                // Stack should not be empty and top must match the opening bracket
                if (st.empty()) return false;

                char top = st.top();
                if ((c == ')' && top == '(') || 
                    (c == '}' && top == '{') || 
                    (c == ']' && top == '[')) {
                    st.pop();
                } else {
                    return false;
                }
            }
        }

        // At the end, the stack should be empty
        return st.empty();
    }
};

```
