
## Encapsulation
	Encapsulation in Java is a mechanism to wrap data (variables) and methods that operate on the data into a single unit (class).
	The variables are declared as private



### Sealed class
- it is used when the class needs only to be extended by certain specific classes
- it uses`permit` keyword to allow specific classes
```java
public sealed class parent permits child, grandchile{

}
```

## Nested classes
- types
	- Static nested classes
		- classes inside a static class
	- non-static nested classes
		- member inner class
		- local inner class
			- defined within a method / constructor of a class
		- anonymous inner class
			- declared without a name, used for a short time 
