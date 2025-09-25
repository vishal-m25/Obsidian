
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
### JVM ( Java Virtual Machine)
- also known as interpreter
- uses JIT (just in time: converted from byte-code to machine code wile runtime) for faster execution
- works:
	- **loading
	- **linking 
	- **initialization
	- **garbage collection
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

### symbol table
- helps find scope of variable, type checking, verify proper calling of functions.
- helps allocate and track memory

### Execution
- The first file to be executed is **java.exe** which is the JVM launcher.
- stages
	- **ClassLoader
		- primordial/bootstrap classloader -- default class loader (the  first special class loader that loads the bootloader class, written in machine code)
			- Loads the necessary classes required for JRE and JVM to function 
		- non-primordial/extension classloader -- all the class loader other than the bootloader class. like libraries
		- user-defined classloader
		
	- **Bytecode verifier 6
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
- Instance variable /non-static field   -----  within a class
- class variable / static fields    -----  within a class
- local variable   ------ inside a function
- parameters 



| Aspect              | JDK                                             | JRE                                    | JVM                                                      |
| ------------------- | ----------------------------------------------- | -------------------------------------- | -------------------------------------------------------- |
| Purpose             | Used to develop Java applications               | Used to run Java applications          | Executes Java bytecode                                   |
| Platform Dependency | Platform-dependent (OS specific)                | Platform-dependent (OS specific)       | JVM is OS-specific, but bytecode is platform-independent |
| Includes            | JRE + Development tools (javac, debugger, etc.) | JVM + Libraries (e.g., rt.jar)         | ClassLoader, JIT Compiler, Garbage Collector             |
| Use Case            | Writing and compiling Java code                 | Running a Java application on a system | Convert bytecode into native machine code                |
|                     |                                                 |                                        |                                                          |

## Naming Convention

| Identifier Type                                     | Rules for Naming                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Examples                                                                                                          |
| --------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| Packages<br><br>(all lowercase)                     | The prefix of a unique package name is always written in all-lowercase ASCII letters and should be one of the top-level domain names, currently com, edu, gov, mil, net, org, or one of the English two-letter codes identifying countries as specified in ISO Standard 3166, 1981.<br><br>Subsequent components of the package name vary according to an organization's own internal naming conventions. Such conventions might specify that certain directory name components be division, department, project, machine, or login names.                                                                                                                                  | com.sun.eng<br><br>com.apple.quicktime.v2<br><br>edu.cmu.cs.bovik.cheese                                          |
| Classes<br>(noun with first letter capital)         | Class names should be nouns, in mixed case with the first letter of each internal word capitalized. Try to keep your class names simple and descriptive. Use whole words-avoid acronyms and abbreviations (unless the abbreviation is much more widely used than the long form, such as URL or HTML).                                                                                                                                                                                                                                                                                                                                                                       | class Raster;  <br>class ImageSprite;                                                                             |
| Interfaces<br>(first letter capital)                | Interface names should be capitalized like class names.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | interface RasterDelegate;  <br>interface Storing;                                                                 |
| Methods<br>                                         | Methods should be verbs, in mixed case with the first letter lowercase, with the first letter of each internal word capitalized.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | run();  <br>runFast();  <br>getBackground();                                                                      |
| Variables                                           | Except for variables, all instance, class, and class constants are in mixed case with a lowercase first letter. Internal words start with capital letters. Variable names should not start with underscore _ or dollar sign $ characters, even though both are allowed.<br><br>Variable names should be short yet meaningful. The choice of a variable name should be mnemonic- that is, designed to indicate to the casual observer the intent of its use. One-character variable names should be avoided except for temporary "throwaway" variables. Common names for temporary variables are `i`, `j`, `k`, `m`, and `n` for integers; `c`, `d`, and `e` for characters. | int             i;<br><br>char            c;<br>float           myWidth;                                          |
| Constants<br>(All caps with underscore btwn words ) | The names of variables declared class constants and of ANSI constants should be all uppercase with words separated by underscores ("_"). (ANSI constants should be avoided, for ease of debugging.)                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | static final int MIN_WIDTH = 4;<br><br>static final int MAX_WIDTH = 999;<br><br>static final int GET_THE_CPU = 1; |

### Packages
| Need                                                                     |     |
| ------------------------------------------------------------------------ | --- |
| Modularity<br>to avoid naming clash between classes<br>code Organization |     |
|                                                                          |     |



## keywords
| Category         | Keywords                                                                          |
| ---------------- | --------------------------------------------------------------------------------- |
| Data Types       | byte, short, int, long, float, double, boolean, char                              |
| Access Modifiers | public, private, protected                                                        |
| Control Flow     | if, else, switch, case, default, while, do, for, break, continue, return          |
| Error Handling   | try, catch, finally, throw, throws                                                |
| Object-Oriented  | class, interface, extends, implements, this, super                                |
| Memory/Threads   | new, static, final, abstract, synchronized, volatile, transient, native, strictfp |
| Other Useful     | instanceof, import, package, assert, enum, void                                   |
|                  |                                                                                   |

- ### Default keyword
	- this keyword can only be used in two places
		- switch case
		- [[#Interface]]

## Access modifiers 

| Context                        | Default | Private | Protected | Public |
| ------------------------------ | ------- | ------- | --------- | ------ |
| Same Class                     | Yes     | Yes     | Yes       | Yes    |
| Same Package Subclass          | Yes     | No      | Yes       | Yes    |
| Same Package Non-Subclass      | Yes     | No      | Yes       | Yes    |
| Different Package Subclass     | No      | No      | Yes       | Yes    |
| Different Package Non-Subclass | No      | No      | No        | Yes    |
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

| Type    | Description                    | Default | Size                             | Example Literals                            | Range of values                                               |
| ------- | ------------------------------ | ------- | -------------------------------- | ------------------------------------------- | ------------------------------------------------------------- |
| boolean | true or false                  | false   | JVM-dependent (typically 1 byte) | true, false                                 | true, false                                                   |
| byte    | 8-bit signed integer           | 0       | 1 byte                           | (none)                                      | -128 to 127                                                   |
| char    | Unicode character(16 bit)      | \u0000  | 2 bytes                          | 'a', '\u0041', '\101', '\\', '\', '\n', 'β' | 0 to 65,535 (unsigned)                                        |
| short   | 16-bit signed integer          | 0       | 2 bytes                          | (none)                                      | -32,768 to 32,767                                             |
| int     | 32-bit signed integer          | 0       | 4 bytes                          | -2,0,1                                      | -2,147,483,648<br>to<br>2,147,483,647                         |
| long    | 64-bit signed integer          | 0L      | 8 bytes                          | -2L,0L,1L                                   | -9,223,372,036,854,775,808<br>to<br>9,223,372,036,854,775,807 |
| float   | 32-bit IEEE 754 floating-point | 0.0f    | 4 bytes                          | 3.14f, -1.23e-10f                           | ~6-7 significant decimal digits                               |
| double  | 64-bit IEEE 754 floating-point | 0.0d    | 8 bytes                          | 3.1415d, 1.23e100d                          | ~15-16 significant decimal digits                             |

### Primitive types
- these are reserved keywords defined by **Java Language Specification(JLS)**
- These are supported directly by JVM
- ON initialization the value are directly stored not stored as reference
- Supports autoboxing and unboxing

### Wrapper classes
- Create to wrap the primitive types in java
- since all the application in java deal with objects, so to adapt the primitive to objects wrapper class is introduced
- it is **Immutable**
- Provides many utility functions to wonk on the primitive type and their values



### Operators
| Operators            | Precedence                                | execute from      |
| -------------------- | ----------------------------------------- | ----------------- |
| postfix              | `_expr_++ _expr_--`                       | right to left     |
| unary                | `++_expr_ --_expr_ +_expr_ -_expr_ ~ !`   | right to left     |
| multiplicative       | `* / %`                                   | left to right     |
| additive             | `+ -`                                     | left to right     |
| shift                | `<< >> >>>`                               | left to right     |
| relational           | `< > <= >= instanceof`                    | left to right     |
| equality             | `== !=`                                   | left to right     |
| bitwise AND          | `&`                                       | left to right     |
| bitwise exclusive OR | `^`                                       | left to right     |
| bitwise inclusive OR | `\|`                                      | left to right<br> |
| logical AND          | `&&`                                      | left to right<br> |
| logical OR           | `\|`                                      | left to right<br> |
| ternary              | `? :`                                     | right to left     |
| assignment           | `= += -= *= /= %= &= ^= \|= <<= >>= >>>=` | left to right<br> |
### Instanceof
- used to compare an object on a specified type. or test if an object is an instance of a class, an instance of a subclass, or an instance of a class that implements a particular interface.

### Enum 
- A special data type that enables a variable to be set of a predefined constants
- it is final by design
- can implement interfaces
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




### Compile-Time Constant 
- When the compiler knows the constant value of the primitive type variables during compilation. It replaces all the variables with the value during the compile time itself

### Expressions
- An _expression_ is a construct made up of variables, operators, and method invocations, which are constructed according to the syntax of the language, that evaluates to a single value.

### Statement
- These are similar to sentence in natural language. A statement forms  a complete form of execution. Some expressions with semicolon in the end represents a statement.

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
		-  a plain `break` keyword that break the loop in which it is present(the immediate loop from its scope)


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
		-  a plain `continue` keyword that skips the current iteration the loop in which it is present(the immediate loop from its scope)

### Components of method declaration
- **Modifier
- **Return Type
- **Method Name
- **Parameters
- **Exception list
- **Method Body

### Method Signature ---- Method name and Parameters

- #### Note -- two methods with same signature and different return types cannot exist, because compiler does not consider return type while differentiating the methods

**Note** --- All classes have at least one constructor. If a class does not explicitly declare any, the Java compiler automatically provides a no-argument constructor, called the **_default constructor_**. This default constructor calls the class parent's no-argument constructor, or the `Object` constructor if the class has no other parent. If the parent has no constructor (`Object` class does have one), the compiler will reject the program. ( This  occurs when a parent class has a parameterized constructor and the child class does not have a constructor. then on trying to create an object in child class will be an error)

**Note** --- Initialization of parent class should be only in the first of the constructor. (i.e: `super()` )

**Covariant return type** --- If a function has a class as its return type, then it can return on object referring to the class itself or to its subclass.

### Garbage Collector
-  An object is eligible for garage collection only if there is no more references to it in the future.


## Class

### Initialization order
- **static variables → static blocks → instance variables → instance blocks → constructor**.
- A **`final`** variable declared but **not initialized** (blank final) can only be initialized inside a **constructor or initializer block**.

### Constructor
- final keyword cannot be given to a constructor
- types 
	- default constructor
	- parameterized constructor
	- No-argument constructor
	- Copy constructor


### Initialization block
- **Instance Initialization Block
	- Used when the initialization is complex and has to be shared across many constructors
	- runs everytime an object is created
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
- It is used when the sub-classes wanted to use the same initialization code as the parent then can be inherited and used, since the static method does not override on inheritance.

### Static method restrictions
- Can only access fields or methods that are static
- Cannot override them
- cannot have **this** or **super** keyword in them

### Override restrictions
- You cannot override a **static/final/private** method.
- __protected__ method can only be overridden as __protected__



### Tightly Coupled
- when change in one class does force the other class to change in implementation then it is said to be tightly coupled.
- has less number of classes compared to loose coupling 

### Loosely coupled
- when change in one class does not affect the structure of another which is using it then it is loosely coupled.
- implementation relies heavily on interface and abstract classes.
- does include more classes but end up being more flexible than tight due to its representation restrictions.

### Interface 
- it is a blueprint for a class, serving as a contract that defines a set of abstract methods and constant fields. It specifies what a class should do, but not how it should do it.
- Interface can be inherited
- Provide complete abstraction
- **`default`** keyword is allowed in here
	- in need of adding new member or function and that is not needed to be a part of all the implemented class then default keyword is used

### Functional interface
- Has only one abstract method irrespective of the other methods
- **Consumer** -- when dealing with single argument
- **Predicate** -- when dealing with boolean value
- **Supplier** -- Does not take argument but returns value
- **Function** --when dealing with single argument and in need of return functionality


### Abstract class
- Provides partial abstraction
- can have both concrete or abstract methods
- cannot have instance
- can be public, final, default


 
## Nested classes
- **Why 
	- to logically group the classes and streamline the packages.
	- Increases encapsulation
- **Note** --- all the nested class has to utilize the __instance__ fields or a methods from the enclosing class with the help of an object
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

### Shadowing
- If a declaration in the enclosing class is the same in the nested class then the field of the enclosing class is shadowed
- The enclosing class variable should be accessed with **`ClassName.this.x`**


### Serialization 
- **it is converting of objects into byte stream so that it can be 
	- saved in a file
	- transferred through a network
- It is done with the help of **Serializable** interface
- Helps in storing the current state of an object and reuse it later
```java 
import java.io.*;

public class SerializeExample {
    public static void main(String[] args) {
        Student s1 = new Student(101, "Alice");

        try {
            FileOutputStream fos = new FileOutputStream("student.ser");
            ObjectOutputStream oos = new ObjectOutputStream(fos);

            oos.writeObject(s1); // 🔹 Serialization
            oos.close();
            fos.close();

            System.out.println("✅ Object serialized and saved to student.ser");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

```

### Local Classes
- can be created inside a block
- has direct access to all the final and static variable of the enclosing class
- **Accessibility
	- can access enclosing class fields and members
	- can access final or effectively final variables 

### Anonymous class
-  You can also declare an inner class within the body of a method without naming the class. 
- instance and member access is same as local class
- Can be created with
	- Interface
	- extend an abstract or concrete class
	
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
                // printing  age
                System.out.print("Age is " + x);
            }
        };
      
        oj1.getAge();
    }
}
```

- Types
	- By implementing interface
	- By extending a class
	- Passed as argument inside a method
```java
abstract class Shape {
    abstract void draw();
}

public class Main {
    static void printShape(Shape s) {
        s.draw();   // ✅ Here we call the overridden method
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

## Exception 
- It is an exceptional event that occurs during the execution of the program that disrupts the flow of instructions.
- when an exceptional event occurs, the method creates an object called __exception__ and sends it to the runtime system.
- when an exception occurs, runtime searches the call stack(method invocations) sequentially to check for an matching exception handler, if matches, handles it and continues the program from that point, else the program is terminated.

- **Checked exception** 
	- Compile time errors
- **Unchecked exception** 
	- Errors
	- Run-time Exceptions
### Suppressed exceptions
- When a try block throws an exception and while closing the resources, the try-wth-resource as well throws an exception then the try-with-resource exception is suppressed within the primary and delivered.
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
- Apart from having the try-catch-finally functionality, it has resources created within parenthesis after `try` keyword
- Such resources should implement **AutoCloseable/Closeable**. interface
- This the resources are automatically closed at the end of try block.

### Chained Exception
- when an exception is caught, it throws another exception to a higher exception handles containing the main exception .
- it helps in associating one exception with other exception, through proper description.


**Stack trace:** A _stack trace_ provides information on the execution history of the current thread and lists the names of the classes and methods that were called at the point when the exception occurred. A stack trace is a useful debugging tool that you'll normally take advantage of when an exception has been thrown.

### Creating Exception classes
- **Note** -- If a client can reasonably be expected to recover from an exception, make it a checked exception. If a client cannot do anything to recover from the exception, make it an unchecked exception.

### Advantages of exception
- **Separates error/exception prone code from regular code
- **propagates error up the call stack
- **Grouping error types

### Overriding a method that throws an exception
- when parent doesn't throw an exception then the child cannot throw a checked exception but can be unchecked
- the child should not throw an exception that is superset of the parent class exception
- The first throws fewer exceptions than the overridden method, and the second, even though it throws more; they’re narrower in scope.
- parent and child can throw irrelevant exceptions

### Note
- if a methods declared to throw a checked exception is called it should be handled inside a try-catch block or the function itself can be declared of throwing the same exception to avoid compile time interruption.



## Collections
- It inherits Iterable class 

| Key                  | Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| what                 | it is an object that represent a group of objects                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| purpose              | used to store, retrieve, manipulate, and communicate aggregate data effieiency                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Collection interface | `java.util.Collection`                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Sub-interfaces       | - list (ArrayList, LinkedList)<br>- set (HashSet,TreeSet)<br>- queue (PriorityQueue)<br>- deque (ArrayDeque)                                                                                                                                                                                                                                                                                                                                                                                    |
| Advantages           | - Ready-made data structures<br>- Increased performance due to common interface<br>- Provides a common language for passing collection between different APIs.                                                                                                                                                                                                                                                                                                                                  |
| Methods              | The `Collection` interface contains methods that perform basic operations, such as **`int size()`**, **`boolean isEmpty()`**, **`boolean contains(Object element)`**, **`boolean add(E element)`**, <br>**`boolean remove(Object element)`**, and **`Iterator<E> iterator()`**.<br><br>**`boolean containsAll(Collection<?> c)`**, **`boolean addAll(Collection<? extends E> c)`**, **`boolean removeAll(Collection<?> c)`**, **`boolean retainAll(Collection<?> c)`**, and **`void clear()`**. |

### Collection Framework
- Unified architecture for representing and manipulating collections
- **final** keyword on list object will only stop it from reassigning not from appending
- contains
	- Interface
	- implementations
	- algorithm


| Interface | Allows Duplicates | Ordered                   | Sorted                  | Nulls Allowed                            |
| --------- | ----------------- | ------------------------- | ----------------------- | ---------------------------------------- |
| List      | Yes               | Yes                       | No                      | Yes (one null in some cases)             |
| Set       | No                | No (except LinkedHashSet) | Yes (TreeSet)           | Only one null (HashSet)                  |
| Queue     | Yes               | Yes                       | Priority-based possible | One null (except PriorityQueue)          |
| sMap      | No (for keys)     | Depends                   | TreeMap sorted by keys  | One null key (HashMap), many null values |

### Collection interface
- It is used to pass around group of objects where maximum generality is desired.

### For iterations of collections 
- Aggregate functions
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
    list.add(4);  // Safe to modify during iteration
}

```



### Set interface
- This collection does not contain duplicate elements
- general implementation
	- HashSet
	- TreeSet
	- LinkedHashSet
#### TreeSet
- Stores elements in red-black tree
- ordered based on their value
- slower than the rest two
#### LinkedHashSet
- maintains the insertion order
- uses hash function for storing and accessing

#### HashSet
- Does not maintain any order of the elements
- use hash table to store and access elements
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
- **Operations
	- get()
	- set()
	- add()
	- addAll()
	- remove()
	- indexOf()
	- lastIndexOf()
	- listIterator()
	- sublist()
- **Algorithms
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

| Type of Operation | Throws exception                     | Returns special value |
| ----------------- | ------------------------------------ | --------------------- |
| Insert            | `add(e)` on exceeding queue size     | `offer(e)`            |
| Remove            | `remove()` when no element to remove | `poll()`              |
| Examine           | `element()` when queue is empty      | `peek()`              |
- Queue itself does not allow null values ,  **but** queue implemented with LinkedList allows.

### Dequeue interface
- It is a **double-ended queue** 
- It supports insertion and deletion of elements on both the ends
- It implements both stack and queue at the same time

| Type of Operation | First Element (Beginning of the `Deque` instance) | Last Element (End of the `Deque` instance) |
| ----------------- | ------------------------------------------------- | ------------------------------------------ |
| **Insert**        | `addFirst(e)`  <br>`offerFirst(e)`                | `addLast(e)`  <br>`offerLast(e)`           |
| **Remove**        | `removeFirst()`  <br>`pollFirst()`                | `removeLast()`  <br>`pollLast()`           |
| **Examine**       | `getFirst()`  <br>`peekFirst()`                   | `getLast()`  <br>`peekLast()`              |

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

| Feature           | HashSet (unordered) | TreeSet (sorted)                               |
| ----------------- | ------------------- | ---------------------------------------------- |
| Data structure    | HashMap             | TreeMap (Red-Black Tree) ordered BST           |
| Ordering          | None                | Natural / Comparator                           |
| Nulls allowed     | One null            | No nulls                                       |
| Time complexity   | O(1) average        | O(log n)                                       |
| Duplicate allowed | No                  | No                                             |
| Iteration order   | Random              | Sorted                                         |
| Extra methods     | Basic (add, remove) | Navigation methods (first, last, subset, etc.) |

### HashMap
- Collitions
	- handled by putting the same hashcode keys in a bucket and use **`equals`** to differentiate them
- Load factor
	- states how full the hashmap can be before its size is increased.
- Not thread-safe
	- is not synchronized and can lead to racing conditions 
- Hashtable is thread-safe
	- use synchronized methods, but has performance overhead

### LinkedHashMap
- Has features of both hash table and doubly-linkedlist


TreeMap/TreeSet does not allow null value because it maintains certain ordering with the help of comparisons 


**Note** -- you are allowed to create your own immutable collection
- can either be done by
	- implementing existing interface
	- or overriding the available function to create from scratch
- it helps in having 
	- read only collection
	- thread safe collection





### Cursor
- it is an object used to traverse 
### Iterator for collection 
- it is an **interface









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
 - quite not recommended for dealing with text files due to a lot of conversions taking place
 - each of the operation is handled directly by the underlying OS so can be less efficient, cause it follows a lot of procedures

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
        write.close();  // always close the stream after using
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
- Buffered input streams read data from a memory area known as a _buffer_; the native input API is called only when the buffer is empty.
- buffered output streams write data to a buffer, and the native output API is called only when the buffer is full.
- so to call the write API before the buffer is full we use **`.flush()`** to immediately call the API and write in the file.

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
	- format statement --- works very much like **`printf`**
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

- **Console 
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

| Data type | Output Method                  | Input Method                 | Sample Value     |
| --------- | ------------------------------ | ---------------------------- | ---------------- |
| `double`  | `DataOutputStream.writeDouble` | `DataInputStream.readDouble` | `19.99`          |
| `int`     | `DataOutputStream.writeInt`    | `DataInputStream.readInt`    | `12`             |
| `String`  | `DataOutputStream.writeUTF`    | `DataInputStream.readUTF`    | `"Java T-Shirt"` |

```java 
class Hostel{
    public static void main(String[] args)  throws Exception {
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


