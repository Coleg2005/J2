# J2 Worksheet
1. The first three lines are basic types and last lines (the string) is an object.
2. (A) A static method is a method that can only access static data and other static methods. Can be called directly by class name without an object.
   (B) Because static method c
3. (Program 1) Will print out "wrong" because the "==" compares addresses rather than what the address points to.
   (Program 2) Will print out "correct" because the .equals goes to where the address points and compares the actual values.
4. No, because the "season" string stays on the heap while the static method changed a separate string "str" on the stack. The change season method \n
   only changes the address that "str" was pointing to without changing the value of "season
