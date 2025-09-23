
### Advantages of java 8
- Introduced lambda function
- Introduced default and static methods in interfaces
- Backward compatibility is mostly intact
- most of the product or service were freely available

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

### symbol table
- helps find scope of variable, type checking, verify proper calling of functions.
- helps allocate and track memory

### Execution
- The first file to be executed is **java.exe** which is the JVM launcher.
- stages
	- **ClassLoader
		- primordial -- default class loader (the  first special class loader that loads the bootloader class, written in machine code)
			- the very first class the JVM loads to start the class loading process. 
		- non-primordial -- all the class loader other than the bootloader class.
		- user-defined cassloader
		
	- **Bytecode verifier
		- checks if the code does any damaging actions
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

- ### Default
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
- __protected__ method can only be overriden as __protected__



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

- **Checked exception
	- Compile time errors
- **Unchecked exception
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
- Such resources should implement **AutoCloseable/Closeable**. interfacee 
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



