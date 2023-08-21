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

```java
public class Main {
    public static void main(String[] args) {
        Mobile mobile1 = new Iphone("Iphone", 14);
        Mobile mobile2 = new Pixel("Pixel", 6);

        mobile1.showStartUpMessage();
        mobile2.showStartUpMessage();

        mobile1.play();
    }
    
}

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
```


