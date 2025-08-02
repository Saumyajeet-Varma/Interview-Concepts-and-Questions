# Shallow Copy

A shallow copy copies all member field values as-is, including pointer addresses, meaning both objects point to the same memory location.

### Behavior

- Provided by the default copy constructor or assignment operator.

### Problem

- Multiple objects point to the same memory.
- If one object deallocates the memory (e.g., in destructor), the other is left with a dangling pointer → can cause undefined behavior or crash.

```cpp
#include <iostream>
using namespace std;

class Shallow {
public:
    int* data;

    Shallow(int value) {
        data = new int(value);
    }

    // Default copy constructor → shallow copy
    void display() {
        cout << "Value: " << *data << endl;
    }

    ~Shallow() {
        delete data;
    }
};

int main() {
    Shallow obj1(10);
    Shallow obj2 = obj1; // shallow copy

    obj1.display();
    obj2.display();

    return 0; // Destructor called twice on same pointer -> crash
}

```

# Deep Copy

A deep copy creates a new memory allocation and copies the actual value, not just the pointer. Each object has its own copy of data.

### Solution

- Write a custom copy constructor and assignment operator.

```cpp
#include <iostream>
using namespace std;

class Deep {
public:
    int* data;

    Deep(int value) {
        data = new int(value);
    }

    // Custom copy constructor (deep copy)
    Deep(const Deep& source) {
        data = new int(*source.data);
    }

    void display() {
        cout << "Value: " << *data << endl;
    }

    ~Deep() {
        delete data;
    }
};

int main() {
    Deep obj1(20);
    Deep obj2 = obj1; // deep copy

    *obj2.data = 30;

    obj1.display(); // 20
    obj2.display(); // 30

    return 0; // No crash, both objects manage their own memory
}

```

# Shallow Copy vs Deep Copy

| Feature         | Shallow Copy                | Deep Copy                       |
| --------------- | --------------------------- | ------------------------------- |
| Pointer copying | Same memory address         | New memory allocation           |
| Memory safety   | Risk of double delete       | Safe, independent copies        |
| Performance     | Faster                      | Slightly slower                 |
| Use case        | When no dynamic memory used | When object owns dynamic memory |
