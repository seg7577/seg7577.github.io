---
title: 📜MAP 2022-09~2022-12
hide_date: true
reading_time: false
date: 2022-09-01
---

- A map is a data structure that stores data in key-value pairs. Each key is unique, which allows efficient searching, insertion, and deletion of values associated with those keys. Maps are available in many programming languages and are typically implemented using either hash tables or binary search trees.
    - The map container is structured as a balanced binary tree with nodes.
    - A map is composed of key-value pairs, stored as pair objects.
    - **Unique Key**: Each key is unique and cannot be duplicated. (If duplicate keys are needed, you can use a multimap instead).
    - **Ordered**: Maps are ordered containers, meaning elements are automatically sorted upon insertion (default is ascending order via `less`).
    
    ![Image14](/images/dataStructureImages/image14.jpg)
    
- **Usage**:
    - Basic declaration → `map<Data type1, Data type2> variable_name;`
        
        Example:
        ```cpp
        map<int, int> m1;
        map<string, int> m2;
        ```

    - `map<int> m(pred);` → You can specify a sorting predicate (ascending or descending order) through `pred`.

- **Main Member Functions**:
    - **Iterators**:
        - `begin()`: Returns an iterator to the beginning of the map.
        - `end()`: Returns an iterator to the end of the map.
        
    - **Insertions and Deletions**:
        - `insert(make_pair(key, value))`: Inserts a key-value pair into the map.
        - `erase(key)`: Removes the element associated with the given key.
        - `clear()`: Removes all elements from the map.
        
    - **Lookups**:
        - `find(key)`: Returns an iterator to the element with the given key.
        - `count(key)`: Returns the number of elements with the given key.
        
    - **Other**:
        - `empty()`: Returns `true` if the map is empty, otherwise `false`.
        - `size()`: Returns the number of elements in the map.

- **Basic Implementation Example**:

    ```cpp
    #include <iostream>
    #include <map>
    
    using namespace std;
    
    int main(void) {
        // Declare a map with int keys and string values
        map<int, string> m;
        m.insert(pair<int, string>(1, "one"));
        m.insert(pair<int, string>(2, "two"));
        m.insert(pair<int, string>(3, "three"));
        m.insert(pair<int, string>(4, "four"));
        
        // Iterate over the map and print each key-value pair
        map<int, string>::iterator iter;
        for (iter = m.begin(); iter != m.end(); iter++) {
            cout << (*iter).first << ", " << (*iter).second << endl;
        }
        
        // Declare another map with int keys and int values
        map<int, int> m2;
        m2[9] = 123;
        m2[3] = 532;
        m2[4] = 999;
        
        // Iterate over the second map and print each key-value pair
        map<int, int>::iterator iter2;
        for (iter2 = m2.begin(); iter2 != m2.end(); iter2++) {
            cout << iter2->first << ' ' << iter2->second << endl;
        }
    }
    // Output:
    // 1, one
    // 2, two
    // 3, three
    // 4, four
    // 3 532
    // 4 999
    // 9 123
    ```

