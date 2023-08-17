# Object Oriented Programming
Object Oriented Programming(OOP) is a programming paradigm that can model real world scenarios using class and object. Class and Object are the two main buddies of Object Oriented Programming.

## Class & Object
Class can be think as a blueprint or building block. It consists of data members and some functions. Example: Human can be considered as a class which have attributes like name, age, hair color etc. and functionalities are walking, sleeping, eating etc. As said before, we can model anything around us using object oriented programing.
If class is the defination of our model, then objects are the instance of the model. Objects are physical entity that contains data attribute and it's own functionality. Object needs class to follow the blueprint. When we create an instance of the object, it occupies some memory. Without creating object, class is useless. Example: We all are the objects of human class. Like I have my own name, age, hair color etc. and I can also perform several tasks.

## Fundamental Features of OOP
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
Here, both **Iphone** and **Pixel** inherits setName() method from **Mobile** class.

**Multiple Inheritance:** Sometimes, we need to inherit data members and methods from multiple classes. So, derived class may have multiple parent class. This is called Multiple Inheritance. Java doesn't support multiple inheritance because of ambiguity problem. Suppose, we have two class named **Software** and **Hardware**. Both of the classes have a public method named **connect()**. Now we want to derive a new class named **Embedded** from Software and Hardware class which will inherit the **connect()** method. But, the problem is, java compiler can't figure out which **connect()** method it should inherit. This is the ambiguity problem. To overcome this problem, we generally use **interface**.
>**Important** How interface support multiple inheritance? The answer is: Regular classes generally implements the method within the class body. In case of interface, the method implementation is provided by the implementation class (that class which is implementing the interface). That's why there is no ambiguity in case of performing a specific method as each class has it's own implementation.

Example:
