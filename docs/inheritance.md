# Inheritance

* Inheritance is one of the main principles of object-oriented programming

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
            System.out.println(name + " has an average lifespan of " + livespan + " and eats " + food + " as its primary food source. ");
        }
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

## ROS on Ubuntu

Installation instructions are [here](http://wiki.ros.org/kinetic/Installation/Ubuntu)

Install *ros-kinetic-desktop* in order to get rospy_tutorials.

!!! note "After installing *ros-kinetic-desktop* initialize `rosdep`"

    ```bash
    sudo rosdep init
    rosdep update
    ```

!!! note "Install dependencies for building packages"

    ```bash
    sudo apt-get install python-rosinstall python-rosinstall-generator python-wstool build-essential
    ```

## ROS on Raspi

Use Ubuntu MATE, not Raspbian.

Download Ubuntu MATE 16.04.2 from [here](https://ubuntu-mate.org/download/)

## ROS on Jetson TX2

!!! warning "If `sudo rosdep init` returns an error about a website being down"

    ```bash
    sudo c_rehash /etc/ss/certs
    ```
 
## ROS on Docker

!!! info "Run *roscore*"

    ```bash
    docker run -it --rm  -p11311:11311  ros roscore
    ```




