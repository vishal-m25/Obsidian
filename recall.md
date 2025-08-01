### keys in DBMS
1. primary key
2. candidate key
3. super key
4. foreign key
5. alternate key
6. surrogate key
7. composite key
8. compound key


### Paging algorithms
- First In First Out (FIFO)
- Optimal Page replacement
- Least Recently Used (LRU)
- Most Recently Used (MRU)

### ACID properties in dbms
<img src="Pasted image 20250429094750.png" width="50%" height="50%">

### Extern in C
- `extern` keyword serves to extend the visibility of variables and functions across multiple source files. It is primarily used for declaration, not definition, meaning it informs the compiler that a variable or function is defined elsewhere, typically in another compilation unit.
```c
    // file1.c
    int global_variable = 10; // Definition and initialization

    // file2.c
    extern int global_variable; // Declaration, indicates it's defined elsewhere

    int main() {
        printf("%d\n", global_variable); // Accessing the variable
        return 0;
    }
```



