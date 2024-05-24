I apologize for that mistake. Let's correct it and reformat the entire set of questions with the proper structure. 

```markdown
### Question 1: Basic Syntax and Data Types
*What will happen if we attempt to compile the following program?*

```cpp
#include <iostream>
using namespace std;

class Rectangle {
public:
    double length;
    double width;

    double getArea() const {
        return length * width;
    }
};

int main() {
    Rectangle rect;
    rect.length = 5.5;
    rect.width = 3.2;
    cout << "Area: " << rect.getArea() << endl;
    return 0;
}
```

A. Compilation error due to missing constructor  
B. A number will be printed  
C. A character will be printed  
D. None of the previous

<details>
  <summary>Answer</summary>
  B. A number will be printed
</details>

### Question 2: Application of Concepts - Predicting Outputs
*What is the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Rectangle {
private:
    double length;
    double width;

public:
    Rectangle() {
        length = 1.0;
        width = 1.0;
    }

    double getLength() const {
        return length;
    }

    double getWidth() const {
        return width;
    }

    void setDimensions(double l, double w) {
        length = l;
        width = w;
    }

    double getArea() const {
        return length * width;
    }
};

int main() {
    Rectangle rect;
    rect.setDimensions(4.0, 5.0);
    cout << "Length: " << rect.getLength() << endl;
    cout << "Width: " << rect.getWidth() << endl;
    cout << "Area: " << rect.getArea() << endl;
    return 0;
}
```

A. Length: 1.0 Width: 1.0 Area: 1.0  
B. Length: 4.0 Width: 5.0 Area: 20.0  
C. Length: 4.0 Width: 5.0 Area: 9.0  
D. Compilation error due to private members

<details>
  <summary>Answer</summary>
  B. Length: 4.0 Width: 5.0 Area: 20.0
</details>

### Question 3: Understanding Access Specifiers
*What will be the output of the following program if the constructor is correctly defined?*

```cpp
#include <iostream>
using namespace std;

class Rectangle {
private:
    double length;
    double width;

public:
    Rectangle(double l, double w) {
        length = l;
        width = w;
    }

    double getLength() const {
        return length;
    }

    double getWidth() const {
        return width;
    }

    double getArea() const {
        return length * width;
    }
};

int main() {
    Rectangle rect(3.0, 4.0);
    cout << "Length: " << rect.getLength() << endl;
    cout << "Width: " << rect.getWidth() << endl;
    cout << "Area: " << rect.getArea() << endl;
    return 0;
}
```

A. Length: 3.0 Width: 4.0 Area: 12.0  
B. Length: 3.0 Width: 4.0 Area: 7.0  
C. Length: 0.0 Width: 0.0 Area: 0.0  
D. Compilation error due to private members

<details>
  <summary>Answer</summary>
  A. Length: 3.0 Width: 4.0 Area: 12.0
</details>

### Question 4: Debugging Code
*Identify the error in the following program and correct it.*

```cpp
#include <iostream>
using namespace std;

class Rectangle {
private:
    double length;
    double width;

public:
    void setDimensions(double l, double w) {
        length = l;
        width = w;
    }

    double getArea() const {
        return length * width;
    }
};

int main() {
    Rectangle rect;
    rect.setDimensions(2.0, 3.0);
    cout << "Area: " << rect.getArea() << endl;
    return 0;
}
```

<details>
  <summary>Answer</summary>
  The code is correct. There is no error.
</details>

### Question 5: Class Design and Member Functions
**Design a class Circle with the following specifications:**
1. Private member variables: radius (double).
2. A default constructor that initializes radius to 1.0.
3. A parameterized constructor that initializes radius to a given value.
4. A public member function getArea that returns the area of the circle.
5. A public member function getCircumference that returns the circumference of the circle.
6. Provide the implementation for each member function.

<details>
  <summary>Answer</summary>
  ```cpp
  class Circle {
  private:
      double radius;

  public:
      Circle() : radius(1.0) {}
      Circle(double r) : radius(r) {}
      double getArea() const {
          return 3.14159 * radius * radius;
      }
      double getCircumference() const {
          return 2 * 3.14159 * radius;
      }
  };
  ```
</details>

### Question 6: Constructor and Destructor
*What is the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Test {
public:
    Test() {
        cout << "Constructor called" << endl;
    }

    ~Test() {
        cout << "Destructor called" << endl;
    }
};

int main() {
    Test t;
    return 0;
}
```

A. Constructor called  
B. Destructor called  
C. Constructor called Destructor called  
D. No output

<details>
  <summary>Answer</summary>
  C. Constructor called Destructor called
</details>

### Question 7: Separating Specification from Implementation
**Given the following class specification in Rectangle.h, provide the implementation in Rectangle.cpp:**

*Rectangle.h*
```cpp
#ifndef RECTANGLE_H
#define RECTANGLE_H

class Rectangle {
private:
    double width;
    double length;

public:
    Rectangle(double w, double l);
    void setWidth(double w);
    void setLength(double l);
    double getWidth() const;
    double getLength() const;
    double getArea() const;
};

#endif
```

<details>
  <summary>Answer</summary>
  ```cpp
  // Rectangle.cpp
  #include "Rectangle.h"

  Rectangle::Rectangle(double w, double l) : width(w), length(l) {}

  void Rectangle::setWidth(double w) {
      width = w;
  }

  void Rectangle::setLength(double l) {
      length = l;
  }

  double Rectangle::getWidth() const {
      return width;
  }

  double Rectangle::getLength() const {
      return length;
  }

  double Rectangle::getArea() const {
      return width * length;
  }
  ```
</details>

### Question 8: Inline Member Functions
*Explain the advantages and disadvantages of using inline member functions. Provide an example of when it would be appropriate to use an inline member function.*

<details>
  <summary>Answer</summary>
  **Advantages:**
  - Reduced function call overhead.
  - Better performance for small functions.
  
  **Disadvantages:**
  - Increased binary size.
  - Compiler may ignore inline request.

  **Example:**
  ```cpp
  class MyClass {
  public:
      inline void myFunction() {
          // Small function logic
      }
  };
  ```
</details>

### Question 9: Arrays of Objects
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class InventoryItem {
private:
    string name;
    int quantity;

public:
    InventoryItem(string n, int q) : name(n), quantity(q) {}
    
    void display() const {
        cout << name << ": " << quantity << endl;
    }
};

int main() {
    InventoryItem inventory[3] = {
        InventoryItem("Hammer", 10),
        InventoryItem("Wrench", 5),
        InventoryItem("Pliers", 7)
    };

    for (int i = 0; i < 3; ++i) {
        inventory[i].display();
    }

    return 0;
}
```

A. Hammer: 10 Wrench: 5 Pliers: 7  
B. Hammer: 10 Wrench: 5 Pliers: 0  
C. Compilation error due to array initialization  
D. Hammer: 10 Wrench: 5 Pliers: 7 plus additional uninitialized values

<details>
  <summary>Answer</summary>
  A. Hammer: 10 Wrench: 5 Pliers: 7
</details>

### Question 10
**What is the output of the following program?**

```cpp
#include <iostream>
using namespace std;

class Box {
private:
    double length;

public:
    Box(double l) : length(l) {}
    double getLength() const {
        return length;
    }
};

int main() {
    Box box(5.0);
    cout << box.getLength() << endl;
    return 0;
}
```
A. 0.0  
B. 5.0  
C. Compilation error  
D. Runtime error



<details>
  <summary>Answer</summary>
  B. 5.0
</details>

### Question 11
**Which of the following is a valid way to declare an object of class `Car`?**

```cpp
class Car {
public:
    Car() {}
};
```
A. `Car car;`  
B. `Car car = Car();`  
C. `Car car();`  
D. `Car;`

<details>
  <summary>Answer</summary>
  B. `Car car = Car();`
</details>

### Question 12
**What will be the output of the following program?**

```cpp
#include <iostream>
using namespace std;

class Student {
private:
    int age;

public:
    Student(int a) : age(a) {}
    int getAge() const {
        return age;
    }
};

int main() {
    Student s(20);
    cout << s.getAge() << endl;
    return 0;
}
```
A. 18  
B. 19  
C. 20  
D. Compilation error

<details>
  <summary>Answer</summary>
  C. 20
</details>

### Question 13
**Which of the following access specifiers allows a class member to be accessed outside the class?**

A. public  
B. private  
C. protected  
D. internal

<details>
  <summary>Answer</summary>
  A. public
</details>

### Question 14
**What will happen if we attempt to compile the following code?**

```cpp
#include <iostream>
using namespace std;

class Test {
private:
    int value;

public:
    Test(int v) : value(v) {}
    int getValue() const {
        return value;
    }
};

int main() {
    Test t(10);
    cout << t.value << endl;
    return 0;
}
```
A. 0  
B. 10  
C. Compilation error  
D. Runtime error

<details>
  <summary>Answer</summary>
  C. Compilation error
</details>

### Question 15
**What is the output of the following program?**

```cpp
#include <iostream>
using namespace std;

class Counter {
private:
    int count;

public:
    Counter() {
        count = 0;
    }
    void increment() {
        count++;
    }
    int getCount() const {
        return count;
    }
};

int main() {
    Counter c;
    c.increment();
    c.increment();
    cout << c.getCount() << endl;
    return 0;
}
```
A. 0  
B. 1  
C. 2  
D. 3

<details>
  <summary>Answer</summary>
  C. 2
</details>

### Question 16
**What does the following code do?**

```cpp
#include <iostream>
using namespace std;

class Person {
private:
    string name;

public:
    void setName(string n) {
        name = n;
    }
    string getName() const {
        return name;
    }
};

int main() {
    Person p;
    p.setName("John");
    cout << p.getName() << endl;
    return 0;
}
```
A. Prints an empty string  
B. Compilation error  
C. Prints "John"  
D. Runtime error

<details>
  <summary>Answer</summary>
  C. Prints "John"
</details>

### Question 17
**Which keyword is used to define a member function that cannot modify the object's data members?**

A. const  
B. static  
C. inline  
D. friend

<details>
  <summary>Answer</summary>
  A. const
</details>

### Question 18
**What will be the output of the following code?**

```cpp
#include <iostream>
using namespace std;

class MyClass {
public:
    MyClass() {
        cout << "Constructor called" << endl;
    }
};

int main() {
    MyClass obj;
    return 0;
}
```
A. Constructor called  
B. No output  
C. Compilation error  
D. Runtime error

<details>
  <summary>Answer</summary>
  A. Constructor called
</details>

### Question 19
**Which of the following is NOT a valid way to access members of an object using a pointer?**

```cpp
class Sample {
public:
    int x;
    void setX(int val) { x = val; }
};
```
A. `Sample *ptr = new Sample; ptr->x = 5;`  
B. `Sample *ptr = new Sample; ptr.x = 5;`  
C. `Sample *ptr = new Sample; ptr->setX(5);`  
D. `Sample obj; Sample *ptr = &obj; ptr->x = 5;`

<details>
  <summary>Answer</summary>
  B. `Sample *ptr = new Sample; ptr.x = 5;`
</details>

### Question 20
**What will be the output of the following program?**

```cpp
#include <iostream>
using namespace std;

class Shape {
private:
    double area;

public:
    Shape(double a) : area(a) {}
    double getArea() const {
        return area;
    }
};

int main() {
    Shape s(25.0);
    cout << "Area: " << s.getArea() << endl;
    return 0;
}
```
A. Area: 0.0  
B. Area: 25.0  
C. Compilation error  
D. Runtime error

<details>
  <summary>Answer</summary>
  B. Area: 25.0
</details>

### Question 21
**Which of the following is the correct syntax for defining a class with a private member and a public member function?**

A.
```cpp
class MyClass {
private:
    int x;
public:
    void setX(int val) { x = val; }
};
```
B.
```cpp
class MyClass {
public:
    int x;
private:
    void setX(int val) { x = val; }
};
```
C.
```cpp
class MyClass {
int x;
void setX(int val) { x = val; }
};
```
D.
```cpp
class MyClass {
private:
    void setX(int val) { x = val; }
public:
    int x;
};
```

<details>
  <summary>Answer</summary>
  A.
  ```cpp
  class MyClass {
  private:
      int x;
  public:
      void setX(int val) { x = val; }
  };
  ```
</details>

### Question 22
**Which of the following correctly declares an object `myObj` of class `Sample` and initializes it using a parameterized constructor?**

```cpp
class Sample {
public:
    Sample(int val) {}
};
```
A. `Sample myObj();`  
B. `Sample myObj = Sample();`  
C. `Sample myObj(10);`  
D. `Sample myObj = 10;`

<details>
  <summary>Answer</summary>
  C. `Sample myObj(10);`
</details>

### Question 23
**What will happen if we attempt to compile the following program?**

```cpp
#include <iostream>
using namespace std;

class Test {
public:
    Test() {
        cout << "Constructor called" << endl;
    }
    ~Test() {
        cout << "Destructor called" << endl;
    }
};

int main() {
    Test *t = new Test();
    delete t;
    return 0;
}
```
A. Constructor called Destructor called  
B. Constructor called  
C. Destructor called  
D. Compilation error

<details>
  <summary>Answer</summary>
  A. Constructor called Destructor called
</details>

### Question 24
**Which of the following is true about constructors in C++?**

A. Constructors cannot have parameters.  
B. Constructors are automatically called when an object is created.  
C. Constructors can be called explicitly.  
D. Constructors must have a return type.

<details>
  <summary>Answer</summary>
  B. Constructors are automatically called when an object is created.
</details>

### Question 25
**What will be the output of the following program?**

```cpp
#include <iostream>
using namespace std;

class Number {
private:
    int value;

public:
    Number(int v) : value(v) {}
    int getValue() const {
        return value;
    }
};

int main() {
    Number num(42);
    cout << "Value: " << num.getValue() << endl;
    return 0;
}
```
A. Value: 0  
B. Value: 10  
C. Value: 42  
D. Compilation error

<details>
  <summary>Answer</summary>
  C. Value: 42
</details>

### Question 26
**What is the default access specifier for members of a class if not explicitly specified?**

A. public  
B. private  
C. protected  
D. internal

<details>
  <summary>Answer</summary>
  B. private
</details>

### Question 27
**Which of the following correctly initializes an object using the default constructor?**

```cpp
class Item {
public:
    Item() {}
};
```
A. `Item item = Item();`  
B. `Item item;`  
C. `Item item();`  
D. `Item();`

<details>
  <summary>Answer</summary>
  B. `Item item;

`
</details>

### Question 28
**What will be the output of the following program?**

```cpp
#include <iostream>
using namespace std;

class Counter {
private:
    int count;

public:
    Counter() {
        count = 0;
    }
    void increment() {
        count++;
    }
    void decrement() {
        count--;
    }
    int getCount() const {
        return count;
    }
};

int main() {
    Counter c;
    c.increment();
    c.increment();
    c.decrement();
    cout << c.getCount() << endl;
    return 0;
}
```
A. 0  
B. 1  
C. 2  
D. 3

<details>
  <summary>Answer</summary>
  B. 1
</details>

### Question 29
**Which keyword is used to prevent a member function from modifying the state of an object?**

A. static  
B. const  
C. inline  
D. friend

<details>
  <summary>Answer</summary>
  B. const
</details>

### Question 30
**What will be the output of the following program?**

```cpp
#include <iostream>
using namespace std;

class Demo {
private:
    int num;

public:
    Demo() : num(0) {}
    Demo(int n) : num(n) {}
    int getNum() const {
        return num;
    }
};

int main() {
    Demo d1;
    Demo d2(10);
    cout << d1.getNum() << ", " << d2.getNum() << endl;
    return 0;
}
```
A. 0, 0  
B. 10, 10  
C. 0, 10  
D. Compilation error

<details>
  <summary>Answer</summary>
  C. 0, 10
</details>

### Question 31
**What will be the output of the following program?**

```cpp
#include <iostream>
using namespace std;

class Data {
private:
    int value;

public:
    Data() : value(0) {}
    void setValue(int v) {
        value = v;
    }
    int getValue() const {
        return value;
    }
};

int main() {
    Data d;
    d.setValue(100);
    cout << d.getValue() << endl;
    return 0;
}
```
A. 0  
B. 10  
C. 100  
D. Compilation error

<details>
  <summary>Answer</summary>
  C. 100
</details>

### Question 32
**Which of the following is true about destructors in C++?**

A. Destructors can be overloaded.  
B. Destructors have a return type.  
C. Destructors are called when an object goes out of scope.  
D. Destructors can take arguments.

<details>
  <summary>Answer</summary>
  C. Destructors are called when an object goes out of scope.
</details>

### Question 33
**What will be the output of the following program?**

```cpp
#include <iostream>
using namespace std;

class Sample {
private:
    int number;

public:
    Sample() : number(0) {}
    void setNumber(int n) {
        number = n;
    }
    int getNumber() const {
        return number;
    }
};

int main() {
    Sample s;
    s.setNumber(50);
    cout << s.getNumber() << endl;
    return 0;
}
```
A. 0  
B. 50  
C. 100  
D. Compilation error

<details>
  <summary>Answer</summary>
  B. 50
</details>

### Question 34
**What is the correct way to define a member function outside the class definition?**

```cpp
class Circle {
private:
    double radius;

public:
    void setRadius(double r);
};
```
A.
```cpp
void Circle::setRadius(double r) {
    radius = r;
}
```
B.
```cpp
void setRadius(Circle::double r) {
    radius = r;
}
```
C.
```cpp
void Circle::setRadius(double radius) {
    this->radius = radius;
}
```
D.
```cpp
void setRadius(Circle r) {
    radius = r;
}
```

<details>
  <summary>Answer</summary>
  A.
  ```cpp
  void Circle::setRadius(double r) {
      radius = r;
  }
  ```
</details>

### Question 35
**What will be the output of the following program?**

```cpp
#include <iostream>
using namespace std;

class Example {
private:
    int data;

public:
    Example() : data(0) {}
    void setData(int d) {
        data = d;
    }
    int getData() const {
        return data;
    }
};

int main() {
    Example e;
    e.setData(75);
    cout << e.getData() << endl;
    return 0;
}
```
A. 0  
B. 75  
C. 100  
D. Compilation error

<details>
  <summary>Answer</summary>
  B. 75
</details>
```

You can now copy and paste this content into an `.md` file to create a properly formatted Markdown document with spoilers hiding the answers.
