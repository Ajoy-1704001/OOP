# Object Oriented Programming
Object Oriented Programming(OOP) is a programming paradigm that can model real world scenarios using class and object. Class and Object are the two main buddies of Object Oriented Programming.

## Class & Object
Class can be think as a blueprint or building block. It consists of data members and some functions. Example: Human can be considered as a class which have attributes like name, age, hair color etc. and functionalities are walking, sleeping, eating etc. As said before, we can model anything around us using object oriented programing.
If class is the defination of our model, then objects are the instance of the model. Objects are physical entity that contains data attribute and it's own functionality. Object needs class to follow the blueprint. When we create an instance of the object, it occupies some memory. Without creating object, class is useless. Example: We all are the objects of human class. Like I have my own name, age, hair color etc. and I can also perform several tasks.

## Fundamental Features of OOP
### Encapsulation
Let's think about a capsule. It is a unit which contains and binds all of it's important elements. We don't know the inside material of it. In OOP, we can think class as a capsule which binds data members and methods together so that we can control the access right of the data members. When we encapsulate a class, objects of other class needs special requirement to access the data. That special requirement depends on the access modifier. By convention, we use private access modifier for data members so that objects from other class can't access it.
Example:
'''java
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
'''

