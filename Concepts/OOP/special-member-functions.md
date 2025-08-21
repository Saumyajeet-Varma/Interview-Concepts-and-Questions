# Special Member Functions

## Constructor

Special method invoked automatically at the time of object creation. Used for initialisation.

- Same name as class
- Constructor doesn't has return type, not even void
- Only called once (automatically), at object creation
- Memory allocation happens when constructor is called

```cpp
class Person
{
public:
    string name;

    Person()
    {
        name = "Samm";
    }
};

int main()
{
    Person p1;

    cout << p1.name;

    return 0;
}

```

### Types of Constructor

#### Default Constructor

No parameters

```cpp
Person() 
{
    name = "Unknown";
}

```

#### Parametrized Constructor

Takes parameters to initialize the object

```cpp
Person(string givenName) 
{
    name = givenName;
}

```

**This pointer**:

```cpp
Person(string name)
{
    this->name = name;
}

```

#### Copy Constructor

Creates a copy of an existing object

```cpp
Person(const Person &p) 
{
    name = p.name;
}

```

> A Class can have multiple constructor (Overloading)

## Destructor

A destructor is a special function that is automatically called when an object is destroyed (e.g., goes out of scope).

- Same name as class but prefixed with `~`
- No return type, no parameters
- Used to release resources (like memory, file handles, etc.)

```cpp
class Person
{
public:
    string name;

    Person(string givenName)
    {
        name = givenName;
        cout << "Constructor called for " << name << endl;
    }

    ~Person()
    {
        cout << "Destructor called for " << name << endl;
    }
};

int main()
{
    Person p1("Samm");
    Person p2("Sv");

    return 0;
}
```

Output:

```
Constructor called for Samm
Constructor called for Sv
Destructor called for Sv
Destructor called for Samm
```

> Destructor is called in reverse order of creation when objects go out of scope.