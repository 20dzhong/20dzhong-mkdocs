# Extra Notes

## Static Blocks and Initializer Blocks

There are two types of initializer blocks in Java, the Static initializer block and the instance initializer block.

Instance initializer blocks are useful when you want a piece of code to execute regardless of which constructor is called, or if you want 
something to run before the constructor

* Instance initialization blocks are called every time an instance of the class is constructed

* Instance initialization blocks can be used to initialize anonymous inner classes
 
Static initializer blocks can be used to initialize static variables when a classes is loaded

* Static initializer blocks are only called once, when the class itself is initialized

!!! note "execution order"
    
    ```java
    class fizzbuzz {
    
            // initializer block
            { System.out.println("block called"); }
        
            // static block
            static { System.out.println("static block called"); }
        
            // constrctor block
            fizzbuzz() {
                System.out.println("constructor called");
            }
        }
        
        public class foobar {
            public static void main(String args[]) {
                fizzbuzz f = new fizzbuzz();
                fizzbuzz s = new fizzbuzz();
        
            }
        }
    ```
    
The output would be:  
    ```
    static block called
    block called
    constructor called
    block called
    constructor called
    ```

As you can see, the static block always gets called first, and it only get called once when the class is loaded. The initializer blocks gets called
second, and  the constructor last




## Nested classes, will add doc later
```java

class LinkedList {

    // static init block
    static { System.out.println("linked list initialized"); }

    private Node head;
    LinkedList(int val) { this.head = new Node(val); }

    // perform factorial operation on head
    public void headFactorial() {
        class Opertaions {
            private int factorial(int n) {
                return ((n == 1) ? 1 : factorial(n - 1) * n);
            }
        }
        Opertaions opt = new Opertaions();
        this.head.val = opt.factorial(head.val);

    }

    // getter method
    class Getter {
        // get head
        int head() { return head.val; }
    }

    // node class
    class Node {
        int val;
        Node next;

        Node(int val) {
            this.val = val;
            this.next = null;
        }
    }
}

class ree {
    public static void main(String args[]) {
        LinkedList ree = new LinkedList(9);
        LinkedList.Node head = ree.new Node(10);
        LinkedList.Getter get = ree.new Getter();
        int headVal = get.head();
        System.out.println(headVal);
    }

}


```