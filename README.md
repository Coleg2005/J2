# J2 Worksheet
1. The first three lines are basic types and last lines (the string) is an object.
   
2. (A) A static method is a method that can only access static data and other static methods. Can be called directly by class name without an object.
   (B) Because static method c

3. (Program 1) Will print out "wrong" because the "==" compares addresses rather than what the address points to.
   (Program 2) Will print out "correct" because the .equals goes to where the address points and compares the actual values.
   
4. No, because the "season" string stays on the heap while the static method changed a separate string "str" on the stack. The change season method
   only changes the address that "str" was pointing to without changing the value of "season
   
5. The output is X: 0, Y: 0, because when the Point method is called, the x and y values in the class point are stored on the heap. Then the point
   function changes its own values stored ont he stack. When returned, it returns the heap values, X = 0 and Y = 0;

6. The private declaration hides the information from people and functions that don't have access to it, i.e. encapsulation.

7. The first Point becauseIt goes to the method that matches the input variables, if 2 ints were input, the first method is chosen.

8. 
