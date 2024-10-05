---
title: 📜GRAPH(그래프) 2022-09~2022-12
hide_date: true
reading_time: false
date: 2022-09-01
---

- 그래프(Graph)는 정점(Vertex, Node)과 간선(Edge)으로 이루어진 자료구조로, 다양한 관계나 연결 구조를 표현하는 데 사용됩니다. 그래프는 네트워크, 소셜 미디어, 웹페이지 간의 링크, 도로망 등 여러 실제 문제에서 자주 사용됩니다.

- 그래프의 구성 요소:
	- 정점(Vertex): 그래프에서 데이터를 나타내는 개체로, 노드(node)라고도 불립니다. 정점은 사람, 도시, 웹페이지 등 여러 개체를 나타낼 수 있습니다.
	- 간선(Edge): 정점 간의 연결을 나타냅니다. 간선은 두 정점을 연결하여 그들 간의 관계를 표현하며, 방향이 있거나 없을 수 있습니다.
- 그래프의 유형: 그래프는 간선의 방향성과 가중치 등에 따라 여러 유형으로 나눌 수 있습니다.
	- 무방향 그래프(Undirected Graph): 간선에 방향이 없는 그래프입니다. 두 정점이 연결되어 있으면 양쪽으로 갈 수 있다는 의미입니다.예: A - B 간선이 있으면 A에서 B로 갈 수도 있고, B에서 A로도 갈 수 있습니다.
	- 방향 그래프(Directed Graph): 간선에 방향이 있는 그래프입니다. 즉, 한 방향으로만 갈 수 있습니다.
	예: A -> B 간선이 있으면 A에서 B로 갈 수 있지만, B에서 A로는 갈 수 없습니다.
	- 가중치 그래프(Weighted Graph): 간선에 가중치(비용)가 부여된 그래프입니다. 가중치는 정점 간의 거리를 나타내거나, 네트워크의 대역폭 또는 비용을 표현할 때 사용됩니다. 예: 도로망에서 각 간선이 도시 간의 거리를 나타내는 경우.
	- 사이클 그래프(Cyclic Graph)와 비사이클 그래프(Acyclic Graph):

	- 사이클 그래프: 사이클이 있는 그래프. 즉, 특정 정점에서 출발해 다른 정점을 거쳐 다시 원래 정점으로 돌아올 수 있는 경로가 존재하는 그래프입니다.
	- 비사이클 그래프: 사이클이 없는 그래프입니다. 트리가 대표적인 비사이클 그래프입니다. 
	- 그래프의 표현 방식: 그래프는 다음과 같은 두 가지 방식으로 주로 표현됩니다.

- 인접 행렬(Adjacency Matrix): 그래프를 2차원 배열로 표현하는 방식입니다. 배열의 각 셀 (i, j)는 정점 i에서 정점 j로 간선이 있는지를 나타냅니다. 값이 1이면 간선이 존재함을 의미하고, 값이 0이면 간선이 없음을 의미합니다.
	- 예시 코드
		
		```cpp
		//방향 그래프(Directed Graph, 인접행렬)
		#include<iostream>
		#include<bits/stdc++.h>
		//방향 그래프(Directed Graph)
		using namespace std;
		int main()
		{
			int node , Edge; //정점과 간선의 개수
			int adj_matrix[100][100];
			cin >> node >> Edge;
			for (int i = 0; i < Edge; i++)
			{
				int u, v;
				cin >> u >> v;
				adj_matrix[u][v] = 1;
			}
		
		}
		```

		
		```cpp
		//무방향 그래프(Undirected Graph, 인접행렬)
		#include<iostream>
		#include<bits/stdc++.h>
		//무방향 그래프(Undirected Graph)
		using namespace std;
		int main()
		{
			int node , Edge; //정점과 간선의 개수
			int adj_matrix[100][100];
			cin >> node >> Edge;
			for (int i = 0; i < Edge; i++)
			{
				int u, v;
				cin >> u >> v;
				adj_matrix[u][v] = 1;
				adj_matrix[v][u] = 1;
			}
		
		}
		```
	
    - 인접리스트
		```cpp
		//무방향 그래프(Undirected Graph, 인접 리스트)
		#include<iostream>
		#include<bits/stdc++.h>
		#include<vector>
		//무방향 그래프(Directed Graph)
		using namespace std;
		int main()
		{
			int node , Edge; //정점과 간선의 개수
			vector <int> adj_matrix[100];
			cin >> node >> Edge;
			for (int i = 0; i < Edge; i++)
			{
				int u, v;
				cin >> u >> v;
				adj_matrix[u].push_back(v);
				adj_matrix[v].push_back(u);
			}
		
		}
		```
		```cpp
		//방향 그래프(Directed Graph, 인접 리스트)
		#include<iostream>
		#include<bits/stdc++.h>
		#include<vector>
		//방향 그래프(Directed Graph)
		using namespace std;
		int main()
		{
			int node , Edge; //정점과 간선의 개수
			vector <int> adj_matrix[100];
			cin >> node >> Edge;
			for (int i = 0; i < Edge; i++) //간선의 개수만큼 반복
			{
				int u, v;
				cin >> u >> v;
				adj_matrix[u].push_back(v);
			}
		
		}
		```
    - 문제
		```cpp
		//BOJ-11724 연결 요소의 개수
		#include <iostream>
		#include <bits/stdc++.h>
		#include <vector>
		#include <queue>
		
		using namespace std;
		bool vis[100005];
		int main()
		{
			int cnt = 0;
			int n, m; //정점의 개수와 간선의 개수
			int u, v; //간선의 양 끝점 u v
		
			vector<int> adj[100005];
		
			queue<int> Q;
		
			cin >> n >> m;
		
			for (int i = 0; i < m; i++)
			{
				cin >> u >> v;
				//간선을 기준으로 양 끝점 u와 v를 입력 받음
		
				adj[u].push_back(v);
				adj[v].push_back(u);
				//문제에서 방향 없는 그래프라고 했으므로 무방향 그래프이므로 adj[u], adj[v]에 각각 push_back 함
			}
			
			for (int i = 1; i <= n; i++)//각 정점을 돌며 연결을 확인해야 하므로 정점의 개수만큼 반복
			{
				if (vis[i])//방문한 곳이면 true
				{
					cnt++;//연결이 끊어진 경우 cnt
					continue; //방문한 경우 넘어간다
					
				}
		
				Q.push(i);//32번째 if문에서 걸러지지 않았으므로 방문하지 않았으니 i와 연결된 정점들을 체크해보기 위해 Q에 push
				vis[i] = true; //방문한 곳을 또 방문하지 않기 위해 표시를 남김
		
				while (!Q.empty()) //연결된 모든 지점을 방문한다.
				{
					int cur = Q.front();//큐에서 정점을 꺼내어 그 정점과 연결된 모든 정점들에 대해 3번을 진행
					Q.pop();//시간초과 or 런타임에러가 발생할 수도 있으니 바로 빼줘야 함 자주하는 실수 중 하나라고 강조
					
		
					for (int nxt : adj[cur])//nxt = adj배열의 내부 값을 가지고 반복 횟수는 adj[cur]의 요소 개수만큼 반복함
					{
						if (vis[nxt])	continue; //이미 방문한 경우 continue 이 말은 즉, 연결이 되었는 지 확인한 경우를 말한다
						Q.push(nxt);//방문하지 않은 곳이므로 Q에 넣고 43번째의 while문을 수행한다.
						vis[nxt] = true;//방문한 곳을 또 방문하지 않기 위해 표시를 남김
					}	
				}
			}
			cout << n - cnt; //정점의 개수에서 continue한 횟수를 빼면 연결이 끊긴 횟수를 알 수 있다.
		
			return 0;
		}
		```
		
		```cpp
		//Graph(BFS) - 연결 그래프에서의 순회
		
		#include <iostream>
		#include <bits/stdc++.h>
		#include <vector>
		#include <queue>
		
		using namespace std;
		
		int main()
		{
			vector<int> adj[10];
			bool vis[10];
			queue<int> q;
		
			q.push(1);//시작하는 정점을 큐에 넣고
			vis[1] = true;//방문했다는 표시를 남김
			//과정1번
		
			while (!q.empty())
			{
				int cur = q.front();//큐에서 정점을 꺼내어 그 정점과 연결된 모든 정점들에 대해 과정 3번 진행
				q.pop();//시간초과 or 런타임 에러를 방지하기 위해 넣어줬으면 바로 빼줘야 됨
				//과정2번
		
				cout << cur << ' ';
		
				for (auto nxt : adj[cur]) //해당 vector [cur]번째에 들어있는 요소의 개수만큼 반복하고 그 값을 nxt에 넣으면서 진행됨
				{
					if (vis[nxt])	continue; //이미 방문한 곳이면 continue함
					q.push(nxt);//큐에 push하여 현재 nxt와 연결된 곳을 탐색
					vis[nxt] = true;//방문하였으므로 중복되어 시간초과가 발생하지 않게 방문표시를 남겨줌
				}//과정3번
			}
		}
		//인접리스트에서는 시간 복잡도 O(V+E), 인접행렬에서는 시간 복잡도O(V^2)이다
		```
		
		```cpp
		//BOJ - 2606 - 바이러스
		
		#include <iostream>
		#include <vector>
		#include <queue>
		
		using namespace std;
		//이 문제에서 방향과 상관없이 연결된 모든 것은 감염된다. 이는 무방향 그래프를 말해준다.
		
		bool vis1[1005]; //방문여부를 확인하기 위한 bool형
		int main()
		{
			int n; //컴퓨터의 개수
			int node1, node2, edge; //정점1과 정점2, 쌍의 개수를 의미함
			int cnt = 0; //바이러스에 감염된 컴퓨터의 수 = 총 컴퓨터의 수 - 감염되지 않은 컴퓨터의 수
			cin >> n >> edge;
		
			vector<int> V1[105];
			queue<int> Q1;
			for (int i = 0; i < edge; i++)
			{
				cin >> node1 >> node2;
				V1[node1].push_back(node2);
				V1[node2].push_back(node1);
				//무방향 그래프이므로 둘다 push_back해줌
			}
		
			Q1.push(1);//시작할 정점을 큐에 넣음
			vis1[1] = 1; //방문표시를 남겨줌.
		
			while (!Q1.empty())
			{
				int cur = Q1.front();//정점을 꺼내어 그 정점과 연결된 모든 정점들을 찾기 위함
				Q1.pop();
				for (auto nxt : V1[cur])
				{
					if (vis1[nxt] == 1)	continue; //이미 방문했다면 continue하는 것
					Q1.push(nxt);//인접 리스트 안에 있는 숫자 중에 방문하지 않은 숫자이므로 방문하여 nxt와 연결 되어 있는 컴퓨터들을 감염
					vis1[nxt] = 1; //방문했으므로 다시 방문하지 않게 감염표시를 남겨줌 
		
				}
			}
		
			for (int i = 1; i <= n; i++)
			{
				if (vis1[i] == 0)	cnt++; //감염되지 않은 컴퓨터의 수를 파악하기 위함
			}
			cout << n - cnt - 1;
		//if (vis[i] == 0)의 구절을 옮기면 더 줄일 수 있음
		}
		```
		
		```cpp
		//BOJ - 5567 - 결혼식
		
		#include <iostream>
		#include <vector>
		#include <queue>
		
		using namespace std;
		//ai와 bi가 친구라는 뜻이며, bi와 ai도 친구관계이다. 이 말은 즉슨 무방향 그래프를 말한다
		bool vis[10005];
		
		int main()
		{
			int n, m;// 상근이의 동기의 수, 리스트의 길이
			int a, b; //친구 관계
			int cnt = 0, count = 0;
			cin >> n >> m;
		
			vector<int> v[505];
			queue<int> q;
		
			for (int i = 0; i < m; i++)//상근이의 리스트의 길이만큼 반복
			{
				cin >> a >> b;
				v[a].push_back(b);
				v[b].push_back(a);
				//친구 관계를 입력 받고 무방향 그래프이므로 양쪽에게 모두 넣어줌.
			}
		
			q.push(1); //시작점(상근이)를 큐에 넣고 상근이의 친구를 탐색한다.
			vis[1] = 1; //친구인 것을 인증하고 난 이후 또 친구인지 아닌지 확인하지 않기 위함
		
			while (!q.empty())
			{
				int cur = q.front();
				q.pop(); //시간초과 or 런타임 에러를 방지하기 위해 cur에 front값을 넣어줬으면 다시 사용하지 않기 때문에 바로 빼줘야 함
		
				
				if (cur == 1) //상근이와 직접 친구 관계인 사람들을 위한 BFS
				{
					for (auto nxt : v[cur])
					{
						if (vis[nxt] == 1)	continue;
						q.push(nxt);
						vis[nxt] = 1;
						cnt++; //상근이와의 직속? 친구 관계인 사람들의 수를 구함.
						count++;
						//이는 BFS
					}
				}
				else if (cnt != 0)//상근이와의 친구의 친구인지를 확인할 BFS
				{
					for (auto nxt : v[cur])
					{
						if (vis[nxt] == 1)	continue;
						vis[nxt] = 1;
						count++;
					}
					cnt--;
				}
			}
			cout << count;
			
			return 0;
		}
		```
		