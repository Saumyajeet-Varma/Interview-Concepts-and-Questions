# Object Oriented Programming

Object Oriented Programming - As the name suggests uses objects in programming. Object-oriented programming aims to implement real-world entities like inheritance, hiding, polymorphism, etc. in programming. The main aim of OOP is to bind together the data and the functions that operate on them so that no other part of the code can access this data except that function.

# Characteristics of an Object-Oriented Programming

- Class
- Objects
- Data Abstraction 
- Encapsulation
- Inheritance
- Polymorphism

## Class

The building block of Object-Oriented programming in C++ is a Class. It is a user-defined data type that act as a blueprint representing a group of objects which share some common properties and behaviours. These properties are stored as data members, and the behaviour is represented by member functions.

**For example**, consider the class of Animals. An Animal class could have common properties like name, age, and species as data members, and behaviors like eat, sleep, and makeSound as member functions. Each individual animal object (such as a dog, cat, or elephant) can be created from this blueprint, and each will have its own unique values for the properties (like the name and age), but all will share the same behaviours defined by the class (like eating, sleeping, and making sounds).

A class is defined using the keyword `class` as shown:

```cpp
class Animal {
public:
    string species;
    int age;
    int name;
    
    // Member functions
    void eat() {
        // eat something
    }
    void sleep() {
        // sleep for few hrs
    }
    void makeSound () {
        // make sound;
    }
};
```

> A blueprint for creating objects. <br> Defines attributes (variables) and behaviors (methods).

## Object

An Object is an identifiable actual entity with some characteristics and behaviour. In C++, it is an instance of a class. For Example, the Animal class is just a concept or category, not an actual entity. But a black cat named VoidShadowDarkFangReaper is actual animal that exists. Similarly, classes are just the concepts and objects are the actual entity that belongs to that concept.

When a class is defined, no memory is allocated but when it is instantiated (i.e. an object is created) memory is allocated. In the above example, even though we have defined the Animal class, it cannot be used if there are no objects of the class. An object of a class is created as shown

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    string species;
    int age;
    int name;
    
    // Member functions
    void eat() {
        // eat something
    }
    void sleep() {
        // sleep for few hrs
    }
    void makeSound () {
        // make sound;
    }
};

int main() {
    Animal VoidShadowDarkFangReaper;
}
```

Objects take up space in memory and have an associated address like a record in pascal or structure or union. When a program is executed, the objects interact by sending messages to one another. Each object contains data and code to manipulate the data. Objects can interact without having to know details of each other's data or code, it is sufficient to know the type of message accepted and the type of response returned by the objects.

> An instance of a class. <br> Has its own state and can perform actions defined by the class.

## Encapsulation

Objects take up space in memory and have an associated address like a record in pascal or structure or union. When a program is executed, the objects interact by sending messages to one another. Each object contains data and code to manipulate the data. Objects can interact without having to know details of each other's data or code, it is sufficient to know the type of message accepted and the type of response returned by the objects.

> Hides internal details of objects and exposes only necessary parts. <br> Achieved using access modifiers (e.g., `private`, `public`, `protected`). <br> Ensures data security and reduces complexity.

## Abstraction

Abstraction is one of the most essential and important features of object-oriented programming in C++. Abstraction means displaying only essential information and ignoring the other details. Data abstraction refers to providing only essential information about the data to the outside world, hiding the background details or implementation. In our case, when we call the makeSound() method, we don't need to know how the sound is produced internally, only that the method makes the animal sound.

> Hides complex implementation details and shows only essential features. <br> Focuses on what an object does instead of how it does it. <br> Achieved through abstract classes or interfaces.

## Polymorphism

The word polymorphism means having many forms. In simple words, we can define polymorphism as the ability of an entity to behave different in different scenarios. person at the same time can have different characteristics.

For example, the same `makeSound()` method, the output will vary depending on the type of animal. So, this is an example of polymorphism where the `makeSound()` method behaves differently depending on the Animal type (Dog or Cat).

In C++, polymorphism can be of three types:

- **Operator Overloading**: The process of making an operator exhibit different behaviours in different instances is known as operator overloading.
- **Function Overloading**: Function overloading is using a single function name to perform different types of tasks.
- **Function Overriding**: Function overriding is changing the behaviour of a function that is derived from the base class using inheritance.

> Means "many forms". <br> The same function or method behaves differently based on the context.

## Inheritance

The capability of a class to derive properties and characteristics from another class is called Inheritance. Inheritance is one of the most important features of Object-Oriented Programming.

- **Sub Class**: The class that inherits properties from another class is called Sub class or Derived Class.
- **Super Class**: The class whose properties are inherited by a sub-class is called Base Class or Superclass.

Inheritance supports the concept of “reusability”, i.e. when we want to create a new class and there is already a class that includes some of the code that we want, we can derive our new class from the existing class. By doing this, we are reusing the fields and methods of the existing class.

**Example**: Dog, Cat, Cow can be Derived Class of Animal Base Class.

> Enables one class to inherit properties and methods from another. <br> Promotes code reuse. <br> Supports hierarchical classification (e.g., Dog → Animal).

