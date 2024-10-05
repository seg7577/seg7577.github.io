---
title: 📜BFS(너비 우선 탐색, Breadth-First Search) 2022-09~2022-12
hide_date: true
reading_time: false
date: 2022-09-01
---


- BFS는 그래프 탐색 알고리즘 중 하나로, 너비를 우선으로 탐색하는 방식입니다. 즉, 루트 노드에서 시작하여 인접한 노드들을 먼저 모두 탐색한 후, 그 다음 단계로 넘어가면서 점차 깊게 탐색을 진행하는 알고리즘입니다. BFS는 주로 큐(Queue) 자료구조를 사용하여 구현됩니다.
	- 작동 원리: 시작 노드를 큐에 삽입하고, 탐색할 노드가 없을 때까지 아래 과정을 반복합니다. 큐에서 노드를 꺼내 해당 노드와 연결된 모든 인접 노드를 큐에 삽입합니다. 이때, 이미 방문한 노드는 다시 큐에 삽입하지 않습니다. 이 과정을 거치며 가장 가까운 노드들부터 차례로 탐색하게 됩니다.
	- 특징: 최단 경로를 찾는 데 유리합니다. BFS는 각 노드를 너비 우선으로 탐색하므로, 가중치가 동일한 그래프에서 최단 경로를 보장합니다.그래프의 모든 노드를 탐색하는 데에도 사용됩니다.
	- 시간 복잡도: BFS의 시간 복잡도는 **O(V + E)**입니다. 여기서 V는 노드의 수(정점), E는 간선의 수입니다. 인접한 모든 노드를 방문하고 탐색을 완료하기 때문에, 그래프의 구조에 따라 달라질 수 있습니다.
	- BFS의 구현 방법: 큐 자료구조를 이용하여 구현합니다. 시작 노드를 큐에 삽입하고, 큐에서 노드를 꺼내면서 인접 노드를 차례로 큐에 추가하는 과정을 반복합니다. 방문 여부를 기록하기 위해 배열을 사용합니다. 이미 방문한 노드는 다시 탐색하지 않도록 합니다.
	- BFS의 예시: 예를 들어, 다음과 같은 그래프가 있다고 가정해봅시다.
    1 -- 2 -- 5
    |    |
    3 -- 4
	1번 노드부터 BFS 탐색을 시작하면, 탐색 순서는 다음과 같습니다: 1 -> 2 -> 3 -> 5 -> 4. 먼저 1번 노드를 큐에 넣고, 1번 노드와 인접한 2번과 3번을 큐에 삽입합니다. 그 다음 2번 노드를 탐색하고, 인접한 5번을 큐에 넣습니다. 3번과 4번 노드도 마찬가지로 탐색을 진행합니다.
- BFS의 응용: 최단 경로 찾기: BFS는 미로 찾기와 같은 문제에서 최단 경로를 찾을 때 유용합니다. 경로 상의 모든 간선의 가중치가 동일할 경우, BFS를 사용하여 최단 경로를 빠르게 찾을 수 있습니다. 네트워크 탐색: 그래프의 모든 노드를 차례대로 탐색해야 하는 경우, BFS가 유용합니다.

- 예시 코드
	- BFS 개념
		```cpp
		
		#include <bits/stdc++.h>
		#include <iostream>
		#include <queue>

		#define X first
		#define Y second

		//pair가 first와 second를 기반으로 접근하기 때문에 선언
		using namespace std;

		int board[502][502] = {};
		bool vis[502][502]; //방문 여부를 저장하기 위한 bool형 이차원 배열
		int n = 7, m = 10; //행과 열의 범위
		int dx[4] = { 1, 0, -1, 0 };
		int dy[4] = { 0, 1, 0, -1 };

		int main()
		{
			ios::sync_with_stdio(0);
			cin.tie(0);

			queue<pair<int, int>> Q;//
			vis[0][0] = 1; //시작점은 1로 표시하고 시작, 과정1, 자주하는 실수 1번 : "시작점에 방문했다는 표시를 남기지 않는다."
			Q.push({ 0, 0 }); //시작점이므로 Q에 넣고 시작, 과정1

			while (!Q.empty())
				//큐가 비면 1을 반환하고 큐가 차있으면 0을 반환 하지만 !을 붙였으니, 비면 0을 반환 차있으면 1을 반환
				//상하좌우 인접한 좌표를 모두 방문했거나, 조건에 충족하지 않을 경우 큐가 비게 되므로 그때 0을 반환할 것이다.
			{
				pair<int, int> cur = Q.front();
				//큐의 과정 2번을 진행하기 위해 pair 선언한 cur에 큐의 front 값을 넣음

				Q.pop(); // 자주하는 실수 2번에서 말한 빼는 경우가 이곳임
				//front 했으면 다음 비교를 위해 cur에 저장한 이후 바로 pop하여 삭제
				cout << '(' << cur.X << ", " << cur.Y << ") -> ";
				
				for (int dir = 0; dir < 4; dir++)
					// dir은 상하좌우로 (x,y) 좌표를 와리가리 치기 위해 반복을 4로 함
				{
					int nx = cur.X + dx[dir];
					int ny = cur.Y + dy[dir];
					//좌표를 상 or 하 or 좌 or 우로 이동시키고 그값을 각각 nx, ny에 저장하여 이후 조건과 비교할 수 있게 만듦

					if (nx < 0 || nx >= n || ny < 0 || ny >= m)	continue;
					//#상하좌우로 이동시킨 좌표값이 혹여나 음수이거나 주어진 n과 m의 값에 벗어나면 바로 continue함 이러기 위해 nx와 ny를 만든 이유1

					if (vis[nx][ny] || board[nx][ny] != 1)	continue;
					//#상하좌우로 이동시킨 좌표값이 혹여나 이미 방문했거나 우리가 원하는 조건에 충족하지 못한 칸이면 바로 continue함  nx와 ny를 만든 이유2

					vis[nx][ny] = 1; //"자주 하는 실수 2 : "큐에 넣을 때 방문했다는 표시를 하는 대신 큐에서 빼낼 때 방문했다는 표시를 남긴 경우" 조심하기, 실수 2번 같은 경우는 메모리 초과 or 시간 초과로 이어지는 경우임
					//위의 2개의 if문의 조건을 불충족하였다면 방문하지 않았고, 우리가 원하는 조건을 충족하고, 좌표의 값이 범위에 벗어나지 않는 것이므로 방문하였단 표시를 남겨주기 위해 vis의 좌표 값에 1을 넣어줌

					Q.push({ nx, ny });
					//이 for문을 빠져 나간 이후 현재 방문한 좌표의 상하좌우를 탐색하기 위해 큐에 저장

				}
			}

			//자주 하는 실수 3 : "이웃한 원소가 범위를 벗어나는지에 대한 체크를 잘못했다.", 44번째의 if문과 47번째의 if문의 실행 순서를 바꾼다면 예를 들어 vis[-1][0] 이러한 좌표 값을 참조할 수 있어 런타임에러가 날 수 있으므로 일단 범위를 먼저 체크하는 것임
		}
		```
	- 문제

		```cpp

		//BOJ-2178 미로 탐색
		#include <iostream>
		#include <queue>
		#include <string>
		#include <algorithm>
		#include <bits/stdc++.h>
		#define X first
		#define Y second
		using namespace std;

		string str_board[105];
		int bord[105][105];
		int vis[105][105];
		int dx[4] = { 1, 0, -1, 0 };
		int dy[4] = { 0, 1, 0, -1 };
		int n, m;

		int main()
		{
			ios::sync_with_stdio(0);
			cin.tie(0);

			cin >> n >> m;
			for (int i = 0; i < n; i++) //board 입력
				cin >> str_board[i];

			for (int i = 0; i < n; i++)
				fill(vis[i], vis[i] + m, -1);//값으로 특점 범위(first, last , val)를 채우는 역할을 하는 함수
			queue<pair<int, int>> Q;
			Q.push({ 0, 0 });
			vis[0][0] = 0;
			//무조건 시작점은 좌상단 0, 0임
			while (!Q.empty())
			{
				auto cur = Q.front();
				//auto 키워드는 선언한 변수나 람다식의 타입을 컴파일러에게 추론하도록 맡김
				//약간 카멜레온 느낌 알아서 바뀜

				Q.pop();
				for (int dir = 0; dir < 4; dir++)
				{
					int nx = cur.X + dx[dir];
					int ny = cur.Y + dy[dir];
					//현재 위치에서 와리가리 하려고

					if (nx < 0 || ny < 0 || nx >= n || ny >= m)	continue;
					//nx, ny가 범위를 벗어날 경우 continue함

					if (vis[nx][ny] >= 0 || str_board[nx][ny] != '1')	continue;
					//vis나 str_board에 1이나 시작점부터의 거리가 표시 되있으면 continue함

					vis[nx][ny] = vis[cur.X][cur.Y] + 1;
					//현재의 위치 = (현재의 상하좌우 기준점)보다 한칸 더 앞에 있으므로 +1을 하여 저장함.

					Q.push({ nx, ny });
				}
			}
			cout << vis[n-1][m-1] + 1;
			//문제에서는 (0,0)이 시작이 아니라 (1, 1)을 시작이라 하기 때문에 [-1]을 해줘야 함
			//+1을 한 이유는 0,0을 0으로 잡고 시작했기 때문에 거리를 계산할때 첫번째 칸을 1이 아닌 0으로 잡고 시작하기 때문에 +1해서 표현함.

			return 0;
		}
		```

		```cpp
		//BOJ-7576 토마토
		#include<iostream>
		#include<bits/stdc++.h>
		#include<string>
		#include<queue>

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
			for (int i = 0; i < m; i++) //입력
				for (int j = 0; j < n; j++)
				{
					cin >> board[i][j];
					
					if (board[i][j] == 1)//익은 토마토인지 판별
					{
						Q.push({ i, j }); //익은 토마토 있으면 큐에 넣기
						vis[i][j] = 0; //익은 애들은 0
					}
						
					else if (board[i][j] == 0)
						vis[i][j] = -1;
				}

			while (!Q.empty())
			{
				pair<int, int> cur = Q.front(); 
				//토마토가 위치한 곳을 cur에 넣어 상하좌우로 탐색
				//여기서 front의 반환값은 입력을 기준으로 첫번째로 익은 애들을 좌표에 넣음 그 다음 2번째... 끝까지 진행..

				Q.pop();//메모리 초과, 시간 초과가 날 수 있기 때문에 빠딱빠딱 빼줘야 됨
				
				for (int dir = 0; dir < 4; dir++)//상하좌우 탐색을 위해 반복
				{
					int nx = cur.X + dx[dir];
					int ny = cur.Y + dy[dir];

					if (nx < 0 || nx >= m || ny < 0 || ny >= n)	continue; //범위에서 벗어나는 겨우 continue
					if (vis[nx][ny] >= 0)	continue; //이미 방문한 경우이거나 토마토가 익어 있지 않은 경우

					vis[nx][ny] = vis[cur.X][cur.Y] + 1; //좌표값에 해당 좌표에 있는 값 +1을 하여 누적 시켜줌. ==> 날짜 증가

					Q.push({ nx, ny });
				}
			}
			
			for (int i = 0; i < m; i++)//이중 for문으 사용하여 -1이 하나라도 있는 지 확인하고, 좌표 값 가장 큰값을 찾는 것이다.
			{
				for (int j = 0; j < n; j++)
				{
					if (vis[i][j] == -1) //익지 않은 토마토가 아직 존재한다는 소리이므로 조건대로 -1출력
					{
						cout << -1;
						return 0;
					}
					
					num = max(num, vis[i][j]);
				}
			}
			cout << num; //아직 익지 않은 토마토가 없으므로 최소 일수 출력.

			return 0;
		}
		```

		```cpp
		//BOJ-1926 그림
		#include <bits/stdc++.h>
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
					if (board[i][j] == 0 || vis[i][j])	continue;

					num++; //그림의 개수 증가
					queue<pair<int, int>> Q;
					Q.push({i , j});//새로운 그림의 시작점 표기라고 봐도 됨
					vis[i][j] = 1; //while 들어가기 전 시작점 표시 크게 보면 다른 그림의 새로운 시작점 표시
					area = 0;
					while (!Q.empty())
					{
						area++; //그림의 넓이 증가

						pair<int, int> cur = Q.front();
						Q.pop();

						for (int dir = 0; dir < 4; dir++) //상하좌우로 이어지는 그림이 있나 확인하기 위해 반복
						{
							int nx = dx[dir] + cur.X;
							int ny = dy[dir] + cur.Y;
							
							if (nx < 0 || ny < 0 || nx >= n || ny >= m)	continue;
							if (vis[nx][ny] || board[nx][ny] != 1)	continue;

							vis[nx][ny] = 1;
							Q.push({ nx, ny });
						}
					}
					mx = max(area, mx);
				}
			}
			cout << num << '\n' << mx;
			return 0;
		}
		```