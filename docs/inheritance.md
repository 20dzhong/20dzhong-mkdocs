# Inheritance

Inheritance is one of the main principles of object-oriented programming, inheritance allows one class to inherit 
features from another class.

When a subclass inherits from a superclass, the subclass can access public variables and functions from the super class 

## Inheritance Basics

* Java only allows one class to incorporate another class into its declaration through the **extend** keyword
* A class that is being inherited is called a *superclass* and the class that does the inheriting is a *subclass*

!!! note "Example through *class animal*"

    ```java
        // animal is the superclass of frog
        public class animal {
            String name;
            String food;
            private String livespan;
        
            void printInfo() {
                System.out.println(name + " has an average lifespan of " + livespan  +
                        " and eats " + food + " as its primary food source. ");
        }
        
        // class frog is a subclass of animal
        class frog extends animal {
            String color;
            boolean isPoisonous;
        
            void isdangerous() {
                System.out.println("frog is poisonous: " + isPoisonous);
            }
        }
        
        class test{
            public static void main(String args[]) {
                frog dartFrog = new frog();
        
                // object dartFrog has access to variables and functions within dangerous
                dartFrog.isPoisonous = true;
                dartFrog.color = "red";
                dartFrog.isdangerous();
        
                // object dartFrog also has access to variables and functions in animal
                dartFrog.name = "okopipi";
                dartFrog.food = "ants";
        
                // dartFrog.livespan will not work because the access is private
                // dartFrog.livespan = "20";
            }
        }
    ```
In the above example, class *dartFrog* is a subclass of *animal*, and have all the features of an animal except for those
that were declared **private**

However, class *animal* does not have access to any features within *dartFrog*

## The **super** keyword

## Overriding methods

## Abstract Classes

## The **final** keyword 

