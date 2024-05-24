
```markdown
### Question 1: Basics of Pointers
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

int main() {
    int num = 10;
    int *ptr = &num;
    cout << *ptr << endl;
    return 0;
}
```

   A. The address of num  
   B. 0  
   C. 10  
   D. Compilation error  

<details>
<summary>Answer</summary>
C. 10
</details>

### Question 2: Pointer Initialization
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

int main() {
    int *ptr = nullptr;
    if (ptr) 
        cout << "Pointer is not null" << endl;
    else 
        cout << "Pointer is null" << endl;
    return 0;
}
```

   A. Pointer is not null  
   B. Pointer is null  
   C. Compilation error  
   D. Runtime error  

<details>
<summary>Answer</summary>
B. Pointer is null
</details>

### Question 3: The Indirection Operator
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

int main() {
    int num = 5;
    int *ptr = &num;
    *ptr = 20;
    cout << num << endl;
    return 0;
}
```

   A. 5  
   B. 20  
   C. The address of num  
   D. Compilation error  

<details>
<summary>Answer</summary>
B. 20
</details>

### Question 4: Relationship Between Arrays and Pointers
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

int main() {
    int vals[] = {4, 7, 11};
    cout << *vals << endl;
    return 0;
}
```

   A. 4  
   B. 7  
   C. 11  
   D. Compilation error  

<details>
<summary>Answer</summary>
A. 4
</details>

### Question 5: Pointer Arithmetic
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

int main() {
    int vals[] = {4, 7, 11};
    int *valptr = vals;
    cout << *(valptr + 2) << endl;
    return 0;
}
```

   A. 4  
   B. 7  
   C. 11  
   D. Compilation error  

<details>
<summary>Answer</summary>
C. 11
</details>

### Question 6: Dynamic Memory Allocation
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

int main() {
    double *dptr = new double;
    *dptr = 3.14;
    cout << *dptr << endl;
    delete dptr;
    return 0;
}
```

   A. 0  
   B. 3.14  
   C. The address of dptr  
   D. Compilation error  

<details>
<summary>Answer</summary>
B. 3.14
</details>

### Question 7: Deleting Dynamic Memory
*What is the purpose of the `delete` operator in C++?*

   A. Allocating memory dynamically  
   B. Initializing a pointer  
   C. Freeing dynamically allocated memory  
   D. None of the above  

<details>
<summary>Answer</summary>
C. Freeing dynamically allocated memory
</details>

### Question 8: Returning Pointers from Functions
*What is the main consideration when returning a pointer from a function?*

   A. The pointer should point to a local variable  
   B. The pointer should point to dynamically allocated memory or data passed to the function  
   C. The pointer should always be `nullptr`  
   D. The function should be inline  

<details>
<summary>Answer</summary>
B. The pointer should point to dynamically allocated memory or data passed to the function
</details>

### Question 9: Smart Pointers
*Which header file must be included to use smart pointers in C++?*

   A. `<iostream>`  
   B. `<vector>`  
   C. `<memory>`  
   D. `<smart>`  

<details>
<summary>Answer</summary>
C. `<memory>`
</details>

### Question 10: Smart Pointers Example
*What will be the output of the following program using a smart pointer?*

```cpp
#include <iostream>
#include <memory>
using namespace std;

int main() {
    unique_ptr<int> ptr(new int);
    *ptr = 42;
    cout << *ptr << endl;
    return 0;
}
```

   A. 0  
   B. 42  
   C. The address of ptr  
   D. Compilation error  

<details>
<summary>Answer</summary>
B. 42
</details>

### Question 11: Pointer to Constant
*What is the output of the following program?*

```cpp
#include <iostream>
using namespace std;

int main() {
    const int SIZE = 3;
    const double rates[SIZE] = {10.5, 20.5, 30.5};
    const double *ptr = rates;
    cout << *ptr << endl;
    return 0;
}
```

   A. 10.5  
   B. 20.5  
   C. 30.5  
   D. Compilation error  

<details>
<summary>Answer</summary>
A. 10.5
</details>

### Question 12: Constant Pointer to Constant
*What is the correct way to declare a constant pointer to a constant?*

   A. `const int *ptr;`  
   B. `int * const ptr;`  
   C. `const int * const ptr;`  
   D. `int const * const ptr;`  

<details>
<summary>Answer</summary>
C. `const int * const ptr;`
</details>

### Question 13: Pointers as Function Parameters
*What is the correct syntax to pass a pointer to a function?*

   A. `void func(int ptr);`  
   B. `void func(int *ptr);`  
   C. `void func(int &ptr);`  
   D. `void func(int **ptr);`  

<details>
<summary>Answer</summary>
B. `void func(int *ptr);`
</details>

### Question 14: Example of Pointer Function Parameter
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

void getNum(int *ptr) {
    *ptr = 100;
}

int main() {
    int num;
    getNum(&num);
    cout << num << endl;
    return 0;
}
```

   A. 0  
   B. 100  
   C. The address of num  
   D. Compilation error  

<details>
<summary>Answer</summary>
B. 100
</details>

### Question 15: Pointer Arithmetic
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

int main() {
    int vals[] = {4, 7, 11};
    int *valptr = vals;
    cout << *(valptr + 1) << endl;
    return 0;
}
```

   A. 4  
   B. 7  
   C. 11  
   D. Compilation error  

<details>
<summary>Answer</summary>
B. 7
</details>

### Question 16: Pointer Comparison
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

int main() {
    int num1 = 5, num2 = 10;
    int *ptr1 = &num1, *ptr2 = &num2;
    if (ptr1 == ptr2)
        cout << "Same address" << endl;
    else
        cout << "Different addresses" << endl;
    return 0;
}
```

   A. Same address  
   B. Different addresses  
   C. The address of num1 and num2  
   D. Compilation error  

<details>
<summary>Answer</summary>
B. Different addresses
</details>

### Question 17: Dynamic Array Allocation
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

int main() {
    int size = 5;
    int *arr = new int[size];
    for (int i = 0; i < size; i++) {
        arr[i] = i * 2;
    }
    cout << arr[3] << endl;
    delete[] arr;
    return 0;
}
```

   A. 3  
   B. 6  
   C. 8  
   D. Compilation error  

<details>
<summary>Answer</summary>
B. 6
</details>

### Question 18: Releasing Dynamic Memory
*What is the correct way to release a dynamically allocated array?*

   A. `delete arr;`  
   B. `delete[] arr;`  
   C. `

free(arr);`  
   D. `release(arr);`  

<details>
<summary>Answer</summary>
B. `delete[] arr;`
</details>

### Question 19: Pointer to Constant Example
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

int main() {
    const int SIZE = 3;
    const double rates[SIZE] = {10.5, 20.5, 30.5};
    const double *ptr = rates;
    ptr++;
    cout << *ptr << endl;
    return 0;
}
```

   A. 10.5  
   B. 20.5  
   C. 30.5  
   D. Compilation error  

<details>
<summary>Answer</summary>
B. 20.5
</details>

### Question 20: Smart Pointer Example
*What will be the output of the following program?*

```cpp
#include <iostream>
#include <memory>
using namespace std;

int main() {
    unique_ptr<int> ptr(new int);
    *ptr = 42;
    cout << *ptr << endl;
    return 0;
}
```

   A. 0  
   B. 42  
   C. The address of ptr  
   D. Compilation error  

<details>
<summary>Answer</summary>
B. 42
</details>
```


The provided questions cover a broad range of topics from the lecture "Chapter 9: Pointers and Dynamic Arrays". However, to ensure that all key areas are thoroughly addressed, let's verify that each major concept from the lecture is represented:

1. **Getting the Address of a Variable**
2. **Pointer Variables**
3. **Pointer Initialization**
4. **The Indirection Operator**
5. **Relationship Between Arrays and Pointers**
6. **Pointer Arithmetic**
7. **Dynamic Memory Allocation**
8. **Releasing Dynamic Memory**
9. **Returning Pointers from Functions**
10. **Smart Pointers**
11. **Pointer to Constant**
12. **Constant Pointer**
13. **Pointers as Function Parameters**

Here are additional questions to ensure all these topics are thoroughly covered:

```markdown
### Question 21: Getting the Address of a Variable
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

int main() {
    int num = 42;
    cout << &num << endl;
    return 0;
}
```

   A. 42  
   B. The address of num  
   C. Compilation error  
   D. Undefined behavior  

<details>
<summary>Answer</summary>
B. The address of num
</details>

### Question 22: Pointer Initialization
*What is the value of the pointer after initialization?*

```cpp
#include <iostream>
using namespace std;

int main() {
    int *ptr = nullptr;
    cout << ptr << endl;
    return 0;
}
```

   A. 0  
   B. nullptr  
   C. The address of ptr  
   D. Compilation error  

<details>
<summary>Answer</summary>
A. 0
</details>

### Question 23: Pointer Variables
*Which of the following correctly defines a pointer to an integer?*

   A. `int ptr;`  
   B. `int *ptr;`  
   C. `int &ptr;`  
   D. `int ptr*;`  

<details>
<summary>Answer</summary>
B. `int *ptr;`
</details>

### Question 24: Using the Indirection Operator
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

int main() {
    int num = 10;
    int *ptr = &num;
    cout << *ptr << endl;
    return 0;
}
```

   A. The address of num  
   B. 0  
   C. 10  
   D. Compilation error  

<details>
<summary>Answer</summary>
C. 10
</details>

### Question 25: Pointer and Array Relationship
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

int main() {
    int vals[] = {10, 20, 30};
    int *ptr = vals;
    cout << ptr[1] << endl;
    return 0;
}
```

   A. 10  
   B. 20  
   C. 30  
   D. Compilation error  

<details>
<summary>Answer</summary>
B. 20
</details>

### Question 26: Using Pointers with Arrays
*Which of the following statements correctly assigns the address of the first element of an array to a pointer?*

   A. `int arr[5], *ptr; ptr = arr;`  
   B. `int arr[5], *ptr; ptr = &arr;`  
   C. `int arr[5], ptr; ptr = arr;`  
   D. `int arr[5], *ptr; ptr = &arr[5];`  

<details>
<summary>Answer</summary>
A. `int arr[5], *ptr; ptr = arr;`
</details>

### Question 27: Pointer Arithmetic
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

int main() {
    int vals[] = {1, 2, 3};
    int *ptr = vals;
    ptr++;
    cout << *ptr << endl;
    return 0;
}
```

   A. 1  
   B. 2  
   C. 3  
   D. Compilation error  

<details>
<summary>Answer</summary>
B. 2
</details>

### Question 28: Dynamic Memory Allocation
*What is the purpose of the `new` operator in C++?*

   A. To delete dynamic memory  
   B. To allocate memory dynamically  
   C. To reallocate memory  
   D. To initialize a pointer  

<details>
<summary>Answer</summary>
B. To allocate memory dynamically
</details>

### Question 29: Returning Pointers from Functions
*Which of the following is a correct way to return a pointer from a function?*

```cpp
int* func() {
    int *ptr = new int;
    *ptr = 10;
    return ptr;
}
```

   A. Returning a pointer to a local variable  
   B. Returning a pointer to dynamically allocated memory  
   C. Returning a pointer to a function argument  
   D. Returning a pointer to a constant  

<details>
<summary>Answer</summary>
B. Returning a pointer to dynamically allocated memory
</details>

### Question 30: Smart Pointers
*Which of the following is NOT a type of smart pointer in C++?*

   A. `unique_ptr`  
   B. `shared_ptr`  
   C. `weak_ptr`  
   D. `auto_ptr`  

<details>
<summary>Answer</summary>
D. `auto_ptr`
</details>

### Question 31: Smart Pointer Usage
*What will be the output of the following program using a smart pointer?*

```cpp
#include <iostream>
#include <memory>
using namespace std;

int main() {
    unique_ptr<int> ptr(new int);
    *ptr = 42;
    cout << *ptr << endl;
    return 0;
}
```

   A. 0  
   B. 42  
   C. The address of ptr  
   D. Compilation error  

<details>
<summary>Answer</summary>
B. 42
</details>

### Question 32: Pointer to Constant
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

int main() {
    const int SIZE = 3;
    const double rates[SIZE] = {10.5, 20.5, 30.5};
    const double *ptr = rates;
    cout << *ptr << endl;
    return 0;
}
```

   A. 10.5  
   B. 20.5  
   C. 30.5  
   D. Compilation error  

<details>
<summary>Answer</summary>
A. 10.5
</details>

### Question 33: Constant Pointer to Constant
*What is the correct way to declare a constant pointer to a constant?*

   A. `const int *ptr;`  
   B. `int * const ptr;`  
   C. `const int * const ptr;`  
   D. `int const * const ptr;`  

<details>
<summary>Answer</summary>
C. `const int * const ptr;`
</details>

### Question 34: Pointers as Function Parameters
*What is the correct syntax to pass a pointer to a function?*

   A. `void func(int ptr);`  
   B. `void func(int *ptr);`  
   C. `void func(int &ptr);`  
   D. `void func(int **ptr);`  

<details>
<summary>Answer</summary>
B. `void func(int *ptr);`
</details>

### Question 35: Example of Pointer Function Parameter
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

void getNum(int *ptr) {
    *ptr = 100;
}

int main() {
    int num;
    getNum(&num);
    cout << num << endl;
    return 0;
}
```

   A. 0  
   B. 100  
   C. The address of num  
   D. Compilation error  

<details>
<summary>Answer</summary>
B. 100
</details>

### Question 36: Pointer Comparison
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

int main() {
    int num1 = 5, num2 = 10;
    int *ptr1 = &num1, *ptr2 = &num2;
    if (ptr1 == ptr2)
        cout << "Same address" << endl;
    else
        cout << "Different addresses" << endl;
    return 0;
}
```

   A. Same address  
   B. Different addresses  
   C. The address of num1 and num2  
   D. Compilation error  

<details>
<summary>Answer</summary>
B. Different addresses
</details>

### Question 37: Dynamic Array Allocation
*What will be the output of the following program?*

```cpp
#include <iostream>
using namespace std;

int size = 5;
int *arr = new int[size];
for (int i = 0; i < size; i++) {
    arr[i] = i * 2;
}
cout << arr[3] << endl;
delete[] arr;
return 0;
```

   A. 3  
   B. 6

  
   C. 8  
   D. Compilation error  

<details>
<summary>Answer</summary>
B. 6
</details>

### Question 38: Releasing Dynamic Memory
*What is the correct way to release a dynamically allocated array?*

   A. `delete arr;`  
   B. `delete[] arr;`  
   C. `free(arr);`  
   D. `release(arr);`  

<details>
<summary>Answer</summary>
B. `delete[] arr;`
</details>

### Question 39: Smart Pointers
*Which of the following is NOT a type of smart pointer in C++?*

   A. `unique_ptr`  
   B. `shared_ptr`  
   C. `weak_ptr`  
   D. `auto_ptr`  

<details>
<summary>Answer</summary>
D. `auto_ptr`
</details>

### Question 40: Smart Pointer Example
*What will be the output of the following program?*

```cpp
#include <iostream>
#include <memory>
using namespace std;

int main() {
    unique_ptr<int> ptr(new int);
    *ptr = 42;
    cout << *ptr << endl;
    return 0;
}
```

   A. 0  
   B. 42  
   C. The address of ptr  
   D. Compilation error  

<details>
<summary>Answer</summary>
B. 42
</details>
```
