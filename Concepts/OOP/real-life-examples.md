# Real-life Examples

## Encapsulation

Real-life example: ATM Machine

When using an ATM, you just insert your card, enter PIN, and withdraw money. You don't know how internally your balance is updated — that's encapsulated.

- Data like balance, PIN is kept private.
- Access/modification is done via public methods.

## Abstraction

Real-life example: Driving a Car

You press the accelerator to speed up, but you don’t need to know how the engine works internally. You just use the exposed functionality.

- Expose only necessary functions (drive(), brake()) via public interface.
- Internal logic (engine combustion, fuel injection) is hidden.

## Inheritance

### Single Inheritance

Real-life example: Student inherits properties of a Person

```cpp
class Person {
  public:
    string name;
};

class Student : public Person {
  public:
    int roll;
};

```

### Multiple Inheritance

Real-life example: A Smartphone has features of both a Phone and a Camera

```cpp
class Phone {
  public:
    void call() { cout << "Calling..." << endl; }
};

class Camera {
  public:
    void click() { cout << "Clicking photo..." << endl; }
};

class Smartphone : public Phone, public Camera {};

```

### Multilevel Inheritance

Real-life example: Baby → Parent → Grandparent

```cpp
class Grandparent {
  public:
    void legacy() { cout << "Family legacy" << endl; }
};

class Parent : public Grandparent {};

class Child : public Parent {};

```

### Hierarchical Inheritance

Real-life example: Vehicle as base class → Car, Bike, Bus as derived classes

```cpp
class Vehicle {
  public:
    void move() { cout << "Moving..." << endl; }
};

class Car : public Vehicle {};
class Bike : public Vehicle {};

```

### Hybrid Inheritance

Real-life example: A Teacher is both a Person and an Employee

```cpp
class Person {
  public:
    void intro() { cout << "I am a person" << endl; }
};

class Employee : virtual public Person {};
class Trainer : virtual public Person {};

class Teacher : public Employee, public Trainer {};

```

> Ambiguity may arise if both base classes inherit from the same parent — resolved with virtual keyword.

## Polymorphism

### Method Overloading

Real-life example: Calling a friend (by phone number or name)

You can call someone using their name or their phone number. Both ways perform the same action ("call") but use different inputs.

```cpp
class Call {
  public:
    void makeCall(string name) {
        cout << "Calling " << name << endl;
    }

    void makeCall(int number) {
        cout << "Calling number: " << number << endl;
    }
};

```

### Operator Overloading

Real-life example: '+' used in calculator and text editor

In calculator: 2 + 3 adds numbers. In text editor: "Hello" + "World" joins strings.

```cpp
class Distance {
  public:
    int km;
    Distance(int k) : km(k) {}

    Distance operator+(Distance d) {
        return Distance(km + d.km);
    }
};

```

### Method Overriding

Real-life example: Printer behavior in different brands

Each printer brand has its own implementation of print() but the method name remains the same.

```cpp
class Printer {
  public:
    virtual void print() {
        cout << "Generic printing" << endl;
    }
};

class HP : public Printer {
  public:
    void print() override {
        cout << "Printing using HP printer" << endl;
    }
};

```