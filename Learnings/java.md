
  
- Java is always pass-by-value.
- Always the type is checked during the compile time.

  
### Advantages of java 8  
- Introduced lambda function  
- Introduced default and static methods in interfaces  
- Backward compatibility is mostly intact  
- most of the product or service were freely available  
  
| Aspect              | Before Java 11 (≤ Java 10)                          | After Java 11                                                    |
| ------------------- | --------------------------------------------------- | ---------------------------------------------------------------- |
| **Adoption**        | Java 8 dominant (stable, LTS)                       | Enterprises slowly moved to Java 11                              |
| **Release Cadence** | Old “every few years” releases                      | 6-month release cycle (LTS every 3 years)                        |
| **Features**        | Streams, Lambdas, Modules (Java 9), `var` (Java 10) | HTTP/2 client, new APIs, `var` for lambdas, ZGC                  |
| **Ecosystem**       | Java EE, CORBA, JavaFX still included               | Removed legacy tech, leaner JDK                                  |
| **Licensing**       | Oracle JDK free                                     | Oracle JDK requires subscription; OpenJDK & vendors fill the gap |
| **Stability**       | Java 8 considered rock-solid                        | Java 11 became next enterprise LTS target                        |
| **Migration**       | Smooth from 7 → 8, rough 8 → 9                      | 8 → 11 migration required significant refactoring                |
  
### Features of java  
- **Platform Independent**  
- **Object-Oriented**  
- **Secure**  
- **Simple**  
- **Multi-threaded**  
  
### How is it secure  
- NO direct memory access  
- automatic memory management  
- classloader security  
- bytecode verification  
- Sandbox model of execution --- is created by JVM  
- access controller  
- strong type checking  
  
### JDK  
- It provides necessary tools and environment to develop java applications,  
- includes JRE, and JVM  
  
### JRE (java runtime environment)  
- consists of JVM and compiler along with necessary standard libraries to aid in converting java file to class file.  
- This is only to run, only used by the end users of the application  
- works:  
- loads the class file  
- verify the bytecode for security  
### JVM (Java Virtual Machine)  
- also known as interpreter  
- uses JIT (just in time: converted from byte-code to machine code wile runtime) for faster execution  
- works:  
	- **loading**
	- **linking**  
	- **initialization**  
	- **garbage collection**  
- memory allocation and deallocation  
- types  
	- stack  
	- heap  
	- PC  
	- register  
### Compilation  
1. maps the source code into AST (Abstract Syntax Tree) sequentially, representing the code structure.  
2. symbols of the variable, class, and methods are entered into symbol table for reference.  
3. compiler then preforms type checking, name resolution, and constant folding from the AST.  
4. data flow analysis is done for code reachability and variable assignments.  
5. converts sugared(complex representation) code to simpler fundamental constructs.  
6. generate `.class` file  
7. Keywords are differentiated from others with the help of lexical analyzer, reserved word list and token recognition  
  
#### Symbol table  
- helps find scope of variable, type checking, verify proper calling of functions.  
- helps allocate and track memory  
  
### Execution  
- The first file to be executed is **java.exe** which is the JVM launcher.  
- stages  
- **ClassLoader  
- primordial/bootstrap classloader -- default class loader (the first special class loader that loads the bootloader class, written in machine code)  
- Loads the necessary classes required for JRE and JVM to function  
- non-primordial/extension classloader -- all the class loader other than the bootloader class. like libraries  
- user-defined classloader  
  
- **Bytecode verifier  
- checks if the code does any damaging actions  
- check for security and integrity are maintained or not  
- **JIT compiler  
  
```  
- The size of heap varies during the runtime  
- The stack size is often defined by the linker, it is private to its thread,  
- it can be manually changed in VS code  
- default windows stack size- 1mb  
- linux - 8mb  
- macos - 512kb  
```  
  
  
### Variables  
- Instance variable /non-static field ----- within a class  
- class variable / static fields ----- within a class  
- local variable ------ inside a function  
- parameters  
  
  
  
| Aspect | JDK | JRE | JVM |  
| ------------------- | ----------------------------------------------- | -------------------------------------- | -------------------------------------------------------- |  
| Purpose | Used to develop Java applications | Used to run Java applications | Executes Java bytecode |  
| Platform Dependency | Platform-dependent (OS specific) | Platform-dependent (OS specific) | JVM is OS-specific, but bytecode is platform-independent |  
| Includes | JRE + Development tools (javac, debugger, etc.) | JVM + Libraries (e.g., rt.jar) | ClassLoader, JIT Compiler, Garbage Collector |  
| Use Case | Writing and compiling Java code | Running a Java application on a system | Convert bytecode into native machine code |  
| | | | |  
  
## Naming Convention  
  
| Identifier Type | Rules for Naming | Examples |  
| --------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |  
| Packages<br><br>(all lowercase) | The prefix of a unique package name is always written in all-lowercase ASCII letters and should be one of the top-level domain names, currently com, edu, gov, mil, net, org, or one of the English two-letter codes identifying countries as specified in ISO Standard 3166, 1981.<br><br>Subsequent components of the package name vary according to an organization's own internal naming conventions. Such conventions might specify that certain directory name components be division, department, project, machine, or login names. | com.sun.eng<br><br>com.apple.quicktime.v2<br><br>edu.cmu.cs.bovik.cheese |  
| Classes<br>(noun with first letter capital) | Class names should be nouns, in mixed case with the first letter of each internal word capitalized. Try to keep your class names simple and descriptive. Use whole words-avoid acronyms and abbreviations (unless the abbreviation is much more widely used than the long form, such as URL or HTML). | class Raster; <br>class ImageSprite; |  
| Interfaces<br>(first letter capital) | Interface names should be capitalized like class names. | interface RasterDelegate; <br>interface Storing; |  
| Methods<br> | Methods should be verbs, in mixed case with the first letter lowercase, with the first letter of each internal word capitalized. | run(); <br>runFast(); <br>getBackground(); |  
| Variables | Except for variables, all instance, class, and class constants are in mixed case with a lowercase first letter. Internal words start with capital letters. Variable names should not start with underscore _ or dollar sign $ characters, even though both are allowed.<br><br>Variable names should be short yet meaningful. The choice of a variable name should be mnemonic- that is, designed to indicate to the casual observer the intent of its use. One-character variable names should be avoided except for temporary "throwaway" variables. Common names for temporary variables are `i`, `j`, `k`, `m`, and `n` for integers; `c`, `d`, and `e` for characters. | int i;<br><br>char c;<br>float myWidth; |  
| Constants<br>(All caps with underscore btwn words ) | The names of variables declared class constants and of ANSI constants should be all uppercase with words separated by underscores ("_"). (ANSI constants should be avoided, for ease of debugging.) | static final int MIN_WIDTH = 4;<br><br>static final int MAX_WIDTH = 999;<br><br>static final int GET_THE_CPU = 1; |  
  
### Packages  
| Need | |  
| ------------------------------------------------------------------------ | --- |  
| Modularity<br>to avoid naming clash between classes<br>code Organization | |  
| | |  

  
  
  
## keywords  
| Category | Keywords |  
| ---------------- | --------------------------------------------------------------------------------- |  
| Data Types | byte, short, int, long, float, double, boolean, char |  
| Access Modifiers | public, private, protected |  
| Control Flow | if, else, switch, case, default, while, do, for, break, continue, return |  
| Error Handling | try, catch, finally, throw, throws |  
| Object-Oriented | class, interface, extends, implements, this, super |  
| Memory/Threads | new, static, final, abstract, synchronized, volatile, transient, native, strictfp |  
| Other Useful | instanceof, import, package, assert, enum, void |  
| | |  
  
- ### Default keyword  
- ==**`default`**== keyword can only be used in two places  
- switch case  
- [[#Interface]]  
  
## Access modifiers  
  
| Context | Default | Private | Protected | Public |  
| ------------------------------ | ------- | ------- | --------- | ------ |  
| Same Class | Yes | Yes | Yes | Yes |  
| Same Package Subclass | Yes | No | Yes | Yes |  
| Same Package Non-Subclass | Yes | No | Yes | Yes |  
| Different Package Subclass | No | No | Yes | Yes |  
| Different Package Non-Subclass | No | No | No | Yes |  
- both static method and variable  
- are given memory only once at the time of class loading  
- are shared resource across all the objects  
- can directly accessed with the class name, doesn't require an object  
  
  
## Java Structure  
- Package declaration  
- import statements  
- class definition  
- class variables  
- class constructor  
- methods  
- main method  
  
### Data Types  
  
| Type | Description | Default | Size | Example Literals | Range of values |  
| ------- | ------------------------------ | ------- | -------------------------------- | ------------------------------------------- | ------------------------------------------------------------- |  
| boolean | true or false | false | JVM-dependent (typically 1 byte) | true, false | true, false |  
| byte | 8-bit signed integer | 0 | 1 byte | (none) | -128 to 127 |  
| char | Unicode character(16 bit) | \u0000 | 2 bytes | 'a', '\u0041', '\101', '\\', '\', '\n', 'β' | 0 to 65,535 (unsigned) |  
| short | 16-bit signed integer | 0 | 2 bytes | (none) | -32,768 to 32,767 |  
| int | 32-bit signed integer | 0 | 4 bytes | -2,0,1 | -2,147,483,648<br>to<br>2,147,483,647 |  
| long | 64-bit signed integer | 0L | 8 bytes | -2L,0L,1L | -9,223,372,036,854,775,808<br>to<br>9,223,372,036,854,775,807 |  
| float | 32-bit IEEE 754 floating-point | 0.0f | 4 bytes | 3.14f, -1.23e-10f | ~6-7 significant decimal digits |  
| double | 64-bit IEEE 754 floating-point | 0.0d | 8 bytes | 3.1415d, 1.23e100d | ~15-16 significant decimal digits |  
  
### Primitive types  
- these are reserved keywords defined by **Java Language Specification(JLS)**  
- These are supported directly by JVM  
- ON initialization the value are directly stored not stored as reference  
- Supports autoboxing and unboxing  
  
### Wrapper classes  
- Create a wrap of the primitive types to object in java  
- since all the application in java deal with objects, so to adapt the primitive to objects, wrapper class is introduced  
- it is **Immutable**  
- Provides many utility functions to wonk on the primitive type and their values  
  
  
  
### Operators  
| Operators            | Precedence                                | execute from      |     |
| -------------------- | ----------------------------------------- | ----------------- | --- |
| postfix              | `_expr_++ _expr_--`                       | right to left     |     |
| unary                | `++_expr_ --_expr_ +_expr_ -_expr_ ~ !`   | right to left     |     |
| multiplicative       | `* / %`                                   | left to right     |     |
| additive             | `+ -`                                     | left to right     |     |
| shift                | `<< >> >>>`                               | left to right     |     |
| relational           | `< > <= >= instanceof`                    | left to right     |     |
| equality             | `== !=`                                   | left to right     |     |
| bitwise AND          | `&`                                       | left to right     |     |
| bitwise exclusive OR | `^`                                       | left to right     |     |
| bitwise inclusive OR | \|                                        | left to right<br> |     |
| logical AND          | `&&`                                      | left to right<br> |     |
| logical OR           | \| \|                                     | left to right<br> |     |
| ternary              | `? :`                                     | right to left     |     |
| assignment           | `= += -= *= /= %= &= ^= \|= <<= >>= >>>=` | left to right<br> |     |
### Instanceof  
- used to compare an object on a specified type. or test if an object is an instance of a class, an instance of a subclass, or an instance of a class that implements a particular interface.  
  
### Enum  
- A special data type that enables a variable to be set of a predefined constants  
- it is final by design  
- can implement interfaces  
- It can have methods, constructors for complex use case  
- yet the constructor can be only called by compiler  
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
  
  
  
  
### Compile-Time Constant  
- When the compiler knows the constant value of the primitive type variables during compilation. It replaces all the variables with the value during the compile time itself  
  
### Expressions  
- An _expression_ is a construct made up of variables, operators, and method invocations, which are constructed according to the syntax of the language, that evaluates to a single value.  
  
### Statement  
- These are similar to sentence in natural language. A statement forms a complete form of execution. Some expressions with semicolon in the end represents a statement.  
  
### Autoboxing  
- Conversion of primitive data type into its wrapper class  
```java  
// Autoboxing  
Integer obj = 10;  
// Explicit casting  
Integer obj2 = Integer.valueOf(10)  
```  
### Unboxing  
- used by compiler to convert the wrapper class into its primitive datatype  
```java  
Integer obj = Integer.valueOf(10);  
// Unboxing  
int i = obj;  
// Explicit value deduction  
i = obj.intValue();  
```  
  
### Break statement  
- Types  
- Labelled  
- points to a label, where the loop below the label is terminated  
- helps in specifically break a certain inner loop in several nested loops  
```java  
int i;  
int j = 0;  
boolean foundIt = false;  
  
search:  
for (i = 0; i < arrayOfInts.length; i++) {  
for (j = 0; j < arrayOfInts[i].length;  
j++) {  
if (arrayOfInts[i][j] == searchfor) {  
foundIt = true;  
break search; // breaks the outer loop as well  
}  
}  
}  
```  
- unlabelled  
- a plain `break` keyword that break the loop in which it is present(the immediate loop from its scope)  
  
  
### Continue statement  
- Types  
- Labelled  
- points to a label, where the current iteration of the labelled loop is skipped  
- helps in specifically skip an iteration of a certain inner loop in several nested loops  
```java  
test:  
for (int i = 0; i <= max; i++) {  
int n = substring.length();  
int j = i;  
int k = 0;  
while (n-- != 0) {  
if (searchMe.charAt(j++) != substring.charAt(k++)) {  
continue test;  
}  
}  
foundIt = true;  
break test;  
}  
```  
- unlabelled  
- a plain `continue` keyword that skips the current iteration the loop in which it is present(the immediate loop from its scope)  
  
### Components of method declaration  
- **Access Modifier  
- **Return Type  
- **Method Name  
- **Parameters  
- **Exception list  
- **Method Body  
  
### Method Signature ---- Method name and Parameters  are only considered
  
- #### Note -- two methods with same signature and different return types cannot exist, because compiler does not consider return type while differentiating the methods  
  
**Note** --- All classes have at least one constructor. If a class does not explicitly declare any, the Java compiler automatically provides a no-argument constructor, called the **_default constructor_**. This default constructor calls the class parent's no-argument constructor, or the `Object` constructor if the class has no other parent. If the parent has no constructor (`Object` class does have one), the compiler will reject the program. ( This occurs when a parent class has a parameterized constructor and the child class does not have a constructor. then on trying to create an object in child class will be an error)  
  
**Note** --- Initialization of parent class should be only in the first of the constructor. (i.e: `super()` )  
  
**Covariant return type** --- If a function has a class as its return type, then it can return on object referring to the class itself or to its subclass.  
  
### Garbage Collector  
- An object is eligible for garage collection only if there is no more references to it in the future.  
  
  
## Class  
  
### Initialization order  
- **static variables → static blocks → instance variables → instance blocks → constructor**.  
- A **`final`** variable declared but **not initialized** (blank final) can only be initialized inside a **constructor or initializer block**.  
  
### Utility class
- Contains static methods for performing useful operation.
  

### Constructor  
- final keyword cannot be given to a constructor  
- types  
	- default constructor  
	- parameterized constructor  
	- No-argument constructor  
	- Copy constructor  
	- Singleton constructor
  
  
### Initialization block  
- **Instance Initialization Block  
- Used when the initialization is complex and has to be shared across many constructors  
- runs every time an object is created  
```java  
class MyClass {  
int instanceVar;  
{ // Instance Initialization Block  
System.out.println("Instance Initializer Block executed.");  
instanceVar = 10;  
}  
MyClass() {  
System.out.println("Constructor executed.");  
}  
}  
```  
  
- **Static Initialization Block  
- Executes only once in the entire  
- executes just after the class is loaded  
```java  
class MyClass {  
static int staticVar;  
static { // Static Initialization Block  
System.out.println("Static Initializer Block executed.");  
staticVar = 20;  
}  
// ... rest of the class  
}  
```  
  
  
### Final Method  
- It is used when the subclasses wanted to use the same initialization code as the parent then can be inherited and used, since the static method does not override on inheritance.  
- cannot be overriden
  
### Static method restrictions  
- Can only access fields or methods that are static  
- Cannot override them  
- cannot have **this** or **super** keyword in them  
  
### Override restrictions  
- You cannot override a **static/final/private** method.  
- __protected__ method can only be overridden as __protected__  

  
### Tightly Coupled  
- When a change in one class does force the other class to change in implementation, then it is said to be tightly coupled.  
- Has less number of classes compared to loose coupling  
- Ex:
	- Assigning Child class object to Child class reference. 
	```java
	Child obj=new child();
	```
  
### Loosely coupled  
- when change in one class does not affect the structure of another which is using it then it is loosely coupled.  
- implementation relies heavily on interface and abstract classes.  
- Does include more classes but end up being more flexible than tight due to its representation restrictions.  
- Ex:
	- Assigning Child class object to parent class reference.
```java
Parent obj = new Child();
```
### Interface  
- it is a blueprint for a class, serving as a contract that defines a set of abstract methods and constant fields. It specifies what a class should do, but not how it should do it.  
- Interface can be inherited  
- Provide complete abstraction  
- ==**`default`**== keyword is allowed in here  
- in need of adding new member or function and that is not needed to be a part of all the implemented class then default keyword is used  
- in case of overriding, can only be overridden with ==**`public`**==  
- Types
	- Functional interface
	- Marker interface

### Abstract class  
- Provides partial abstraction  
- can have both concrete or abstract methods  
- cannot have instance  
- can be public, final, default  
  
  
  
## Nested classes  
- **Why**  
	- to logically group the classes and streamline the packages.  
	- Increases encapsulation  
- **Note** --- all the nested class has to utilize the __instance__ fields or a methods from the enclosing class with the help of an object  
- Only a nested class be a private class  
- A base class being private cannot be accessed  
- types  
	- Static nested classes  
		- classes inside a static class can only be s static
	- non-static nested classes  
		- member inner class  
	- local inner class  
		- defined within a method / constructor of a class  
	- anonymous inner class  
		- declared without a name, used for a short time  
  
### Shadowing  
- If a declaration in the enclosing class is the same in the nested class then the field of the enclosing class is shadowed  
- The enclosing class variable should be accessed with **`ClassName.this.x`**  
  
### Inner class  
- Declared directly inside a class block  and outside methods
- considered similar to fields and methods of the class.  
  
### Local Classes  
- can be created inside a block  
- has direct access to all the final and static variable of the enclosing class  
- **Accessibility**
	- can access enclosing class fields and members and instance variables
	- can access final or effectively final variables 
 - When the enclosing method’s execution ends,  any variables accessed by the local class are **copied (if local)** or **referenced (if instance)**, so the local class instance continues to work safely —   the enclosing context remains reachable through these captured values.
```java 
class Main {
    
    static public void print(){
        int a=10;
        System.out.println("enclosing");
        class Inner{
            public void run2(){
                System.out.println(a);
            }
        }
        Inner obj=new Inner();
        obj.run2();
    }

    public static void main(String[] args) {
        print();
    }
}
```
  
### Anonymous class  
- is ==**`final`**== by default  
- cannot have constructor because of not having a name and cannot have instance due to absence of constructor.  
- cannot have static declaration inside them  
- instance and member access is same as local class  
- Can be created with  
	- Interface  
	- extend an abstract or concrete class  
- Compiler see these classes as ==**`Outer$1.class`**==  
  
```java  
// Java Program to Demonstrate Anonymous inner class  
  
// Interface  
interface Age {  
int x = 21;  
void getAge();  
}  
  
// Main class  
class AnonymousDemo {  
  
// Main driver method  
public static void main(String[] args)  
{  
  
// A hidden inner class of Age interface is created  
// whose name is not written but an object to it  
// is created.  
Age oj1 = new Age() {  
  
@Override public void getAge()  
{  
// printing age  
System.out.print("Age is " + x);  
}  
};  
  
oj1.getAge();  
}  
}  
```  
  
- Types  
- By implementing interface  
- By extending a class of an abstract class   
- Passed as argument inside a method  
```java  
abstract class Shape {  
abstract void draw();  
}  
  
public class Main {  
static void printShape(Shape s) {  
s.draw(); // ✅ Here we call the overridden method  
}  
  
public static void main(String[] args) {  
printShape(new Shape() {  
@Override  
void draw() {  
System.out.println("Drawing a Circle");  
}  
});  
}  
}  
```  
  

### Sealed class  
- it is used when the class needs only to be extended by certain specific classes  
- it uses`permit` keyword to allow specific classes  
```java  
public sealed class parent permits child, grandchile{  
  
}  
```  
  

### Serialization  
- it is converting of objects into byte stream so that it can be  
	- saved in a file  
	- transferred through a network  
- It is done with the help of **==Serializable**== interface  (It is marker interface used to let the JVM know it is serializable)
- Helps in storing the current state of an object and reuse it later  
- ==**`transient`**== keyword is used on fields or variable that are not supposed to be serialized (security credentials, etc). so when deserialized are assigned to default values.
```java  
import java.util.*;
import java.io.*;

class Parent implements Serializable{
    int a;
    char b='w';
    Parent(int a){
        this.a=a;
    }
}

public class Main
{
	public static void main(String[] args) throws Exception{
		Parent obj=new Parent(10);
		ObjectOutputStream oos=new ObjectOutputStream(new FileOutputStream("output.txt"));
		oos.writeObject(obj);
		ObjectInputStream ois = new ObjectInputStream(new FileInputStream("output.txt"));
		Parent objd =(Parent)ois.readObject();
		System.out.println(objd.a);
	}
}  
```  
  
  
## Exception  
  
- All Error and Exception related classes are descendants of ==**`Throwable`**== class.
- It is an exceptional event that occurs during the execution of the program that disrupts the flow of instructions.  
- when an exceptional event occurs, the method creates an object called __exception__ and sends it to the runtime system.  
- when an exception occurs, runtime searches the call stack(method invocations) sequentially to check for an matching exception handler, if matches, handles it and continues the program from that point, else the program is terminated.  
- ==**Errors**== in specific are not recommended to be handled  
  
- **Checked exception**  
	- Compile time errors (checked during compile time)  
- **Unchecked exception**  
	- Errors  
	- Run-time Exceptions  
- ==**NOTE**== - when try throws an exception and finally as well throws, then exception by try will be lost if the catch is not used.  
  
  

  
### Suppressed exceptions  
- When a try block throws an exception and while closing the resources, the try-with-resource as well throws an exception then the try-with-resource exception is suppressed within the primary exception and delivered.  
- it can be accessed by  
```java  
} catch (Exception e) {  
System.out.println("Caught Exception: " + e.getMessage());  
for (Throwable t : e.getSuppressed()) {  
System.out.println("Suppressed: " + t);  
}  
}  
```

  
### Try-with-resource  
- Apart from having the try-catch-finally functionality, it has autocloseable resources created within parenthesis after `try` keyword  
- Such resources should implement **AutoCloseable/Closeable**. interface  
- This the resources are automatically closed at the end of try block.  
 - ==**NOTE**==  
	- when the close method is not called on the resources created once its use is over.  
	- and when the [[#Garbage Collector]] finds the object, it only frees the object memory, the resource will not be closed  
	- thus when it repeats, then the limit of resource access exceed.  
	- It can handle more than one object.
  
  
### Chained Exception  
- when an exception is caught, it throws another exception to a higher exception handler containing the main exception .  
- it helps in associating one exception with other exception, through proper description.  
- helps to keep note on the root cause of the exception
  
  
**Stack trace:** A _stack trace_ provides information on the execution history of the current thread and lists the names of the classes and methods that were called till the point when the exception occurred. A stack trace is a useful debugging tool that you'll normally take advantage of when an exception has been thrown.  
  
### Creating custom Exception classes  
- **Note** -- If a client can reasonably be expected to recover from an exception, make it a checked exception. If a client cannot do anything to recover from the exception, make it an unchecked exception.  
- Can be created by extending ==**`Exception`**== class  
  
### Advantages of exception  
- **Separates error/exception prone code from regular code**  
- **propagates error up the call stack**  
- **Grouping error types**
  
### Overriding a method that throws an exception  
- when parent method doesn't throw an exception then the child method cannot throw a checked exception but can be unchecked  
- the child should not throw an exception that is superset of the parent class exception  
- The first throws fewer exceptions than the overridden method, and the second, even though it throws more; they’re narrower in scope.  
- parent and child can throw irrelevant exceptions  
  
### Note  
- if a methods declared to throw a checked exception is called it should be handled inside a try-catch block or the function itself can be declared of throwing the same exception to avoid compile time interruption.  but it is recommended to handle it.
  
  
  
## Collections  
- It inherits ==**`Iterable`**== class  
- ==**`Collection`**== is an interface.
- ==**`Collections`**== is a Utility class

- the ==**Collection**== class has [_synchronization wrappers_](https://docs.oracle.com/javase/8/docs/api/java/util/Collections.html#synchronizedCollection-java.util.Collection-) that can be used to synchronize any unsynchronized collections  
  
| Key | Value |  
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |  
| what | it is an object that represent a group of objects |  
| purpose | used to store, retrieve, manipulate, and communicate aggregate data effieiency |  
| Collection interface | `java.util.Collection` |  
| Sub-interfaces | - list (ArrayList, LinkedList)<br>- set (HashSet,TreeSet)<br>- queue (PriorityQueue)<br>- deque (ArrayDeque) |  
| Advantages | - Ready-made data structures<br>- Increased performance due to common interface<br>- Provides a common language for passing collection between different APIs. |  
| Methods | The `Collection` interface contains methods that perform basic operations, such as **`int size()`**, **`boolean isEmpty()`**, **`boolean contains(Object element)`**, **`boolean add(E element)`**, <br>**`boolean remove(Object element)`**, and **`Iterator<E> iterator()`**.<br><br>**`boolean containsAll(Collection<?> c)`**, **`boolean addAll(Collection<? extends E> c)`**, **`boolean removeAll(Collection<?> c)`**, **`boolean retainAll(Collection<?> c)`**, and **`void clear()`**. |  
  
### Collection Framework  
- Unified architecture for representing and manipulating collections  
- **final** keyword on list object will only stop it from reassigning not from appending  
- contains  
	- Interface  
	- implementations  
	- algorithm  
  
| Interface | Hash Table | Resizable Array | Balanced Tree | Linked List | Hash Table + Linked List |  
| --------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |  
| `Set` | [HashSet](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html) | | [TreeSet](https://docs.oracle.com/javase/8/docs/api/java/util/TreeSet.html) | | [LinkedHashSet](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashSet.html) |  
| `List` | | [ArrayList](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html) | | [LinkedList](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html) | |  
| `Deque` | | [ArrayDeque](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayDeque.html) | | [LinkedList](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html) | |  
| `Map` | [HashMap](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html) | | [TreeMap](https://docs.oracle.com/javase/8/docs/api/java/util/TreeMap.html) | | [LinkedHashMap](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashMap.html) |  
  
| Interface | Allows Duplicates | Ordered | Sorted | Nulls Allowed |  
| --------- | ----------------- | ------------------------- | ----------------------- | ---------------------------------------- |  
| List | Yes | Yes | No | Yes (one null in some cases) |  
| Set | No | No (except LinkedHashSet) | Yes (TreeSet) | Only one null (HashSet) |  
| Queue | Yes | Yes | Priority-based possible | One null (except PriorityQueue) |  
| sMap | No (for keys) | Depends | TreeMap sorted by keys | One null key (HashMap), many null values |  

.

| **Need / Requirement**                        | **Best Choice**            | **Reason**                                |
| --------------------------------------------- | -------------------------- | ----------------------------------------- |
| Fast random access (by index)                 | `ArrayList`                | O(1) access, dynamic array                |
| Frequent insert/remove in middle              | `LinkedList`               | O(1) insertion/removal if node known      |
| Maintain order & allow duplicates             | `ArrayList` / `LinkedList` | Lists keep insertion order                |
| Prevent duplicates, don’t care about order    | `HashSet`                  | O(1) average lookup                       |
| Prevent duplicates, preserve insertion order  | `LinkedHashSet`            | Hash + linked list preserves order        |
| Prevent duplicates, keep sorted order         | `TreeSet`                  | Red-black tree, O(log n)                  |
| Key → Value mapping, fastest lookup           | `HashMap`                  | O(1) average lookup                       |
| Key → Value mapping, preserve insertion order | `LinkedHashMap`            | Useful for LRU caches                     |
| Key → Value mapping, sorted by keys           | `TreeMap`                  | Natural/custom key order                  |
| Key → Value mapping, thread-safe              | `ConcurrentHashMap`        | High concurrency, safe in multi-threading |
| Queue (FIFO)                                  | `ArrayDeque`               | Faster than `LinkedList` for queues       |
| Double-ended queue (Deque)                    | `ArrayDeque`               | Efficient add/remove at both ends         |
| Stack (LIFO)                                  | `ArrayDeque` (not `Stack`) | Modern replacement, no sync overhead      |
| Priority ordering (min/max element first)     | `PriorityQueue`            | Heap-based, O(log n) insert/remove        |
  

### Default size for collections  
- **ArrayList:** In Java 8 and later, the default initial capacity is 0, but it's lazily initialized to 10 when the first element is added. In older versions, it was directly initialized to 10.  
- **Vector:** The default initial capacity is 10.  
- **HashMap, HashSet, LinkedHashMap, LinkedHashSet, ConcurrentHashMap, WeakHashMap:** The default initial capacity is typically 16.  
- **Hashtable:** The default initial capacity is 11.  
- **LinkedList, TreeSet, TreeMap:** These classes do not have a concept of a fixed "capacity" in the same way as array-backed collections.  
  
### Collection interface  
- It is used to pass around group of objects where maximum generality is desired.  
  
### For iterations of collections  
- Aggregate functions  
- ==**`.stream()`**==  
- ==**`.parallelStream()`**== can be used when the collection is big enough to make the computer struggle loading entirely  
  
```java  
import java.util.ArrayList;  
  
class Sample{  
public static void main(String[] args) {  
ArrayList<Integer> arl=new ArrayList<>();  
arl.add(1);  
arl.add(2);  
arl.stream().filter(e-> e>1).forEach(i -> System.out.println(i)); //aggregate function  
System.out.println(arl.stream().count());  
}  
}  
```  
- for-each loop  
```java  
for (Object o : collection)  
System.out.println(o);  
  
```  
- `Iterators`  
```java  
  
import java.util.ArrayList;  
import java.util.Iterator;  
  
class Sample{  
public static void main(String[] args) {  
ArrayList<Integer> arl=new ArrayList<>();  
arl.add(1);  
arl.add(2);  
Iterator<Integer> iter=arl.iterator();  
while(iter.hasNext()){  
System.out.println(iter.next());  
  
}  
}  
}  
```  
### Fail fast and fail safe iterators  
|Aspect|Fail-Fast Iterator|Fail-Safe Iterator|  
|---|---|---|  
|Behavior on concurrent modification|Throws `ConcurrentModificationException` immediately|Does not throw exception; iterates on a snapshot|  
|Method of iteration|Iterates on the actual collection|Iterates on a clone/copy of the collection|  
|Overhead|Low overhead (no copying)|Higher overhead due to copying|  
|Use case|Single-threaded or controlled modification environments|Multi-threaded environments supporting concurrent modifications|  
|Exception thrown|Yes|No|  
- **Fail-safe iterator** , can also apply to a copy of the collection created in other ways  
```java  
CopyOnWriteArrayList<Integer> list = new CopyOnWriteArrayList<>(Arrays.asList(1, 2, 3));  
Iterator<Integer> iterator = list.iterator();  
while (iterator.hasNext()) {  
Integer num = iterator.next();  
list.add(4); // Safe to modify during iteration  
}  
  
```  
  
  
  
### Set interface  
- This collection does not contain duplicate elements  
- general implementation  
	- HashSet  
	- TreeSet  
	- LinkedHashSet  



#### HashSet  
- Does not maintain any order of the elements  
- use hash table to store and access elements  
- internally backed by **HashMap** of key with single value

#### LinkedHashSet  
- maintains the insertion order  
- uses hash function for storing and accessing  
- the node consists of 
	- key
	- value
	- previous node
	- next node
	- hash value
  
#### TreeSet  
- Stores elements in red-black tree  
- ordered based on their value  
- slower than the rest two  

#### Operations  
- basic  
- size()  
- isEmpty()  
- Iterator  
- bulk  
- containsAll()  
- retainAll()  
- addAll()  
- removeAll()  
```java  
Set<Type> union = new HashSet<Type>(s1);  
union.addAll(s2);  
  
Set<Type> intersection = new HashSet<Type>(s1);  
intersection.retainAll(s2);  
  
Set<Type> difference = new HashSet<Type>(s1);  
difference.removeAll(s2);  
```  
  
### List interface  
- Ordered collection / sequence  
- **Operations**
	- get()  
	- set()  
	- add()  
	- addAll()  
	- remove()  
	- indexOf()  
	- lastIndexOf()  
	- listIterator()  
	- sublist()  
- **Algorithms** 
	- sort()  
	- shuffle()  
	- reverse()  
	- rotate()  
	- swap()  
	- replaceAll()  
	- fill()  
	- copy()  
	- binarySearch()  
	- indexOfSublist()  
	- lastIndexOfSublist()  
  
### Queue interface  
  
| Type of Operation | Throws exception | Returns special value |  
| ----------------- | ------------------------------------ | --------------------- |  
| Insert | `add(e)` on exceeding queue size | `offer(e)` |  
| Remove | `remove()` when no element to remove | `poll()` |  
| Examine | `element()` when queue is empty | `peek()` |  
- Queue itself does not allow null values , **but** queue implemented with LinkedList allows.  
  
### Dequeue interface  
- It is a **double-ended queue**  
- It supports insertion and deletion of elements on both the ends  
- It implements the features of both stack and queue at the same time  
  
| Type of Operation | First Element (Beginning of the `Deque` instance) | Last Element (End of the `Deque` instance) |  
| ----------------- | ------------------------------------------------- | ------------------------------------------ |  
| **Insert** | `addFirst(e)` <br>`offerFirst(e)` | `addLast(e)` <br>`offerLast(e)` |  
| **Remove** | `removeFirst()` <br>`pollFirst()` | `removeLast()` <br>`pollLast()` |  
| **Examine** | `getFirst()` <br>`peekFirst()` | `getLast()` <br>`peekLast()` |  
  
### Map interface  
- it is an object that maps keys to values  
- Cannot contain duplicate keys  
- one key can utmost point to one value  
- Operations  
	- get()  
	- put()  
	- remove()  
	- containsKey()  
	- containsValue()  
	- size()  
	- empty()  
	- putAll()  
	- clear()  
	- Views  
	- keySet  
	- entrySet  
	- values  
  
  
### TreeSet vs HashSet  
  
| Feature | HashSet (unordered) | TreeSet (sorted) |  
| ----------------- | ------------------- | ---------------------------------------------- |  
| Data structure | HashMap | TreeMap (Red-Black Tree) ordered BST |  
| Ordering | None | Natural / Comparator |  
| Nulls allowed | One null | No nulls |  
| Time complexity | O(1) average | O(log n) |  
| Duplicate allowed | No | No |  
| Iteration order | Random | Sorted |  
| Extra methods | Basic (add, remove) | Navigation methods (first, last, subset, etc.) |  
  
### HashMap  
- Collitions  
	- handled by putting the same hashcode keys in a bucket and use **`equals`** to differentiate them  
- Load factor  
	- states how full the hashmap can be before its size is increased.  
- Not thread-safe  
	- is not synchronized and can lead to racing conditions  
- Hash-table is thread-safe  
- use synchronized methods, but has performance overhead due to obtaining lock for the operations  
- in-case of overriding **`hashCode()`**  do override **`equals()`** as well.
- do not change the key after inserting.
-  the node consists of 
	- key
	- value
	- next node
	- hash value
  
### Hashtable
- contains a array of bucket to store key-value pairs
- does not allow null keys, due to *legacy design* later to overcome this HashMap was introduced.
- provides synchronization
- uses `Enumerator` instead of `Iterator`
- is now considered a legacy since it was brought in 1.2

### LinkedHashMap  
- Has features of both hash table and doubly-LinkedList  
- LinkedList for preserving the insertion order/ access order
- HashMap for faster access
  
  
TreeMap/TreeSet does not allow null value because it maintains certain ordering with the help of comparisons  
  
  
**Note** -- you are allowed to create your own immutable collection  
- can either be done by  
	- implementing existing interface  
	- or overriding the available function to create from scratch  
- it helps in having  
	- read only collection  
	- thread safe collection  
  
  
  
  
  
### Cursor  
- "cursors" are **objects used to iterate, or traverse, a collection's elements one by one** 
- Types
	- Iterator  ----- forward only ,  supports read and remove
	- ListIterator  ----- bi-directional,  supports read, remove, add, set
	- Enumerator ----- legacy forward only , supports only read


### Iterator and stream for collection  

| Iterator | Stream |
| - | - |
| used when performing a complex iteration logic| for a functional approach in collections |
|can remove elements from collection during iteration| 	can modify or remove elements when dealing with a copy of the collection |
| high performance and low overhead | usually deal with large collection and support **parallelStream()** causing high overhead |  
| better for simple iteration| better for complex iteration and manipulation process|
#### Iterator
- It points between elements so it has `next()` that gives the next element in the sequence.
 
#### Stream API
- Recommended for java 8+ version due to its built-in parallel execution
 - used **`sorted`** method to sort collection when converted to a stream.
```java
List<String> fruits = Arrays.asList("banana", "apple", "orange", "grape");
 
List<String> sortedFruits = fruits.stream()
        .sorted()
        .collect(Collectors.toList());
```  
### Searching and Sorting in collections
- there are two interfaces that help in creating a comparison method for collection. ==**`Comparable`**== and ==**`Comparator`**== 

#### Comparable (interface)
- helps implement **`compareTo`** method, used for sorting
- only contains **`compareTo()`** 

#### Comparator (functional interface)
- helps define a custom **`compareTo`** methods, later used for sorting
  
 
#### Sorting maps
- can be done with by converting them into list of map entries and sorting them.  


### searching in collection
- can use
	- Linear search
	- Binary Search
	- Methods from collections



  
## I/O  
  
  
### [I/O Streams](https://docs.oracle.com/javase/tutorial/essential/io/streams.html)  
  
- [Byte Streams](https://docs.oracle.com/javase/tutorial/essential/io/bytestreams.html) handle I/O of raw binary data.  
- [Character Streams](https://docs.oracle.com/javase/tutorial/essential/io/charstreams.html) handle I/O of character data, automatically handling translation to and from the local character set.  
- [Buffered Streams](https://docs.oracle.com/javase/tutorial/essential/io/buffers.html) optimize input and output by reducing the number of calls to the native API.  
- [Scanning and Formatting](https://docs.oracle.com/javase/tutorial/essential/io/scanfor.html) allows a program to read and write formatted text.  
- [I/O from the Command Line](https://docs.oracle.com/javase/tutorial/essential/io/cl.html) describes the Standard Streams and the Console object.  
- [Data Streams](https://docs.oracle.com/javase/tutorial/essential/io/datastreams.html) handle binary I/O of primitive data type and `String` values.  
- [Object Streams](https://docs.oracle.com/javase/tutorial/essential/io/objectstreams.html) handle binary I/O of objects.  
  
  
  
### Byte Stream  
- Handle input and output of 8-bit bytes  
- each of the operation is handled directly by the underlying OS, so can be less efficient, cause it follows a lot of procedures  
 - **FileInputStream** extends InputStream which implements closeable.
 - It uses FileDescriptor to create connection to the file
```java  
import java.io.*;  
  
public class Sample {  
  
public static void main(String[] args) throws Exception {// not recommended, instead handle the exception  
String path="Data.txt";  
FileInputStream read=new FileInputStream(path);  
FileOutputStream write=new FileOutputStream("writefile.txt",true); // true is used to append in the file  
int c=0;  
while((c=read.read())!=-1){  
System.out.println((char)c);  
}  
String s="this is s sample output\n and this is next line";  
for(char ch:s.toCharArray()){  
write.write(ch);  
}  
read.close(); // always close the stream after using  
write.close(); // always close the stream after using  
}  
}  
```  
  
  
### Character stream  
- directly deals with the Unicode values  
- no conversion takes place  
- each of the operation is handled directly by the underlying OS so can be less efficient, cause it follows a lot of procedures  
  
```java  
import java.io.*;  
  
public class Sample {  
  
public static void main(String[] args) throws Exception {  
String path="Data.txt";  
FileReader read=new FileReader(path);  
FileWriter write=new FileWriter("writefile.txt",true);  
int c=0;  
while((c=read.read())!=-1){  
System.out.println((char)c);  
}  
String s="this is s sample output\n and this is next line";  
for(char ch:s.toCharArray()){  
write.write(ch);  
}  
}  
}  
```  
  
- For line oriented file operation  
```java  
import java.io.*;  
  
public class Sample {  
  
public static void main(String[] args) throws Exception {  
String path="Data.txt";  
BufferedReader read=new BufferedReader(new FileReader(path));  
PrintWriter write=new PrintWriter(new FileWriter("writefile.txt"));  
String c;  
while((c=read.readLine())!=null){  
System.out.println(c);  
}  
String s[]=new String[]{"this is s sample output\n"," and this is next line"};  
for(String sh:s){  
write.println(sh);  
}  
write.flush(); //to flush the content into the file, can be used if it takes time ti close the write  
read.close();  
write.close();  
}  
}  
```  
  
  
### Buffered streams  
- Normally , the file is read -> decoded(UTF-8) (By Reader) -> Stored in buffer -> Accessed by the program.
- Buffered input streams read data from a memory area known as a _buffer_ (8KB) , the native input API is called only when the buffer is empty.  
- buffered output streams write data to a buffer, and the native output API is called only when the buffer is full.  
- so to call the write API before the buffer is full we use ==**`.flush()`**== to immediately call the API and write in the file.  
  
```java  
import java.io.*;  
  
public class Sample {  
  
public static void main(String[] args) throws Exception {  
String path="Data.txt";  
BufferedReader reader=new BufferedReader(new FileReader(path));  
BufferedWriter writer=new BufferedWriter(new FileWriter("writefile.txt",true));  
String c;  
while((c=reader.readLine())!=null){  
System.out.println(c);  
}  
String s[]=new String[]{"this is s sample output\n"," and this is next line"};  
for(String sh:s){  
writer.write(sh);;  
}  
writer.flush();;  
reader.close();  
writer.close();  
}  
}  
```  
  
  
### Scanning  
-Uses CharBuffer implicitly
- Objects of type Scanner are useful for breaking down formatted input into tokens and translating individual tokens according to their data type.  
```java  
import java.io.*;  
import java.util.Scanner;  
  
import javax.sound.sampled.SourceDataLine;  
  
public class Sample { // prints each word in the file line by line  
  
public static void main(String[] args) throws Exception {  
String path="Data.txt";  
Scanner scan=new Scanner(new BufferedReader(new FileReader(path)));  
scan.useDelimiter(",");  
String word;  
while(scan.hasNext()){ // hasnextLine() & nextLine for each line  
System.out.println(scan.next());  
}  
}  
}  
```  
  
  
  
### Formatting  
- Can be done with the help of  
	- print and println statements  
	- ==**`format`**== statement --- works very much like **`printf`**  
```java  
System.out.format("%f, %<+1.10f %n", Math.PI);  
```  
  
### I/O for command line  
- **Standard Streams**  
- Input  
	- System.in  
- Output  
	- System.out  
	- System.err  
- These are of ByteStreams despite being standard and most used due to historical reasons.  
  
- **Console**
	- It is of character streams and does provide a lot of functionalities and more than the standard ones.  
	- The console object has to be requested form the os before using it.  
	- It provides safe password entry by making entry in console invisible and return the password as character array  
```java  
import java.io.Console;  
  
public class Sample {  
  
public static void main(String[] args) throws Exception {  
Console c=System.console();  
String name=c.readLine("Enter name:");  
System.out.println(name);  
char []ar=c.readPassword("Enter pass:");  
for (char i:ar){  
System.out.println(i);  
}  
}  
}  
```  
  
  
### Data Streams  
  
| Data type | Output Method | Input Method | Sample Value |  
| --------- | ------------------------------ | ---------------------------- | ---------------- |  
| `double` | `DataOutputStream.writeDouble` | `DataInputStream.readDouble` | `19.99` |  
| `int` | `DataOutputStream.writeInt` | `DataInputStream.readInt` | `12` |  
| `String` | `DataOutputStream.writeUTF` | `DataInputStream.readUTF` | `"Java T-Shirt"` |  
  
```java  
class Hostel{  
public static void main(String[] args) throws Exception {  
String path="src/Data.txt";  
int ar[]=new int[]{1,2,3,4,5};  
String []sr=new String[]{"a","b","c","d","e"};  
DataOutputStream out=new DataOutputStream(new BufferedOutputStream(new FileOutputStream(path,true)));  
for (int i=0;i<5;i++){  
out.writeInt(ar[i]);  
out.writeUTF(sr[i]);  
}  
out.flush();  
DataInputStream in=new DataInputStream(new BufferedInputStream(new FileInputStream(path)));  
try {  
while (true) {  
int a=in.readInt();  
String s = in.readUTF();  
System.out.println(a+" "+s);  
}  
}  
catch(EOFException e){  
System.out.println("End of the file");  
}  
finally{  
in.close();  
out.close();  
}  
}  
}  
```  
  
  
  
### Object Streams  
- The `writeObject` and `readObject` methods are simple to use, but they contain some very sophisticated object management logic. This isn't important for a class like Calendar, which just encapsulates primitive values. But many objects contain references to other objects. If `readObject` is to reconstitute an object from a stream, it has to be able to reconstitute all of the objects the original object referred to. These additional objects might have their own references, and so on. In this situation, `writeObject` traverses the entire web of object references and writes all objects in that web onto the stream. Thus a single invocation of `writeObject` can cause a large number of objects to be written to the stream.  
- A stream can only contain one copy of an object, though it can contain any number of references to it.  
- Cannot be used on class objects that does not implement serializable interface.  
- the serialization mechanism is  done by JVM 
- the interface is only a marker interface used to indicate to the JVM 
  
  
  
**Serialization** is a mechanism of converting the state of an object into a byte stream.  
  
**Important Points of Serialisation:**  
  
- **Platform-Independent:** In Java, the serialization is a platform-independent process. It means that if we serialize an object using a byte stream on one platform can be easily deserialized on different platforms.  
- **Serializable Interface:** If we want to make a class serializable, then it must implement the Serializable interface. This interface does not contain any methods or variables ( marker interface), but it gives a signal that the class is ready for serialization.  
  
**Deserialization** is the reverse process where the byte stream is used to recreate the actual Java object in memory. This mechanism is used to persist the object.  
  
**Important Points of Deserialization:**  
  
- **Rebuilds Objects:** Deserialization takes the byte stream and turns it back into the original object with the same state as before.  
- **Platform-Independent:** Deserialization works well with different platforms without any issues.  
- **Class Must Be Available:** When we deserialize an object, it is necessary that the class definition be present in the program.  
  
```java  
import java.io.*;  
  
class Demo implements Serializable {  
public int a;  
public String b;  
  
public Demo(int a, String b) {  
this.a = a;  
this.b = b;  
}  
}  
  
public class Geeks {  
public static void main(String[] args) {  
Demo object = new Demo(1, "geeksforgeeks");  
String filename = "file.ser";  
  
// Serialization  
try {  
FileOutputStream file = new FileOutputStream(filename);  
ObjectOutputStream out = new ObjectOutputStream(file);  
out.writeObject(object);  
out.close();  
file.close();  
System.out.println("Object has been serialized");  
  
} catch (IOException ex) {  
System.out.println("IOException is caught");  
}  
  
Demo object1 = null;  
  
// Deserialization  
try {  
FileInputStream file = new FileInputStream(filename);  
ObjectInputStream in = new ObjectInputStream(file);  
object1 = (Demo) in.readObject();  
in.close();  
file.close();  
System.out.println("Object has been deserialized");  
System.out.println("a = " + object1.a);  
System.out.println("b = " + object1.b);  
  
} catch (IOException ex) {  
System.out.println("IOException is caught");  
} catch (ClassNotFoundException ex) {  
System.out.println("ClassNotFoundException is caught");  
}  
}  
}  
```  

### Scanner 
- it can be used for
	- user input
	- file reading
	- string reading
- it used a buffer of 1KB to store the data and parses inside the buffer with the help of regular expressions
- it is a wrapper over a readable object
- slower than bufferedReader.

  
  
  
  
## Threading in java  
  
- The JVM starts with a single non-daemon thread in the start. which call the main method of the program
- It continues to execute thread until
	- exit() method of `RunTime` class is called, or  
	- all the Non-Daemon thread have died  
  
- A customized thread class can be created by  
	- implementing ==**`Runnable`**== interface. has only  run() in it.
	- extending ==**`Thread`**== class  
	- creating anonymous class of ==**`Thread`**==  
- The Main class thread can be accessed with the help of ==**`Thread.currentThread()`**==  

- **NOTE** --- Thread group is used to group created threads so that the operation can be commonly applied to all the threads in it.
  
**When to Use Which**  
- **Use Runnable:**  
This is the recommended and preferred approach for most scenarios where you only need to define the task to be executed. You instantiate a Thread object and pass your Runnable object to it to start the task.  
  
- **Use Thread:**  
Extend the Thread class only in very specific, rare cases where you need to override or specialize other behaviors of the Thread class itself, such as the `interrupt()` method, in addition to the `run()` method.  
  
  
#### Thread lifecycle and states  
  
  NEW,
  RUNNABLE, 
  BLOCKED,
  WAITING, 
  TIMED_WAITING, 
  TERMINATED.
    
![[Pasted image 20250926112146.png]]  
  
  
### Synchronization  
- Threads communicate primarily by sharing access to fields and the objects reference fields refer to. This form of communication is extremely efficient, but makes two kinds of errors possible: _thread interference_ and _memory consistency errors_. The tool needed to prevent these errors is _synchronization_.  
  
- However, synchronization can introduce __thread contention__, which occurs when two or more threads try to access the same resource simultaneously _and_ cause the Java runtime to execute one or more threads more slowly, or even suspend their execution. [Starvation and livelock](https://docs.oracle.com/javase/tutorial/essential/concurrency/starvelive.html) are forms of thread contention. See the section [Liveness](https://docs.oracle.com/javase/tutorial/essential/concurrency/liveness.html) for more information.  
  
- It helps in ensuring integrity among the threads.  
- ==**constructors**== cannot be declared as synchronized.  
  
  
### Intrinsic lock  
- Synchronization is built around an internal entity known as ==**intrinsic/monitor locks**==.  
- when a ==**static synchronized method is invoked**==, since a static method is associated with a class, not an object. In this case, the thread acquires the intrinsic lock for the ==**`Class`**== object associated with the class. Thus access to class's static fields is controlled by a lock that's distinct from the lock for any instance of the class.  
  
#### Reentrant Synchronization  
  
- Recall that a thread cannot acquire a lock owned by another thread. But a thread _can_ acquire a lock that it already owns. Allowing a thread to acquire the same lock more than once enables _reentrant synchronization_. This describes a situation where synchronized code, directly or indirectly, invokes a method that also contains synchronized code, and both sets of code use the same lock. Without reentrant synchronization, synchronized code would have to take many additional precautions to avoid having a thread cause itself to block.  
  
### Synchronized statement  
  
```java  
public void addName(String name) {  
synchronized(this) {  
lastName = name;  
nameCount++;  
}  
nameList.add(name);  
}  
```  
  
```java  
public class MsLunch {  
private long c1 = 0;  
private long c2 = 0;  
private Object lock1 = new Object();  
private Object lock2 = new Object();  
  
public void inc1() {  
synchronized(lock1) {  
c1++;  
}  
}  
  
public void inc2() {  
synchronized(lock2) {  
c2++;
```

### Thread pooling
- consists of 
	- Task queue  (queue of task to be executed)
	- worker threads (list of thread controlled by executor)
	- executor (Manages both queues and worker threads)


### Executors
- To efficiently use thread and maintain thread pools instead of creating new threads for every single time.
- __Thread Pool__ consists of number of worker nodes that can be assigned with tasks.
- __Task queue__ It consists of tasks given to the executor.
- there are different structure of executor that can be created;
	- **newFixedThreadPool()** -- to allow a certain number of threads execute parallelly
	- **newSingleThreadExecutor()** -- to have single thread execute all the tasks sequentially
	- **newCachedThreadPool()** -- variable number of threads are created according to the need and availability, when available uses previously constructed thread, else creates a new thread
	- **new ScheduledExecutor()** -- to have tasks repeat itself on certain intervals.

| **Method**            | **Return Type** | **Use Case**                                        |
| --------------------- | --------------- | --------------------------------------------------- |
| `execute(Runnable)`   | `void`          | Fire-and-forget task. No result needed.             |
| `submit(Runnable)`    | `Future<?>`     | Need to check completion or handle exceptions.      |
| `submit(Callable<V>)` | `Future<V>`     | Task returns a result or throws checked exceptions. 

- **Note** 
	- ==**Runnable**== is used when there is no need for the function to give anything in return, most likely for simpler and logging kind of jobs.
	- ==**Callable**== is used when a function needs to return.  so ==**Future**== interface is used. it can hold exception and can be viewed later with **.get()**

#### Future
- it consists of methods like
	- get() -- make the main thread wait until the task in completed and the value is returned.
	- get(timeout, unit) -- to avoid constant wait
	- isDone() -- checks if the task is completed and the values is returned to the future variable.
	- cancel(true) -- cancel the task

#### shutdown methods
- shutdown() -- wait for the task to complete and stops
- shutdownNow() -- interrupt all tasks and stop immediately
- awaitTermination(timeout) -- wait for task completion

#### Queues
- Unbounded queue -- accepts all tasks and might lead to indefinite wait of tasks 
- Bounded queue -- avoids memory overflow but can reject tasks.

#### Rejection handling
- default or custom policies can be used to reject tasks


#### ThreadFactory
- it is an interface
- the interface contains the properties of a created thread.
- it can be implemented to customize thread properties
- Thread properties are such as
	- thread name
	- daemon status
	- priority
	- uncaughtException handler
	- thread group




## JDBC
- Standard interface to connect to any database specific API with the help of their drivers.

### JDBC Architecture
- Connection
- Statement
- PreparedStatement
- ResultSet
- DriverManager


### Establishing Connection
```java
Connection con = DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/mydb", "root", "password");
```

### Create Statement

```java
Statement stmt = con.createStatement();
```

### ExecuteQuery
```java
ResultSet rs = stmt.executeQuery("SELECT * FROM employees");
```

### Process result
```java 
while (rs.next()) {
    System.out.println(rs.getInt("id") + " " + rs.getString("name"));
}
```



```java 
import java.sql.*;

public class MultiResourceJDBC {
    public static void main(String[] args) {
        String url = "jdbc:mysql://localhost:3306/testdb";
        String user = "root";
        String pass = "password";

        String query = "SELECT id, name FROM employee";

        try (
            Connection con = DriverManager.getConnection(url, user, pass);
            PreparedStatement ps = con.prepareStatement(query);
            ResultSet rs = ps.executeQuery();
        ) {
            while (rs.next()) {
                System.out.println(rs.getInt("id") + " - " + rs.getString("name"));
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

### PreparedStatement
- it is a precompiled statement that uses **?** to later set values and execute with less computation compared to statement itself.
- it is precompiled by the database itself.
- It prevents SQL Injection
- Supports bulk execution

```java 
String sql = "SELECT * FROM users WHERE username = ? AND password = ?";
PreparedStatement ps = con.prepareStatement(sql);
ps.setString(1, "vishal");
ps.setString(2, "1234");

ResultSet rs = ps.executeQuery();
```

### CallableStatement
- this interface is used to call stored procedures in the database itself.
in SQL
- Allows IN, OUT, INOUT parameters.
- 

```sql
DELIMITER //
CREATE PROCEDURE getEmployeeName(IN empId INT, OUT empName VARCHAR(50))
BEGIN
    SELECT name INTO empName FROM employees WHERE id = empId;
END //
DELIMITER ;
```
```java 
CallableStatement cs = conn.prepareCall("{CALL getEmployeeName(?, ?)}");
cs.setInt(1, 2);              // IN parameter
cs.registerOutParameter(2, Types.VARCHAR); // OUT parameter

cs.execute();
String name = cs.getString(2);
System.out.println("Employee Name: " + name);
```

### JDBC for MySQL

#### Connection
```java 
import java.sql.*;

public class JDBCExample {
    static final String URL = "jdbc:mysql://localhost:3306/testdb";
    static final String USER = "root";
    static final String PASS = "password";

    public static void main(String[] args) {
        try (Connection conn = DriverManager.getConnection(URL, USER, PASS)) {
            System.out.println("Connected to MySQL successfully!");
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

#### CRUD operations
```java
//creation
String insertQuery = "INSERT INTO employees (name, age, department) VALUES (?, ?, ?)";

try (Connection conn = DriverManager.getConnection(URL, USER, PASS);
     PreparedStatement pstmt = conn.prepareStatement(insertQuery)) {

    pstmt.setString(1, "John Doe");
    pstmt.setInt(2, 28);
    pstmt.setString(3, "Engineering");

    int rowsInserted = pstmt.executeUpdate();
    System.out.println(rowsInserted + " row(s) inserted.");
}


//Read

String selectQuery = "SELECT id, name, age, department FROM employees";

try (Connection conn = DriverManager.getConnection(URL, USER, PASS);
     Statement stmt = conn.createStatement();
     ResultSet rs = stmt.executeQuery(selectQuery)) {

    while (rs.next()) {
        int id = rs.getInt("id");
        String name = rs.getString("name");
        int age = rs.getInt("age");
        String dept = rs.getString("department");
        System.out.println(id + " | " + name + " | " + age + " | " + dept);
    }
}


//Update
String updateQuery = "UPDATE employees SET department = ? WHERE id = ?";

try (Connection conn = DriverManager.getConnection(URL, USER, PASS);
     PreparedStatement pstmt = conn.prepareStatement(updateQuery)) {

    pstmt.setString(1, "Marketing");
    pstmt.setInt(2, 3);

    int rowsUpdated = pstmt.executeUpdate();
    System.out.println(rowsUpdated + " row(s) updated.");
}

//Delete

String deleteQuery = "DELETE FROM employees WHERE id = ?";

try (Connection conn = DriverManager.getConnection(URL, USER, PASS);
     PreparedStatement pstmt = conn.prepareStatement(deleteQuery)) {

    pstmt.setInt(1, 4);
    int rowsDeleted = pstmt.executeUpdate();
    System.out.println(rowsDeleted + " row(s) deleted.");
}

```


### Connection Pooling 
- It is a technique used to reuse database connections instead of repeatedly establishing new one.
- **Initailization**
	- when the program starts the connection pool manager creates a predefined number of database connections and stores them in a memory-based architecture.
- **Connection request and use**
	- Request -> Borrowing -> Logical Close
- **Pool management**
	- Scaling -- on demand creates new connections 
	- reaping -- connections that are idle beyond certain time are close to conserve resource.
	- health check -- Constantly check on their status, and re-establish that are broken due to some reasons.

- These are implemented using a dedicated library or service.
	- Application -- Tomcat, JBoss, WebLogic
	- External Libraries -- HikariCP, Apache DBCP
	- Managed environments -- J2EE/ Jakarta EE


### Best practices
- Always use prepared statements
- use try-with-resource
- avoid hard-coding credentials
- Maintain minimum open connections
- use batch processing -- using .addBatch() and executeBatch()
- handle transaction properly -- using commit() and Rollback()
- Use Connection pooling


### Lambda Expression
- **Lambda = Behavior**
- To avoid complex implementation of anonymous class lambda expression id introduces.
- Since anonymous class create separate java file for all of it.
- So to deal it functionally and to pass code/logic as data lambda expression was introduced.
- Lambda expressions are liked to a functional interface (Single Abstract Method)
- It only captures effectively final variables.
```java 
Runnable r = () -> System.out.println("Hello");
r.run();
```

```java
import java.util.*;
import java.util.function.*;

@FunctionalInterface 
interface Funcc{
    public void printt();
}

public class FnInterface {
    public static void main(String[] args) throws Exception {
        Funcc obj=()-> System.out.println("adsf");
        obj.printt();
        List<Integer> nums=List.of(1,2,3,4,5);
        checkprint(nums,i->System.err.println(i));
    }   
    public static void checkprint(List<Integer> nums,Consumer<Integer> cons){
        for (int i:nums){
            cons.accept(i);
        }
    }
    
}

```




  
### Functional interface  
- Functional Interfaces are mainly used for Lambda expressions, Method reference, and constructor references.  
- In functional programming, code can be treated as data. For this purpose, Lambda expressions are introduced. They can be used to pass a block of code to another method or object. Functional Interface serves as a data type for Lambda expressions.  
- Since a Functional interface contains only one abstract method, the implementation of that method becomes the code that gets passed as an argument to another method.  
- Introduces to enable lambda function in interface  
- Has only one abstract method irrespective of the other methods  
	- **Consumer** -- when dealing width single argument  
	- **Predicate** -- when dealing with Boolean value  
	- **Supplier** -- Does not take argument but returns value  
	- **Function** --when dealing with single argument and in need of return functionality  
- __Created as an alternative for complex anonymous class__
- advantages
	- does not create `.class` file for every single usage.
	- removes the overriding `this` for local instead of it being used on enclosing class

```java 
@FunctionalInterface
interface Supplier{
	public void give();
}
```


### Stream API
- Sequence of elements from a source.
- Supports function-style operations
- Not a data structure and does not store elements in any format.
- Operation are executed only when terminal operation is invoked.
- Types
	- ParallelStream
	- Sequential stream
- Operations
	- Intermediate --  return a new stream

| Operation | Purpose | Example |
|-|-|-|
|`filter`| Keep elements matching a predicate|`stream.filter(x -> x > 10)`|
|`map`| Transform elements|`stream.map(String::toUpperCase)`|
|`flatMap`|Flatten nested structures|`stream.flatMap(List::stream)`|
|`distinct`|Remove duplicates|`stream.distinct()`|
|`sorted`|Sort elements|`stream.sorted()`|
|`peek`|Debug / inspect elements|`stream.peek(System.out::println)`|
|`limit`|Take first n elements|`stream.limit(5)`|
|`skip`|Skip first n elements|`stream.skip(2)`|

	- Terminal -- trigger evaluation

| Operation   | Return Type               | Example                               |
| ----------- | ------------------------- | ------------------------------------- |
| `forEach`   | `void`                    | `stream.forEach(System.out::println)` |
| `collect`   | Collection / Map / Custom | `stream.collect(Collectors.toList())` |
| `reduce`    | Single value              | `stream.reduce(0, Integer::sum)`      |
| `count`     | `long`                    | `stream.count()`                      |
| `anyMatch`  | `boolean`                 | `stream.anyMatch(x -> x > 10)`        |
| `allMatch`  | `boolean`                 | `stream.allMatch(x -> x > 0)`         |
| `noneMatch` | `boolean`                 | `stream.noneMatch(x -> x < 0)`        |
| `findFirst` | `Optional`                | `stream.findFirst()`                  |
| `findAny`   | `Optional`                | `stream.findAny()`                    |


### Optional Class
- `Optional<T>` is a container object that may or may not contain a value of type `T`
- Introduced to avoid null reference and `NullPointerExcaption`
```java 
Optional<String> emptyOpt = Optional.empty(); // empty container
Optional<String> nonEmpty = Optional.of("Hello"); // value must be non-null
Optional<String> nullable = Optional.ofNullable(null); // can be null


optional.isPresent();  // true if value exists
optional.isEmpty();    // true if no value

String val = optional.get(); // throws NoSuchElementException if empty

String val = optional.orElse("default");
String val2 = optional.orElseGet(() -> "lazy default");
String val3 = optional.orElseThrow(() -> new IllegalStateException("missing"));



```
- `of()` → throws `NullPointerException` if value is null
- `ofNullable()` → allows null, returns empty optional if null
- `empty()` → creates an empty Optional
- `orElse(T other)` → return value if present, else `other`
- `orElseGet(Supplier<? extends T> other)` → lazily compute default
- `orElseThrow()` → throw exception if empty


### Default and static methods in interface
- Before java 8, interface allow abstract methods only, so adding method breaks all implementing classes.
- `default` -- provides a default implementation of the method of the class
	- can be overridden by implementing class/interface.
- `static` -- does not depend on an instance. 

### Logger
- It is a tool to record runtime information about a program
- It helps track application behavior , debug issues, monitor performance and audit events.