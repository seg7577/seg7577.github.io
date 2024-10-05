---
title: 📜UNORDERED MAP 2022-09~2022-12
hide_date: true
reading_time: false
date: 2022-09-01
---

- **Concept**
    - `unordered_map` is a type of data structure designed for faster search operations compared to a regular map.
    - `unordered_map` is implemented using a **hash table**, and its average time complexity for operations is **O(1)**.
    - In contrast, a regular `map` is implemented as a **Binary Search Tree** (BST) with a time complexity of **O(log N)**.
    - `unordered_map` does not allow duplicate keys and performs better than a regular map when handling large data sets, thanks to hash-based collision management.
  
- **Member Functions**
    - `empty()`
        - Checks if the map is empty. Returns `1` if it is empty, otherwise returns `0`.
    - `size()`
        - Returns the size of the map.
    - `operator []`
        - Assigns a value to a key in the map.
        - Usage: `map_name[key] = value`
    - `find(key)`
        - Finds the element with the specified key in the map. Returns an iterator to the element if found.
    - `count(key)`
        - Returns the number of elements with the specified key (either `0` or `1` for `unordered_map`).
    - `insert({key, value})`
        - Inserts a key-value pair into the map.
    - `erase(key)`
        - Removes the element with the specified key from the map.
    - `clear()`
        - Clears all elements from the map.
    - `operator=`
        - Assignment operator for copying or assigning one `unordered_map` to another.

- **Example Code**

    ```cpp
    #include <iostream>
    #include <string>
    #include <unordered_map>
    
    using namespace std;
    
    int main(){
        
        unordered_map<string,int> um;
        
        // Check if the map is empty
        if(um.empty()){
            cout << "The unordered_map is empty" << endl;
        }
        
        // Insert elements into the unordered_map
        um.insert(make_pair("key", 1));
        um["banana"] = 2;
        um.insert({"melon", 3});
        
        // Output the size of the unordered_map
        cout << "The size of the unordered_map is: " << um.size() << endl;
        
        // Loop through the unordered_map and print its elements
        for(pair<string, int> elem : um){
            cout << "Key: " << elem.first << " Value: " << elem.second << endl;
        }
        
        // Find and erase an element
        if(um.find("banana") != um.end()){
            um.erase("banana");
        }
        
        // Output the size of the unordered_map after deletion
        cout << "The size of the unordered_map after erasing 'banana' is: " << um.size() << endl;
        
        // Print the remaining elements
        for(auto elem : um){
            cout << "Key: " << elem.first << " Value: " << elem.second << endl;
        }
        
        return 0;
    }
    ```
