Java Map API

# Hashing
not finished

## Hashsets:

Hashsets implement Sets interface
!!! note "HashSet Examples"

    ```java
    // Create a HashSet
    HashSet<String> hset = new HashSet<>();

    //add elements to HashSet
    hset.add("AA");
    hset.add("BB");

    // clone hashset
    HashSet<String> hset2 = (HashSet) hset.clone();

    // return true or false
    hset.contains("AA"); // output: true

    // check is empty
    hset.isEmpty(); output: false

    // create object of iterator class
    Iterator value = hset.iterator();
    if(value.hasNext()) System.out.println(true);

    // remove a value, return true if removed, else false
    hset.remove("CC");  

    // return a integer representing size
    hset.size();

    // clears the set
    hset.clear();
    ```

## Hashmap
Hashmap implements Map interface 

!!! note "Hashmap"

    ```java
    // create hashmap
    HashMap<String, Integer> hmap = new HashMap<>();

    // put index and values
    hmap.put("age", 17);
    hmap.put("grade", 11);

    // size
    hmap.size(); // output: 2

    // clone the hashmap
    HashMap<String, Integer> hmap2 = (HashMap) hmap.clone();

    // if the hashmap contains the index, return true, return false otherwise
    hmap.containsKey("age"); // output: true

    // return true if contains value, false otherwise;
    hmap.containsValue(11); // output: true

    // get value
    hmap.get("age"); // output: 17

    // check if empty
    hmap.isEmpty(); // output: false

    // return a set view of keys
    hmap.keySet(); // output: [age, grade]

    // returns collection of all values
    hmap.values(); // output: [17, 11]
    
    // put all values
    hmap2.putAll(hmap);

    // removes key and value
    hmap.remove("age");
    
    // clear
    hmap.clear();
    ```
