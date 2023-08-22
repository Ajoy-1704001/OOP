# Class Relationship
Class relationship refers to relation between two or more classes. Relationships are needed to use the feature of one class to another or to create a special communication between classes. Like, there is a special relation between **Electronic** class and **TV** class. In object oriented programming, It supports four types of relationship such as Inheritance, Association, Aggregation and Composition. These relations are based on **Is-A*** relation, **Has-A** relation and **Part-of** relation. 

### Is-A Relation
When one class is a type of another class and can inherit the common attributes, that is know as **Is-A** relation. Example: **Iphone** is a **Mobile**. But we can't say, Mobile is a Iphone. Another example can be: Cow is an Animal. But "An animal is a cow" can't be possible since all animals are not cow. So, from this we can understand that **Is-A** relation is unidirectional. We can represent Is-A relaton simply by an unidirectional arrow. Inheritance follows the is-a relationship.

<img src="https://github.com/Ajoy-1704001/OOP/assets/57573642/30666ec8-7e8c-4346-8cbf-3b6c6a7269fc" width=50% height=50%>

### Has-A Realtion
Let, **Class A** and **class B** have a has-a relationship if one or both need the other’s object to perform an operation, but both class objects can exist independently of each other. This is actually a one way ownership. Example: **Student** has an **Address**. But, it is not neccesary that each address contains a student. So, here **Student** is the owner entity. Student class owns the Address Object. So, arrow will be towards the owner entity and arrow head will be a diamond shape.

<img src="https://github.com/Ajoy-1704001/OOP/assets/57573642/ccfd6c69-89ba-411d-a75f-0b6fba7a5864" width=50% height=50%>

### Part-Of Relation
Suppose, we have an **Mobile** and we need **Chip**,**Battery** and **Storage**. So, **Chip**,**Battery** and **Storage** are part of **Mobile**. So, the components will be only available when we have the **Mobile**. And also **Mobile** is dependent on the components. So, we can see there is interdependency between Mobile and other components.

<img src="https://github.com/Ajoy-1704001/OOP/assets/57573642/f65a505f-1061-40af-b11f-45b8b40064b4" width=50% height=50%>

## Association

Association is a relation between two separate classes through their Objects. Association is the common term used for both the **has-a** and **part-of** relationships but is not limited to these. Association relationship can be one to one, One to many, many to one and many to many. Suppose, we have a **Teacher** class and **Student** class. A single student can associate with multiple teachers and a teacher can handle multiple students. And also both the student and teacher can be independent. Again, A person can one national id card. This is also falls under association relationship. So, it can be both unidirectional and bidirectional.

Example:
```java
import java.util.ArrayList;
import java.util.List;

class Teacher
{
    private String name;
    private List<Student> students;

    public Teacher(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public List<Student> getStudents() {
        return students;
    }

    public void setStudents(List<Student> students) {
        this.students = students;
    }

    
  
}
class Student
{
    private String name;
    Student(String name)
    {
        this.name = name;
     }
    public String getName() {
        return name;
    }
}
public class Association
{
  public static void main (String[] args){
        Teacher teacher = new Teacher("Sudeb Paul");
        Student student1 = new Student("Ajoy Deb Nath");
        Student student2 = new Student("Bijoy Deb Nath");
    
        List<Student> students = new ArrayList<>();
        students.add(student1);
        students.add(student2);
        teacher.setStudents(students);
    }
}
```
In this case, we have an association of one to many in the above code. Teacher class have a list of student objects.
However, There are specialized form of Association. Such as:
1. Aggregation
2. Composition

### Aggregation
Aggregation follows the **Has-A** relational model. It creates a relationship where one class can contain the object of anther. Example: In Neural Semiconductor, each team can have many employees. Suppose, There are can be many employees at Software team. But an employee can not be under multiple team. So, this is an one way association. We can also notice that both **Team** and **Employee** can be independent which means destroying any of the entity or class will not affect the other one.
Example:
```java
public class Aggregation {
    public static void main(String[] args) {
        Team team = new Team("Software");
        {
            Employee employee = new Employee("Ajoy", team); //Inside the scope
            System.out.println(employee);
        } // out of this scope
        System.out.println(team); // The Team object still exists!
    }
}


class Team {
  
    private String teamName;

    public Team(String n) {
      teamName = n;
    }

    public String getTeamName() {
        return teamName;
    }

    @Override
    public String toString() {
        return "Team [teamName=" + teamName + "]";
    }

    
  
}
class Employee {
  
    private String name;
    private Team team; // An instance of Team class

    public Employee(String n, Team t) {
      name = n;
      team = t;
    }

    @Override
    public String toString() {
        return "Employee [name=" + name + ", team=" + team + "]";
    }
}
```
The output is:
>Employee [name=Ajoy, team=Team [teamName=Software]]
>Team [teamName=Software]

### Composition
Composition follows **Part-Of** relationship. In this case, Owner class owns the other class object. Suppose, Class A owns the object of class B. So, object of B will only be created when object of A is created. So, what's the difference between Aggregation and Composition? Mainly, In aggregation, we use the reference of the object in case of creating a relation. On the other hand, owned objects are created inside the owner class which results interdependency. Owned objects will be deleted if the object of owner class gets destroyed.
```java
public class Composition {
    public static void main(String[] args) {
    Mobile mobile = new Mobile("Iphone", 4000, "A15");
    mobile.printDetails();
  }
}
class Chip {
    private String version;

    public Chip(String version) {
    this.version = version;
    }

    public String getVersion() {
        return version;
    }
}

class Battery {
  
    private long power;

    public Battery(long power) {
        this.power = power;
    }
  
    public void batteryCapacity(){
        System.out.println("Battery Capacity:"+power);
    }
}

class Mobile {
    private String brandname;
    private Battery battery;
    private Chip chip;
    public Mobile(String brandname, long power, String chipVersion) {
        this.brandname = brandname;
        this.battery = new Battery(power);
        this.chip = new Chip(chipVersion);
    }

    public void printDetails(){
        System.out.println("Mobile Brand Name: "+brandname);
         System.out.println("Chip: "+chip.getVersion());
        battery.batteryCapacity();
    }
}
```
Here, we can see that we are creating the Battery and Chip objects inside the Mobile class. If, Mobile dies, other inside objects will be also dead.

