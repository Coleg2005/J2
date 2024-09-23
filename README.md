# J2 Worksheet
### 1. Which of the following is an object and which is a basic type?
   ```java
   int a;
   double b;
   int c[] = {1, 2, 3};
   String s = "Hello World";
   ```
   The first three lines are basic types and last lines (the string) is an object.
   
### 2. Two part question:
   (A) What is a static method in Java?
    A static method is a method that can only access static data and other static methods. Can be called directly by class name without an object.

   (B) Why does the main method need to be a static method?
    Because static methods can access other static methods, main needs to be able to access all methods so it needs to be static.

### 3. What is the output of the following programs?
   ```java
   /* Program 1 */
   public static void main(final String args[]) {
       String choice = new String("A");
       if (choice == "A") {
           System.out.println("Correct");
       }
       else {
           System.out.println("Wrong");
       }
   }
   ```
   ``` java
   /* Program 2 */
   public static void main(final String args[]) {
       String choice = new String("A");
       if (choice.equals("A")) {
           System.out.println("Correct");
       }
       else {
           System.out.println("Wrong");
       }
   }
   ```
   (Program 1) Will print out "wrong" because the "==" compares addresses rather than what the address points to.

   (Program 2) Will print out "correct" because the .equals goes to where the address points and compares the actual values.
   
### 4. Does the below program change the season? Why, or why not?
   ```java
   static void change_season(String str) {
       str = "Spring";
   }
   
   public static void main(final String args[]) {
       String season = "Winter";
       change_season(season);
       System.out.println("The current season is: " + season);
   }
   ```

   No, because the "season" string stays on the heap while the static method changed a separate string "str" on the stack. The change season method
   only changes the address that "str" was pointing to without changing the value of "season
   
### 5. What is the output of the main method below? Please explain.
   ```java
   public class Point {
       double x = 0;
       double y = 0;
   
       public Point(double x, double y) {
           x = x;
           y = y;
       }
   }
   ```
   ```java
   public static void main(final String args[]) {
       Point point = new Point(1, 2);
       System.out.println("X: " + point.x + " Y: " + point.y);
   }
   ```
 
   The output is X: 0, Y: 0, because when the Point method is called, the x and y values in the class point are stored on the heap. Then the point
   function changes its own values stored ont he stack. When returned, it returns the heap values, X = 0 and Y = 0;

### 6. What principle of OOP does the private declaration for variable and functions achieve? Explain.
   The private declaration hides the information from people and functions that don't have access to it, i.e. encapsulation.

### 7. In the Point class below, how does Java choose between the two constructors.
   ```java
   public class Point {
   
      private double x, y; 
      
      public Point(double x, double y) {
           this.x = x;
           this.y = y;
      }
   
      public Point(Point other) {
          this.x = other.getX();
          this.y = other.getY();
      }
   
   }
   ```
   The first Point because it goes to the method that matches the input variables, if 2 ints were input, the first method is chosen.

### 8. For the below questions, when the class Point is referenced, we are talking about the below class, which you can assume is fully implemented and working as described:
   Option 4 because we declare our own variables, use public methods, and set the x and y to the negative corresponding values. 

### 9. If we add this constructor to CustomPoint:
   ```java
    public CustomPoint() {
           setXY(10, 10); // Line 1
           super(0, 0); // Line 2
       }
   ```
   …and then run this program, what is the output?
   
   ``` java
   public static void main(final String args[]) {
           CustomPoint p = new CustomPoint();
           System.out.println(p.toString());
       }
   ```
   The program won't compile because the super line must be the first line in the method

### 10. What if we switch line 1 and 2 in the previous question?
   If we swicthed the lines so that the "super" line is first, then the program would give the expected output i.e. (10,10).

### 11. If we want to override sum_x_y in our custom point, but first reflect the point before returning the sum, which of the following implementations are valid? (Note: assume that reflect has a valid implementation)
   ```java
   //Option 1
       public double sum_x_y() {
           this.reflect()
           return super.sum_x_y();
       }
   
       //Option 2
       public double sum_x_y() {
           this.reflect();
           return this.getX() + this.getY();
       }
   
       //Option 3
       public double custom_sum_x_y() {
           this.reflect()
           return super.sum_x_y();
       }
   
       //Option 4
       public double custom_sum_x_y() {
           this.reflect();
           return this.getX() + this.getY();
       }
   ```
   Explain your answer.

   Option 2. Can't change the name of the method, and super cannot be in the second line of the method. Option 2 is the only one that works.

### 12. What is the point of the protected modifier? Why do we have it and how does it work in terms of inheritance?
   To allow for the beneifits of a private method with easy access. The protected modifier allows for the inheritance methods to access the protected variables. 

### 13. Consider the following class
   ```java
   public class Racecar {
   
       private int number; 
       private Driver driver; //assume implemented properly
       protected String sponsor = null;
       public Racecar(int n, Driver d) {
           number = n;
           driver = d;
       }
   
       public String toString() {
           return "Car #" + number + " Driver: " + driver;
       }
       
       protected addSponsor(String sp) {
           sponsor = sp;
       }
   }
   ```
   Suppose we want to extend this to a FormulaOne class which has a make, e.g., Mercedes. Complete the constructor and toString() method.
   ```java
   public class FormulaOne extends Racecar {
       private String make;
   
       //TODO

       public FormulaOne(int n, Driver d, String make){
          super(n, d);
          this.make = make;     
       }

       public String toString(){
          return super.toString() + "Make" + FormulaOne;
       }

   }
   ```
### 14. Using the Racecar and FormulaOne classes above, if we had a main method in a different class than either of those,
   ```java
   public static void main(String args[]) {
   
   
      Racecar r = new Racecar(/* ... some args .. */);
      r.addSponsor("Home Depot"); //<--A
   
      FormulaOne f1 = new FormulaOne(/* ... some args .. */);
      f1.addSponsor("Home Depot"); //<--B
        
   }
   ```
   Does the code work at mark A or mark B or neither? Explain.

   Neither A nor B will work because we are trying to call "addSponsor" while that method is protected. Thus, we cannot access it.

### 15. Consider the UML diagram from the notes. Expand this to include an intern. An intern is like an employee, has a manager, unit, but has an expiration on their employment. How does this fit into the UML diagram?

   Include your UML diagram and explanation below in this markdown file.
