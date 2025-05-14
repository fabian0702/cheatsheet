# Classes
Classes in C++ are similar to structs, being objects which can contain member variables and member functions. The main difference is that member variables are private by default (important for exams as this can make code that looks valid fail to compile).

```cpp
class MyClass {
private:
    int privateVar;  // private by default
    void privateFunc();
    
public:
    int publicVar;
    void publicFunc();
    
protected:
    int protectedVar;
};
```

### Constructor
Constructors are special member functions used to initialize new objects. Here are key aspects:

#### Constructor Types
```cpp
class Example {
public:
    // Default constructor
    Example() {}
    
    // Parameterized constructor
    Example(int x) : value(x) {}
    
    // Copy constructor
    Example(const Example& other) : value(other.value) {}
    
private:
    int value;
};
```

#### Key Characteristics
- Must have same name as the class
- Called automatically when object is created

### Definition Location
```cpp
// Inside class (common)
class Inside {
public:
    Inside() {} 
};

// Outside class
class Outside {
public:
    Outside();
};
Outside::Outside() {}
```

### Access Modifiers

#### private
Private variables/functions are only accessible to member functions and will cause compiler errors if accessed from outside the class. All members before the first access modifier or after `private:` are private by default.

#### public
Public members are accessible from anywhere the object is visible.

#### Example
```cpp
class Person {
private:
    string name;
    int age;
    
public:
    Person(string n, int a) : name(n), age(a) {}
    void displayInfo() {
        cout << name << " is " << age << " years old" << endl;
    }
};
```

#### Key Points
- Members are private by default
- Constructor can be used to initialize members
- Member functions can access private members

### Member Function Definitions

Member functions can be defined in two ways:

#### 1. Inside Class Definition
```cpp
class Rectangle {
    int width, height;
public:
    void setValues(int w, int h) {  // Defined inside
        width = w;
        height = h;
    }
};
```

#### 2. Outside Class Definition
```cpp
class Rectangle {
    int width, height;
public:
    void setValues(int w, int h);  // Declaration only
    int getArea();
};

// Use ClassName:: to define outside
void Rectangle::setValues(int w, int h) {
    width = w;
    height = h;
}

int Rectangle::getArea() {
    return width * height;
}
```

#### Key Points About Member Functions
- Outside definitions need the scope resolution operator `::`
- Declaration must be in the class even if defined outside
- Large functions are typically defined outside for better readability
- Header files usually contain only declarations

### Structure / Files

C++ classes are typically split into two files:

#### Header File (.h)
```cpp
// MyClass.h
class MyClass {
    int x;
public:
    void func();  // Declaration only
};
```
- Contains class declaration
- Includes member declarations
- Used in other files that need the class

#### Implementation File (.cpp)
```cpp
// MyClass.cpp
#include "MyClass.h"

void MyClass::func() {  // Definition
    // Implementation here
}
```
- Contains actual implementations of the classes defined in the .h file
- Must include corresponding header in the .cpp file
- Basically never include .cpp files in other files

#### Why do it?
- Code organization (All definitions are in one place without the implementation makeing them cluttered)   
- Compilation efficiency (doen't need to compile the same code multiple times)   
