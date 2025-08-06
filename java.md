
### Memory models
- #### heap 
	- stores objects
- #### stack
	- stores local variables and method call information

### Garbage collection 
- mark and sweep is a popular method to build a user-defined garbage collector

## Encapsulation
	Encapsulation in Java is a mechanism to wrap data (variables) and methods that operate on the data into a single unit (class).
	The variables are declared as private


- Anonymous class or object or anything does utilize memory

### Anonymous class
```java
class A{

}

new A()
```



### Sealed class
- it is used when the class needs only to be extended by certain specific classes
- it uses`permit` keyword to allow specific classes
```java
public sealed class parent permits child, grandchile{

}
```

## Nested classes
- Only a nested class be a private class
- A base class being private cannot be accessed
- types
	- Static nested classes
		- classes inside a static class
	- non-static nested classes
		- member inner class
		- local inner class
			- defined within a method / constructor of a class
		- anonymous inner class
			- declared without a name, used for a short time 

### Enum 
- A special data type that enables a variable to be set of a predefined constants
- It can have methods, constructors for complex use case
- it provides type safety
```java 
public enum Day {
    SUNDAY,
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY; // Semicolon is required if you have methods/fields
}

public class EnumExample {
    public static void main(String[] args) {
        Day today = Day.MONDAY;
        System.out.println("Today is: " + today); // Output: Today is: MONDAY

        if (today == Day.SUNDAY) {
            System.out.println("It's the weekend!");
        } else {
            System.out.println("It's a weekday."); // Output: It's a weekday.
        }
    }
}
```


### Tightly Coupling
- when change in one class does force the other class to change in implementation then it is said to be tightly coupled.
- has less number of classes compared to loose coupling but 

### Loosely coupled
- when change in one class does not affect the structure of another which is using it then it is loosely coupled.
- implementation relies heavily on interface and abstract classes.
- does include more classes but end up being more flexible than tight due to its representation restrictions.

### Overriding 
- it is a case of function having the same signature of an existing function to bypass the existing function.
- in case of overriding if the functions does not have the same return type it rises an error