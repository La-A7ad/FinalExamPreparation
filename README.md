Certainly! Here's the formatted content suitable for an MD (Markdown) file:

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

### Question 5: Class Design and Member Functions
**Design a class Circle with the following specifications:**
1. Private member variables: radius (double).
2. A default constructor that initializes radius to 1.0.
3. A parameterized constructor that initializes radius to a given value.
4. A public member function getArea that returns the area of the circle.
5. A public member function getCircumference that returns the circumference of the circle.
6. Provide the implementation for each member function.

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

### Question 8: Inline Member Functions
*Explain the advantages and disadvantages of using inline member functions. Provide an example of when it would be appropriate to use an inline member function.*

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
```

You can copy and paste this content into an `.md` file to create a properly formatted Markdown document.
