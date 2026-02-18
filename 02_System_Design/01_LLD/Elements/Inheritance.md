parent -> child

It is the process where one class acquires the properties (variables) and behaviors (methods) of another class
Inheritance is about **Reusability**

### The Key Players

1. **Superclass (Parent):** The class whose features are inherited. (Example: `Animal`)
    
2. **Subclass (Child):** The class that inherits the features. (Example: `Dog`)
    
3. **The Keyword:** In Java, we use the keyword **`extends`**.

### Why use Inheritance?

- **Code Reusability:** You write the common code once in the Parent class, and all Child classes use it automatically.
    
- **Method Overriding:** You can change how a specific child performs an action (like we did with `draw()`).
    
- **Structure:** It helps organize your code into a logical "Family Tree."

```
class Shape {
    String color;

    void setColor(String color) {
        this.color = color;
    }

    void displayColor() {
        System.out.println("The color is: " + color);
    }
}

class Circle extends Shape {
    double radius;

    void draw() {
        System.out.println("Drawing a " + color + " circle.");
    }
}

public class Main {
    public static void main(String[] args) {
        Circle myCircle = new Circle();
        
	        myCircle.color = "Red"; 
        myCircle.displayColor(); 
        myCircle.draw();
    }
}
```


2nd example:

```
class User {
    String name;
    int age;
    String add;

    public User getUserByName(String name) {
        System.out.println("Searching for User: " + name);
        return new User(); 
    }
}

class Student extends User {
    int sid;
    String dept;
    int rank;

    public Student getStudent() {
        System.out.println("Student Details: " + name + ", " + age + ", " + add);
        
        User currUser = getUserByName(this.name);
        
        return new Student();
    }
}

public class Main {
    public static void main(String[] args) {
        Student st = new Student();
        
        st.name = "Rahul";
        st.age = 22;
        st.add = "Mumbai, India";
        
        st.sid = 101;
        st.dept = "Computer Science";
        
        st.getStudent();
    }
}

```