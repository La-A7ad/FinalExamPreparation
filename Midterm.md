
```markdown
### Question 1: Basic Syntax and Data Types
*What will happen if we attempt to compile the following program?*

```cpp
#include <iostream>
using namespace std;

int main() {
    int x = 65;
    char c = x;
    cout << c << endl;
    return 0;
}
```

   A. Compilation error  
   B. A number will be printed.  
   C. A character will be printed.  
   D. None of the previous  

### Question 2: Application of Concepts - Predicting Outputs
*What is the output of the following program if the user types "Hello, World!" and hits Enter, then types "C++ is fun" then hits Enter?*

```cpp
#include <iostream>
using namespace std;

int main() {
    string s1, s2;
    getline(cin, s1);
    cin >> s2;
    cout << "s1 = " << s1 << "\ns2 = " << s2 << endl;
    return 0;
}
```

   A. s1 = Hello, World!  
      s2 = C++ is fun  
   B. s1 = Hello, World!  
      s2 = World!  
   C. s1 = Hello,  
      s2 = World!  
   D. s1 = Hello, World!  
      s2 = C++  

### Question 3: Operators
___ is the scope resolution operator and ___ is the "address of" operator.

   A. ::, &  
   B. [], &  
   C. ::, &&  
   D. None of the previous  

### Question 4: Increment and Decrement
*What are the values of a, b, and c after the following statements are executed?*

```cpp
int a = 2;
int b = 5;
int c = a * b++;
```

   A. a = 2, b = 5, c = 10  
   B. a = 2, b = 6, c = 10  
   C. a = 2, b = 6, c = 13  
   D. a = 3, b = 6, c = 10  

### Question 5: Structures
*What is the output of the following program?*

```cpp
#include <iostream>
using namespace std;

struct Point2D {
    float x, y;
};

Point2D InitPoint2D() {
    Point2D zero = {0.0, 0.0};
    return zero;
}

int main() {
    Point2D p = InitPoint2D();
    Point2D q = InitPoint2D();
    if (p == q)
        cout << "p = q\n";
    else
        cout << "p != q\n";
    return 0;
}
```

   A. p = q  
   B. Compilation error at line Point2D p = InitPoint2D();  
   C. p != q  
   D. Compilation error at line if (p == q)  

### Question 6: Structure Initialization
*What is the output of the following program?*

```cpp
#include <iostream>
using namespace std;

struct A {
    int x;
    string s;
    char c;
};

int main() {
    A a1 = {1};
    A a2 = {2, "hello"};
    A a3 = {3, "world", 'A'};
    A a4 = {4, 'B'};
    cout << a1.x << a2.x << a3.x << a4.x;
    return 0;
}
```

   A. Compilation error at line A a1 = {1};  
   B. 1234  
   C. Compilation error at line A a2 = {2, "hello"};  
   D. Compilation error at line A a4 = {4, 'B'};  

### Question 7: Arrays
*What is the output of the following code?*

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[] = {1, 2, 3, 4, 5};
    for(int i = 0; i < 10; i++)
        cout << arr[i] << " ";
    cout << endl;
    return 0;
}
```

   A. Compilation error at line 6 due to missing braces {}  
   B. 1 2 3 4 5  
   C. Compilation error at line 7 due to array index overflow  
   D. None of the previous  

### Question 8: Arrays and Dimensions
In C++, you can create arrays of ___ dimension(s).

   A. only 1  
   B. only 1 and 2  
   C. only 1, 2, and 3  
   D. None of the previous  

### Question 9: Scope Resolution Operator
*What is the output of the following program?*

```cpp
#include <iostream>
using namespace std;

char c = 'A';
int main() {
    char c = 'B';
    {
        char c = 'C';
        cout << c;
        cout << ::c;
    }
    cout << c;
    cout << ::c;
    return 0;
}
```

   A. CABA  
   B. AAAA  
   C. Compilation error: Cannot have multiple variables with the same name.  
   D. BCBA  

### Question 10: Class and Object
*What does the following program print on the screen?*

```cpp
#include <iostream>
using namespace std;

class Student {
    string name;
};

int main() {
    Student s;
    s.name = "Mohamed Hassan";
    cout << s.name << endl;
    return 0;
}
```

   A. Mohamed Hassan  
   B. Compilation error at line 10 because name is private.  
   C. Compilation error at line 10 because name is public.  
   D. Compilation error at line 6 because the class has no constructors.  

### Question 11: Class Design
**Write a class named Complex that represents a complex number with the following specifications:**

1. Two private float members named real and imaginary that represent the real and imaginary parts of the number respectively. (1 Point)
2. A public constructor that takes no arguments and initializes the real and imaginary parts to zeros. (1 Point)
3. A public constructor that takes two arguments to initialize the real and imaginary parts. (1 Point)
4. Get methods and set methods for the two members of the class. (1 Point)
5. A method called print that prints a complex number on the screen as \( a + bi \), where \( a \) and \( b \) are the real and imaginary parts respectively. (1 Point)
6. A method called add that takes one Complex object, adds it to the existing object and returns the result as a Complex object. If \( a + bi \) and \( c + di \) are two complex numbers, then their addition is \( (a+c) + (b+d)i \). (1 Point)
```

You can copy and paste this content into an `.md` file to create a properly formatted Markdown document.
