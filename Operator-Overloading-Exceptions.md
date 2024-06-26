
### Question 1: Basic Syntax
*What is the correct syntax to overload the `+` operator in a class?*

```cpp
class Complex {
private:
    float real, imaginary;
public:
    Complex operator+(Complex other) const;
};
```

   A. `Complex Complex::operator+(Complex other) const;`  
   B. `Complex operator+ Complex::(Complex other) const;`  
   C. `Complex operator+(Complex other) const;`  
   D. `Complex operator+(Complex other);`  

<details>
<summary>Answer</summary>
C. `Complex operator+(Complex other) const;`
</details>

### Question 2: Access Specifiers
*Which access specifier is typically used for member variables that should not be directly accessed outside the class?*

   A. public  
   B. private  
   C. protected  
   D. internal  

<details>
<summary>Answer</summary>
B. private
</details>

### Question 3: Overloading Stream Insertion Operator
*What is the correct way to overload the stream insertion operator (`<<`) for a class `Complex`?*

```cpp
class Complex {
private:
    float real, imaginary;
public:
    friend ostream& operator<<(ostream& os, const Complex& c);
};
```

   A. `ostream& operator<<(ostream& os, const Complex& c);`  
   B. `ostream& operator<<(ostream& os, Complex& c);`  
   C. `ostream& operator<<(ostream os, const Complex c);`  
   D. `ostream& operator<<(ostream os, Complex c);`  

<details>
<summary>Answer</summary>
A. `ostream& operator<<(ostream& os, const Complex& c);`
</details>

#### Application of Concepts

### Question 4: Predicting Outputs
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Complex {
private:
    float real, imaginary;
public:
    Complex() { real = 0; imaginary = 0; }
    Complex(float r, float i) { real = r; imaginary = i; }
    Complex operator+(Complex other) const {
        return Complex(real + other.real, imaginary + other.imaginary);
    }
    void print() {
        cout << real << (imaginary >= 0 ? " + " : " - ") << (imaginary >= 0 ? imaginary : -imaginary) << "i";
    }
};

int main() {
    Complex c1(2.5, -3.5);
    Complex c2(15.6, 39.12);
    (c1 + c2).print();
    return 0;
}
```

   A. 18.1 + 35.62i  
   B. 18.1 - 35.62i  
   C. 18.1 + 42.62i  
   D. 2.5 - 3.5i  

<details>
<summary>Answer</summary>
A. 18.1 + 35.62i
</details>

### Question 5: Debugging Code
*Identify the error in the following program and correct it.*

```cpp
#include <iostream>
using namespace std;

class Complex {
private:
    float real, imaginary;
public:
    Complex() { real = 0; imaginary = 0; }
    Complex(float r, float i) { real = r; imaginary = i; }
    Complex operator+(Complex other) const {
        return Complex(real + other.get_real(), imaginary + other.get_imaginary());
    }
    void print() {
        cout << real << (imaginary >= 0 ? " + " : " - ") << (imaginary >= 0 ? imaginary : -imaginary) << "i";
    }
};

int main() {
    Complex c1(2.5, -3.5);
    Complex c2(15.6, 39.12);
    (c1 + c2).print();
    return 0;
}
```

<details>
<summary>Answer</summary>
The error is that the member functions `get_real` and `get_imaginary` are not defined.

Corrected code:
```cpp
#include <iostream>
using namespace std;

class Complex {
private:
    float real, imaginary;
public:
    Complex() { real = 0; imaginary = 0; }
    Complex(float r, float i) { real = r; imaginary = i; }
    float get_real() const { return real; }
    float get_imaginary() const { return imaginary; }
    Complex operator+(Complex other) const {
        return Complex(real + other.get_real(), imaginary + other.get_imaginary());
    }
    void print() {
        cout << real << (imaginary >= 0 ? " + " : " - ") << (imaginary >= 0 ? imaginary : -imaginary) << "i";
    }
};

int main() {
    Complex c1(2.5, -3.5);
    Complex c2(15.6, 39.12);
    (c1 + c2).print();
    return 0;
}
```
</details>

### Question 6: Exception Handling
*What will be the output of the following program?*

```cpp
#include <iostream>
#include <string>
using namespace std;

float divide(float x, float y) {
    if (y == 0) {
        throw string("Division by zero.");
    }
    return x / y;
}

int main() {
    float x = 1, y = 2;
    cout << divide(x, y) << endl;
    y = 0;
    try {
        cout << divide(x, y) << endl;
    } catch (string err) {
        cout << "Exception: " << err << endl;
    }
    return 0;
}
```

   A. 0.5 Exception: Division by zero.  
   B. 0.5 0  
   C. 0.5 Exception: 0  
   D. Exception: Division by zero.  

<details>
<summary>Answer</summary>
A. 0.5 Exception: Division by zero.
</details>

### Question 7: Custom Exceptions
*What will be the output of the following program if the user inputs -500 for the radius?*

```cpp
#include <iostream>
using namespace std;

class Circle {
private:
    double radius;
public:
    static const double LIMIT;
    class NegativeRadiusException {};
    class RadiusTooBigException {};
    Circle() { radius = 0; }
    Circle(double r) {
        if (r < 0)
            throw NegativeRadiusException();
        else if (r > LIMIT)
            throw RadiusTooBigException();
        radius = r;
    }
    void set_radius(double r) {
        if (r < 0)
            throw NegativeRadiusException();
        else if (r > LIMIT)
            throw RadiusTooBigException();
        radius = r;
    }
    void print() { cout << "Circle with radius: " << radius << endl; }
};

const double Circle::LIMIT = 5000;

int main() {
    try {
        Circle c(-500);
        c.print();
    } catch (Circle::NegativeRadiusException) {
        cout << "Error: Negative radius" << endl;
    } catch (Circle::RadiusTooBigException) {
        cout << "Error: Radius too big" << endl;
    }
    return 0;
}
```

   A. Circle with radius: -500  
   B. Circle with radius: 0  
   C. Error: Negative radius  
   D. Error: Radius too big  

<details>
<summary>Answer</summary>
C. Error: Negative radius
</details>

#### Understanding Classes and Structures

### Question 8: Overloading the Extraction Operator
*What is the correct way to overload the extraction operator (`>>`) for a class `Complex`?*

```cpp
class Complex {
private:
    float real, imaginary;
public:
    friend istream& operator>>(istream& is, Complex& c);
};
```

   A. `istream& operator>>(istream& is, Complex& c);`  
   B. `istream& operator>>(istream& is, const Complex& c);`  
   C. `istream& operator>>(istream is, Complex c);`  
   D. `istream operator>>(istream& is, Complex& c);`  

<details>
<summary>Answer</summary>
A. `istream& operator>>(istream& is, Complex& c);`
</details>

### Question 9: Function Signatures
*Which of the following function signatures correctly overloads the `==` operator for a class `Complex`?*

```cpp
class Complex {
private:
    float real, imaginary;
public:
    bool operator==(Complex other) const;
};
```

   A. `bool Complex::operator==(Complex other) const;`  
   B. `bool operator==(const Complex other) const;`  
   C. `bool operator== Complex(const Complex other) const;`  
   D. `bool operator==(Complex other) const;`  

<details>
<summary>Answer</summary>
D. `bool operator==(Complex other) const;`
</details>

### Question 10: Handling Multiple Exceptions
*What will be the output of the following program if the user inputs 6000 for the radius?*

```cpp
#include <iostream>
using namespace std;

class Circle {
private:
    double radius;
public:
    static const double LIMIT;


    class NegativeRadiusException {};
    class RadiusTooBigException {};
    Circle() { radius = 0; }
    Circle(double r) {
        if (r < 0)
            throw NegativeRadiusException();
        else if (r > LIMIT)
            throw RadiusTooBigException();
        radius = r;
    }
    void set_radius(double r) {
        if (r < 0)
            throw NegativeRadiusException();
        else if (r > LIMIT)
            throw RadiusTooBigException();
        radius = r;
    }
    void print() { cout << "Circle with radius: " << radius << endl; }
};

const double Circle::LIMIT = 5000;

int main() {
    try {
        Circle c(6000);
        c.print();
    } catch (Circle::NegativeRadiusException) {
        cout << "Error: Negative radius" << endl;
    } catch (Circle::RadiusTooBigException) {
        cout << "Error: Radius too big" << endl;
    }
    return 0;
}
```

   A. Circle with radius: 6000  
   B. Circle with radius: 0  
   C. Error: Negative radius  
   D. Error: Radius too big  

<details>
<summary>Answer</summary>
D. Error: Radius too big
</details>

### Question 11: Overloading != Operator
*What is the correct way to overload the `!=` operator for a class `Complex`?*

```cpp
class Complex {
private:
    float real, imaginary;
public:
    bool operator!=(Complex other) const;
};
```

   A. `bool Complex::operator!=(Complex other) const { return !(*this == other); }`  
   B. `bool operator!=(Complex other) const { return !(*this == other); }`  
   C. `bool Complex::operator!=(const Complex other) const { return !(*this == other); }`  
   D. `bool operator!=(Complex other) const { return !(*this == other); }`  

<details>
<summary>Answer</summary>
A. `bool Complex::operator!=(Complex other) const { return !(*this == other); }`
</details>

### Question 12: Custom Exception Classes
*Which of the following statements is true about custom exception classes?*

   A. Custom exception classes must inherit from the `exception` class.  
   B. Custom exception classes cannot have member variables.  
   C. Custom exception classes are used to handle specific error conditions in a program.  
   D. Custom exception classes must override the `what` method.  

<details>
<summary>Answer</summary>
C. Custom exception classes are used to handle specific error conditions in a program.
</details>

### Question 13: Operator Overloading Restrictions
*Which of the following operators cannot be overloaded in C++?*

   A. `+`  
   B. `==`  
   C. `.`  
   D. `>>`  

<details>
<summary>Answer</summary>
C. `.`
</details>

### Question 14: Exception Handling Keywords
*Which of the following keywords is used to throw an exception in C++?*

   A. `try`  
   B. `throw`  
   C. `catch`  
   D. `except`  

<details>
<summary>Answer</summary>
B. `throw`
</details>

### Question 15: Overloading Stream Operators
*What is the correct return type for the overloaded stream insertion operator (`<<`) in a class `Complex`?*

```cpp
class Complex {
private:
    float real, imaginary;
public:
    friend ostream& operator<<(ostream& os, const Complex& c);
};
```

   A. `Complex`  
   B. `ostream`  
   C. `ostream&`  
   D. `void`  

<details>
<summary>Answer</summary>
C. `ostream&`
</details>

### Question 16: Exception Handling Example
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

float divide(float x, float y) {
    if (y == 0) {
        throw "Division by zero.";
    }
    return x / y;
}

int main() {
    float x = 1, y = 2;
    cout << divide(x, y) << endl;
    y = 0;
    try {
        cout << divide(x, y) << endl;
    } catch (const char* err) {
        cout << "Exception: " << err << endl;
    }
    return 0;
}
```

   A. 0.5 Exception: Division by zero.  
   B. 0.5 0  
   C. 0.5 Exception: 0  
   D. Exception: Division by zero.  

<details>
<summary>Answer</summary>
A. 0.5 Exception: Division by zero.
</details>

### Question 17: Friend Functions
*What is the purpose of a friend function in C++?*

   A. To allow a function to access private and protected members of a class.  
   B. To enable dynamic binding.  
   C. To allow multiple inheritance.  
   D. To hide the base class function.  

<details>
<summary>Answer</summary>
A. To allow a function to access private and protected members of a class.
</details>

### Question 18: Catching Exceptions
*What is the correct way to catch an exception thrown by a function in C++?*

```cpp
void func() {
    throw "Error occurred.";
}

int main() {
    try {
        func();
    } catch (const char* msg) {
        cout << msg << endl;
    }
    return 0;
}
```

   A. `catch (char* msg)`  
   B. `catch (const char* msg)`  
   C. `catch (char msg)`  
   D. `catch (const char msg)`  

<details>
<summary>Answer</summary>
B. `catch (const char* msg)`
</details>

### Question 19: Multiple Catch Blocks
*What will be the output of the following program if the user inputs -10 for the radius?*

```cpp
#include <iostream>
using namespace std;

class Circle {
private:
    double radius;
public:
    static const double LIMIT;
    class NegativeRadiusException {};
    class RadiusTooBigException {};
    Circle() { radius = 0; }
    Circle(double r) {
        if (r < 0)
            throw NegativeRadiusException();
        else if (r > LIMIT)
            throw RadiusTooBigException();
        radius = r;
    }
    void set_radius(double r) {
        if (r < 0)
            throw NegativeRadiusException();
        else if (r > LIMIT)
            throw RadiusTooBigException();
        radius = r;
    }
    void print() { cout << "Circle with radius: " << radius << endl; }
};

const double Circle::LIMIT = 5000;

int main() {
    try {
        Circle c(-10);
        c.print();
    } catch (Circle::NegativeRadiusException) {
        cout << "Error: Negative radius" << endl;
    } catch (Circle::RadiusTooBigException) {
        cout << "Error: Radius too big" << endl;
    }
    return 0;
}
```

   A. Circle with radius: -10  
   B. Circle with radius: 0  
   C. Error: Negative radius  
   D. Error: Radius too big  

<details>
<summary>Answer</summary>
C. Error: Negative radius
</details>

### Question 20: Operator Overloading Rules
*Which of the following statements is true about operator overloading in C++?*

   A. You can change the number of operands of an operator.  
   B. You cannot overload the `[]` operator.  
   C. You can overload the `.` operator.  
   D. You cannot change the precedence of an operator.  

<details>
<summary>Answer</summary>
D. You cannot change the precedence of an operator.
</details>
```

To ensure the exam questions cover all content from Lecture 10 on Operator Overloading and Exceptions, let's revisit the key topics discussed in the lecture and verify if each is addressed in the questions:

1. **Operator Overloading Basics**
   - Syntax and concepts
   - Overloading specific operators (+, ==, <<, >>)
2. **Exception Handling Basics**
   - Keywords (throw, try, catch)
   - Handling exceptions (built-in and custom exceptions)
3. **Example Implementations**
   - Overloading operators in the `Complex` class
   - Handling specific error conditions in custom exception classes

Here’s a comprehensive set of questions addressing each topic:

### Exam Questions on Lecture 10: Operator Overloading and Exceptions

#### Emphasis on Fundamentals

### Question 1: Basic Syntax
*What is the correct syntax to overload the `+` operator in a class?*

```cpp
class Complex {
private:
    float real, imaginary;
public:
    Complex operator+(Complex other) const;
};
```

   A. `Complex Complex::operator+(Complex other) const;`  
   B. `Complex operator+ Complex::(Complex other) const;`  
   C. `Complex operator+(Complex other) const;`  
   D. `Complex operator+(Complex other);`  

<details>
<summary>Answer</summary>
C. `Complex operator+(Complex other) const;`
</details>

### Question 2: Access Specifiers
*Which access specifier is typically used for member variables that should not be directly accessed outside the class?*

   A. public  
   B. private  
   C. protected  
   D. internal  

<details>
<summary>Answer</summary>
B. private
</details>

### Question 3: Overloading Stream Insertion Operator
*What is the correct way to overload the stream insertion operator (`<<`) for a class `Complex`?*

```cpp
class Complex {
private:
    float real, imaginary;
public:
    friend ostream& operator<<(ostream& os, const Complex& c);
};
```

   A. `ostream& operator<<(ostream& os, const Complex& c);`  
   B. `ostream& operator<<(ostream& os, Complex& c);`  
   C. `ostream& operator<<(ostream os, const Complex c);`  
   D. `ostream& operator<<(ostream os, Complex c);`  

<details>
<summary>Answer</summary>
A. `ostream& operator<<(ostream& os, const Complex& c);`
</details>

#### Application of Concepts

### Question 4: Predicting Outputs
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Complex {
private:
    float real, imaginary;
public:
    Complex() { real = 0; imaginary = 0; }
    Complex(float r, float i) { real = r; imaginary = i; }
    Complex operator+(Complex other) const {
        return Complex(real + other.real, imaginary + other.imaginary);
    }
    void print() {
        cout << real << (imaginary >= 0 ? " + " : " - ") << (imaginary >= 0 ? imaginary : -imaginary) << "i";
    }
};

int main() {
    Complex c1(2.5, -3.5);
    Complex c2(15.6, 39.12);
    (c1 + c2).print();
    return 0;
}
```

   A. 18.1 + 35.62i  
   B. 18.1 - 35.62i  
   C. 18.1 + 42.62i  
   D. 2.5 - 3.5i  

<details>
<summary>Answer</summary>
A. 18.1 + 35.62i
</details>

### Question 5: Debugging Code
*Identify the error in the following program and correct it.*

```cpp
#include <iostream>
using namespace std;

class Complex {
private:
    float real, imaginary;
public:
    Complex() { real = 0; imaginary = 0; }
    Complex(float r, float i) { real = r; imaginary = i; }
    Complex operator+(Complex other) const {
        return Complex(real + other.get_real(), imaginary + other.get_imaginary());
    }
    void print() {
        cout << real << (imaginary >= 0 ? " + " : " - ") << (imaginary >= 0 ? imaginary : -imaginary) << "i";
    }
};

int main() {
    Complex c1(2.5, -3.5);
    Complex c2(15.6, 39.12);
    (c1 + c2).print();
    return 0;
}
```

<details>
<summary>Answer</summary>
The error is that the member functions `get_real` and `get_imaginary` are not defined.

Corrected code:
```cpp
#include <iostream>
using namespace std;

class Complex {
private:
    float real, imaginary;
public:
    Complex() { real = 0; imaginary = 0; }
    Complex(float r, float i) { real = r; imaginary = i; }
    float get_real() const { return real; }
    float get_imaginary() const { return imaginary; }
    Complex operator+(Complex other) const {
        return Complex(real + other.get_real(), imaginary + other.get_imaginary());
    }
    void print() {
        cout << real << (imaginary >= 0 ? " + " : " - ") << (imaginary >= 0 ? imaginary : -imaginary) << "i";
    }
};

int main() {
    Complex c1(2.5, -3.5);
    Complex c2(15.6, 39.12);
    (c1 + c2).print();
    return 0;
}
```
</details>

### Question 6: Exception Handling
*What will be the output of the following program?*

```cpp
#include <iostream>
#include <string>
using namespace std;

float divide(float x, float y) {
    if (y == 0) {
        throw string("Division by zero.");
    }
    return x / y;
}

int main() {
    float x = 1, y = 2;
    cout << divide(x, y) << endl;
    y = 0;
    try {
        cout << divide(x, y) << endl;
    } catch (string err) {
        cout << "Exception: " << err << endl;
    }
    return 0;
}
```

   A. 0.5 Exception: Division by zero.  
   B. 0.5 0  
   C. 0.5 Exception: 0  
   D. Exception: Division by zero.  

<details>
<summary>Answer</summary>
A. 0.5 Exception: Division by zero.
</details>

### Question 7: Custom Exceptions
*What will be the output of the following program if the user inputs -500 for the radius?*

```cpp
#include <iostream>
using namespace std;

class Circle {
private:
    double radius;
public:
    static const double LIMIT;
    class NegativeRadiusException {};
    class RadiusTooBigException {};
    Circle() { radius = 0; }
    Circle(double r) {
        if (r < 0)
            throw NegativeRadiusException();
        else if (r > LIMIT)
            throw RadiusTooBigException();
        radius = r;
    }
    void set_radius(double r) {
        if (r < 0)
            throw NegativeRadiusException();
        else if (r > LIMIT)
            throw RadiusTooBigException();
        radius = r;
    }
    void print() { cout << "Circle with radius: " << radius << endl; }
};

const double Circle::LIMIT = 5000;

int main() {
    try {
        Circle c(-500);
        c.print();
    } catch (Circle::NegativeRadiusException) {
        cout << "Error: Negative radius" << endl;
    } catch (Circle::RadiusTooBigException) {
        cout << "Error: Radius too big" << endl;
    }
    return 0;
}
```

   A. Circle with radius: -500  
   B. Circle with radius: 0  
   C. Error: Negative radius  
   D. Error: Radius too big  

<details>
<summary>Answer</summary>
C. Error: Negative radius
</details>

#### Understanding Classes and Structures

### Question 8: Overloading the Extraction Operator
*What is the correct way to overload the extraction operator (`>>`) for a class `Complex`?*

```cpp
class Complex {
private:
    float real, imaginary;
public:
    friend istream& operator>>(istream& is, Complex& c);
};
```

   A. `istream& operator>>(istream& is, Complex& c);`  
   B. `istream& operator>>(istream& is, const Complex& c);`  
   C. `istream& operator>>(istream is, Complex c);`  
   D. `istream operator>>(istream& is, Complex& c);`  

<details>
<summary>Answer</summary>
A. `istream& operator>>(istream& is, Complex& c);`
</details>

### Question 9: Function Signatures
*Which of the following function signatures correctly overloads the `==` operator for a class `Complex`?*

```cpp
class Complex {
private:
    float real, imaginary;
public:
    bool operator==(Complex other) const;
};
```

   A. `bool Complex::operator==(Complex

 other) const;`  
   B. `bool operator==(const Complex other) const;`  
   C. `bool operator== Complex(const Complex other) const;`  
   D. `bool operator==(Complex other) const;`  

<details>
<summary>Answer</summary>
D. `bool operator==(Complex other) const;`
</details>

### Question 10: Handling Multiple Exceptions
*What will be the output of the following program if the user inputs 6000 for the radius?*

```cpp
#include <iostream>
using namespace std;

class Circle {
private:
    double radius;
public:
    static const double LIMIT;
    class NegativeRadiusException {};
    class RadiusTooBigException {};
    Circle() { radius = 0; }
    Circle(double r) {
        if (r < 0)
            throw NegativeRadiusException();
        else if (r > LIMIT)
            throw RadiusTooBigException();
        radius = r;
    }
    void set_radius(double r) {
        if (r < 0)
            throw NegativeRadiusException();
        else if (r > LIMIT)
            throw RadiusTooBigException();
        radius = r;
    }
    void print() { cout << "Circle with radius: " << radius << endl; }
};

const double Circle::LIMIT = 5000;

int main() {
    try {
        Circle c(6000);
        c.print();
    } catch (Circle::NegativeRadiusException) {
        cout << "Error: Negative radius" << endl;
    } catch (Circle::RadiusTooBigException) {
        cout << "Error: Radius too big" << endl;
    }
    return 0;
}
```

   A. Circle with radius: 6000  
   B. Circle with radius: 0  
   C. Error: Negative radius  
   D. Error: Radius too big  

<details>
<summary>Answer</summary>
D. Error: Radius too big
</details>

### Question 11: Overloading != Operator
*What is the correct way to overload the `!=` operator for a class `Complex`?*

```cpp
class Complex {
private:
    float real, imaginary;
public:
    bool operator!=(Complex other) const;
};
```

   A. `bool Complex::operator!=(Complex other) const { return !(*this == other); }`  
   B. `bool operator!=(Complex other) const { return !(*this == other); }`  
   C. `bool Complex::operator!=(const Complex other) const { return !(*this == other); }`  
   D. `bool operator!=(Complex other) const { return !(*this == other); }`  

<details>
<summary>Answer</summary>
A. `bool Complex::operator!=(Complex other) const { return !(*this == other); }`
</details>

### Question 12: Custom Exception Classes
*Which of the following statements is true about custom exception classes?*

   A. Custom exception classes must inherit from the `exception` class.  
   B. Custom exception classes cannot have member variables.  
   C. Custom exception classes are used to handle specific error conditions in a program.  
   D. Custom exception classes must override the `what` method.  

<details>
<summary>Answer</summary>
C. Custom exception classes are used to handle specific error conditions in a program.
</details>

### Question 13: Operator Overloading Restrictions
*Which of the following operators cannot be overloaded in C++?*

   A. `+`  
   B. `==`  
   C. `.`  
   D. `>>`  

<details>
<summary>Answer</summary>
C. `.`
</details>

### Question 14: Exception Handling Keywords
*Which of the following keywords is used to throw an exception in C++?*

   A. `try`  
   B. `throw`  
   C. `catch`  
   D. `except`  

<details>
<summary>Answer</summary>
B. `throw`
</details>

### Question 15: Overloading Stream Operators
*What is the correct return type for the overloaded stream insertion operator (`<<`) in a class `Complex`?*

```cpp
class Complex {
private:
    float real, imaginary;
public:
    friend ostream& operator<<(ostream& os, const Complex& c);
};
```

   A. `Complex`  
   B. `ostream`  
   C. `ostream&`  
   D. `void`  

<details>
<summary>Answer</summary>
C. `ostream&`
</details>

### Question 16: Exception Handling Example
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

float divide(float x, float y) {
    if (y == 0) {
        throw "Division by zero.";
    }
    return x / y;
}

int main() {
    float x = 1, y = 2;
    cout << divide(x, y) << endl;
    y = 0;
    try {
        cout << divide(x, y) << endl;
    } catch (const char* err) {
        cout << "Exception: " << err << endl;
    }
    return 0;
}
```

   A. 0.5 Exception: Division by zero.  
   B. 0.5 0  
   C. 0.5 Exception: 0  
   D. Exception: Division by zero.  

<details>
<summary>Answer</summary>
A. 0.5 Exception: Division by zero.
</details>

### Question 17: Friend Functions
*What is the purpose of a friend function in C++?*

   A. To allow a function to access private and protected members of a class.  
   B. To enable dynamic binding.  
   C. To allow multiple inheritance.  
   D. To hide the base class function.  

<details>
<summary>Answer</summary>
A. To allow a function to access private and protected members of a class.
</details>

### Question 18: Catching Exceptions
*What is the correct way to catch an exception thrown by a function in C++?*

```cpp
void func() {
    throw "Error occurred.";
}

int main() {
    try {
        func();
    } catch (const char* msg) {
        cout << msg << endl;
    }
    return 0;
}
```

   A. `catch (char* msg)`  
   B. `catch (const char* msg)`  
   C. `catch (char msg)`  
   D. `catch (const char msg)`  

<details>
<summary>Answer</summary>
B. `catch (const char* msg)`
</details>

### Question 19: Multiple Catch Blocks
*What will be the output of the following program if the user inputs -10 for the radius?*

```cpp
#include <iostream>
using namespace std;

class Circle {
private:
    double radius;
public:
    static const double LIMIT;
    class NegativeRadiusException {};
    class RadiusTooBigException {};
    Circle() { radius = 0; }
    Circle(double r) {
        if (r < 0)
            throw NegativeRadiusException();
        else if (r > LIMIT)
            throw RadiusTooBigException();
        radius = r;
    }
    void set_radius(double r) {
        if (r < 0)
            throw NegativeRadiusException();
        else if (r > LIMIT)
            throw RadiusTooBigException();
        radius = r;
    }
    void print() { cout << "Circle with radius: " << radius << endl; }
};

const double Circle::LIMIT = 5000;

int main() {
    try {
        Circle c(-10);
        c.print();
    } catch (Circle::NegativeRadiusException) {
        cout << "Error: Negative radius" << endl;
    } catch (Circle::RadiusTooBigException) {
        cout << "Error: Radius too big" << endl;
    }
    return 0;
}
```

   A. Circle with radius: -10  
   B. Circle with radius: 0  
   C. Error: Negative radius  
   D. Error: Radius too big  

<details>
<summary>Answer</summary>
C. Error: Negative radius
</details>

### Question 20: Operator Overloading Rules
*Which of the following statements is true about operator overloading in C++?*

   A. You can change the number of operands of an operator.  
   B. You cannot overload the `[]` operator.  
   C. You can overload the `.` operator.  
   D. You cannot change the precedence of an operator.  

<details>
<summary>Answer</summary>
D. You cannot change the precedence of an operator.
</details>

### Question 21: Overloading Stream Insertion Operator
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Complex {
private:
    float real, imaginary;
public:
    Complex() { real = 0; imaginary = 0; }
    Complex(float r, float i) { real = r; imaginary = i; }
    friend ostream& operator<<(ostream& os, const Complex& c) {
        os << c.real << (c.imaginary >= 0 ? " + " : " - ") << (c.imaginary >= 0 ? c.imaginary : -c.imaginary) << "i";
        return os;
    }
};

int main() {
    Complex c1(2.5, -3.5);
    Complex c2(15.6, 39.12);
    cout << c1 << endl;
    cout <<

 c2 << endl;
    return 0;
}
```

   A. 2.5 - 3.5i 15.6 + 39.12i  
   B. 2.5 - 3.5i 15.6 - 39.12i  
   C. 2.5 + 3.5i 15.6 + 39.12i  
   D. Compilation error  

<details>
<summary>Answer</summary>
A. 2.5 - 3.5i 15.6 + 39.12i
</details>

### Question 22: Exception Handling Example
*What will be the output of the following program?*

```cpp
#include <iostream>
#include <string>
using namespace std;

float divide(float x, float y) {
    if (y == 0) {
        throw string("Division by zero.");
    }
    return x / y;
}

int main() {
    float x = 1, y = 0;
    try {
        cout << divide(x, y) << endl;
    } catch (string err) {
        cout << "Exception: " << err << endl;
    }
    return 0;
}
```

   A. 0  
   B. 1  
   C. Exception: Division by zero.  
   D. Undefined behavior  

<details>
<summary>Answer</summary>
C. Exception: Division by zero.
</details>

### Question 23: Overloading == Operator
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

class Complex {
private:
    float real, imaginary;
public:
    Complex() { real = 0; imaginary = 0; }
    Complex(float r, float i) { real = r; imaginary = i; }
    bool operator==(const Complex& other) const {
        return (real == other.real && imaginary == other.imaginary);
    }
};

int main() {
    Complex c1(2.5, -3.5);
    Complex c2(2.5, -3.5);
    Complex c3(15.6, 39.12);
    cout << "Is c1 == c2? " << (c1 == c2) << endl;
    cout << "Is c1 == c3? " << (c1 == c3) << endl;
    return 0;
}
```

   A. Is c1 == c2? 0 Is c1 == c3? 0  
   B. Is c1 == c2? 1 Is c1 == c3? 0  
   C. Is c1 == c2? 0 Is c1 == c3? 1  
   D. Compilation error  

<details>
<summary>Answer</summary>
B. Is c1 == c2? 1 Is c1 == c3? 0
</details>

### Question 24: Creating Custom Exceptions
*What will be the output of the following program if the user inputs 6000 for the radius?*

```cpp
#include <iostream>
using namespace std;

class Circle {
private:
    double radius;
public:
    static const double LIMIT;
    class NegativeRadiusException {};
    class RadiusTooBigException {};
    Circle() { radius = 0; }
    Circle(double r) {
        if (r < 0)
            throw NegativeRadiusException();
        else if (r > LIMIT)
            throw RadiusTooBigException();
        radius = r;
    }
    void set_radius(double r) {
        if (r < 0)
            throw NegativeRadiusException();
        else if (r > LIMIT)
            throw RadiusTooBigException();
        radius = r;
    }
    void print() { cout << "Circle with radius: " << radius << endl; }
};

const double Circle::LIMIT = 5000;

int main() {
    try {
        Circle c(6000);
        c.print();
    } catch (Circle::NegativeRadiusException) {
        cout << "Error: Negative radius" << endl;
    } catch (Circle::RadiusTooBigException) {
        cout << "Error: Radius too big" << endl;
    }
    return 0;
}
```

   A. Circle with radius: 6000  
   B. Circle with radius: 0  
   C. Error: Negative radius  
   D. Error: Radius too big  

<details>
<summary>Answer</summary>
D. Error: Radius too big
</details>

### Question 25: Throwing and Catching Exceptions
*What will be the output of the following program?*

```cpp
#include <iostream>
#include <string>
using namespace std;

void checkAge(int age) {
    if (age < 18) {
        throw string("Too young.");
    }
    cout << "Access granted." << endl;
}

int main() {
    try {
        checkAge(15);
    } catch (string err) {
        cout << "Exception: " << err << endl;
    }
    return 0;
}
```

   A. Access granted.  
   B. Exception: Too young.  
   C. Compilation error  
   D. Undefined behavior  

<details>
<summary>Answer</summary>
B. Exception: Too young.
</details>

---
