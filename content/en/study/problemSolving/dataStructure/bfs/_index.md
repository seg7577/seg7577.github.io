---
title: 📜Breadth-First Search 2022-09~2022-12
hide_date: true
reading_time: false
date: 2022-09-01
---

- BFS (Breadth-First Search) is a graph traversal algorithm that explores all nodes at the present depth level before moving on to nodes at the next depth level. It starts from the root node and explores all its neighbors before moving to the next level. BFS typically uses a **queue** data structure to implement this process.
  - Working Principle: Insert the starting node into the queue and repeat the following steps until there are no more nodes to explore. Dequeue a node and enqueue all its neighboring nodes that haven’t been visited yet. Repeat this process, and nodes are explored in increasing order of distance from the root.
  - Characteristics: BFS is ideal for finding the **shortest path**. Since BFS explores all nodes at the current depth before moving deeper, it guarantees the shortest path in an unweighted graph. It's also useful for exploring all nodes in a graph.
  - Time Complexity: The time complexity of BFS is **O(V + E)**, where V is the number of vertices and E is the number of edges. BFS traverses all adjacent nodes and completes the search depending on the structure of the graph.
  - BFS Implementation: BFS is implemented using a queue data structure. The algorithm enqueues the starting node and continues dequeuing nodes while enqueuing their unvisited adjacent nodes. A visited array is used to track which nodes have been explored to prevent revisiting nodes.
  - Example of BFS: Consider the following graph:
    ```
    1 -- 2 -- 5
    |    |
    3 -- 4
    ```
    Starting BFS from node 1, the exploration order will be: 1 -> 2 -> 3 -> 5 -> 4. First, node 1 is added to the queue, and its neighbors, 2 and 3, are enqueued. Then node 2 is dequeued, and its neighbor 5 is enqueued. The process continues similarly for nodes 3 and 4.
  - Applications of BFS: 
    - **Shortest Path Search**: BFS is useful for finding the shortest path in problems such as maze solving. When all edge weights are the same, BFS can quickly find the shortest path.
    - **Network Exploration**: BFS can be used to explore all nodes in a graph efficiently.

### Example Code
- BFS Basic Concept
	```cpp
		#include <bits/stdc++.h>
		#include <iostream>
		#include <queue>

		#define X first
		#define Y second

		using namespace std;

		int board[502][502] = {};
		bool vis[502][502];  // Visited array to track visited nodes
		int n = 7, m = 10;   // Rows and columns
		int dx[4] = { 1, 0, -1, 0 };
		int dy[4] = { 0, 1, 0, -1 };

		int main()
		{
			ios::sync_with_stdio(0);
			cin.tie(0);

			queue<pair<int, int>> Q;
			vis[0][0] = 1;  // Mark the starting point as visited
			Q.push({0, 0}); // Enqueue the starting point

			while (!Q.empty())
			{
				pair<int, int> cur = Q.front();
				Q.pop();
				cout << '(' << cur.X << ", " << cur.Y << ") -> ";

				for (int dir = 0; dir < 4; dir++)
				{
					int nx = cur.X + dx[dir];
					int ny = cur.Y + dy[dir];

					if (nx < 0 || nx >= n || ny < 0 || ny >= m) continue; // Check if out of bounds
					if (vis[nx][ny] || board[nx][ny] != 1) continue; // Skip visited or invalid nodes

					vis[nx][ny] = 1;  // Mark as visited
					Q.push({nx, ny}); // Enqueue valid neighbors
				}
			}
		}
	```
- Problems

	```cpp
		//BOJ-2178 Maze Exploration
		#include <iostream>
		#include <queue>
		#include <string>
		#include <algorithm>
		#include <bits/stdc++.h>
		#define X first
		#define Y second

		using namespace std;

		string str_board[105];
		int board[105][105];
		int vis[105][105];
		int dx[4] = { 1, 0, -1, 0 };
		int dy[4] = { 0, 1, 0, -1 };
		int n, m;

		int main()
		{
			ios::sync_with_stdio(0);
			cin.tie(0);

			cin >> n >> m;
			for (int i = 0; i < n; i++) // Input board
				cin >> str_board[i];

			for (int i = 0; i < n; i++)
				fill(vis[i], vis[i] + m, -1); // Initialize visited array with -1

			queue<pair<int, int>> Q;
			Q.push({0, 0});
			vis[0][0] = 0;

			while (!Q.empty())
			{
				auto cur = Q.front();
				Q.pop();

				for (int dir = 0; dir < 4; dir++)
				{
					int nx = cur.X + dx[dir];
					int ny = cur.Y + dy[dir];

					if (nx < 0 || ny < 0 || nx >= n || ny >= m) continue;
					if (vis[nx][ny] >= 0 || str_board[nx][ny] != '1') continue;

					vis[nx][ny] = vis[cur.X][cur.Y] + 1;
					Q.push({nx, ny});
				}
			}
			cout << vis[n-1][m-1] + 1;
			return 0;
		}

	```


	```cpp
		///BOJ-7576 Tomato Problem
		#include <iostream>
		#include <bits/stdc++.h>
		#include <queue>

		#define X first
		#define Y second

		using namespace std;

		int board[1005][1005];
		int vis[1005][1005];
		int dx[4] = { 1, 0, -1, 0 };
		int dy[4] = { 0, 1, 0, -1 };

		int main()
		{
			int m, n, num = 0;
			cin >> m >> n;
			queue<pair<int, int>> Q;

			for (int i = 0; i < m; i++)
			{
				for (int j = 0; j < n; j++)
				{
					cin >> board[i][j];
					if (board[i][j] == 1)
					{
						Q.push({i, j});
						vis[i][j] = 0;
					}
					else if (board[i][j] == 0)
						vis[i][j] = -1;
				}
			}

			while (!Q.empty())
			{
				pair<int, int> cur = Q.front();
				Q.pop();

				for (int dir = 0; dir < 4; dir++)
				{
					int nx = cur.X + dx[dir];
					int ny = cur.Y + dy[dir];

					if (nx < 0 || nx >= m || ny < 0 || ny >= n) continue;
					if (vis[nx][ny] >= 0) continue;

					vis[nx][ny] = vis[cur.X][cur.Y] + 1;
					Q.push({nx, ny});
				}
			}

			for (int i = 0; i < m; i++)
			{
				for (int j = 0; j < n; j++)
				{
					if (vis[i][j] == -1)
					{
						cout << -1;
						return 0;
					}
					num = max(num, vis[i][j]);
				}
			}
			cout << num;
			return 0;
		}

	```

	```cpp
		//BOJ-1926 Picture Problem
		
		#include <iostream>
		#include <queue>

		#define X first
		#define Y second

		using namespace std;

		int n, m;
		int area = 0, mx = 0, num = 0;
		int board[502][502] = {};
		bool vis[502][502];
		int dx[4] = { 1, 0, -1, 0 };
		int dy[4] = { 0, 1, 0, -1 };

		int main()
		{
			ios::sync_with_stdio(0);
			cin.tie(0);

			cin >> n >> m;
			for (int i = 0; i < n; i++)
				for (int j = 0; j < m; j++)
					cin >> board[i][j];

			for (int i = 0; i < n; i++)
			{
				for (int j = 0; j < m; j++)
				{
					if (board[i][j] == 0 || vis[i][j]) continue;

					num++;
					queue<pair<int, int>> Q;
					Q.push({i, j});
					vis[i][j] = 1;
					area = 0;

					while (!Q.empty())
					{
						area++;
						pair<int, int> cur = Q.front();
						Q.pop();

						for (int dir = 0; dir < 4; dir++)
						{
							int nx = dx[dir] + cur.X;
							int ny = dy[dir] + cur.Y;

							if (nx < 0 || ny < 0 || nx >= n || ny >= m) continue;
							if (vis[nx][ny] || board[nx][ny] != 1) continue;

							vis[nx][ny] = 1;
							Q.push({nx, ny});
						}
					}
					mx = max(area, mx);
				}
			}
			cout << num << '\n' << mx;
			return 0;
		}

	```