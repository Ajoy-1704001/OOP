# Object Oriented Programming
Object Oriented Programming (OOP) is a programming paradigm that can model real world scenarios using class and object. Class and Object are the two main buddies of Object Oriented Programming.

## Class & Object
Class can be think as a blueprint or building block. It consists of data members and some functions. Example: Mobile can be considered as a class which have attributes like brand name, color, version etc. and functionalities are calculating, taking picture, calling, messaging etc. As said before, we can model anything around us using object oriented programing.
If class is the defination of our model, then objects are the instance of the model. Objects are physical entity that contains data attribute and it's own functionality. Object needs class to follow the blueprint. When we create an instance of the object, it occupies some memory. Without creating object, class is useless. Example: Iphone 10, Pixel 6, Huwaei pro, etc. are the objects of Mobile class.

### Access Modifiers
In java, there are some modifier tags which is used to impose restrictions on data member and methods. They are **Private**, **Public**, **Protected** and **Default**.

**Private:** A private member can't be directly access outside the class. It is used to hide class members from other classes. Example:
```java
class Mobile{
    private int buildVersion;
    public Mobile(int version){
        buildVersion = version;
    }
}
class Main{
    public static void main(String[] args) {
        Mobile mobile = new Mobile(5);
        System.out.println(mobile.buildVersion); //Error: Can't access the buildVersion
    }
}
```
So, in this case, we can't access the variable **buildVersion** outside the class.

**Public:** A public member can be access directly by anything which is in the same scope as the class object. The above code will compile and run successfully if we declare the **buildVersion** variable as public.

**Protected:** Protected members have package level access. That means, we can't access a protected member of any class if the class is not defined in the same package scope. But if we inherit the class, then we can acess it through derived class from any package. Example:
```java
package mobile;
public class Iphone {
  private int version;
  public int getVersion(){
    return version;  
  }
  protected void display(){
    System.out.println("welcome!");
  }
}
```
```java
package hardware;  
import mobile.*; 
class Hardware{  
  public static void main(String args[]){  
   Iphone obj = new Iphone();  
   obj.display();     //Compile Time Error  
  }  
} 
```
Here, we can see that protected member **display()** from package mobile can not be accessed in package hardware.

**Default:** If we do not declare any access modifier, then it is considered as default modifier. It has similarity with protected modifier, but it can't be accessed through inherited class. 


## Fundamental Principle of OOP
### Encapsulation
Let's think about a capsule. It is a unit which contains and binds all of it's important elements. We don't know the inside material of it. In OOP, we can think class as a capsule which binds data members and methods together so that we can control the access right of the data members. When we encapsulate a class, objects of other class needs special requirement to access the data. That special requirement depends on the access modifier. By convention, we use private access modifier for data members so that objects from other class can't access it.
Example:
```java
public class Human {
    private String name;
    private int age;

    public Human() {
    }

    public Human(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    } 
}
```
In this case, we can't directly access any data member from other classes. We must use public methods(for above example, getter/setter) if want any specific data. Another example: NSL have some confidential employee data which you want to access. As per rule, you can't access the data directly. You must get it through any of the official persons. So these official person working here as a public methods.

### Inheritance
Sometimes we want to create a class which should have some common attributes. In this case, we may write the common things again and again for the same class. Example: I have an account in a bank. Now I want to open a Super Saver Account. Those two account may vary by some advantages and functionality, but both need some common information like my name, mobile no, gender, nid no etc. So to model these account in object oriented programming, we have a feature called inheritence. Example:
```java
class BankAccount{
    private String name;
    private String accountNumber;
    private int balance;

    public BankAccount(){
        name = "Ajoy";
        accountNumber = "0012-12111212";
        balance = 2000;
    }

    public String getName() {
        return name;
    }
    public String getAccountNumber() {
        return accountNumber;
    }
    public int getBalance() {
        return balance;
    }
}
```
So this is the class that we have already in the bank. We want to create another class called SuperSaver. So to avoid redundant code, we can simply inherit the class from the BankAccount class. To inherit a class, we use **extends** keyword with the derived class and then the parent class name comes;

```java
class SuperSaver extends BankAccount{
    private int year;

    public SuperSaver(int y){
        year = y;
    }

    public String getInformation(){
        return getName()+", "+getAccountNumber();
    }
}
public static void main(String[] args) {
    SuperSaver sAccount = new SuperSaver(10);
    System.out.println(sAccount.getInformation());
}
```
As we can see, **SuperSaver** class inherited the public members of BankAccount class. So, SuperSaver Account is the derived/child class and **BankAccount** is the Base class/Parent class. Only public and protected data members and methods can be inherited. Private methods are not allowed to inherit from base class.

There are generally 5 types of Inheritance. Such as:
1. Single Inheritance
2. Multi-level Inheritance
3. Hierarchical Inheritance
4. Multiple Inheritance
5. Hybrid Inheritance

We have already discussed the concept of **single inheritance** in the above code.

**Multi-level Inheritance:** Suppose, we have a Iphone class which is our parent class. From Iphone class, we derive another class called Iphone14. From class Iphone14, we can derive class Iphone15 and so on. So this is called multi-level inheritance.
Example:
```java
class Iphone {   //base class
  private int version;
  public void setVersion(int version) {
    this.version=version;
  }

  public int getVersion(){
    return version;
  }  
}

class Iphone14 extends Iphone { // Derived from Iphone class
  public void feature(){
    System.out.println("This phone has dynamic island feature.");
  }
} 

class Iphone15 extends Iphone14 {// Derived from Iphone14
  public void printVersion(){
    System.out.println("This is Iphone "+getVersion()); 
  } 
}
```
So now, we can create a object of Iphone15 and which have the priviliege of both getVersion() of **Iphone** class and feature() of **Iphone14** class. Here is the main function:

```java
public class Oop {
  public static void main(String[] args) {
    Iphone15 iphone = new Iphone15(); 
    iphone.setVersion(15);
    iphone.feature();
    iphone.printVersion();
  }
}
```
**Hierarchical Inheritance:** When more than one class inherits from the base/parent class, that is called Hierarchical Inheritance. That means, multiple class can extend the base class for it's own purpose.

Example:
```java
class Mobile{
    private String brand;

    public void setName(String brand) {
        this.brand = brand;
    }
}

class Iphone extends Mobile{
    public Iphone(){}
    // Other attributes and methods
}

class Pixel extends Mobile{
    public Pixel(){}
    // Other attributes and methods
}

class MobileOOP {
    public static void main(String[] args) {
        Iphone iphone = new Iphone();
        Pixel pixel = new Pixel();

        iphone.setName("Apple");
        pixel.setName("Google");
    }
}
```
Here, both **Iphone** and **Pixel** inherit setName() method from **Mobile** class.

**Multiple Inheritance:** Sometimes, we need to inherit data members and methods from multiple classes. So, derived class may have multiple parent class. This is called Multiple Inheritance. Java doesn't support multiple inheritance because of ambiguity problem. Suppose, we have two class named **Software** and **Hardware**. Both of the classes have a public method named **connect()**. Now we want to derive a new class named **Embedded** from Software and Hardware class which will inherit the **connect()** method. But, the problem is, java compiler can't figure out which **connect()** method it should inherit. This is the ambiguity problem. To overcome this problem, we generally use **interface**.
>**Important** How interface support multiple inheritance? The answer is: Regular classes generally implements the method within the class body. In case of interface, the method implementation is provided by the implementation class (that class which is implementing the interface). That's why there is no ambiguity in case of performing a specific method as each class has it's own implementation.

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
    default void verify(){  
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
We have declared two interfaces and inherited **connect()** method inside the **Embedded** class. Only default and static members can have the full implementation inside the interface. Other public/private method should be abstract, that means no implementation details. Here is the main function:
```java
public class Multiple {
    public static void main(String[] args) {
        Embedded embedded = new Embedded();
        embedded.connect();
        embedded.test();
        embedded.verify();
    }
}
```
>**Output:** ```Software connected successfully
Testing.....
Verifying.....```

**Hybrid Inheritance:** This is actually the combination of both the multiple and multi-level inheritance. This is also not supported by java because of ambiguity (diamond problem).

### Abstraction
Suppose, we want to provide a button to user which increase the brightness of the device. User only know that the button increases brightness. But, they don't know how it actually worked in the background. Because, we don't want user to know what is behind the functionality. This is known as Abstraction. Example: In Java, List, Math, Stack, etc. are Abstract Data Type.
```java
Math.sqrt(25);
```
We know the work of the sqrt() function. But don't know the actual implementation details. Abstraction can be achieved by both abstract types and interface. We have already discussed about interface. 

We must use **abstract** keyword for declaring abstract classes or methods. Abstract classes can not be instantiated. They must be inherited from other class.
Example:
```java
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
public class Abstraction {
    public static void main(String[] args) {
        Mobile mobile = new Pixel();
        mobile.play();
        mobile.close();
    }
}
```

### Difference between Abstract class and Interface
Abstract class is a class that can not have it's own object, but it can be inherited by other concrete classes and those subclass can have their object. If the subclass is a regular class, then we must implement all the abstract methods. Otherwise, it will generate compilation error. If the subclass is also an abstract class, then there is no need to implement all the abstract methods. Abstract class can have non-abstract methods and their body implementation. Abstract class can also have constructor. As abstract class can contain both abstract and regular methods, we can not achieve 100% abstraction using abstraction.
Example: (Using Abstract class)
```java
public class Main
{
    public static void main(String[] args) {
        System.out.println("Welcome to Online IDE!! Happy Coding :)");
        Chip device = new Iphone();
        device.play();
        device.stop();
    }
}

abstract class Chip{
    public abstract void play();
    public abstract void waiting();
    public void stop(){
        System.out.println("Bye!");
    }
}

class Iphone extends Chip{
    public void play(){
        System.out.println("Welcome!");
    }
    public void waiting(){
        System.out.println("waiting!");
    }
}
```
Interface class can not have it's own object like abstract class. Regular and abstract classes can implement interfaces (even more than one). If the subclass is regular class, then it is a must to implement all the methods inside subclass. If the subclass is abstract class, then it is not mandatory to implement all the methods. The other subclass that inherits the abstract class, it's his duty to implement all the methods. Interface can't have constructor and methods can't be declared as private. Interface can also have static or default methods with it's implementation. Interface can have static/constant attributes.
Example: (Using Interface)
```java
public class Main
{
    public static void main(String[] args) {
        System.out.println("Welcome to Online IDE!! Happy Coding :)");
        Chip device = new Iphone();
        device.play();
        device.stop();
    }
}

interface Chip{
    public void play();
    public void waiting();
    public default void stop(){
        System.out.println("Bye!");
    }
}

class Iphone implements Chip{
    public void play(){
        System.out.println("Welcome!");
    }
    public void waiting(){
        System.out.println("waiting!");
    }
}
```
### Polymorphism
When same object shows different forms and behaviour, we refer this as polymorphism. What happens if one of the methods of derived class needs different type of implementation rather than the one mentioned in the parent class? Polymorphism allows us to write multiple definitions of a method. This improves code readabilty and inheritance allows code reusability. Polymorphism are of two types:
1. Static Polymorphism
2. Dynamic Polymorphism

Example: We have "Mobile" class and two derived class such as "Iphone" and "Pixel". "Mobile" class contains a method "showMessage()" which is inherited by both the derived classes. But each of the derived class have different message to show. So, they overrides the message.
```java
class Mobile{
    public void showMessage(){
        //Other functionality
        System.out.println("This is a basic startup message!");
    }
}

class Iphone extends Mobile{
    public void showMessage(){
        //Other functionality
        System.out.println("Welcome to Iphone!");
    }
}

class Pixel extends Mobile{
    public void showMessage(){
        //Other functionality
        System.out.println("Welcome to Google Pixel!");
    }
}

public class Main
{
    public static void main(String[] args) {
        Iphone iphone = new Iphone();
        iphone.showMessage();
        
        Pixel pixel = new Pixel();
        pixel.showMessage();
    }
}
```
So, this is how function overriding works. This is the example of Dynamic polymorphism. Dynamic polymorphism is also known as runtime polymorphism as compiler detects the overriden method in runtime.
Sometimes, we use same name for different methods which performs quite similar task. That increases code reusability and saves memory. This is known as method overloading or static polymorphism or compile time polymorphism. As the functions are same with different parameters or return type, compiler can easily detect it during compile time. Example: We want to update an existing feature in our class "Iphone". So, to avoid unnecessary modification in the function, we can simply overload the fucntion, and  write our code. Example:

```java
class Iphone{
    public void takePicture(double depth){ //old method
        //other functionality
        System.out.println("Taking picture!!! depth:" + depth);
    }
    public void takePicture(double depth, int brightness){ //new method
        //other functionality
        System.out.println("Taking picture!!! depth:" + depth+" , brightness:"+brightness+"%");
    }
}
public class Main
{
    public static void main(String[] args) {
        Iphone iphone = new Iphone();
        iphone.takePicture(3.5);
        
        iphone.takePicture(3.5,90);
    }
}
```
So, we can see that, takePicture(parameters) function is overloaded. This is method of static polymorphism.


