# LEETCODE-Stacks-1106
**Method Breakdown:**

1. **Initialization:**
   - A stack `st` is created to store characters during parsing.
   - `temp` and `op` are initialized to store temporary values for evaluation.

2. **Iteration:**
   - The `expression` is iterated character by character.
   - If the current character is '(' or ',', it's skipped.
   - If the character is 't', 'f', '!', '&', or '|', it's pushed onto the stack.
   - If the character is ')', the following logic is applied:
     - While the top of the stack is not '!', '&', or '|', pop characters and evaluate them.
     - If 't' is encountered, set `hasTrue` to true.
     - If 'f' is encountered, set `hasFalse` to true.
     - If the top of the stack is '!', evaluate the negation of the last popped value.
     - If the top of the stack is '&', evaluate the logical AND of the last two popped values.
     - If the top of the stack is '|', evaluate the logical OR of the last two popped values.
     - Push the evaluated result onto the stack.

3. **Return Value:**
   - After processing the entire expression, the top of the stack should contain the final result.
   - Return `true` if the top of the stack is 't', otherwise return `false`.

**Dry Run Example:**

Consider the expression `!(f|t) & (t|f)`

1. The stack initially contains: `( f t ! & t f | )`
2. After processing the first 'f', the stack becomes: `( f t ! & t f | )`
3. After processing the 't', the stack becomes: `( f t ! & t f | )`
4. After processing '!', the stack becomes: `( t & t f | )`
5. After processing '&', the stack becomes: `( f | )`
6. After processing '|', the stack becomes: `( t )`
7. The final result is 't', indicating that the expression evaluates to true.

**Explanation:**

The code effectively parses the boolean expression using a stack to store operators and operands. It evaluates the expression following the rules of boolean logic, correctly handling parentheses, logical operators, and truth values.
