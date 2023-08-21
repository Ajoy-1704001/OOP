## Why do we need private variables?

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


## Why we need getter and setter?

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
