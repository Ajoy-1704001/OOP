## When to use Interface and Abstract Class?

Abstraction in Object-Oriented Programming refers to showing only the essential features of an object to the user and hiding the inner details to reduce complexity. It highlights what object does rather than how it does. In java, There are two ways to obtain abstraction, such as:
1. Abstract class
2. Interface

### When to use Abstract Class:
As we know, Abstract class can have concrete methods along with abstract ones. That means we can have non-abstract methods with full implementation inside an abstract class. Example: 
```java
public class Main
{
    public static void main(String[] args) {
        Mobile mobile = new Pixel();
        mobile.play();
        mobile.close();
    }
}

abstract class Mobile{
    public abstract void play();
    public void close(){
        System.out.println("System is shutting down.");
    }
}

class Pixel extends Mobile{
    public void play(){
        System.out.println("Welcome to Pixel!!!");
    }
}
```
From above code example, we can see that an abstract class can contain both the abstract and non-abstract class. Moreover, Abstract can also have constructor. So, if we want to initialize the member(if any) of abstract class before the instantiation of a subclass actually takes place, we must invoke the constructor of abstract class in subclass. Suppose, our abstract class have some fields which are non-finals, non-static which need some initialization. As abstract class can't be instantiated but it's data member can be initialized using the constructor which will be common for all the subclasses. Example:
```java
public class Main
{
    public static void main(String[] args) {
        Mobile mobile = new Iphone(14, "Iphone", "Blue");  //print: Iphone 14, Color:Blue
        Mobile mobile2 = new Pixel(6, "Pixel", "100MP");   //print: Pixel 6, Resolution:100MP
    }
}

abstract class Mobile{
    private long version;
    private String brandName;
    public Mobile(long version,String brandName){
        this.version = version;
        this.brandName = brandName;
    }
    //other abstract methods
}
class Iphone extends Mobile{
  public Iphone(long version,String brandName,String color){
    super(version,brandName);
    System.out.println(brandName+" "+version+", Color:"+color);
  }
}

class Pixel extends Mobile{
  public Pixel(long version,String brandName,String resolution){
    super(version,brandName);
    System.out.println(brandName+" "+version+", Resolution: "+ resolution);
  }
}
```
So, we can see that having constructor in abstract class, we can avoid redundancy in the subclass.
Moreover, Abstraction can't be used for multiple inheritance, because we can't extend multiple abstract classes at a time as it wll still create ambiguity due to the other concrete classes. Additionally, all abstract method must be implemented in subclass unless the subclass is abstract. 

### When to use Interface
Interface are more likely to hide unneccessary details and only show the important details of an object. Due to the advancement of java, now-a-days, interface can also have default methods. But most of the cases, interface is used as a contract that have to be fulfilled in implementing classes. Moreover, Interface is used for achieving multiple inheritance in java as we can implement multiple interface separated by comma.
Example:
```java
interface Software{
    //other methods
    default void test(){   //// Only default and static methods can have implementation details inside an interface
        System.out.println("Testing.....");
    }
    public void connect();
}

interface Hardware{
    default void verify(){   //// Only default and static methods can have implementation details inside an interface
        System.out.println("Verifying.....");
    }
    public void connect();
}

class Embedded implements Software,Hardware{
    public void connect(){
        System.out.println("Software connected successfully");
    }
}
```
We can also extend interface with another interface. Other than, all the other functionality can also be achieved by abstract class. 





