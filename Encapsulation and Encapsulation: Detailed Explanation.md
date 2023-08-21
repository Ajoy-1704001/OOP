# Encapsulation and Abstraction: Detailed Documentation

Encapsulation and Abstraction both come from the concept of Data hiding which is very essential in Object Oriented Programming. Data hiding refers to the concept of hiding the inner logic of a class and simply providing an interface through which the outside world can interact with the class without knowing what’s going on inside. One class doesn't need to know anything of another class inner logic which makes the system more reliable and secure. So, how Encapsulation and Abstraction achieves data hiding?

## Encapsulation

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

## Abstraction
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



