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

    public Student getStudent() {
        System.out.println("Student: " + name + " from " + dept);
        return new Student();
    }
}

class Teacher extends User {
    int employeeId;
    String subject;
    double salary;

    public void getTeacherDetails() {
        System.out.println("Teacher: " + name + " teaches " + subject);
    }
}

public class Main {
    public static void main(String[] args) {
        Student st = new Student();
        st.name = "Rahul;
        st.dept = "CS";
        st.getStudent();

        Teacher prof = new Teacher();
        prof.name = "Dr. Smith;
        prof.subject = "Java OOP";
        prof.getTeacherDetails();
        
    }
}

```

**Inheritance** can fix a great amount of code duplication problem.