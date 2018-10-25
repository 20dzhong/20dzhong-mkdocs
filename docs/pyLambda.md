# Functional Programming in Python

## Lambdas: 
Lambda operators are used for small, quick, one-time anonymous function. The goal is to have a simple behavior passed into an object. Lambda in Python is different than Lambda in Java.

Python are used a lot in filtering, sorting and operation on arrays. 

Normal functions are created with the **def** keyword, anonymous functions are created with the **lambda** keyword.

Lambda Basic Syntax: ``lambda arguments : expression``

A Lambda can take any number of arguments but it can only have one expression, it can only be one line.

!!! note "Sorting even numbers with Lambda"
    
    ```python
    nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10] # an array of integers
        
    # passing the behavior to an object
    # lambda gets argument arg, if arg has a remainder of 2, it will stay
    x = lambda arg: arg % 2 == 0
    
    # sort the array with the behavior
    nums = list(filter(x, nums)) # filter expects a function and a list
    
    print(nums) # [2, 4, 6, 8, 10]
    ```

The short code above use *filter()* to filter through the list and take the even numbers using lambda

!!! note "Operations with Multiple Arguments"
    
    ```python
    addition = lambda x, y: x + y
    print(addition(1, 2))
    ```
    
The code above demonstrate a simple calculation with the use of lambda with multiple arguments

!!! note "Chaining Lambdas"
    
    ```python
    a = 1
    b = 3
    c = 9
    
    quadratic = lambda x: (a * x) ** 2 + (lambda b: b * x + c) (b)
    print(quadratic(2))
    ```
    
The code above demonstrate chaining lambda together, I don't see why anyone would do this, but just know this is a thing you can do
    
The code above demonstrate the use of multiple lambdas together

## So why Lambdas?

The power of lambda is better shown when using it as an anonymous function inside of another function, below is an example of how it is useful

!!! note "Lambda Example, to the powerOf()"

    ```python
    #powerOf requires a int to know the operation it will eventually perform
    def powerOf(n): 
        return lambda a: a ** n
    
    cube = powerOf(3) 
    print(cube(2))
    
    square = powerOf(2)
    print(square(2))
    ```

In the above, you can think of powerOf() as a skeleton method for the inner lambda function. **a** will multiply itself by **n** time, so ``a^n``, a to the ``n``th power
It's assigning the function pointer to **triple()** while passing in the argument **3** as **n**, and the lambda is invoked
when pass in an argument into **triple()**

This is very useful when you want different functions that are closely linked but have 1 or 2 different parameters.

## Other Applications

Lambda is used most in sorting, filtering, mapping, and operations on arrays, and here you will see why

### Maps:

Let's start with the **Map()** function, an extremely useful function that modifies elements in a list based on a behavior:

The basic syntax for map: ``map(function, list1, list2...)``
!!! note "function with map"

    ```python
    def double(x): # the function returns whatever 2*x is
        return 2 * x
    
    list1 = [1, 2, 3, 4, 5, 6, 7]
    
    # here, map will apply double to all elements in list1
    res = list(map(double, list1))
    # as seen above, you'll have to convert the mapped list to a list again
    # if you don't, res becomes a map object and you'll only print the memory address
    
    # output: [2, 4, 6, 8, 10, 12, 14]
    print(res)
    ```

As seen above, ``map(double, list1)`` uses the ``double`` behavior to modify every element in ``list1``

However, defining a function for this seems a little extra for such a simple process, this is where lambda comes in:

!!! note "lambda with map"

    ```python
    list1 = [1, 2, 3, 4, 5, 6, 7]
    res = list(map(lambda x: 2*x, list1))
    
    # output: [2, 4, 6, 8, 10, 12, 14]
    print(res)
    ```

This strip of code above does the exact same thing as the one with the functions, but with much simpler and cleaner syntax.


### Filters:

Filter expect the same thing as map, a behavior and an iterable, the basic syntax is ``filter(behavior, list)``

As the name suggest, ``filter()`` takes an existing list and create a new list based on whether the element passes the filter
or not, ``filter()`` ony returns element when the behavior return ``true``

!!! note "lambda with filter" 

    ```python
    list1 = range(-30, 30) # create a list from -50 to 50
    # take all number that is divisible by 5 using lambda
    res = list(filter(lambda x: x % 5 == 0, list1))
    
    # output: [-30, -25, -20, -15, -10, -5, 0, 5, 10, 15, 20, 25]
    print(res)
    ```
It's very useful for searching for objects inside a list or finding objects with specific qualities within a list as it's faster than a loop.

### Sort:

Before going into details, there are a couple of difference between `sorted` and `sort`:

* ``list1.sort()`` will change the content of `list1` and permanently change it
* ``list2 = sorted(list1)`` will return a new sorted list to `list2` but the content of `list1` is never altered

Sort functions can be very useful when integrated with lambda, especially when there is a need to sort by a certain index,
here's an example of using sort with lambda to sort the second element in a tuple:

!!! note "lambda with sort"

    ```python
    list1 = [1, 2, 3, 4, 5]
    list2 = [5, 4, 3, 2, 1]
    
    # zip basically takes multiple list and string
    # it strings them as tuple pairs/triplets depending on how many list you gave in
    list3 = list(zip(list1, list2))
    # list 3 = [(1, 5), (2, 4), (3, 3), (4, 2), (5, 1)]
    
    # sorting by numerical order of the second number
    res = sorted(list3, key=lambda x: x[1])
    print(res)
    ```
    
By gaining a good understanding of those topics, you'll never loose a single coding game

    