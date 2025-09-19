
### Advantages of java 8
-  Introduced lambda fucntion
- Introduced default and static methods in interfaces
- Backward compatibility is mostly intact
- most of the product or service were freely available


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

### Naming Convention
- constraints set to name a variable, package, function or etc...
- keywords cannot be used as identifiers


### keywords
|Category|Keywords|
|---|---|
|Data Types|byte, short, int, long, float, double, boolean, char|
|Access Modifiers|public, private, protected|
|Control Flow|if, else, switch, case, default, while, do, for, break, continue, return|
|Error Handling|try, catch, finally, throw, throws|
|Object-Oriented|class, interface, extends, implements, this, super|
|Memory/Threads|new, static, final, abstract, synchronized, volatile, transient, native, strictfp|
|Other Useful|instanceof, import, package, assert, enum, void|


### Java Structure
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

**Note** --- All classes have at least one constructor. If a class does not explicitly declare any, the Java compiler automatically provides a no-argument constructor, called the _default constructor_. This default constructor calls the class parent's no-argument constructor, or the `Object` constructor if the class has no other parent. If the parent has no constructor (`Object` does have one), the compiler will reject the program. ( This  occurs when a parent class has a parameterized constructor and the child class does not have a constructor. then on trying to create an object in child class will be an error)

**Note** --- Initialization of parent class should be only in the first of the constructor.

**Covariant return type** --- If a function has a class as its return type, then it can return on object referring to the class itself or to its subclass.

### Garbage Collector
-  An object is eligible for garage collection only if there is no more references to it in the future.































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