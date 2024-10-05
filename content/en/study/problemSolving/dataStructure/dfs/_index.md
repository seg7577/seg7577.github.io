---
title: 📜Depth-First Search (DFS) 2022-09~2022-12
hide_date: true
reading_time: false
date: 2022-09-01
---

- DFS (Depth First Search) is an algorithm used for searching all the vertices of a graph or tree by going deep into the graph. It explores as far as possible along a branch before backtracking to explore other branches. It starts at a given node, then visits an adjacent unvisited node, and repeats the process until no unvisited adjacent nodes are found. It then backtracks to previous nodes to continue the search for unvisited nodes. This continues until all nodes are visited.

    - **How DFS works**: DFS uses a stack data structure to track the nodes to be explored. It can also be implemented using recursion, where the call stack simulates the stack data structure. DFS visits one path deeply until it can’t continue, then backtracks to explore another path.

    - **DFS Characteristics**:
        - **Time Complexity**: O(V + E), where V is the number of vertices and E is the number of edges.
        - **Space Complexity**: O(V), where an array is required to track visited nodes.
        - **Order of Exploration**: DFS prioritizes depth, visiting the deepest unvisited nodes first before backtracking.

    - **Applications of DFS**:
        - **Pathfinding**: Checking if there is a path from a source to a destination.
        - **Cycle Detection**: DFS can help detect cycles in a graph.
        - **Connected Components**: It can help explore all the connected components of a graph.
        - **Maze Solving**: DFS is used in puzzles like mazes to explore all possible paths.
        - **Strongly Connected Components**: In directed graphs, DFS is useful for finding SCCs.

    - **Example Code**:
        ```cpp
        // DFS Implementation

        #include <bits/stdc++.h>
        #include <iostream>
        #include <stack>

        using namespace std;

        #define X first
        #define Y second

        // Sample board: 1 represents a path, 0 represents a wall.
        int board[502][502] = {
            {1, 1, 1, 0, 1, 0, 0, 0, 0, 0},
            {1, 0, 0, 0, 1, 0, 0, 0, 0, 0},
            {1, 1, 1, 0, 1, 0, 0, 0, 0, 0},
            {1, 1, 0, 0, 1, 0, 0, 0, 0, 0},
            {0, 1, 0, 0, 0, 0, 0, 0, 0, 0},
            {0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
            {0, 0, 0, 0, 0, 0, 0, 0, 0, 0}
        };

        bool vis[502][502];  // To track visited cells

        int n = 7, m = 10;  // n: number of rows, m: number of columns

        // Direction vectors for moving up, right, down, left
        int dx[4] = {1, 0, -1, 0};
        int dy[4] = {0, 1, 0, -1};

        int main(void) {
            ios::sync_with_stdio(0);
            cin.tie(0);
            cout.tie(0);

            stack<pair<int, int>> S;
            vis[0][0] = 1;  // Mark starting point (0, 0) as visited
            S.push({0, 0});  // Push starting point onto the stack

            while (!S.empty()) {
                pair<int, int> cur = S.top();  // Get the current top of the stack
                S.pop();  // Pop it off the stack after retrieving
                cout << '(' << cur.X << ", " << cur.Y << ") -> ";

                // Explore all 4 directions (up, right, down, left)
                for (int dir = 0; dir < 4; dir++) {
                    int nx = cur.X + dx[dir];
                    int ny = cur.Y + dy[dir];

                    // Skip if out of bounds
                    if (nx < 0 || nx >= n || ny < 0 || ny >= m) continue;

                    // Skip if the cell has already been visited or is a wall
                    if (vis[nx][ny] || board[nx][ny] != 1) continue;

                    vis[nx][ny] = 1;  // Mark the cell as visited
                    S.push({nx, ny});  // Push the new cell onto the stack
                }
            }
        }
        ```

- **Handling Memory in Large Test Cases**:
    - When the input size increases (e.g., from 600 to 700), the program may stop compiling due to memory limitations. Monitoring the memory usage shows that it stops at around 6MB. After a few seconds, it crashes with a `EXC_BAD_ACCESS` error, indicating a stack overflow.
        
        ```xml
        Thread 1: EXC_BAD_ACCESS (code=2, address=0x16f603ff8)
        ```

    - **Memory Exceeded**: Stack overflow occurs when too many recursive calls are made. This is common in recursive DFS implementations. Even if you use dynamic memory (heap), overusing it can lead to failure.

    - **Available Memory**: Systems typically allow 1MB to 8MB of stack memory.

        ```xml
        ulimit -s
        ```

    - **Key Memory Impact**:
        - **DFS Recursive Calls**: Each function call adds to the stack memory usage. For example, at n = 700, the stack might use 16 bytes per call * 490,000 calls (worst case) = 7.58MB.
        - **Local Variables**: Each recursive call has local variables, adding more to the stack.

    - **Solutions**:
        1. **Convert Recursion to Iteration**: Using a stack data structure in a loop reduces stack memory usage.
        2. **Increase Stack Size**: Adjust system settings to increase the available stack memory (e.g., linker settings in IDE or terminal settings).

- **Test Case Generation**:
    - Initially, I wasn’t concerned with time complexity, space complexity, or input size. However, when n = 1000 or n = 10,000, I realized stack overflow was a potential issue with recursive DFS. I planned to use file uploads for larger input sizes but opted for a more direct solution.
    - Recursive DFS may encounter stack overflow due to frequent function calls.

    - **Memory Calculation (Theoretical Memory)**:
        ---
        **For n = 1000**:
        - **Recursive Stack Memory**: {16 bytes * 1,000,000 (function calls in worst case)} * {4 bytes * 4 * 1,000,000 (function parameters, local variables)} = 32MB.
        - **Iterative Stack Memory**: {(4 bytes + 4 bytes) * 1,000,000} = 8MB.
        - **Dynamic Memory** (for `board` and `vis`): 1000 * 1000 * 4 bytes = 4MB, and 1000 * 1000 * 1 byte = 1MB → Total 5MB.

        ---
        **For n = 10,000**:
        - **Recursive Stack Memory**: {16 bytes * 10,000,000 (function calls in worst case)} * {4 bytes * 4 * 10,000,000 (function parameters, local variables)} = 3.2GB.
        - **Iterative Stack Memory**: {(4 bytes + 4 bytes) * 10,000,000} = 800MB.
        - **Dynamic Memory**: 10,000 * 10,000 * 4 bytes = 400MB, and 10,000 * 10,000 * 1 byte = 100MB → Total 500MB.
        
        ---

        **Stack Overflow Solutions**:
        1. Use dynamic memory for `board` and `vis` with vectors instead of arrays.
        2. Convert the recursive DFS to an iterative DFS using the stack data structure to avoid excessive recursion.
