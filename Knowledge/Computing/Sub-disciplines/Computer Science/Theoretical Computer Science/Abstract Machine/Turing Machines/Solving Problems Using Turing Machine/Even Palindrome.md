# Even Palindrome
**Basic Representation**
![[Even Palindrome Basic Representation.png]]

**Start of Computation :**
The *tape* contains the input string w, the tape head is on the leftmost symbol of ${w}$, and the Turing machine is in the start state ${Q_{0}}$.

**Basic Idea :**
The tape head reads the **leftmost** *symbol of w, deletes* this symbol and *“remembers” it by means of a state*.
Then the tape head moves to **rightmost** symbol and tests whether it is *equal to the (already deleted) leftmost* symbol.

If they are equal, then the rightmost symbol is deleted, the tape head moves to the new leftmost symbol, and the whole process is repeated. 

Else the machine can’t reach the final state and the string will be rejected.

![[Even Palindrome.png]]

**Meanings of symbols used:**  
*R, L* – direction of movement of one unit on either side .  
*B* – Blank  
*a, b* – symbols whose combination string is to be tested