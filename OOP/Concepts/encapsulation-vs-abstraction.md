# Encapsulation vs Abstraction

## Encapsulation

**Encapsulation** is defined as the wrapping up of data and information in a single unit. In Object Oriented Programming, encapsulation is defined as binding together the data and the functions that manipulate them.

> Encapsulation is wrapping up of data and member functions in a single unit called class.

In C++, OOPs encapsulation is implemented using classes and access specifiers that keeps the data, and the manipulating methods enclosed inside a single unit. The direct advantage of this packaging is that only the required components are visible to the user, and other information is hidden.

### Real-life example

Consider a real-life example of encapsulation, in a company, there are different sections like the accounts section, finance section, sales section, etc. Now,

- The finance section handles all the financial transactions and keeps records of all the data related to finance. All the financial processes are done by this section.
- Similarly, the sales section handles all the sales-related activities and keeps records of all the sales.

### Example of Encapsulation

```cpp
#include <iostream>
using namespace std;

class EncapsulationExample {
private:
    // we declare a as private to hide it from outside
    int a; 

public:
    // set() function to set the value of  a
    void set(int x) 
    {
        a = x;
    }

    // get() function to return the value of a
    int get() 
    {
        return a;
    }
};

// main function
int main() 
{
    EncapsulationExample e1;

    e1.set(10);

    cout<<e1.get();
    return 0;
}
```

### Advantages of Encapsulation

- **Modularity**: Encapsulation promotes modularity by organizing code into separate objects that handle specific tasks, making the program more structured and easier to manage.
- **Code Maintenance**: Encapsulation helps in maintaining and updating the code more easily.
- **Improved Security**: By hiding data and restricting unauthorized access to it, encapsulation improves the security of the program.
- **Decoupling**: It helps in reducing the dependency between components of a system, allowing them to function independently and making the system easier to maintain and extend.
- **Facilitates Implementation of Other OOP Features**: It also makes it possible to implement other OOPs features such as polymorphism, inheritance, abstraction, etc.

## Abstraction

**Data abstraction** is one of the most essential and important features of object-oriented programming in C++. Abstraction means displaying only essential information and ignoring the details. Data abstraction refers to providing only essential information about the data to the outside world, ignoring unnecessary details or implementation.

### Real-life example

Consider a real-life example of a man driving a car. The man only knows that pressing the accelerator will increase the speed of the car or applying brakes will stop the car but he does not know how on pressing the accelerator the speed is actually increasing, he does not know about the inner mechanism of the car or the implementation of the accelerator, brakes, etc in the car. This is what abstraction is.

### Types of Abstraction
- **Data abstraction** - This type only shows the required information about the data and ignores unnecessary details.
- **Control Abstraction** - This type only shows the required information about the implementation and ignores unnecessary details.

### Abstraction using Classes

We can implement Abstraction in C++ using classes. The class helps us to group data members and member functions using available access specifiers. A Class can decide which data member will be visible to the outside world and which is not. 

### Abstraction in Header files

One more type of abstraction in C++ can be header files. For example, consider the pow() method present in math.h header file. Whenever we need to calculate the power of a number, we simply call the function pow() present in the math.h header file and pass the numbers as arguments without knowing the underlying algorithm according to which the function is actually calculating the power of numbers.

### Abstraction using Access Specifiers

Access specifiers are the main pillar of implementing abstraction in C++. We can use access specifiers to enforce restrictions on class members. For example:

- Members declared as **public** in a class can be accessed from anywhere in the program.
- Members declared as **private** in a class, can be accessed only from within the class. They are not allowed to be accessed from any part of the code outside the class.

### Example of Abstraction

```cpp
#include <iostream>
using namespace std;

class Summation {
private:
    // private variables
    int a, b, c; 
public:
    void sum(int x, int y)
    {
        a = x;
        b = y;
        c = a + b;
        cout<<"Sum of the two number is : "<<c<<endl;
    }
};
int main()
{
    Summation s;
    s.sum(5, 4);
    return 0;
}
```

### Advantages of Abstraction

- Helps the user to avoid writing the low-level code
- Avoids code duplication and increases reusability.
- Can change the internal implementation of the class independently without affecting the user.
- Helps to increase the security of an application or program as only important details are provided to the user.
- It reduces the complexity as well as the redundancy of the code, therefore increasing the readability.
- New features or changes can be added to the system with minimal impact on existing code.

# Encapsulation vs Abstraction

## Encapsulation

Encapsulation is the process or method to contain the information. Encapsulation is a method to hide the data in a single entity or unit along with a method to protect information from outside world. This method encapsulates the data and function together inside a class which also results in data abstraction. 

## Abstraction

In OOPs, Abstraction is the method of getting information where the information needed will be taken in such a simplest way that solely the required components are extracted, and also the ones that are considered less significant are unnoticed. The concept of abstraction only shows necessary information to the users. It reduces the complexity of the program by hiding the implementation complexities of programs. 

## Differences

| Encapsulation                                                                                   | Abstraction                                                                 |
|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| Encapsulation is the process or method to contain the information.                              | Abstraction is the process or method of gaining the information.           |
| In encapsulation, problems are solved at the implementation level.                              | In abstraction, problems are solved at the design or interface level.      |
| Encapsulation is a method to hide the data in a single entity or unit and protect it from outside. | Abstraction is the method of hiding the unwanted information.              |
| Encapsulation can be implemented using access modifiers i.e. private, protected, and public.    | We can implement abstraction using abstract classes and interfaces.        |
| Data is hidden using methods like getters and setters.                                           | Implementation complexities are hidden using abstract classes and interfaces. |
| The objects that result in encapsulation need not be abstracted.                                | The objects that help to perform abstraction are encapsulated.             |
