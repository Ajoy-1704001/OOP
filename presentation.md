# Object Oriented Programming
Object Oriented Programming (OOP) is a programming paradigm that can model real world scenarios using class and object. Class and Object are the two main buddies of Object Oriented Programming.

## Class & Object
Class can be think as a blueprint or building block. It consists of data members and some functions. Example: Mobile can be considered as a class which have attributes like brand name, color, version etc. and functionalities are calculating, taking picture, calling, messaging etc. As said before, we can model anything around us using object oriented programing.
If class is the definition of our model, then objects are the instance of the model. Objects are physical entity that contains data attribute and it's own functionality. Object needs class to follow the blueprint. When we create an instance of the object, it occupies some memory. Without creating object, class is useless. Example: Iphone 10, Pixel 6, Huwaei pro, etc. are the objects of Mobile class. Audi, Nissan, Volvo, etc. are object of Car class.

<img src="https://github.com/Ajoy-1704001/OOP/assets/57573642/67601eed-8b99-431d-a489-0f15b2eee670" width=70% height=60%> 

>Image Reference: https://www.analyticsvidhya.com/

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

<img src="https://github.com/Ajoy-1704001/OOP/assets/57573642/9ac1b25f-2908-4a39-a775-1f203a6f772b" width=70% height=60%> 

>Image Reference: [Java – What are Access Modifiers? - Simple2Code](https://simple2code.com/java/access-modifiers-in-java/)


## Fundamental Principle of OOP
### Encapsulation

<img src="https://github.com/Ajoy-1704001/OOP/assets/57573642/11fbd334-84d9-4163-af4d-e584598bb0b7" width=40% height=40%> 

>Image Reference: [Educative](https://www.educative.io/) 

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
        Mobile iphone = new Iphone();
        iphone.showMessage();
        
        Mobile pixel = new Pixel();
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
So, we can see that, **takePicture(parameters)** function is overloaded. This is method of static polymorphism.


# Case Study

## 1. Encapsulation and Abstraction

Encapsulation and Abstraction both come from the concept of Data hiding which is very essential in Object Oriented Programming. Data hiding refers to the concept of hiding the inner logic of a class and simply providing an interface through which the outside world can interact with the class without knowing what’s going on inside. One class doesn't need to know anything of another class inner logic which makes the system more reliable and secure. So, how Encapsulation and Abstraction achieves data hiding?

### Encapsulation
Encapsulation is basically binding the data and methods in a single unit. Encapsulation is normally done to hide the state and representation of an object from outside world. It protects object(including data and methods) from unwanted access using different access modifiers such as public, private, protected and default. By convention, we use private access modifier for the data members and public access modifer for the methods to provide interface for outside communication. 
Example: In the below code example, we created a class **Iphone** and the data members are declared private.
```java
class Iphone{
    private int version;
    private String macAddress;

    public Iphone(int version, String macAddress) {
        this.version = version;
        this.macAddress = macAddress;
    }
}
```
As, the data members are private, we can't access the data members outside class.
```java
  Iphone iphone = new Iphone(14, "19:21:23:23");
  System.out.println(iphone.version); //compilation error as version is not visible outside the class
```
So, we need public interface to access the data outside the class.
```java
class Iphone{
    private int version;
    private String macAddress;

    public Iphone(int version, String macAddress) {
        this.version = version;
        this.macAddress = macAddress;
    }

    public int getVersion() {
        return version;
    }

    public void setVersion(int version) {
        this.version = version;
    }

    public String getMacAddress() {
        return macAddress;
    }

    public void setMacAddress(String macAddress) {
        this.macAddress = macAddress;
    }
}
```
Using these public methods, we can access the data members.

### Abstraction
Abstraction in Object-Oriented Programming refers to showing only the essential features of an object to the user and hiding the inner details to reduce complexity. Sounds similar to the concept of Encapsulation, right? Let's go through some example.

Example: An UI designer designs an interface which contains three buttons which have unique functionality. As a user, I know what these three buttons do which I have learned from the UI designer. The developers know what is the logic behind those three working buttons. So, the main point is that UI designer is providing us the abstract view where Implementation details are hidden. The abstract view is representing **What it does** and hides **How it does**. Only developers know how the inner workings are done. This is what Abstraction is all about.

But as we know, developer must need tools, database(username, password) etc. for performing the inner workings. And, for system security, developers want to hide the required information to perform the inner workings. So, here comes the concept of encapsulation. Developer represents **How it does**, but hides **what does it uses to implement**(i.e: database password, enviroment variables etc.).

```java
abstract class Mobile{
    public abstract void showStartUpMessage();
    public void call(String number){
        System.out.println("Calling "+number+"......");
    }
}

class Iphone extends Mobile{
    private String brandName;
    private long version;


    public Iphone(String brandName, long version) {
        this.brandName = brandName;
        this.version = version;
    }

    public void showStartUpMessage(){
        //other functionality
        System.out.println("Welcome to "+brandName+" "+version);
    }
}

class Pixel extends Mobile{
    private String brandName;
    private long version;


    public Pixel(String brandName, long version) {
        this.brandName = brandName;
        this.version = version;
    }

    public void showStartUpMessage(){
        //other functionality
        System.out.println("Welcome to "+brandName+" "+version);
    }
}

public class Main {
    public static void main(String[] args) {
        Mobile mobile1 = new Iphone("Iphone", 14);
        Mobile mobile2 = new Pixel("Pixel", 6);

        mobile1.showStartUpMessage();
        mobile2.showStartUpMessage();
    }
}
```
The above code shows **Mobile** is an abstract class which has an abstract method **showStartUpMessage()**. In the Main class, user only know about the **Mobile** class and it's methods. They don't know how the methods are implemented by the derived classes. This is known as Abstraction.

On the other hand, **Pixel** and **Iphone** class both have implemented the **showStartUpMessage()** function and restricted the **brandName** and **version** from access outside access. This concept is known as Encapsulation.

So, the conclusion is Encapsulation hides object details by controlling access and Abstraction creates higher level abstract view for user to tell what the object does.


## 2. Why do we need private variables?

Suppose, we have a login system where user is authenticated by it's username and password. We create a class **User** which have two member variables **username** and **password**. We declare the variables as public. As a result, any other class can easily access the sensitive user information.

```java
public class Main {
    public static void main(String[] args) {
        User user1 = new User("ajoy","12345");
        
        user1.login("ajoy","12345"); //"Logged in Successfully"
        user1.password = "54321";
        user1.login("ajoy","12345"); //"Login not Successful"
    }
}
class User{
    public String userName;
    public String password;
    
    public User(String theUserName, String thePassword){
        userName = theUserName;
        password = thePassword;
    }
    
    public void login(String theUserName, String thePassword){
        //functionality
        if(userName==theUserName && password==thePassword){
            System.out.println("Logged in Successfully");   
        }else{
            System.out.println("Login not Successful");   
        }
    }
}
```
As we can see, user password is manipulated from main class which leads to unsuccessful authentication. If we declare these variable private, these variable can be only accessible inside it's own class. So, it ensures data integrity. It is also a representaion of encapsulation.
So, above example can clearly identifies the need of private variables.


## 3. Why we need getter and setter?

Getter and Setter are generally used for accessing restricted fields. But it is not always necessary. It has some use cases. Let's discuss them one by one:

1. Sometimes, we declare member variables as private and we need to access the variables from other class. We can use getter to access the variable.
2. Creating an object and modifying the member variable can cause exception. So, before assigning a value, we must allow validation process. In this case, we can write our custom code in setter method.

```java
private int index;

public void setIndex(int id){
  if(id>0){
    this.index = id;
  }else{
    this.index = 0;
  }
}
```

3. When we want a variable to be read only, we can use getter method and ommiting setter method so that it can be access from outside the class.
4. Debugging can be easy if we use getter/setter as we know the only way to manipulate the object is the setter method. So, in case of any accidental modification, we can find out the bug.

## 4. Is code reusability the only purpose of Inheritance?
Inheritance makes the code reusable. Let's consider we have a class named **BankAccount** and now we want to add another banking option in our system. Suppose we want to add "Super Saver Account". So, rather than implementing the **SuperSaver** class from scratch, we can extend the existing **BankAccount** class as a starting point and reuse its attributes that are common to both.
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
class SuperSaver extends BankAccount{
    private int year;

    public SuperSaver(int y){
        year = y;
    }
    public String getInformation(){
        return getName()+", "+getAccountNumber();
    }
}
class Main{
    public static void main(String[] args) {
    SuperSaver sAccount = new SuperSaver(10);
    System.out.println(sAccount.getInformation());
  }
}
```
Along with code reusabilty, we can achieve another benefit called extensibility. Suppose, we eant to extend the functionality of a class by creating a subclass that inherits its properties and methods. But, now we want to update or modify an existing feature without changing the main codebase. So, Using Inheritance promotes flexibility and adaptability in our code, as we can easily modify the behavior of objects without modifying the parent class.
Example:
```java
class SuperSaver extends BankAccount{
    private int year;

    public SuperSaver(int y){
        year = y;
    }
    public String getInformation(){
        //return getName()+", "+getAccountNumber();// old code
        return "Welcome to Bank!!\n"+getName()+", "+getAccountNumber();
    }
}
```
As, we can see, inheritance also provide us the opportunity increase extensibility of our system. Moreover, base class can keep some data private so that it cannot be modified by the derived class. So, it also provides the benefit of encapsulation.

## 5. When to use Interface and Abstract Class?

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
From above code example, we can see that an abstract class can contain both the abstract and non-abstract class. Moreover, Abstract can also have constructor. So, if we want to initialize the member(if any) of abstract class before the instantiation of a subclass actually takes place, we must invoke the constructor of abstract class in subclass. Suppose, our abstract class have some fields which are non-finals, non-static which need some initialization. Abstract class can't be instantiated but it's data member can be initialized using the constructor which will be common for all the subclasses. Example:
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

