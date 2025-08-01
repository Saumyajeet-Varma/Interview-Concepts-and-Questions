# Classes and Objects

- Objects are entities in real world
- Class is like a blueprint of these entities

## Classes

A class is a user-defined data type, which holds its own data members and member functions that can be accessed and used by creating an instance of that class. A C++ class is like a blueprint for an object.

```cpp
class ClassName {
  private:
    // Private members (not accessible outside)
  
  public:
    // Public members (accessible outside)
    
    // Constructor
    ClassName();

    // Member functions
    void someFunction();
};

```

### Important Concepts with Classes

- **Constructor** – Special method called when an object is created.
- **Destructor** – Cleans up resources when the object goes out of scope.
- **Encapsulation** – Keeping data safe from outside interference.
- **Abstraction** – Hiding complex implementation details.

## Objects

When a class is defined, only the specification (attributes and behaviour) for the object is defined. No memory is allocated to the class definition. To use the data and access functions defined in the class, we need to create its objects.

```cpp
#include <iostream>
using namespace std;

// Define a class
class Car {
  public:
    string brand;
    string model;

    // Constructor
    Car(string b, string m) {
        brand = b;
        model = m;
    }

    // Member function
    void drive() {
        cout << brand << " " << model << " is driving." << endl;
    }
};

int main() {
    // Create objects
    Car car1("Toyota", "Camry");
    Car car2("Honda", "Civic");

    // Call methods
    car1.drive();  // Output: Toyota Camry is driving.
    car2.drive();  // Output: Honda Civic is driving.

    return 0;
}

```

### Access Specifiers

we can control the access to the members of the class using Access Specifiers. Also known as access modifier, they are the keywords that are specified in the class and all the members of the class under that access specifier will have particular access level.

| Keyword     | Meaning                               |
| ----------- | ------------------------------------- |
| `public`    | Accessible from outside the class     |
| `private`   | Only accessible within the class      |
| `protected` | Accessible in derived (child) classes |

```cpp
class Example
{
private:
    int pvtData;

public:
    int data;

    void show()
    {
        cout << data << endl;
        cout << data * pvtData;
    }

    // Setter
    void setPvtData(int val)
    {
        pvtData = val;
    }

    // Getter
    int getPvtData()
    {
        return pvtData;
    }
};

int main()
{
    Example e;

    e.data = 10;
    e.setPvtData(5);

    cout << e.getPvtData() << endl;
    e.show();

    return 0;
}

```

> we will learn about `Protected` keyword, while learning about **Inheritence**