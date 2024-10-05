---
title: 📜Binary Search 2022-09~2022-12
hide_date: true
reading_time: false
date: 2022-09-01
---

- Binary Search is an algorithm that can only be used on sorted arrays. The array must be sorted in either ascending or descending order for binary search to work. Binary search works by checking the middle value of the array first, then comparing it to the target value. If the middle value is greater than the target, it continues searching in the left half; if smaller, it searches the right half. This process of halving the search range makes binary search very efficient in terms of time complexity.

- **Concept of `lower_bound`**: You can use the `<algorithm>` STL to apply `lower_bound`.
    - **Purpose**: It is used to find the index of the first occurrence of a number that is **equal to or greater than** the key in a sorted array or vector.
    - **Usage Condition**: The array or vector must be sorted in ascending order for `lower_bound` to work.
    - **Mechanism**: It traverses the array or vector, and returns the address of the first position where a number greater than or equal to the key is found.
        - To get the index of the first occurrence of the key, subtract the first address of the array or vector from the return value of `lower_bound`.
    - **Example Code**:
        ```cpp
        // Code using an array
        int main()
        {
            int arr[6] = { 1, 2, 3, 4, 5, 6 };
            cout << "lower_bound(6) : " << lower_bound(arr, arr + 6, 6) - arr;
            // Output: 5
        }

        // Code using a vector
        int main()
        {
            vector<int> arr = { 1, 2, 3, 4, 5, 6, 6, 6 };
            cout << "lower_bound(6) : " << lower_bound(arr.begin(), arr.end(), 6) - arr.begin();
            // Output: lower_bound(6) : 5

            return 0;
        }
        ```

- **Concept of `upper_bound`**: You can also use the `<algorithm>` STL to apply `upper_bound`.
    - **Purpose**: It is used to find the index of the first occurrence of a number that is **strictly greater** than the key in a sorted array or vector.
    - **Usage Condition**: The array or vector must be sorted in ascending order.
    - **Mechanism**: It traverses the array or vector, and returns the index where a number greater than the key first appears.
    - **Example Code**:
        ```cpp
        // Code using an array
        int main()
        {
            int arr[10] = { 1, 2, 3, 4, 6, 7, 8, 9, 10, 11 };
            cout << "upper_bound(6) : " << upper_bound(arr, arr + 6, 6) - arr;
            // Output: 5
        }

        // Code using a vector
        int main()
        {
            vector<int> arr = { 1, 3, 5, 5, 7, 8, 8, 10, 10, 11, 13 };
            cout << "Count of numbers between 5 and 11: " << upper_bound(arr.begin(), arr.end(), 11) - lower_bound(arr.begin(), arr.end(), 5);
            // Output: Count of numbers between 5 and 11: (depends on the input array)

            return 0;
        }
        ```
