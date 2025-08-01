# Static Keyword

In Cpp, the `static` keyword is used in different contexts with different meanings

## Static Variable Inside a Function

- Retains its value across multiple function calls.
- Lifetime: Entire program.
- Scope: Local to the function.

```cpp
void counter() {
    static int count = 0;
    count++;
    std::cout << count << std::endl;
}

int main() {
    counter(); // prints 1
    counter(); // prints 2
    counter(); // prints 3
    return 0;
}

```

## Static Member Variable in a Class

- Shared among all objects of the class.
- Must be defined outside the class as well.

```cpp
class MyClass {
public:
    static int count;
    MyClass() { count++; }
};

int MyClass::count = 0;

int main() {
    MyClass a, b;
    std::cout << MyClass::count << std::endl; // prints 2
}

```

## Static Member Function in a Class

- Can be called without an object.
- Can only access static data members or other static functions.

```cpp
class Math {
public:
    static int square(int x) {
        return x * x;
    }
};

int main() {
    std::cout << Math::square(5); // prints 25
}

```

## Static Global Variable

- Restricts the variable's linkage to the current file (internal linkage).
- Useful in large projects to avoid name collisions.

```cpp
// file1.cpp
static int x = 10; // Not visible in other files

```

## Static Functions at File Scope

- Same as static global variables — limits scope to the file.

```cpp
static void helper() {
    std::cout << "This function is only visible in this file.";
}

```

### Summary

| Use Case                   | Lifetime       | Scope      | Use                  |
| -------------------------- | -------------- | ---------- | -------------------- |
| Inside function            | Entire program | Function   | Preserve state       |
| Static data member         | Entire program | Class-wide | Shared among objects |
| Static member function     | N/A            | Class-wide | Utility functions    |
| Static global var          | Entire program | File       | Avoid name clash     |
| Static file-scope function | Entire program | File       | Internal helper      |
