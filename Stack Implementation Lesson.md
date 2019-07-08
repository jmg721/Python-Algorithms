# Bracket-matching application
Now let us look at an example of how we can use our stack implementation. 
We are going to write a little function that will verify whether a statement containing brackets--(, [, or {--is balanced, that is, 
whether the number of closing brackets matches the number of opening brackets. 
It will also ensure that one pair of brackets really is contained in another:

![image](https://user-images.githubusercontent.com/19671036/60817677-c0335500-a161-11e9-9172-a876a632f8b9.png)

Our function parses each character in the statement passed to it. If it gets an open bracket, it pushes it onto the stack. If it gets a closing bracket, it pops the top element off the stack and compares the two brackets to make sure their types match: ( should match ), [ should match ], and { should match }. If they don't, we return False, otherwise we continue parsing.

Once we have got to the end of the statement, we need to do one last check. If the stack is empty, then we are fine and we can return True. But if the stack is not empty, then we have some opening bracket which does not have a matching closing bracket and we shall return False. We can test the bracket-matcher with the following little code:

![image](https://user-images.githubusercontent.com/19671036/60817723-db05c980-a161-11e9-95c6-0d2ba5abd044.png)

