

## 1. golden ratio
	golden proportion or the divine proportion, is a ratio between two numbers that equals approximately 1.618

 
## interpolation 
 - using `{}` to print a variable in html

# JAVA
### constant pool 
	used in strings an area in heap memory where Java stores literal string values. The heap is an area of memory used for run-time operations. When a new variable is created and given a value, Java checks to see if that exact value exists in the pool.

# general
## deep and shallow copy

| Shallow Copy                                                                                  | Deep Copy                                                                                    |
| --------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| Shallow Copy stores the references of objects to the original memory address.                 | Deep copy stores copies of the object’s value.                                               |
| Shallow Copy reflects changes made to the new/copied object in the original object.           | Deep copy doesn’t reflect changes made to the new/copied object in the original object.      |
| Shallow Copy stores the copy of the original object and points the references to the objects. | Deep copy stores the copy of the original object and recursively copies the objects as well. |
| A shallow copy is faster.                                                                     | Deep copy is comparatively slower.                                                           |

### Evaluation metrics
- #### accuracy
	- It calculated by dividing models correct predictions with the total predictions 
- #### Precision
	- Measure the proportion of correctly predicted positive predictions out of all instances predicted as positive
- #### Recall
	- Measure the proportion of all the correctly predicted positive out of count of actual positive instances
- #### F1 score
	- Mean of both precision and recall

## API
- a set of rules and specifications that allow different software systems to communicate


### java vs c++
| **Parameters**        | **Java**                                                                                            | **C++**                                                                                    |
| --------------------- | --------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| Platform Dependency   | Platform-independent, Java bytecode works on any operating system.                                  | Platform dependent should be compiled for different platforms.                             |
| Compilation           | Java is both a Compiled and Interpreted Language.                                                   | C++ is a Compiled Language.                                                                |
| Memory Management     | Memory Management is System Controlled.                                                             | Memory Management in C++ is Manual.                                                        |
| Virtual Keyword       | It doesn't have Virtual keywords.                                                                   | It has Virtual keywords.                                                                   |
| Multiple Inheritance  | It supports only single inheritance. Multiple inheritances are achieved partially using interfaces. | It supports both single and multiple Inheritance                                           |
| Overloading           | It supports only method overloading and doesn't allow operator overloading.                         | It supports both method and operator overloading.                                          |
| Pointers              | It has limited support for pointers.                                                                | It strongly supports pointers                                                              |
| Documentation Comment | It supports documentation comments (e.g., /**.. */) for source code.                                | It doesn’t support documentation comments for source code.                                 |
| Thread Support        | Java provides built-in support for multithreading.                                                  | C++ doesn’t have built-in support for threads, depends on third-party threading libraries. |
| Type                  | Java is only an object-oriented programming language                                                | C++ is both a procedural and an object-oriented programming language.                      |
| goto Keyword          | Java doesn't support the goto Keyword                                                               | C++ supports the goto keyword                                                              |
| Parameter Passing     | Java supports only the Pass by Value technique.                                                     | C++ supports both Pass by Value and pass-by-reference.                                     |
| Global Scope          | It supports no global scope.                                                                        | It supports both global scope and namespace scope.                                         |
| Object Management     | Automatic object management with garbage collection.                                                | It supports manual object management using new and deletes.                                |
| Hardware              | Java is not so interactive with hardware.                                                           | C++ is nearer to hardware.                                                                 |
