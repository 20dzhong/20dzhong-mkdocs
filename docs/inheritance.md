# Inheritance

Inheritance is one of the main principles of object-oriented programming, inheritance allows one class to inherit 
features from another class.

When a subclass inherits from a superclass, the subclass can access public variables and functions from the super class 

## Inheritance Basics

* Java only allows one class to incorporate another class into its declaration through the **extend** keyword
* A class that is being inherited is called a *superclass* and the class that does the inheriting is a *subclass*

!!! note "Example through *class animal*"

    ```java
        // Animal is the superclass of Frog
        public class Animal {
            String name;
            String food;
            private int lifespan;
        
            void printInfo() {
                System.out.println(name + " has an average lifespan of " + lifespan  +
                        " and eats " + food + " as its primary food source. ");
        }
        
        // class Frog is a subclass of Animal
        class Frog extends Animal {
            String color;
            boolean poisonous;
        
            void isDangerous() {
                System.out.println("Frog is poisonous: " + poisonous);
            }
        }
        
        class test{
            public static void main(String args[]) {
                Frog dartFrog = new Frog();
        
                // object dartFrog has access to variables and functions within dangerous
                dartFrog.poisonous = true;
                dartFrog.color = "red";
                dartFrog.isDangerous();
        
                // object dartFrog also has access to variables and functions in Animal
                dartFrog.name = "okopipi";
                dartFrog.food = "ants";
        
                // dartFrog.livespan will not work because the access is private
                // dartFrog.livespan = "20";
            }
        }
    ```
In the above example, class *dartFrog* is a subclass of *Animal*, and have all the features of an Animal except for those
that were declared **private**

* class *Animal* has variables `name` and `food` and function `printInfo`, that means all classes that inherit from *Animals*
will have access `name`, `food`, and `printInfo`

However, class *Animal* does not have access to any features within *dartFrog*

Private variables and functions cannot be access from anywhere outside of its class, however, a controlled way of accessing
private members is to use an accessor method. 

!!! note "Member Access"

    ```java
        // Animal class
        public class Animal {
            String name;
            String food;
            private int lifespan = 15;
            
            // setLifespan is within the class Animal so it's able to access lifespan
            void setLifespan(int time) {
                 lifespan = time;
            }
        }
        
        class test{
            public static void main(String args[]) {
                Animal cheetah = new Animal();
        
                // and now, this line of code will work!
                // the function setLifespan() will be able to access the variable lifespan
                cheetah.setLifespan(10);
            }
        }
    ```


        
## The **super** keyword

### As Constructors:
A subclass can call a constructor by its superclass by using the keyword **super**

!!! note "Constructing using Super"

    ```java
        // superclass Shapes
        class Shapes {
            private double width;
            private double height;
        
            // Parameterized constructor for Shapes
            Shapes(double w, double h) {
                width = w;
                height = h;
            }
        
            // Accessor methods for width and height
            double getWidth() { return width; }
            double getHeight() { return height; }
        }
        
        // subclass triangle inherits from Shapes
        class Triangle extends Shapes {
            private String style;
        
            // constructor for Triangle
            Triangle(String s, double w, double h){
                super(w, h); // <- super calls on the constructor for Shapes and pass w, h into it
                style = s;
            }
            
            double area() {return (getWidth() * getHeight()) / 2.0;}
        }
    ```
Here, ``super(w,h)`` changes the width and height in the superclass from the subclass.

Any form of constructors defined by the superclass can be called by ``super()``. The constructor executed will be the one that matches the arguments, 
very useful for overloading. 

* For example ``super()`` will call on the default constructor with no parameters, ``super(w, h)`` will call on the constructor that has 
those two parameters, and so on. 

When a subclass calls ``super()`` it is calling the constructor of its immediate superclass, so this allows chaining constructors to be
possible. Also, ``super()`` must always be the first statement executed inside a subclass constructor.

### Access Superclass:

You can also use **super** to access members of the superclass  

* similar to the way **this** is being used, except it always refers to the immediate superclass of the subclass .

* This is especially helpful when a member name of a subclass hides the member by the same name in the superclass, although hiding
fields is discouraged.

!!! note "Using super to access Superclass"

    ```java 
        // using super to overcome name hiding
        class A {
            int i;
        }
        
        // subclass B inherits A
        class B extends A {
            int i; //local variable i hides i in superclass A
            
            // constructor
            B(int a, int b) {
                this.i = a; // i in subclass takes the value of a
                super.i = b; // i in superclass takes the value of b
            }
        }    
    ```
    
As shown above, ``i`` in ``B`` has the same name as ``i`` in ``A``, so the ``i`` in ``B`` will hide the ``i`` in ``A``
and in this case, you can use``super`` to access the hidden variable.

## Multilevel Hierarchy

A demonstration of all the stuff from above. You can build as many layers of inheritance as you like, it's not limited to
only 1 subclass and 1 superclass

!!! note "Hierarchy example"

    ```java
        // superclass Shapes
        class Shapes {
            private double width;
            private double height;
            
            // overloading constructors:
            // default constructor
            Shapes() {
                width = height = 0;
            }
        
            // Parameterized constructor for Shapes
            Shapes(double w, double h) {
                width = w;
                height = h;
            }
        
            // Accessor methods for width and height
            double getWidth() { return width; }
            double getHeight() { return height; }
        }
        
        // subclass triangle inherits from Shapes
        class Triangle extends Shapes {
            private String style;
        
            // default constructor
            Triangle() {
                super(); // calls the default constructor for Shapes
                style = "none";
            }
            
            // constructor for Triangle
            Triangle(String s, double w, double h){
                super(w, h); // <- super calls on the constructor for Shapes and pass w, h into it
                style = s;
            }
        
            double area() {return (getWidth() * getHeight()) / 2.0;}
        }
        
        class ColorTriangle extends Triangle {
            private String color;
            
            ColorTriangle(String c, String s, double w, double h) {
                super(s, w, h); 
                color = c; // <- only the color is unique to the class ColorTriangle,
            }
            
            String getColor() { return color; }
        }    
    ```
    
In the example above, ``ColoredTriangle`` inherits from ``Triangle`` which inherits from ``Shapes``

It's also useful to know that constructors are executed in order of derivation, it always starts from the *source* superclass
and find its way down since a superclass has no knowledge of any subclass. 

## Overriding methods

### Overriding example:
Exactly how it sounds, when a method in a subclass has the same return type and signature as a method in the superclass,
the subclass method will override the methods from the superclass, and the superclass version of the method will stay hidden.

!!! note "Overriding example"
    
    ```java
    class A {
        int foo, bar;
        A(int a, int b){
            foo = a;
            bar = b;
        }
    
        //display foo and bar
        void show(){
            System.out.println(String.format("foo is: %s\n bar is: %s", foo, bar));
        }
    }
    
    class B extends A {
        int fizz;
    
        B(int a, int b, int c) {
            super(a, b);
            fizz = c;
        }
    
        @Override // denotes that something is being overidden
        // displays the overridden print statement
        void show() {
            System.out.println(String.format("fizz is %s, show method has been overridden", fizz));
        }
    }
    ```

When ``show()`` is called on a **B** object, it will use **B**'s version of the ``show()`` method, because it overrides
**A**'s ``show()`` method. If you want to access the superclass version of ``show()``, you can simply do ``super.show()``.

Overriding only happens when the name and parameter of two methods are identical, if they're not, it simply becomes overloaded.

Override is usually denoted by using ``@Override`` 


## Abstract Classes


In some cases, you would want a super class that defines only a generalized form of its subclass, that is when you would use a abstract class, think of it as a skeleton structure for a subclass.

Abstract Classes are classes that contains abstract functions, and when a subclass inherits an abstract class, it must implement ALL of the abstract methods
unless it itself is an abstract class, subclasses will continue to be abstract until all abstract methods are implemented. 
   
Take in consideration the Shape class, Shape class has an area() function, but every different shape has a different area formula. In this case, the abstract method
states that there must be a area() functions for every subclass that inherits from the class shape

!!! note "Abstract Method in an Abstract Class"

    ```java
    // unlike interfaces, abstract class can contain abstract methods and  implemented methods
    abstract class Shape {
        double width;
        double height;
        String name;
    
        Shape(double width, double height, String name) {
            this.width = width;
            this.height = height;
            this.name = name;
        }
    
        // abstract method area
        abstract double area();
    }
    
    
    class Triangle extends Shape {
        Triangle(double width, double height, String name) {
            super(width, height, name);
        }
    
        @Override
        double area() {
            return 0.5 * width * height;
        }
    }
    
    
    class Rectangle extends Shape {
        Rectangle(double width, double height, String name) {
            super(width, height, name);
        }
    
        @Override
        double area() {
            return width * height;
        }
    }
    
    
    class Square extends Rectangle {
        Square(double side, String name) {
            super(side, side, name);
        }
    
        @Override
        final double area() {
            return width * width;
        }
    }
    ```
