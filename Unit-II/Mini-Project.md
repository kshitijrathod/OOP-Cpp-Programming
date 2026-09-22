# Unit II Mini-Project

Banking System with Account Hierarchy
Create a base Account class and derived classes SavingsAccount, CurrentAccount, and
FixedDepositAccount. Include account number, holder name, balance, deposit, withdrawal, and
interest-calculation features. Use virtual functions for account-specific behavior.



Unit III: Polymorphism
Syllabus Coverage
 •   Introduction to polymorphism
 •   Types of polymorphism
 •   Operator overloading
 •   Unary and binary operator overloading
 •   Function overloading
 •   Run-time polymorphism
 •   Base-class pointers
 •   Virtual functions
 •   Pure virtual functions and virtual tables
 •   Virtual destructors
 •   Abstract base classes
Industry Relevance
Polymorphism enables extensible systems. It is valuable in graphics engines, user-interface
frameworks, configurable payment systems, document processors, simulation systems, media
applications, and plug-in architectures. Function and operator overloading make APIs clearer
when used consistently and without surprising behavior.
Real-Time Application 1: CAD Shape Drawing System
Problem Scenario
A computer-aided design application handles circles, rectangles, and triangles. Each shape is
drawn and its area is calculated through a common base-class interface.
OOP Concepts Used
 •   Abstract base class
 •   Pure virtual functions
 •   Runtime polymorphism
 •   Vector of smart pointers
 •   Virtual destructor



Live Example
#include <iostream>
#include <memory>
#include <vector>
using namespace std;


class Shape {
public:
     virtual double area() const = 0;
     virtual void draw() const = 0;
     virtual ~Shape() = default;
};


class Circle : public Shape {
private:
     double radius;


public:
     explicit Circle(double r) : radius(r) {}


     double area() const override {
         return 3.14159265359 * radius * radius;
     }


     void draw() const override {
         cout << "Drawing circle with radius " << radius << endl;
     }
};


class Rectangle : public Shape {
private:



     double length;
     double width;


public:
     Rectangle(double l, double w) : length(l), width(w) {}


     double area() const override {
         return length * width;
     }


     void draw() const override {
         cout << "Drawing rectangle " << length << " x " << width << endl;
     }
};


class Triangle : public Shape {
private:
     double base;
     double height;


public:
     Triangle(double b, double h) : base(b), height(h) {}


     double area() const override {
         return 0.5 * base * height;
     }


     void draw() const override {
         cout << "Drawing triangle with base " << base
            << " and height " << height << endl;
     }



};


int main() {
     vector<unique_ptr<Shape>> shapes;
     shapes.push_back(make_unique<Circle>(5.0));
     shapes.push_back(make_unique<Rectangle>(4.0, 6.0));
     shapes.push_back(make_unique<Triangle>(3.0, 8.0));


     cout << "=== CAD Shape System ===" << endl;
     for (const auto& shape : shapes) {
         shape->draw();
         cout << "Area: " << shape->area() << " square units" << endl;
     }
}


Real-Time Application 2: Complex Number Calculator
Problem Scenario
Engineering, signal processing, and simulation applications use complex numbers. Operator
overloading allows arithmetic expressions to be written naturally.
OOP Concepts Used
    •    Binary operator overloading
    •    Constructor with default arguments
    •    Constant member functions
    •    Encapsulation
Live Example
#include <iostream>
using namespace std;


class Complex {
private:



     double real;
     double imag;


public:
     Complex(double r = 0.0, double i = 0.0) : real(r), imag(i) {}


     Complex operator+(const Complex& other) const {
         return Complex(real + other.real, imag + other.imag);
     }


     Complex operator-(const Complex& other) const {
         return Complex(real - other.real, imag - other.imag);
     }


     Complex operator*(const Complex& other) const {
         return Complex(
              real * other.real - imag * other.imag,
              real * other.imag + imag * other.real
         );
     }


     bool operator==(const Complex& other) const {
         return real == other.real && imag == other.imag;
     }


     void display() const {
         cout << real << " + " << imag << "i" << endl;
     }
};


int main() {



    Complex c1(3.0, 4.0);
    Complex c2(1.0, 2.0);


    cout << "C1: ";
    c1.display();
    cout << "C2: ";
    c2.display();


    cout << "Sum: ";
    (c1 + c2).display();


    cout << "Difference: ";
    (c1 - c2).display();


    cout << "Product: ";
    (c1 * c2).display();
}


Real-Time Application 3: Input Validation Service
Problem Scenario
A business application validates different kinds of user data, including marks, names, and payment
amounts. Function overloading offers a common, readable validate() interface.
OOP Concepts Used
    •   Function overloading
    •   Compile-time polymorphism
    •   String processing
    •   Input validation
Live Example
#include <cctype>
#include <iostream>



#include <string>
using namespace std;


class Validator {
public:
     bool validate(int marks) const {
         return marks >= 0 && marks <= 100;
     }


     bool validate(double amount) const {
         return amount > 0.0 && amount <= 1000000.0;
     }


     bool validate(const string& name) const {
         if (name.empty()) {
             return false;
         }


         for (char ch : name) {
             if (!isalpha(static_cast<unsigned char>(ch)) && ch != ' ') {
                 return false;
             }
         }
         return true;
     }
};


int main() {
     Validator validator;


     cout << boolalpha;



    cout << "Marks 88 valid: " << validator.validate(88) << endl;
    cout << "Marks 120 valid: " << validator.validate(120) << endl;
    cout << "Amount 4500.50 valid: " << validator.validate(4500.50) << endl;
    cout << "Name Priya Sharma valid: "
       << validator.validate(string("Priya Sharma")) << endl;
    cout << "Name Priya123 valid: "
       << validator.validate(string("Priya123")) << endl;
}


Unit III Mini-Project
Media Player with Polymorphic Controls
Create a base class Media with derived classes Audio, Video, and Image. Provide operations such
as play(), pause(), stop(), and showDetails(). Manage media items using a collection of base-class
pointers.
