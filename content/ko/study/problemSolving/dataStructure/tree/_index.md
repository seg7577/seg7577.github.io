---
title: 📜TREE 2022-09~2022-12
hide_date: true
reading_time: false
date: 2022-09-01
---


- 트리의 정의 : 무방향이면서 사이클이 없는 연결 그래프(Undirected Acyclic Connected Graph), 그래프의 한 종류라고 함. 앞서 배운 stack, queue, list 등과는 다르게 선형이 아니라 **계층적인 구조(hierarchical structure)**를 가지고 있다.
    - ![그림1](images/dataStructureImages/image1.jpg)
        
- 특징
    1. → 정의 상으로는 계층과 관계된 것이 없으며, 또 정점이 1개이고 간선이 없는 그래프도 트리임에 유의해야함
    2. 연결 그래프이면서 임의의 간선을 제거하면 연결 그래프가 아니게 되는 그래프(그림 1 참고)
    3.  V개의 정점을 가지고 V- 1개의 간선을 가지는 연결 그래프 >> (V - 1인 이유 어떤 연결 그래프든 간선이 V ≤ 간선의 개수일 경우 사이클(Circle)이 생긴다.)
    4.  **한줄 요약 : V개의 정점을 가진 트리는 V - 1개의 간선을 가지고 있다는 성질과 임의의 두 점을 연결하는 simple path가 유일하다, self loop가 존재하지 않음**
- 용어
    
    → **서브 트리 (subtree)** :  트리는 한 개의 이상의 노드로 이루어진 유한 집합이며, 이들 중 하나의 노드는 루트 노드이고 이를 제외한 나머지 노드들은 **서브트리(subtree)**라고 한다.
    
    → **루트 노드 (root node)** : 부모가 없는 노드로 트리는 단 하나의 루트 노드를 가진다. 제일 꼭대기
    
    → **단말 노드 (leaf node)** : 자식이 없는 노드로 terminal 노드라고도 부른다. 최하단에 존재하는 노드들을 부르는 느낌
    
    ![그림2](%E1%84%80%E1%85%A2%E1%84%82%E1%85%A7%E1%86%B7%20d0a5b586da3c4f7bb031f7187fc28b4e/Untitled.png)
    
    `
    

- 이진트리의 정의 : 각 노드의 자식이 최대 2개인 트리를 말한다.
    - 특징
        1. 이진 탐색 트리의 노드에 저장된 키(key)는 유일하다.
        2. 부모의 키가 왼쪽 자식 노드의 키보다 크다.
        3. 부모의 키가 오른쪽 자식 노드의 키보다 작다.
        4. 왼쪽과 오른쪽 서브 트리도 이진 탐색 트리이다.
        5. n개의 노드를 가진 트리는 n - 1개의 간선을 가지게 된다.
        
        주의 사항 :  **전체 노드의 수 =  2^k - 1** 이 식은 포화 이진트리의 경우만 해당 되니 먼저 포화 이진트리에 대해 검사를 진행한 이후 식을 사용해야 한다. 
        
    - 그림2
        
        [https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcycePn%2Fbtq9IZY6CZx%2FT5jBed5A535HHx1GwnJLWk%2Fimg.png](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcycePn%2Fbtq9IZY6CZx%2FT5jBed5A535HHx1GwnJLWk%2Fimg.png)
        
    
- 트리의 표현 방식 (일반 트리 vs 이진 트리)
    - 일반 트리의 경우 자식 노드의 개수를 n개 가질 수 있는 방면 이진 트리는 자식 노드를 최대 2개까지 가질 수 있다.
        
        여기서 주의 사항은 일반 트리가 여러 개의 자식 노드를 가지는 만큼 **사이클이 생기는 것을 생각해야 한다는 점이다.**
        
        ![Untitled](%E1%84%80%E1%85%A2%E1%84%82%E1%85%A7%E1%86%B7%20d0a5b586da3c4f7bb031f7187fc28b4e/Untitled%201.png)
        

- 포화 이진트리(Perfect Binary Tree)
    - 특징
        1. 모든 레벨이 노드로 꽉 차 있는 트리를 뜻한다.
        2. **전 이진트리의 성질도 만족해야 한다. 즉 모든 노드가 0개 혹은 2개의 자식 노드를 갖는다.**
        3. **모든 말단 노드가 동일한 깊이 또는 레벨을 갖는다.**
        4. 트리의 노드 개수가 정확히 2^k-1개여야 한다. 여기서 k는 트리의 높이(Level)이다.
    - 그림3
        
        [https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdfWC2R%2Fbtq9LqomTS7%2Frt4Io0pCfqBCckCs92CNz0%2Fimg.png](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdfWC2R%2Fbtq9LqomTS7%2Frt4Io0pCfqBCckCs92CNz0%2Fimg.png)
        

- 완전 이진트리(Complete binary tree)
    - 특징
        1. 높이가 k인 트리에서 level 1부터 k - 1까지는 노드가 모두 채워져 있고 마지막 level k에서는 왼쪽부터 끝까지 순차적으로 채워져 있는 이진 트리이다.
        2. level k에서의 노드가 꽉 차는 경우 포화 이진트리이며, 완전 이진 트리의 경우 중간이 비어 있지 않은 걸 말한다.
    - 그림4
        
        ![Untitled](%E1%84%80%E1%85%A2%E1%84%82%E1%85%A7%E1%86%B7%20d0a5b586da3c4f7bb031f7187fc28b4e/Untitled%202.png)
        
    

- 이진트리의 순회
    - 레벨 순회 (Level - order Traversal)
        - 레벨 순회는 이름 그대로 레벨, 즉 높이 순으로 방문하는 순회이다.
        
        ```cpp
        //이진트리의 순회 -> 레벨 순회(Level-order Traversal)
        
        #include <iostream>
        #include <queue>
        #include <vector>
        using namespace std;
        
        int lc[9] = { 0, 2, 4, 6, 0, 0, 0, 0, 0 }; //left child
        int rc[9] = { 0, 3, 5, 7, 0, 8, 0, 0, 0 }; //right child
        
        void bfs()
        {
        	int root = 1;
        	queue<int> q;
        	q.push(1);
        	while (!q.empty())
        	{
        		int cur = q.front();
        		q.pop();
        		cout << cur << ' ';
        		if (lc[cur]) q.push(lc[cur]);
        		if (rc[cur]) q.push(rc[cur]);
        	}
        }
        //레벨 순회란 이름 그대로 높이 순으로 방문하는 순회이다.
        
        int main()
        {
        	bfs();
        }
        ```
        
    - 전위 순회 (Preorder Traversal)
        
        →순서:
        
        1. 현재 정점을 방문한다.
        2. 왼쪽 서브 트리를 전위 순회한다.
        3. 오른쪽 서브 트리르 전위 순회한다.
        
        [https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F5VGKz%2FbtrnLHxVF6L%2FJ541A3dz2O96IOkyqNkReK%2Fimg.png](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F5VGKz%2FbtrnLHxVF6L%2FJ541A3dz2O96IOkyqNkReK%2Fimg.png)
        
        → 전위 순회는 DFS와 방문 순서가 동일하다. DFS는 일단 자기 자신을 방문한 후 첫번째 자식부터 들어가 거기에서 DFS를 다시 시작하는 구조이기 때문, 그리고 구현 또한 재귀를 이용해 간단하게 가능하다. 자기 자신을 출력한 후 왼쪽 자식과 오른쪽 자식 각각에 대해 존재할 경우 전위 수노히를 하도록 구현하면 된다.
        
        →DFS와 유사(구현 가능)
        
        ```cpp
        //이진트리의 순회 -> 전위 순회(Preorder Traversal)
        
        #include <iostream>
        #include <queue>
        #include <vector>
        using namespace std;
        
        int lc[9] = { 0, 2, 4, 6, 0, 0, 0, 0, 0 }; //left child
        int rc[9] = { 0, 3, 5, 7, 0, 8, 0, 0, 0 }; //right child
        
        void preorder(int cur)
        {
        	cout << cur << ' ';
        	if (lc[cur] != 0)	preorder(lc[cur]);
        	if (rc[cur] != 0)	preorder(rc[cur]);
        }
        // preorder(1);
        ```
        
    - 중위 순회 (Inorder Traversal)
        - 방문 순서
            1. 왼쪽 서브 트리를 중위 순회히한다.
            2. 현재 정점을 방문한다.
            3. 오른쪽 서브 트리를 중위 순회한다.
        
        [https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbn5XGj%2FbtrnQ3sPaOC%2FmkGBKVZbKkOSRZyEOP3ock%2Fimg.png](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbn5XGj%2FbtrnQ3sPaOC%2FmkGBKVZbKkOSRZyEOP3ock%2Fimg.png)
        
        - 중위 순회는 왼쪽 서브 트리 → 나 → 오른쪽 서브 트리순으로 처리하는 순회 방법
        
        ```cpp
        //이진트리의 순회 -> 중위 순회(Inorder Traversal)
        
        #include <iostream>
        #include <queue>
        #include <vector>
        using namespace std;
        
        int lc[9] = { 0, 2, 4, 6, 0, 0, 0, 0, 0 }; //left child
        int rc[9] = { 0, 3, 5, 7, 0, 8, 0, 0, 0 }; //right child
        
        void Inorder(int cur)
        {
        	if (lc[cur] != 0)	Inorder(lc[cur]);
        	cout << cur << ' ';
        	if (rc[cur] != 0)	Inorder(rc[cur]);
        }
        // Inorder(1);
        ```
        
    - 후위 순회(Postorder Traversal)
        - 방문 순서
            1. 왼쪽 서브 트리를 후위 순회한다.
            2. 오른쪽 서브 트리를 후위 순회한다.
            3. 현재 정점을 방문한다.
        
        [https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcKf4oK%2FbtrnORmndUY%2F0nMS4lWln0rHT1Sy3SVDO1%2Fimg.png](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcKf4oK%2FbtrnORmndUY%2F0nMS4lWln0rHT1Sy3SVDO1%2Fimg.png)
        
        - 후위 순회는 왼쪽 서브 트리 → 오른쪽 서브 트리 → 나 순으로 처리한다.
        
        ```cpp
        //이진트리의 순회 -> 후위 순회(Postorder Traversal)
        
        #include <iostream>
        #include <queue>
        #include <vector>
        using namespace std;
        
        int lc[9] = { 0, 2, 4, 6, 0, 0, 0, 0, 0 }; //left child
        int rc[9] = { 0, 3, 5, 7, 0, 8, 0, 0, 0 }; //right child
        
        void Postorder(int cur)
        {
        	if (lc[cur] != 0)	Postorder(lc[cur]);
        	if (rc[cur] != 0)	Postorder(rc[cur]);
        	cout << cur << ' ';
        }
        // Postorder(1);
        ```
        
    - **서로 다른 순회라고 하더라도 순회 결과가 일치할 수 있다.**

- 이진 트리의 여러 멤버 함수
    
    ```cpp
    	int getLeafCount() //이진트리의 단말 노드 개수 구하는 멤버 함수
    	{
    		return isEmpty() ? 0 : getLeafCount(root);
    	}
    	int getLeafCount(BinaryNode* node)
    	{
    		if (node == NULL)		return 0;
    		if (node->isLeaf())		return 1;
    		// 현재 노드가 leaf노드인 경우 개수를 정수 1을 누적 시킨다.
    		else
    			return getLeafCount(node->getLeft()) + getLeafCount(node->getRight());
    			//전위 순회와 비슷한 느낌으로 DFS 형식으로 진행된다.
    	}
    ```
    
    ```cpp
    //책의 예시 코드
    
    	int getHeight() //이진 트리의 높이를 구하는 함수
    	{
    		return isEmpty() ? 0 : getHeight(root);
    	}
    	int getHeight(BinaryNode* node)
    	{
    		if (node == NULL)	return 0;
    		int hleft = getHeight(node->getLeft());
    		int hright = getHeight(node->getRight());
    		return (hleft > hright) ? hleft + 1 : hright + 1;
    	}
    
    //내가 직접 짠 예시 코드
    	int height(BinaryNode* root) //이진 트리의 높이를 구하는 함수
    	//매개변수를 각 서브트리의 root부터 시작하여 가장 깊은 곳까지 탐색을 진행함
    	{
    		if (root == nullptr)
    			return 1; // 노드가 없으면 높이는 1
    
    		int left_height = height(root->getLeft());
    		int right_height = height(root->getRight());
    		return 1 + max(left_height, right_height);
    		//현재노드를 기준으로 왼쪽과 오른쪽 중 더 깊게 방문한 곳을 찾고
    		//그 깊이에 1을 더하여 반환하여 가장 깊은 곳에서부터 깊이를 체크하며 root 노드까지 올라온다.
    	}
    ```
    

탐색 

- 과정
    
    경우의 수
    
    1. 비교한 결과가 같으면 탐색이 성공적으로 끝난다.
    2. 비교한 결과 탐색키가 루트 노드의 키 값보다 작으면 탐색은 이 루트 노드의 왼쪽 자식을 기준으로 다시 시작한다.
    3. 비교한 결과 탐색키가 루트 노드의 키 값보다 크면 탐색은 이 루트 노드의 오른쪽 자식을 기준으로 다시 시작한다.
- 탐색 함수 구현(반복, 순환)
    - 아래의 두 함수의 공통점이라면 키 값을 가지고 현재 노드의 data 값의 대소 비교를 통해 찾고자 하는 노드로 접근한다는 것이다.
    
    ```cpp
    	//키 값으로 노드를 탐색하는 함수 (반복적인 방법)
    	BinaryNode* searchIter(BinaryNode* n, int key)	//키 값으로 노드를 탐색하는 함수 (반복적인 방법)
    	{
    		while (n != NULL)
    		{
    			if (key == n->getData())	return n;
    			else if (key < n->getData())n = n->getLeft();
    			else
    				n = n->getRight();
    		}
    		return NULL;
    	}
    ```
    
    ```cpp
    	
    	//키 값으로 노드를 탐색하는 함수 (순환적인 방법)
    	BinaryNode* searchRecur(BinaryNode* n, int key)	//키 값으로 노드를 탐색하는 함수 (순환적인 방법)
    	{
    		if (n == NULL)					return NULL;
    		if (key == n->getData())		return n;
    		else if (key < n->getData())	return searchRecur(n->getLeft(), key);
    		else
    			return searchRecur(n->getRight(), key);
    
    	}
    	BinaryNode* searchIter(BinaryNode* n, int key)	//키 값으로 노드를 탐색하는 함수 (반복적인 방법)
    	{
    		while (n != NULL)
    		{
    			if (key == n->getData())	return n;
    			else if (key < n->getData())n = n->getLeft();
    			else
    				n = n->getRight();
    		}
    		return NULL;
    	}
    ```
    
- 삽입 함수 구현(반복, 순환)
    
    ```cpp
    //순환적인 방법 책의 예시 코드
    void insertRecur(BinaryNode* r, BinaryNode* n)
    	{
    		if (n->getData() == r->getData())
    		//중복된 노드가 존재하는 경우 삽입 연산을 진행하지 않음
    		//why? key값은 중복이 되면 안 되기 때문
    			return;
    		else if (n->getData() < r->getData())
    		//key값 == (n->getData())가 기준이 되는 노드보다 값이 작을 경우 왼쪽으로 이동
    		{
    			if (r->getLeft() == NULL)
    			//더 이상 탐색할 노드가 없는 경우
    				r->setLeft(n);
    			else
    			//더 이상 탐색할 노드가 있는 경우 탐색 진행
    				insertRecur(r->getLeft(), n);
    		}
    		else
    		//key값 == (n->getData())가 기준이 되는 노드보다 값 보다 클 경우 오른쪽으로 이동
    		{
    			if (r->getRight() == NULL)
    			//더 이상 탐색할 노드가 없는 경우
    				r->setRight(n);
    			else
    			//더 이상 탐색할 노드가 존재하는 경우 탐색 진행
    				insertRecur(r->getRight(), n);
    		}
    	}
    //내가 직접 짠 코드
    void insertNode(BinaryNode* root, BinaryNode* temp)
    	{
    		if (root == NULL)
    			setRoot(temp);
    
    		else if (root->getData() < temp->getData() && root->getRight() != NULL)
    			insertNode(root->getRight(), temp);
    		else if (root->getData() > temp->getData() && root->getLeft() != NULL)
    			insertNode(root->getLeft(), temp);
    		
    		else
    		{
    			if (root->getData() < temp->getData())
    				root->setRight(temp);
    			else
    				root->setLeft(temp);
    		}
    
    	}
    ```
    
- 삭제 함수 구현(반복, 순환)
    - 고려 해야 될 사항
        1. **삭제 하려는 노드가 단말 노드인 경우**
        2. **삭제하려는 노드가 왼쪽이나 오른쪽 서브트리 중 오나만 가지고 있는 경우**
        3. **삭제하려는 노드가 두 개의 서브트리 모두 가지고 있는 경우**
    
    ```cpp
    void remove(BinaryNode* parent, BinaryNode* node)
    	{
    		//case1 : 삭제하려는 노드가 단말 노드인 경우
    		if (node->isLeaf())
    		{
    			if (parent == NULL)	root = NULL;
    			//삭제하려는 노드가 root 노드인 경우
    
    			else
    			//root 노드가 아닌 경우 parent의 해당 자식을 NULL로 바꿈
    			{
    				if (parent->getLeft() == node)	parent->setLeft(NULL);
    				//찾고자 하는 노드가 parent의 왼쪽인 경우
    				else
    				//찾고자 하는 노드가 parent의 오른쪽인 경우
    					parent->setRight(NULL);
    			}
    		}
    
    		//case2: 삭제하려는 노드가 왼쪽이나 오른쪽 자식만 갖는 경우, == 하나의 서브트리만 존재하는 경우
    		else if (node->getLeft() == NULL || node->getRight() == NULL)
    		{	//삭제할 노드의 유일한 자식 노드 => child
    			BinaryNode* child = (node->getLeft() != NULL) ? node->getLeft() : node->getRight();
    
    			if (node == root)	root = child;
    			//삭제할 노드가 루트이면 ==> child가 새로운 root가 됨
    
    			else
    			//아니면 ==> 부모 노드의 자식으로 자식 노드 child를 직접 연결
    			{
    				if (parent->getLeft() == node)	parent->setLeft(child);
    				else
    					parent->setRight(child);
    			}
    		}
    
    		//case3: 삭제하려는 노드가 두 개의 자식이 모두 있는 경우
    		else
    		{
    			//삭제하려는 노드의 오른쪽 서브트리에서 가장 작은 노드를 탐색
    			//succ => 후계 노드: 오른쪽 서브트리에서 가장 key가 작은 노드
    			//sucp => 후계 노드의 부모노드
    			BinaryNode* sucp = node;
    			BinaryNode* succ = node->getRight();
    			while (succ->getLeft() != NULL)
    			//후계 노드 탐색
    			{
    				sucp = succ;
    				//후계 노드의 부모 노드
    
    				succ = succ->getLeft();
    				//후계 노드
    			}
    
    			if (sucp->getLeft() == succ)
    			//후계 노드의 부모와 후계 노드의 오른쪽 자식을 직접 연결
    				sucp->setLeft(succ->getRight());
    			else
    			//후계 노드 정보를 삭제할 노드에 복사
    				sucp->setRight(succ->getRight());
    
    			node->setData(succ->getData());
    			//후계 노드 정보를 삭제할 노드에 복사
    
    			node = succ;
    			//삭제할 노드를 후계 노드로 변경
    		}
    		delete node;
    	}
    ```
	
	- 문제
		```cpp
		//BFS 예시 코드1 - 부모 배열 채우기
		#include <iostream>
		#include <vector>
		#include <queue>
		using namespace std;

		void bfs()
		{
			int root;
			cin >> root;
			vector<int> adj[10];
			int p[10];
			queue<int> q;
			q.push(root);
			while (!q.empty())
			{
				int cur = q.front();
				q.pop();

				for (auto nxt : adj[cur])
				{
					if (p[cur] == nxt)	continue;
					q.push(nxt);
					p[nxt] = cur; //자식 노드의 부모 노드를 재방문해서 다른 곳으로 새는 것을 막기 위함 기존의 BFS와의 차이
				}
			}
		}
		```

		```cpp
		//BFS 예시 코드2 - 부모와 depth 배열 채우기
		#include <iostream>
		#include <vector>
		#include <queue>
		using namespace std;

		//시간 복잡도는 동일 O(V+E)이며 트리에서는 E = V - 1이기에 O(V)가 됨
		//vis를 이용할 때와 코드의 흐름은 큰 차이는 없음 vis의 용도를 바꾸기 위해 bool형이 아닌 int형의로 해당 칸에서의 왔던 길?을 체크해주기 때문
		//예시 코드1과는 큰 차이가 없음 추가된 것은 depth를 활용하여 거리를 측정하는 것

		void bfs()
		{

			int root;
			cin >> root;
			vector<int> adj[10];
			int p[10];
			//P배열의 용도는 부모 노드를 재방문해서 왔던 길로 다시 돌아가지 않게 하기 위함
			int depth[10];
			queue<int> q;
			q.push(root);
			while (!q.empty())//BFS의 일반적인 틀
			{
				int cur = q.front();
				q.pop();
				cout << cur << ' ';

				for (auto nxt : adj[cur])
				{
					if (p[cur] == nxt)	continue;
					q.push(nxt);
					p[nxt] = cur; //자식 노드의 부모 노드를 재방문해서 다른 곳으로 새는 것을 막기 위함 기존의 BFS와의 차이
					depth[nxt] = depth[cur] + 1; //root에서부터 부모 노드의 거리 + 1 = root에서부터 현재 노드까지의 거리
				}
			}
		}
		```

		```cpp
		#include <iostream>
		#include <stack>
		#include <vector>
		using namespace std;

		//DFS 예시 코드1 - 부모와 depth 배열 채우기, 비재귀
		//기존 BFS 예시 코드와의 차이는 크게 없다. queue을 stack으로 바꾸면 된다.

		void dfs()
		{

			int root;
			cin >> root;
			vector<int> adj[10];
			int p[10];
			//P배열의 용도는 부모 노드를 재방문해서 왔던 길로 다시 돌아가지 않게 하기 위함
			int depth[10];
			stack<int> s;
			s.push(root);
			while (!s.empty())//BFS의 일반적인 틀
			{
				int cur = s.top();
				s.pop();
				cout << cur << ' ';

				for (auto nxt : adj[cur])
				{
					if (p[cur] == nxt)	continue;
					s.push(nxt);
					p[nxt] = cur; //자식 노드의 부모 노드를 재방문해서 다른 곳으로 새는 것을 막기 위함 기존의 BFS와의 차이
					depth[nxt] = depth[cur] + 1; //root에서부터 부모 노드의 거리 + 1 = root에서부터 현재 노드까지의 거리
				}
			}
		}
		```

		```cpp
		#include <iostream>
		#include <stack>
		#include <vector>
		using namespace std;

		//DFS 예시 코드2 - 부모와 depth 배열 채우기, 재귀
		//기존 BFS 예시 코드와의 차이는 크게 없다. queue을 stack으로 바꾸면 된다.

		vector<int> adj[10];
		int p[10];
		//P배열의 용도는 부모 노드를 재방문해서 왔던 길로 다시 돌아가지 않게 하기 위함
		int depth[10];

		void dfs(int cur)
		{
			cout << cur << ' ';
			for (auto nxt : adj[cur])
			{
				if (p[cur] == nxt)	continue;
				p[nxt] = cur; //자식 노드의 부모 노드를 재방문해서 다른 곳으로 새는 것을 막기 위함 기존의 BFS와의 차이
				depth[nxt] = depth[cur] + 1; //root에서부터 부모 노드의 거리 + 1 = root에서부터 현재 노드까지의 거리
				dfs(nxt);
			}
		}
		//재귀로 구현시 코드는 상당히 깔끔해짐. 하지만 스택 메모리가 1MB로 제한되어 있을 땐 V가 대략 3만 이상일 때 1-2-3-4-5-6
		//형태의 일자 트리 모양에서 스택 메모리 한계를 넘어설 수 있기때문에 스택 메모리에 대한 별도의 제한이 있을 때에는 주의해야 함
		```

		```cpp
		//DFS 예시 코드3 - 단순 순회, 재귀

		#include <iostream>
		#include <stack>
		#include <vector>
		using namespace std;

		vector<int> adj[10];
		int p[10];
		//P배열의 용도는 부모 노드를 재방문해서 왔던 길로 다시 돌아가지 않게 하기 위함
		int depth[10];

		void dfs(int cur, int par)
		{
			cout << cur << ' ';
			for (auto nxt : adj[cur])
			{
				if (par == nxt)	continue;
				dfs(nxt, cur);
			}
		}
		//call dfs(1, 0);
		```