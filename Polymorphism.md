
### Question 1: Basic Syntax
*What is the correct syntax to declare a virtual function in a base class?*

```cpp
class Base {
public:
    virtual void display();
};
```

   A. `void virtual display();`  
   B. `virtual void display();`  
   C. `void display() virtual;`  
   D. `virtual display() void;`  

<details>
<summary>Answer</summary>
B. `virtual void display();`
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

### Question 3: Static Members
*Which of the following is true about static member variables?*

   A. They are shared among all objects of a class.  
   B. Each object has its own copy.  
   C. They cannot be accessed without an object.  
   D. They are always constant.  

<details>
<summary>Answer</summary>
A. They are shared among all objects of a class.
</details>

#### Application of Concepts

### Question 4: Predicting Outputs
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void display() {
        cout << "Base display" << endl;
    }
};

class Derived : public Base {
public:
    void display() override {
        cout << "Derived display" << endl;
    }
};

int main() {
    Base *b = new Derived();
    b->display();
    delete b;
    return 0;
}
```

   A. Base display  
   B. Derived display  
   C. Compilation error  
   D. Undefined behavior  

<details>
<summary>Answer</summary>
B. Derived display
</details>

### Question 5: Debugging Code
*Identify the error in the following program and correct it.*

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void display() {
        cout << "Base display" << endl;
    }
};

class Derived : public Base {
public:
    void display() {
        cout << "Derived display" << endl;
    }
};

int main() {
    Base *b = new Derived();
    b->display();
    return 0;
}
```

<details>
<summary>Answer</summary>
The error is that `delete b;` is missing in the `main` function to avoid memory leak. 

Corrected code:
```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void display() {
        cout << "Base display" << endl;
    }
};

class Derived : public Base {
public:
    void display() override {
        cout << "Derived display" << endl;
    }
};

int main() {
    Base *b = new Derived();
    b->display();
    delete b; // Added delete to avoid memory leak
    return 0;
}
```
</details>

### Question 6: Static Member Functions
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Circle {
private:
    double radius;
    static const double PI;
public:
    Circle(double r) : radius(r) {}
    double get_area() const {
        return PI * radius * radius;
    }
    static double get_pi() {
        return PI;
    }
};

const double Circle::PI = 3.14159;

int main() {
    Circle c1(10);
    cout << "Area: " << c1.get_area() << endl;
    cout << "PI: " << Circle::get_pi() << endl;
    return 0;
}
```

   A. Area: 314.159 PI: 3.14159  
   B. Area: 314.159 PI: 0  
   C. Area: 0 PI: 3.14159  
   D. Compilation error  

<details>
<summary>Answer</summary>
A. Area: 314.159 PI: 3.14159
</details>

### Question 7: Static Binding
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Square {
private:
    int x;
public:
    Square(int len) { x = len; }
    int get_x() { return x; }
    void print() { cout << "Square of length: " << x << endl; }
};

class Rectangle : public Square {
private:
    int y;
public:
    Rectangle(int len, int wid) : Square(len), y(wid) {}
    void print() { cout << "Rectangle of sides: " << get_x() << " & " << y << endl; }
};

void test(Square s) {
    s.print();
}

int main() {
    Square s(10);
    Rectangle r(20, 30);
    test(s);
    test(r);
    return 0;
}
```

   A. Square of length: 10 Square of length: 20  
   B. Square of length: 10 Rectangle of sides: 20 & 30  
   C. Square of length: 10 Rectangle of sides: 10 & 30  
   D. Compilation error  

<details>
<summary>Answer</summary>
A. Square of length: 10 Square of length: 20
</details>

#### Understanding Classes and Structures

### Question 8: Polymorphism
*What is polymorphism in C++?*

   A. The ability to define multiple functions with the same name  
   B. The ability to redefine base class functions in a derived class  
   C. The ability to process objects differently based on their data type or class  
   D. The ability to inherit from multiple base classes  

<details>
<summary>Answer</summary>
C. The ability to process objects differently based on their data type or class
</details>

### Question 9: Virtual Functions
*What is the purpose of a virtual function in C++?*

   A. To allow function overloading  
   B. To enable dynamic binding  
   C. To hide the base class function  
   D. To allow multiple inheritance  

<details>
<summary>Answer</summary>
B. To enable dynamic binding
</details>

### Question 10: Pure Virtual Functions
*What is a pure virtual function?*

   A. A function with no return type  
   B. A function that must be overridden in a derived class  
   C. A function that can only be called from the base class  
   D. A function that cannot be overridden  

<details>
<summary>Answer</summary>
B. A function that must be overridden in a derived class
</details>

### Question 11: Abstract Classes
*What will be the result of trying to instantiate an abstract class?*

   A. A runtime error  
   B. Successful instantiation  
   C. A compilation error  
   D. The program will execute but the object will not be created  

<details>
<summary>Answer</summary>
C. A compilation error
</details>

### Question 12: Redefining Functions
*What is the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Square {
private:
    int x;
public:
    Square(int len) { x = len; }
    virtual int get_area() { return x * x; }
    virtual void print() { cout << "Square of length: " << x << endl; }
};

class Rectangle : public Square {
private:
    int y;
public:
    Rectangle(int len, int wid) : Square(len), y(wid) {}
    int get_area() override { return get_x() * y; }
    void print() override { cout << "Rectangle of sides: " << get_x() << " & " << y << endl; }
};

int main() {
    Square s(12);
    Rectangle r(13, 15);
    s.print();
    r.print();
    return 0;
}
```

   A. Square of length: 12 Rectangle of sides: 13 & 15  
   B. Square of length: 12 Rectangle of sides: 12 & 15  
   C. Square of length: 144 Rectangle of sides: 13 & 15  
   D. Compilation error  

<details>
<summary>Answer</summary>
A. Square of length: 12 Rectangle of sides: 13 & 15
</details>

### Question 13: Pure Virtual Functions Example
*What is the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Shape {
public:
    virtual void print() { cout << "This is an abstract shape.\n"; }
    virtual int get_area() = 0;
};

class Square : public Shape {
private:
    int x;
public:
    Square(int len) { x = len; }
    int get_area() override { return x * x; }
    void print() override { cout << "Square of length: " << x << endl; }
};

int main() {
    Square s(5);
    s.print();
    cout << "Area: " << s.get_area() << endl;
    return 0;
}
```

   A. This is an abstract shape. Area: 25  
   B. Square of length: 5 Area: 25  
   C. Compilation error  


   D. This is an abstract shape. Square of length: 5 Area: 25  

<details>
<summary>Answer</summary>
B. Square of length: 5 Area: 25
</details>

### Question 14: Abstract Class Instantiation
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Shape {
public:
    virtual void print() { cout << "This is an abstract shape.\n"; }
    virtual int get_area() = 0;
};

int main() {
    Shape s;
    s.print();
    return 0;
}
```

   A. This is an abstract shape.  
   B. Compilation error: object of abstract class type "Shape" is not allowed  
   C. This is an abstract shape. Area: 0  
   D. Undefined behavior  

<details>
<summary>Answer</summary>
B. Compilation error: object of abstract class type "Shape" is not allowed
</details>

### Question 15: Multiple Inheritance
*What is the correct syntax for a class to inherit from multiple base classes?*

   A. `class Derived : Base1 Base2 { ... };`  
   B. `class Derived inherits Base1, Base2 { ... };`  
   C. `class Derived : public Base1, public Base2 { ... };`  
   D. `class Derived : Base1, public Base2 { ... };`  

<details>
<summary>Answer</summary>
C. `class Derived : public Base1, public Base2 { ... };`
</details>

### Question 16: Using `using` for Inheriting Constructors
*What is the purpose of the `using` keyword in the context of inheritance in C++?*

   A. It allows the derived class to inherit constructors from the base class.  
   B. It allows the derived class to inherit private members from the base class.  
   C. It allows the derived class to use base class's private methods.  
   D. It allows the derived class to redefine base class's protected methods.  

<details>
<summary>Answer</summary>
A. It allows the derived class to inherit constructors from the base class.
</details>

### Question 17: Redefining Functions Example
*What is the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Square {
private:
    int x;
public:
    Square(int len) { x = len; }
    virtual int get_area() { return x * x; }
    virtual void print() { cout << "Square of length: " << x << endl; }
};

class Rectangle : public Square {
private:
    int y;
public:
    Rectangle(int len, int wid) : Square(len), y(wid) {}
    int get_area() override { return get_x() * y; }
    void print() override { cout << "Rectangle of sides: " << get_x() << " & " << y << endl; }
};

int main() {
    const int SIZE = 4;
    Square *s[SIZE] = { new Square(12), new Square(3), new Square(43), new Rectangle(3, 4) };
    for (int i = 0; i < SIZE; i++) {
        s[i]->print();
        cout << "Area: " << s[i]->get_area() << "\n\n";
    }
    return 0;
}
```

   A. Square of length: 12 Area: 144 Square of length: 3 Area: 9 Square of length: 43 Area: 1849 Square of length: 3 Area: 9  
   B. Square of length: 12 Area: 144 Square of length: 3 Area: 9 Square of length: 43 Area: 1849 Rectangle of sides: 3 & 4 Area: 12  
   C. Square of length: 12 Area: 144 Square of length: 3 Area: 9 Square of length: 43 Area: 1849 Square of length: 3 Area: 12  
   D. Compilation error  

<details>
<summary>Answer</summary>
B. Square of length: 12 Area: 144 Square of length: 3 Area: 9 Square of length: 43 Area: 1849 Rectangle of sides: 3 & 4 Area: 12
</details>

### Question 18: Polymorphic Behavior
*What is the correct way to ensure polymorphic behavior in the following program?*

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void display() { cout << "Base display" << endl; }
};

class Derived : public Base {
public:
    void display() { cout << "Derived display" << endl; }
};

void show(Base &obj) {
    obj.display();
}

int main() {
    Base b;
    Derived d;
    show(b);
    show(d);
    return 0;
}
```

   A. Add `override` keyword to `Derived::display()`  
   B. Remove `virtual` keyword from `Base::display()`  
   C. Change `void show(Base &obj)` to `void show(Base obj)`  
   D. No changes needed  

<details>
<summary>Answer</summary>
D. No changes needed
</details>

### Question 19: Dynamic Binding
*What is dynamic binding in C++?*

   A. Matching a function call with the correct function definition at compile time  
   B. Matching a function call with the correct function definition at runtime  
   C. Matching a function call with the correct function definition using a base class pointer  
   D. Matching a function call with the correct function definition using function overloading  

<details>
<summary>Answer</summary>
B. Matching a function call with the correct function definition at runtime
</details>

### Question 20: Pure Virtual Functions Example
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Shape {
public:
    virtual void print() { cout << "This is an abstract shape.\n"; }
    virtual int get_area() = 0;
};

class Square : public Shape {
private:
    int x;
public:
    Square(int len) { x = len; }
    int get_area() override { return x * x; }
    void print() override { cout << "Square of length: " << x << endl; }
};

int main() {
    Shape *s = new Square(5);
    s->print();
    cout << "Area: " << s->get_area() << endl;
    delete s;
    return 0;
}
```

   A. This is an abstract shape. Area: 25  
   B. Square of length: 5 Area: 25  
   C. Compilation error  
   D. This is an abstract shape. Square of length: 5 Area: 25  

<details>
<summary>Answer</summary>
B. Square of length: 5 Area: 25
</details>
```

### Question 21: Redefining Base Class Functions
*What is the correct way to redefine a function in a derived class?*

```cpp
class Base {
public:
    void display() {
        cout << "Base display" << endl;
    }
};

class Derived : public Base {
public:
    void display() {
        cout << "Derived display" << endl;
    }
};

int main() {
    Derived d;
    d.display();
    return 0;
}
```

   A. Use the `override` keyword  
   B. Define a function with the same name and parameters in the derived class  
   C. Define a function with the same name but different parameters in the derived class  
   D. Use the `virtual` keyword in the derived class function  

<details>
<summary>Answer</summary>
B. Define a function with the same name and parameters in the derived class
</details>

#### Static Members

### Question 22: Static Member Variables
*What is the correct way to initialize a static member variable in a class?*

```cpp
class Circle {
private:
    double radius;
    static const double PI;
public:
    Circle(double r) : radius(r) {}
    double get_area() const {
        return PI * radius * radius;
    }
};

const double Circle::PI = 3.14159;
```

   A. `const double Circle::PI = 3.14159;`  
   B. `double Circle::PI = 3.14159;`  
   C. `const Circle::PI = 3.14159;`  
   D. `static const double Circle::PI = 3.14159;`  

<details>
<summary>Answer</summary>
A. `const double Circle::PI = 3.14159;`
</details>

### Question 23: Static Member Functions
*What is the purpose of a static member function?*

   A. To access only static member variables  
   B. To access both static and non-static member variables  
   C. To be called on class instances only  
   D. To initialize static member variables  

<details>
<summary>Answer</summary>
A. To access only static member variables
</details>

#### Polymorphism & Virtual Functions

### Question 24: Polymorphism Definition
*What does polymorphism mean in C++?*

   A. The ability to create multiple classes with the same name  
   B. The ability of different classes to be treated as instances of the same class through inheritance  
   C. The ability to define multiple functions with the same name but different parameters  
   D. The ability to use a single function to perform different tasks  

<details>
<summary>Answer</summary>
B. The ability of different classes to be treated as instances of the same class through inheritance
</details>

### Question 25: Virtual Functions
*Why are virtual functions used in C++?*

   A. To allow function overloading  
   B. To enable dynamic binding  
   C. To allow multiple inheritance  
   D. To enforce function overriding  

<details>
<summary>Answer</summary>
B. To enable dynamic binding
</details>

### Question 26: Polymorphism Example
*What is the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void show() {
        cout << "Base show" << endl;
    }
};

class Derived : public Base {
public:
    void show() override {
        cout << "Derived show" << endl;
    }
};

int main() {
    Base *b;
    Derived d;
    b = &d;
    b->show();
    return 0;
}
```

   A. Base show  
   B. Derived show  
   C. Compilation error  
   D. Undefined behavior  

<details>
<summary>Answer</summary>
B. Derived show
</details>

#### Static vs. Dynamic Binding

### Question 27: Static vs. Dynamic Binding
*What is the difference between static binding and dynamic binding?*

   A. Static binding occurs at runtime, dynamic binding occurs at compile time  
   B. Static binding occurs at compile time, dynamic binding occurs at runtime  
   C. Both occur at runtime  
   D. Both occur at compile time  

<details>
<summary>Answer</summary>
B. Static binding occurs at compile time, dynamic binding occurs at runtime
</details>

### Question 28: Static Binding Example
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    void display() {
        cout << "Base display" << endl;
    }
};

class Derived : public Base {
public:
    void display() {
        cout << "Derived display" << endl;
    }
};

void show(Base b) {
    b.display();
}

int main() {
    Derived d;
    show(d);
    return 0;
}
```

   A. Base display  
   B. Derived display  
   C. Compilation error  
   D. Undefined behavior  

<details>
<summary>Answer</summary>
A. Base display
</details>

### Question 29: Dynamic Binding Example
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void display() {
        cout << "Base display" << endl;
    }
};

class Derived : public Base {
public:
    void display() override {
        cout << "Derived display" << endl;
    }
};

void show(Base &b) {
    b.display();
}

int main() {
    Derived d;
    show(d);
    return 0;
}
```

   A. Base display  
   B. Derived display  
   C. Compilation error  
   D. Undefined behavior  

<details>
<summary>Answer</summary>
B. Derived display
</details>

#### Pure Virtual Functions & Abstract Classes

### Question 30: Pure Virtual Functions
*What is a pure virtual function?*

   A. A function with no return type  
   B. A function that must be overridden in a derived class  
   C. A function that can only be called from the base class  
   D. A function that cannot be overridden  

<details>
<summary>Answer</summary>
B. A function that must be overridden in a derived class
</details>

### Question 31: Abstract Classes
*What will be the result of trying to instantiate an abstract class?*

   A. A runtime error  
   B. Successful instantiation  
   C. A compilation error  
   D. The program will execute but the object will not be created  

<details>
<summary>Answer</summary>
C. A compilation error
</details>

### Question 32: Pure Virtual Function Example
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Shape {
public:
    virtual void print() { cout << "This is an abstract shape.\n"; }
    virtual int get_area() = 0;
};

class Square : public Shape {
private:
    int x;
public:
    Square(int len) { x = len; }
    int get_area() override { return x * x; }
    void print() override { cout << "Square of length: " << x << endl; }
};

int main() {
    Shape *s = new Square(5);
    s->print();
    cout << "Area: " << s->get_area() << endl;
    delete s;
    return 0;
}
```

   A. This is an abstract shape. Area: 25  
   B. Square of length: 5 Area: 25  
   C. Compilation error  
   D. This is an abstract shape. Square of length: 5 Area: 25  

<details>
<summary>Answer</summary>
B. Square of length: 5 Area: 25
</details>

### Question 33: Pure Virtual Function Declaration
*What is the correct way to declare a pure virtual function in a base class?*

   A. `virtual void display() = 0;`  
   B. `void virtual display() = 0;`  
   C. `virtual void display();`  
   D. `void display() = 0;`  

<details>
<summary>Answer</summary>
A. `virtual void display() = 0;`
</details>

### Question 34: Abstract Class Instantiation
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Shape {
public:
    virtual void print() { cout << "This is an abstract shape.\n"; }
    virtual int get_area() = 0;
};

int main() {
    Shape s;
    s.print();
    return 0;
}
```

   A. This is an abstract shape.  
   B. Compilation error: object of abstract class type "Shape" is not allowed  
   C. This is an abstract shape. Area: 0  
   D. Undefined behavior  

<details>
<summary>Answer</summary>
B. Compilation error: object of abstract class type "Shape" is not allowed
</details>

### Question 35

: Implementing Abstract Methods
*What is the correct way to implement the pure virtual function `get_area` in a derived class?*

```cpp
class Shape {
public:
    virtual int get_area() = 0;
};

class Square : public Shape {
private:
    int x;
public:
    Square(int len) { x = len; }
    int get_area() override { return x * x; }
};
```

   A. `int get_area() override { return x * x; }`  
   B. `int get_area() { return x * x; }`  
   C. `override int get_area() { return x * x; }`  
   D. `virtual int get_area() override { return x * x; }`  

<details>
<summary>Answer</summary>
A. `int get_area() override { return x * x; }`
</details>

---
