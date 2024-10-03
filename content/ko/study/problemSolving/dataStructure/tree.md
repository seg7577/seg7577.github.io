# Tree

[개념](Tree%20448e909ae2e945c69376117b1848d153/%E1%84%80%E1%85%A2%E1%84%82%E1%85%A7%E1%86%B7%20d0a5b586da3c4f7bb031f7187fc28b4e.md)

[예시 코드](Tree%20448e909ae2e945c69376117b1848d153/%E1%84%8B%E1%85%A8%E1%84%89%E1%85%B5%20%E1%84%8F%E1%85%A9%E1%84%83%E1%85%B3%20ca1f513a87df49878dc66a0e0a15ed0d.md)

```cpp
//BOJ - 11725 - 트리의 부모 찾기
#include <iostream>
#include <vector>
#include <queue>
using namespace std;

int main()
{
	ios::sync_with_stdio(0);
	cin.tie(0);

	int n, node1, node2;//정점의 개수
	int p[1000001] = {};
	vector<int> v[1000001];
	queue<int> q;
	cin >> n;
	for (int i = 0; i < n - 1; i++)
	{
		cin >> node1 >> node2;
		v[node1].push_back(node2);
		v[node2].push_back(node1);
	}
	q.push(1);
	while (!q.empty())
	{
		int cur = q.front();
		q.pop();

		for (auto nxt : v[cur])
		{
			if (p[cur] == nxt)	continue;
			q.push(nxt);
			p[nxt] = cur;
		}
	}
	for (int i = 2; i <= n; i++)
		cout << p[i] << '\n';

	return 0;
}
```

```cpp
//BOJ - 1991 - 트리 순회
#include <iostream>
#include <vector>
#include <queue>

using namespace std;

int lc[300]; //left child
int rc[300];//right child

void preorder(int cur)
{
	cout << (char)cur;
	if (lc[cur] != 0)	preorder(lc[cur]);
	if (rc[cur] != 0)	preorder(rc[cur]);
}
void Inorder(int cur)
{
	if (lc[cur] != 0)	Inorder(lc[cur]);
	cout << (char)cur;
	if (rc[cur] != 0)	Inorder(rc[cur]);
}

void Postorder(int cur)
{
	if (lc[cur] != 0)	Postorder(lc[cur]);
	if (rc[cur] != 0)	Postorder(rc[cur]);
	cout << (char)cur;
}
int main()
{
	//root = A
	int n;
	char node1, node2, node3;
	cin >> n;
	for (int i = 0; i < n; i++)
	{
		cin >> node1 >> node2 >> node3;
		if (node2 != '.')	lc[node1] = node2;
		if (node3 != '.')	rc[node1] = node3;
	}
	preorder('A');
	cout << '\n';
	Inorder('A');
	cout << '\n';
	Postorder('A');

}
```