
## 30th Sep
### java 8 vs 11 compilation and execution
- ==**Java 8**==
	- needs to be compiled before executing explicitly
	- class-path hell --  due to unspecific class path
- ==**Java 11**==
	- **`java Main.java`** -- does both compilation and execution implicitly
	- Has JMPS (Java Module Path Specification) to avoid class-path hell
### syntax code illegal forward reference
- during compilation 2 steps of occur
	- an iteration to find all the declaration of methods,variables,...
	- then the symbol table is created.
	- now when the bytecode conversion occurs the reference is before initialization.
### package structure// naming package with example
- ==**`com.example.smartnote.addons.calendarsync`**==
- in.zoho.mail.addon.spamidentifier
- in.zoho.mail.addon.spamidentifier.api
- in.zoho.mail.addon.spamidentifier.model

### mutable and immutable
|Mutable|Immutable|
|---|---|
|State can be changed after creation|State cannot be changed after creation|
|Provides setter methods|Does not provide setter methods|
|Changes happen in existing object|Changes create new objects|
|May require synchronization for thread safety|Thread-safe by design|
|Examples: `StringBuilder`, `Date`|Examples: `String`, `Integer`|
- since int directly stores the value,
	- so ==**`int`**== itself is immutable bit ==**int variable**== is mutable
- In ==**`Integer`**== the value is not changes rather reassigned, hence it is immutable
### java multiple inheritance
- using ==**`extends`**== can only inherit one class

### wrapper class
- Collections are a group of objects
- thus object of values are needed, thus a wrapper class provides the classes for the primitive datatypes.
### volatile keyword
- used when referring to a device register
- used in multi-threading.
- makes the changes directly in the main memory instead of thread local cache.
### private constructor
- can be used when all the fields and methods are stated as static.
- To create a singleton class
### final methods overloading
- can be done without any restrictions
### Final method overriding
- cannot be done



## 27th Oct
- ### Transform, indent in string
	- was introduced in java 12
- ### Ways to create object 
	- Using new keyword
	- Using clone() method
	- Using Deserialization
	- Using Constructor.newInstance()  //  from Reflection API 
	- Using ClassName.class.newInstance() // deprecated can only invoke no-argument constructor
- ### Polymorphism relationship 
	- is-a relationship (in terms of inheritance)
	- has-a relationship (in terms of interface)
- ### Can we create instance for interface
	- no, it does not have a constructor
- ### Runtime exceptions 
	- NullPointerException
	- ArithmethicException
	- ArrayIndexOutOfBoundException
	- ClassCastException
	- NumberFormatException
	- IllegalArgumentException
	- IllegalStateException
	- UnSupportedOperationException
- ### Exception package path
	- ==**`java.lang`**== 