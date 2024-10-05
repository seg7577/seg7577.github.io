---
title: 📜GRAPH 2022-09~2022-12
hide_date: true
reading_time: false
date: 2022-09-01
---

- A Graph is a data structure consisting of vertices (nodes) and edges that represent relationships or connections between entities. Graphs are widely used in real-world applications such as networks, social media, web page links, road maps, and many others.

- **Components of a Graph**:
    - **Vertex (Node)**: Represents an entity in the graph. Vertices can represent people, cities, web pages, or any other entity.
    - **Edge**: Represents the connection between two vertices. Edges define the relationship between vertices and can be either directed or undirected.

- **Types of Graphs**: Graphs can be categorized based on directionality, weights, and cycles.
    - **Undirected Graph**: A graph where edges have no direction, meaning if there is an edge between A and B, it can be traversed in both directions.
    - **Directed Graph**: A graph where edges have a specific direction, meaning an edge from A to B can only be traversed from A to B, not the other way around.
    - **Weighted Graph**: A graph where edges have weights or costs associated with them. This could represent distances, costs, or other metrics between nodes.
    - **Cyclic and Acyclic Graphs**:
        - **Cyclic Graph**: A graph where at least one cycle exists, meaning there is a path that begins and ends at the same vertex.
        - **Acyclic Graph**: A graph without cycles, such as a tree.
    
- **Graph Representation**: Graphs can be represented in two main ways:
    - **Adjacency Matrix**: A 2D array where each cell (i, j) represents the existence of an edge between vertex i and vertex j. A value of 1 means there is an edge, and a value of 0 means there is no edge.
    
    - **Example Code**:

        ```cpp
        // Directed Graph using an Adjacency Matrix
        #include<iostream>
        #include<bits/stdc++.h>

        using namespace std;

        int main() {
            int nodes, edges; // number of vertices and edges
            int adj_matrix[100][100];
            cin >> nodes >> edges;

            for (int i = 0; i < edges; i++) {
                int u, v;
                cin >> u >> v;
                adj_matrix[u][v] = 1;  // edge from u to v
            }
        }
        ```

        ```cpp
        // Undirected Graph using an Adjacency Matrix
        #include<iostream>
        #include<bits/stdc++.h>

        using namespace std;

        int main() {
            int nodes, edges; // number of vertices and edges
            int adj_matrix[100][100];
            cin >> nodes >> edges;

            for (int i = 0; i < edges; i++) {
                int u, v;
                cin >> u >> v;
                adj_matrix[u][v] = 1;  // edge from u to v
                adj_matrix[v][u] = 1;  // edge from v to u (undirected)
            }
        }
        ```

    - **Adjacency List**:
    
        ```cpp
        // Undirected Graph using an Adjacency List
        #include<iostream>
        #include<bits/stdc++.h>
        #include<vector>

        using namespace std;

        int main() {
            int nodes, edges; // number of vertices and edges
            vector<int> adj_list[100];
            cin >> nodes >> edges;

            for (int i = 0; i < edges; i++) {
                int u, v;
                cin >> u >> v;
                adj_list[u].push_back(v);
                adj_list[v].push_back(u);  // undirected graph
            }
        }
        ```

        ```cpp
        // Directed Graph using an Adjacency List
        #include<iostream>
        #include<bits/stdc++.h>
        #include<vector>

        using namespace std;

        int main() {
            int nodes, edges; // number of vertices and edges
            vector<int> adj_list[100];
            cin >> nodes >> edges;

            for (int i = 0; i < edges; i++) {
                int u, v;
                cin >> u >> v;
                adj_list[u].push_back(v);  // directed graph
            }
        }
        ```

    - **Example Problems**:

        ```cpp
        // BOJ-11724: Number of Connected Components
        #include <iostream>
        #include <bits/stdc++.h>
        #include <vector>
        #include <queue>

        using namespace std;

        bool visited[100005];

        int main() {
            int count = 0;
            int n, m; // number of vertices and edges
            int u, v; // vertices

            vector<int> adj[100005];
            queue<int> Q;

            cin >> n >> m;

            for (int i = 0; i < m; i++) {
                cin >> u >> v;
                adj[u].push_back(v);
                adj[v].push_back(u);  // undirected graph
            }

            for (int i = 1; i <= n; i++) {
                if (visited[i]) {
                    count++;
                    continue;
                }

                Q.push(i);
                visited[i] = true;

                while (!Q.empty()) {
                    int current = Q.front();
                    Q.pop();

                    for (int next : adj[current]) {
                        if (visited[next]) continue;
                        Q.push(next);
                        visited[next] = true;
                    }
                }
            }
            cout << n - count;
            return 0;
        }
        ```

        ```cpp
        // BFS traversal in an undirected graph
        #include <iostream>
        #include <bits/stdc++.h>
        #include <vector>
        #include <queue>

        using namespace std;

        int main() {
            vector<int> adj[10];
            bool visited[10];
            queue<int> Q;

            Q.push(1);  // start from vertex 1
            visited[1] = true;

            while (!Q.empty()) {
                int current = Q.front();
                Q.pop();

                cout << current << ' ';

                for (int next : adj[current]) {
                    if (visited[next]) continue;
                    Q.push(next);
                    visited[next] = true;
                }
            }
        }
        ```

        ```cpp
        // BOJ-2606: Virus Problem
        #include <iostream>
        #include <vector>
        #include <queue>

        using namespace std;

        bool visited[1005];

        int main() {
            int n;  // number of computers
            int u, v, edges;
            int infected_count = 0;

            cin >> n >> edges;

            vector<int> adj[105];
            queue<int> Q;

            for (int i = 0; i < edges; i++) {
                cin >> u >> v;
                adj[u].push_back(v);
                adj[v].push_back(u);  // undirected graph
            }

            Q.push(1);  // start from computer 1
            visited[1] = true;

            while (!Q.empty()) {
                int current = Q.front();
                Q.pop();

                for (int next : adj[current]) {
                    if (visited[next]) continue;
                    Q.push(next);
                    visited[next] = true;
                }
            }

            for (int i = 1; i <= n; i++) {
                if (!visited[i]) infected_count++;
            }
            cout << n - infected_count - 1;
            return 0;
        }
        ```

        ```cpp
        // BOJ-5567: Wedding Invitations Problem
        #include <iostream>
        #include <vector>
        #include <queue>

        using namespace std;

        bool visited[10005];

        int main() {
            int n, m;  // number of friends, number of connections
            int a, b;  // pairs of friends
            int direct_friends = 0, total_invited = 0;

            cin >> n >> m;

            vector<int> adj[505];
            queue<int> Q;

            for (int i = 0; i < m; i++) {
                cin >> a >> b;
                adj[a].push_back(b);
                adj[b].push_back(a);  // undirected graph
            }

            Q.push(1);  // start from Sang-keun
            visited[1] = true;

            while (!Q.empty()) {
                int current = Q.front();
                Q.pop();

                if (current == 1) {
                    for (int next : adj[current]) {
                        if (visited[next]) continue;
                        Q.push(next);
                        visited[next] = true;
                        direct_friends++;
                        total_invited++;
                    }
                } else if (direct_friends != 0) {
                    for (int next : adj[current]) {
                        if (visited[next]) continue;
                        visited[next] = true;
                        total_invited++;
                    }
                    direct_friends--;
                }
            }
            cout << total_invited;
            return 0;
        }
        ```

