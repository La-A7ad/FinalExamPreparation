### Exam Questions on Inheritance

#### Emphasis on Fundamentals

### Question 1: Basic Syntax
*What is the correct syntax to define a derived class `Student` from a base class `Person`?*

```cpp
class Person {
    // Base class members
};

class Student : public Person {
    // Derived class members
};
```

   A. `class Student inherits Person { ... };`  
   B. `class Student : private Person { ... };`  
   C. `class Student extends Person { ... };`  
   D. `class Student : public Person { ... };`  

<details>
<summary>Answer</summary>
D. `class Student : public Person { ... };`
</details>

### Question 2: Access Specifiers
*Which access specifier allows members of a base class to be accessible only by objects of its derived classes?*

   A. public  
   B. private  
   C. protected  
   D. internal  

<details>
<summary>Answer</summary>
C. protected
</details>

### Question 3: Inheritance Hierarchy
*In an inheritance hierarchy, which class is at the top?*

   A. Derived class  
   B. Subclass  
   C. Base class  
   D. Child class  

<details>
<summary>Answer</summary>
C. Base class
</details>

#### Application of Concepts

### Question 4: Predicting Outputs
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    Base() {
        cout << "Base's constructor\n";
    }
    ~Base() {
        cout << "Base's destructor\n";
    }
};

class Derived : public Base {
public:
    Derived() {
        cout << "Derived's constructor\n";
    }
    ~Derived() {
        cout << "Derived's destructor\n";
    }
};

int main() {
    Derived d;
    return 0;
}
```

   A. Base's constructor Derived's constructor Derived's destructor Base's destructor  
   B. Derived's constructor Base's constructor Base's destructor Derived's destructor  
   C. Base's constructor Derived's constructor Base's destructor Derived's destructor  
   D. Derived's constructor Base's destructor Derived's destructor Base's destructor  

<details>
<summary>Answer</summary>
A. Base's constructor Derived's constructor Derived's destructor Base's destructor
</details>

### Question 5: Debugging Code
*Identify the error in the following program and correct it.*

```cpp
#include <iostream>
using namespace std;

class Base {
private:
    int x;

public:
    Base(int val) : x(val) {}
    int getX() const { return x; }
};

class Derived : public Base {
public:
    Derived(int val) {
        x = val;
    }
};

int main() {
    Derived d(10);
    cout << d.getX() << endl;
    return 0;
}
```

<details>
<summary>Answer</summary>
The error is that `x` is a private member of the `Base` class and cannot be directly accessed in the `Derived` class. The `Derived` class should call the `Base` constructor with the `val` parameter.

Corrected code:
```cpp
#include <iostream>
using namespace std;

class Base {
private:
    int x;

public:
    Base(int val) : x(val) {}
    int getX() const { return x; }
};

class Derived : public Base {
public:
    Derived(int val) : Base(val) {}
};

int main() {
    Derived d(10);
    cout << d.getX() << endl;
    return 0;
}
```
</details>

### Question 6: Constructors and Destructors
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Parent {
public:
    Parent() {
        cout << "Parent's constructor\n";
    }
    ~Parent() {
        cout << "Parent's destructor\n";
    }
};

class Child : public Parent {
public:
    Child() {
        cout << "Child's constructor\n";
    }
    ~Child() {
        cout << "Child's destructor\n";
    }
};

int main() {
    Child c;
    return 0;
}
```

   A. Parent's constructor Child's constructor Parent's destructor Child's destructor  
   B. Child's constructor Parent's constructor Child's destructor Parent's destructor  
   C. Parent's constructor Child's constructor Child's destructor Parent's destructor  
   D. Parent's constructor Child's constructor Child's destructor Parent's destructor  

<details>
<summary>Answer</summary>
C. Parent's constructor Child's constructor Child's destructor Parent's destructor
</details>

#### Understanding Classes and Structures

### Question 7: Class Design
*Design a class `Teacher` that inherits from a class `Person` and adds a private member `subject` and public methods to set and get the subject. Provide the class definitions.*

```cpp
class Person {
private:
    string name;

public:
    Person() : name("") {}
    void set_name(string n) { name = n; }
    string get_name() const { return name; }
};

class Teacher : public Person {
private:
    string subject;

public:
    void set_subject(string s) { subject = s; }
    string get_subject() const { return subject; }
};
```

### Question 8: Inheritance and Access Specifiers
*What is the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Base {
protected:
    int value;

public:
    Base() : value(0) {}
};

class Derived : public Base {
public:
    void setValue(int val) { value = val; }
    int getValue() const { return value; }
};

int main() {
    Derived d;
    d.setValue(42);
    cout << d.getValue() << endl;
    return 0;
}
```

   A. Compilation error  
   B. 0  
   C. 42  
   D. Undefined behavior  

<details>
<summary>Answer</summary>
C. 42
</details>

### Question 9: Inherited Methods
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    void speak() {
        cout << "Animal speaks" << endl;
    }
};

class Dog : public Animal {
public:
    void speak() {
        cout << "Dog barks" << endl;
    }
};

int main() {
    Dog d;
    d.speak();
    return 0;
}
```

   A. Animal speaks  
   B. Dog barks  
   C. Compilation error  
   D. Undefined behavior  

<details>
<summary>Answer</summary>
B. Dog barks
</details>

### Question 10: Polymorphism
*What is the output of the following program if the `speak` method is declared as `virtual` in the `Animal` class?*

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    virtual void speak() {
        cout << "Animal speaks" << endl;
    }
};

class Dog : public Animal {
public:
    void speak() override {
        cout << "Dog barks" << endl;
    }
};

int main() {
    Animal *a = new Dog();
    a->speak();
    delete a;
    return 0;
}
```

   A. Animal speaks  
   B. Dog barks  
   C. Compilation error  
   D. Undefined behavior  

<details>
<summary>Answer</summary>
B. Dog barks
</details>

### Question 11: Protected Members
*What is the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Base {
protected:
    int num;

public:
    Base() : num(0) {}
    void setNum(int val) { num = val; }
};

class Derived : public Base {
public:
    void printNum() {
        cout << num << endl;
    }
};

int main() {
    Derived d;
    d.setNum(10);
    d.printNum();
    return 0;
}
```

   A. Compilation error  
   B. 0  
   C. 10  
   D. Undefined behavior  

<details>
<summary>Answer</summary>
C. 10
</details>

### Question 12: Private Inheritance
*What is the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    void display() {
        cout << "Base class display" << endl;
    }
};

class Derived : private Base {
public:
    void show() {
        display();
    }
};

int main() {
    Derived d;
    d.show();
    return 0;
}
```

   A. Compilation error  
   B. Base class display  
   C. Undefined behavior  
   D. Derived class display  

<details>
<summary>Answer</summary>
B. Base class display
</details>

### Question 13: Multiple Inheritance
*What is the output of the following program?*

```cpp
#include <iostream>


using namespace std;

class A {
public:
    void display() {
        cout << "Class A" << endl;
    }
};

class B {
public:
    void display() {
        cout << "Class B" << endl;
    }
};

class C : public A, public B {
public:
    void show() {
        A::display();
    }
};

int main() {
    C obj;
    obj.show();
    return 0;
}
```

   A. Class A  
   B. Class B  
   C. Compilation error  
   D. Class A Class B  

<details>
<summary>Answer</summary>
A. Class A
</details>

### Question 14: Function Overriding
*What is the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void display() {
        cout << "Base class display" << endl;
    }
};

class Derived : public Base {
public:
    void display() override {
        cout << "Derived class display" << endl;
    }
};

int main() {
    Base *b;
    Derived d;
    b = &d;
    b->display();
    return 0;
}
```

   A. Base class display  
   B. Derived class display  
   C. Compilation error  
   D. Undefined behavior  

<details>
<summary>Answer</summary>
B. Derived class display
</details>

### Question 15: Virtual Destructor
*What is the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    Base() {
        cout << "Base constructor" << endl;
    }
    virtual ~Base() {
        cout << "Base destructor" << endl;
    }
};

class Derived : public Base {
public:
    Derived() {
        cout << "Derived constructor" << endl;
    }
    ~Derived() {
        cout << "Derived destructor" << endl;
    }
};

int main() {
    Base *b = new Derived();
    delete b;
    return 0;
}
```

   A. Base constructor Derived constructor Derived destructor  
   B. Base constructor Derived constructor Base destructor Derived destructor  
   C. Base constructor Derived constructor Base destructor  
   D. Compilation error  

<details>
<summary>Answer</summary>
B. Base constructor Derived constructor Base destructor Derived destructor
</details>

### Question 16: Function Overloading vs. Overriding
*Which of the following is true about function overloading and function overriding in C++?*

   A. Overloading is defining multiple functions with the same name but different parameters, overriding is redefining a base class function in a derived class.  
   B. Overloading is redefining a base class function in a derived class, overriding is defining multiple functions with the same name but different parameters.  
   C. Overloading and overriding are the same in C++.  
   D. Neither overloading nor overriding exist in C++.  

<details>
<summary>Answer</summary>
A. Overloading is defining multiple functions with the same name but different parameters, overriding is redefining a base class function in a derived class.
</details>

### Question 17: Using `using` in Inheritance
*What is the purpose of the `using` keyword in the context of inheritance in C++?*

   A. It allows the derived class to inherit constructors from the base class.  
   B. It allows the derived class to inherit private members from the base class.  
   C. It allows the derived class to use base class's private methods.  
   D. It allows the derived class to redefine base class's protected methods.  

<details>
<summary>Answer</summary>
A. It allows the derived class to inherit constructors from the base class.
</details>

### Question 18: Accessing Base Class Members
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Base {
protected:
    int value;

public:
    Base(int val) : value(val) {}
};

class Derived : public Base {
public:
    Derived(int val) : Base(val) {}
    void printValue() {
        cout << value << endl;
    }
};

int main() {
    Derived d(100);
    d.printValue();
    return 0;
}
```

   A. 0  
   B. 100  
   C. Compilation error  
   D. Undefined behavior  

<details>
<summary>Answer</summary>
B. 100
</details>

### Question 19: Order of Constructors
*What is the correct order of constructor calls when a derived class object is created?*

   A. Derived class constructor, then base class constructor  
   B. Base class constructor, then derived class constructor  
   C. Derived class constructor only  
   D. Base class constructor only  

<details>
<summary>Answer</summary>
B. Base class constructor, then derived class constructor
</details>

### Question 20: Order of Destructors
*What is the correct order of destructor calls when a derived class object is destroyed?*

   A. Derived class destructor, then base class destructor  
   B. Base class destructor, then derived class destructor  
   C. Derived class destructor only  
   D. Base class destructor only  

<details>
<summary>Answer</summary>
A. Derived class destructor, then base class destructor
</details>
```

### Question 21: Destructor Example 1
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class A {
    int *arr; // private
    int size;

public:
    A(int s) {
        cout << "Constructor executing...\n";
        size = s;
        arr = new int[size];
    }
    ~A() {
        cout << "Destructor executing...\n";
        delete[] arr;
    }
};

int main() {
    A a(10);
    return 0;
}
```

   A. Constructor executing...  
   B. Destructor executing...  
   C. Constructor executing... Destructor executing...  
   D. Compilation error  

<details>
<summary>Answer</summary>
C. Constructor executing... Destructor executing...
</details>

### Question 22: Destructor Example 2
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class A {
    int *arr; // private
    int size;

public:
    A(int s) {
        cout << "Constructor executing...\n";
        size = s;
        arr = new int[size];
    }
    ~A() {
        cout << "Destructor executing...\n";
        delete[] arr;
    }
};

void test() {
    A a(10);
}

int main() {
    test();
    return 0;
}
```

   A. Constructor executing...  
   B. Destructor executing...  
   C. Constructor executing... Destructor executing...  
   D. Compilation error  

<details>
<summary>Answer</summary>
C. Constructor executing... Destructor executing...
</details>

#### Inheritance Basics and Benefits

### Question 23: Inheritance Basics
*What does the term "base class" refer to in C++ inheritance?*

   A. The class that inherits properties from another class  
   B. The class from which properties are inherited  
   C. A class that cannot be inherited from  
   D. A class with only private members  

<details>
<summary>Answer</summary>
B. The class from which properties are inherited
</details>

### Question 24: Benefits of Inheritance
*Which of the following is NOT a benefit of inheritance in C++?*

   A. Code reusability  
   B. Extending existing classes  
   C. Overloading operators  
   D. Modifying existing classes by overloading methods  

<details>
<summary>Answer</summary>
C. Overloading operators
</details>

#### Inheritance Hierarchy

### Question 25: Inheritance Hierarchy
*In an inheritance hierarchy, which class is at the top?*

   A. Derived class  
   B. Subclass  
   C. Base class  
   D. Child class  

<details>
<summary>Answer</summary>
C. Base class
</details>

#### Inherited Constructors & Destructors

### Question 26: Order of Constructors
*What is the correct order of constructor calls when a derived class object is created?*

   A. Derived class constructor, then base class constructor  
   B. Base class constructor, then derived class constructor  
   C. Derived class constructor only  
   D. Base class constructor only  

<details>
<summary>Answer</summary>
B. Base class constructor, then derived class constructor
</details>

### Question 27: Order of Destructors
*What is the correct order of destructor calls when a derived class object is destroyed?*

   A. Derived class destructor, then base class destructor  
   B. Base class destructor, then derived class destructor  
   C. Derived class destructor only  
   D. Base class destructor only  

<details>
<summary>Answer</summary>
A. Derived class destructor, then base class destructor
</details>

#### Access Specifiers: public, protected, private

### Question 28: Access Specifiers
*Which access specifier allows members of a base class to be accessible only by objects of its derived classes?*

   A. public  
   B. private  
   C. protected  
   D. internal  

<details>
<summary>Answer</summary>
C. protected
</details>

#### Polymorphism and Virtual Functions

### Question 29: Virtual Functions
*What is the purpose of declaring a function as `virtual` in a base class?*

   A. To make the function static  
   B. To allow the function to be overridden in a derived class  
   C. To prevent the function from being overridden  
   D. To allow multiple inheritance  

<details>
<summary>Answer</summary>
B. To allow the function to be overridden in a derived class
</details>

#### Function Overriding and Overloading

### Question 30: Function Overloading
*Which of the following is true about function overloading in C++?*

   A. It allows multiple functions with the same name but different parameters  
   B. It allows a function to be overridden in a derived class  
   C. It prevents a function from being overridden  
   D. It is the same as function overriding  

<details>
<summary>Answer</summary>
A. It allows multiple functions with the same name but different parameters
</details>

### Question 31: Function Overriding
*What is function overriding in C++?*

   A. Defining multiple functions with the same name but different parameters  
   B. Redefining a base class function in a derived class  
   C. Preventing a function from being inherited  
   D. Using a function without parameters  

<details>
<summary>Answer</summary>
B. Redefining a base class function in a derived class
</details>

#### Multiple Inheritance

### Question 32: Multiple Inheritance
*What is multiple inheritance in C++?*

   A. A class inheriting from multiple base classes  
   B. A class with multiple member functions  
   C. A class with multiple constructors  
   D. A class that cannot be inherited  

<details>
<summary>Answer</summary>
A. A class inheriting from multiple base classes
</details>

#### Using `using` for Inheriting Constructors

### Question 33: Using `using` in Inheritance
*What is the purpose of the `using` keyword in the context of inheritance in C++?*

   A. It allows the derived class to inherit constructors from the base class  
   B. It allows the derived class to inherit private members from the base class  
   C. It allows the derived class to use base class's private methods  
   D. It allows the derived class to redefine base class's protected methods  

<details>
<summary>Answer</summary>
A. It allows the derived class to inherit constructors from the base class
</details>

#### Redefining Base Class Functions

### Question 34: Redefining Functions
*What is the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Rectangle {
private:
    double length, width;

public:
    Rectangle(double len, double w) : length(len), width(w) {}
    double get_area() const {
        return length * width;
    }
    void print() const {
        cout << "Length: " << length << " Width: " << width << endl;
    }
};

class Solid : public Rectangle {
private:
    double depth;

public:
    Solid(double len, double w, double d) : Rectangle(len, w), depth(d) {}
    double get_area() const {
        return Rectangle::get_area() * depth;
    }
    void print() const {
        Rectangle::print();
        cout << "Depth: " << depth << endl;
    }
};

int main() {
    Solid s(4.5, 10.1123, 10);
    s.print();
    cout << "Solid's area: " << s.get_area() << endl;
    return 0;
}
```

   A. Length: 4.5 Width: 10.1123 Depth: 10 Solid's area: 455.053  
   B. Length: 4.5 Width: 10.1123 Depth: 10 Solid's area: 45.5053  
   C. Length: 4.5 Width: 10.1123 Solid's area: 45.5053  
   D. Compilation error  

<details>
<summary>Answer</summary>
A. Length: 4.5 Width: 10.1123 Depth: 10 Solid's area: 455.053
</details>

### Question 35: Constructor Inheritance
*What is the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Base {
private:
    int x, y;

public:
    Base() {
        cout << "Base's constructor...\n";
        x = 0;
        y = 0;
    }
    Base(int a, int b) {
        x = a;
        y = b;
    }
    ~Base() {
        cout << "Base's destructor...\n";
    }
    void print() {
        cout

 << "x = " << x << " y = " << y << endl;
    }
};

class Child2 : public Base {
public:
    using Base::Base;
    Child2() {
        cout << "Child2's constructor...\n";
    }
    ~Child2() {
        cout << "Child2's destructor...\n";
    }
};

int main() {
    Child2 c2(1, 2);
    c2.print();
    cout << endl;
    return 0;
}
```

   A. Base's constructor... x = 1 y = 2 Child2's constructor... Child2's destructor... Base's destructor...  
   B. Child2's constructor... x = 1 y = 2 Base's constructor... Child2's destructor... Base's destructor...  
   C. Base's constructor... x = 0 y = 0 Child2's constructor... Child2's destructor... Base's destructor...  
   D. Compilation error  

<details>
<summary>Answer</summary>
A. Base's constructor... x = 1 y = 2 Child2's constructor... Child2's destructor... Base's destructor...
</details>

---

These additional questions ensure that all key topics from the lecture on Inheritance are thoroughly covered. This comprehensive set of questions will test students' understanding of fundamental concepts, application of knowledge, and understanding of object-oriented programming principles in C++.
