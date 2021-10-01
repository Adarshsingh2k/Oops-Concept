### Oops - Concept

## Polymorphism:-
   
   ### Compile Time Polymorphism
   
      A. Function Overloading
        When there are multiple functions with same name but different parameters then these functions are said to be
        overloaded. Functions can be overloaded by change in number of arguments or/and change in type of arguments.
        
        
```c++
#include <bits/stdc++.h>
using namespace std;
// function Overloading
class prac{
    public:
        void func(int x){
            cout<<"FIrst Func Called "<<x<<endl;
        }

        void func(int x,int y){
            cout<<"Second Func "<< x+y<<endl;
        }

};
int main() {
    prac p;

    p.func(5);
    p.func(5,25);

    
}

Output-
FIrst Func Called 5
Second Func 30

```
        B. Operator Overloading
        
           C++ also provide option to overload operators. For example, we can make the operator (‘+’) for string class to
           concatenate two strings. We know that this is the addition operator whose task is to add two operands. 
           So a single operator ‘+’ when placed between integer operands , adds them and when placed between 
           string operands, concatenates them.
           
           List of operators that can be overloaded are:

              +    -    *    /      %        ^
              &    |    ~    !,        =
                  =      ++        --
                  ==    !=      &&        ||
              +=    -=    /=    %=      ^=        &=
              |=    *=    =      []        ()
              ->    ->*    new    new []      delete    delete []
            
            List of operators that cannot be overloaded

              1> Scope Resolution Operator  (::)    
              2> Pointer-to-member Operator (.*)    
              3> Member Access or Dot operator  (.)    
              4> Ternary or Conditional Operator (?:) 
              5> Object size Operator   (sizeof) 
              6> Object type Operator   (typeid) 
              
              
```c++
Return_Type classname :: operator op(Argument list)
{
    Function Body
}

```
              
        
```c++
#include<iostream>
using namespace std;
   
class Complex {
private:
    int real, imag;
public:
    Complex(int r = 0, int i =0)  {real = r;   imag = i;}
       
    // This is automatically called when '+' is used with
    // between two Complex objects
    Complex operator + (Complex const &obj) {
         Complex res;
         res.real = real + obj.real;
         res.imag = imag + obj.imag;
         return res;
    }
    void print() { cout << real << " + i" << imag << endl; }
};
   
int main()
{
    Complex c1(10, 5), c2(2, 4);
    Complex c3 = c1 + c2; // An example call to "operator+"
    c3.print();
}

```
 ### Run Time Polymorphism

      A. Function Overriding
        Function overriding on the other hand occurs when a derived class has a definition for one of the member functions
        of the base class. That base function is said to be overridden.
        

```c++
#include <bits/stdc++.h>
using namespace std;
// function Overloading
class prac{
    public:
       virtual void print ()
    { cout<< "print parent class" <<endl; }

        void func(int x,int y){
            cout<<"Second Func "<< x+y<<endl;
        }

};

// inheritance

class prac2 : public prac{
    public:

     void print () //print () is already virtual function in derived class, we could also declared as virtual void print () explicitly
    { cout<< "print child class" <<endl; }

    void func(int x,int y){
            cout<<"Second Func  from child"<< x-y<<endl;
        }

};
int main() {
    prac2 p;

    p.print();
    p.func(5,25);

    
}

Output
print child class
Second Func  from child-20



