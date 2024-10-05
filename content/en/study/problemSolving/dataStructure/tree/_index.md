---
title: 📜TREE September 2022~December 2022
hide_date: true
reading_time: false
date: 2022-09-01
---

- Definition of Tree: An undirected acyclic connected graph, which is a type of graph. Unlike the linear structures such as stacks, queues, and lists that we have studied earlier, a tree has a **hierarchical structure**.
    ![Figure1](/images/dataStructureImages/image1.jpg)

- Characteristics:
    1. → By definition, it is not related to hierarchy, and note that a graph with a single vertex and no edges is also considered a tree.
    2. A connected graph that becomes disconnected if any edge is removed (see Figure 1).
    3. A connected graph with V vertices has V - 1 edges. >> The reason for V - 1 is that if a connected graph has V or more edges, it forms a cycle.
    4. **In summary: A tree with V vertices has V - 1 edges, and there is a unique simple path connecting any two points, with no self-loops.**

- Terminology:
    → **Subtree**: A tree is a finite set of nodes with one node designated as the root, and all remaining nodes form the **subtree**.

    → **Root Node**: The node at the top of the tree that has no parent.

    → **Leaf Node**: A node with no children, also called a terminal node.

- Definition of Binary Tree: A tree where each node has at most two children.
    - Characteristics:
        1. The key (value) stored in each node of the binary search tree is unique.
        2. The parent node's key is greater than the left child node's key.
        3. The parent node's key is smaller than the right child node's key.
        4. The left and right subtrees are also binary search trees.
        5. A tree with n nodes has n - 1 edges.
        
        Note: The equation **Total number of nodes = 2^k - 1** applies only to full binary trees, so always check whether it's a full binary tree before using the equation.

        ![Figure3](/images/dataStructureImages/image3.jpg)

- Tree Representation (General Tree vs. Binary Tree):
    - A general tree can have n children, whereas a binary tree can have at most 2 children.

    Keep in mind that in a general tree, multiple child nodes can create a cycle.
    ![Figure2](/images/dataStructureImages/image2.jpg)

- Perfect Binary Tree:
    - Characteristics:
        1. A tree where all levels are fully filled with nodes.
        2. **It must also satisfy the properties of a binary tree, meaning all nodes have either 0 or 2 children.**
        3. **All leaf nodes have the same depth or level.**
        4. The total number of nodes is exactly 2^k - 1, where k is the height (or level) of the tree.
    ![Figure5](/images/dataStructureImages/image5.jpg)

- Complete Binary Tree:
    - Characteristics:
        1. A binary tree where all levels are fully filled except possibly the last level, which is filled from left to right.
        2. If the last level is completely filled, it is a perfect binary tree. In a complete binary tree, there are no gaps between nodes.
    ![Figure6](/images/dataStructureImages/image6.jpg)

- Traversals of a Binary Tree:
    - Level-order Traversal:
        - This traversal visits nodes level by level, from top to bottom.

        ```cpp
        //Binary Tree Traversal -> Level-order Traversal

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

        int main()
        {
        	bfs();
        }
        ```

    - Preorder Traversal:
        - Visit order:
            1. Visit the current node.
            2. Preorder traversal of the left subtree.
            3. Preorder traversal of the right subtree.

        ```cpp
        //Binary Tree Traversal -> Preorder Traversal

        #include <iostream>
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

    - Inorder Traversal:
        - Visit order:
            1. Inorder traversal of the left subtree.
            2. Visit the current node.
            3. Inorder traversal of the right subtree.

        ```cpp
        //Binary Tree Traversal -> Inorder Traversal

        #include <iostream>
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

    - Postorder Traversal:
        - Visit order:
            1. Postorder traversal of the left subtree.
            2. Postorder traversal of the right subtree.
            3. Visit the current node.

        ```cpp
        //Binary Tree Traversal -> Postorder Traversal

        #include <iostream>
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

    - **Even if the traversal method differs, the traversal results may match.**

- Various Member Functions of a Binary Tree:
    
    ```cpp
    	int getLeafCount() // Function to get the number of leaf nodes in a binary tree
    	{
    		return isEmpty() ? 0 : getLeafCount(root);
    	}
    	int getLeafCount(BinaryNode* node)
    	{
    		if (node == NULL)		return 0;
    		if (node->isLeaf())		return 1;
    		else
    			return getLeafCount(node->getLeft()) + getLeafCount(node->getRight());
    	}
    ```

    ```cpp
    // Example code from a book
    
    	int getHeight() // Function to get the height of the binary tree
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
    
    // Example code I wrote
    	int height(BinaryNode* root) // Function to get the height of the binary tree
    	{
    		if (root == nullptr)
    			return 1;
    		int left_height = height(root->getLeft());
    		int right_height = height(root->getRight());
    		return 1 + max(left_height, right_height);
    	}
    ```

- Tree Search:

    Scenarios:
    
    1. If the key matches, the search is successful.
    2. If the key is smaller than the root node's key, search the left subtree.
    3. If the key is larger than the root node's key, search the right subtree.

- Implementing Search Functions (Iterative, Recursive):
    - Both functions compare the current node's data with the search key to locate the desired node.

    ```cpp
    	// Function to search for a node by key (iterative method)
    	BinaryNode* searchIter(BinaryNode* n, int key)
    	{
    		while (n != NULL)
    		{
    			if (key == n->getData())	return n;
    			else if (key < n->getData())	n = n->getLeft();
    			else
    				n = n->getRight();
    		}
    		return NULL;
    	}
    ```

    ```cpp
    	// Function to search for a node by key (recursive method)
    	BinaryNode* searchRecur(BinaryNode* n, int key)
    	{
    		if (n == NULL)					return NULL;
    		if (key == n->getData())		return n;
    		else if (key < n->getData())	return searchRecur(n->getLeft(), key);
    		else
    			return searchRecur(n->getRight(), key);
    	}
    ```

- Implementing Insertion Functions (Iterative, Recursive):

    ```cpp
    // Recursive method from a book
    void insertRecur(BinaryNode* r, BinaryNode* n)
    {
        if (n->getData() == r->getData())	return;
        else if (n->getData() < r->getData())
        {
            if (r->getLeft() == NULL)
                r->setLeft(n);
            else
                insertRecur(r->getLeft(), n);
        }
        else
        {
            if (r->getRight() == NULL)
                r->setRight(n);
            else
                insertRecur(r->getRight(), n);
        }
    }

    // Example code I wrote
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

- Implementing Deletion Functions (Iterative, Recursive):
    - Considerations:
        1. **The node to be deleted is a leaf node.**
        2. **The node to be deleted has only one child (left or right subtree).**
        3. **The node to be deleted has both left and right subtrees.**

    ```cpp
    void remove(BinaryNode* parent, BinaryNode* node)
    {
        if (node->isLeaf())
        {
            if (parent == NULL)	root = NULL;
            else
            {
                if (parent->getLeft() == node)	parent->setLeft(NULL);
                else
                    parent->setRight(NULL);
            }
        }
        else if (node->getLeft() == NULL || node->getRight() == NULL)
        {
            BinaryNode* child = (node->getLeft() != NULL) ? node->getLeft() : node->getRight();

            if (node == root)	root = child;
            else
            {
                if (parent->getLeft() == node)	parent->setLeft(child);
                else
                    parent->setRight(child);
            }
        }
        else
        {
            BinaryNode* sucp = node;
            BinaryNode* succ = node->getRight();
            while (succ->getLeft() != NULL)
            {
                sucp = succ;
                succ = succ->getLeft();
            }

            if (sucp->getLeft() == succ)
                sucp->setLeft(succ->getRight());
            else
                sucp->setRight(succ->getRight());

            node->setData(succ->getData());
            node = succ;
        }
        delete node;
    }
    ```

	- Problem Example:

		```cpp
		// BFS Example Code 1 - Filling the Parent Array
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
					p[nxt] = cur;
				}
			}
		}
		```

		```cpp
		// BFS Example Code 2 - Filling Parent and Depth Arrays
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
			int depth[10];
			queue<int> q;
			q.push(root);
			while (!q.empty())
			{
				int cur = q.front();
				q.pop();
				cout << cur << ' ';

				for (auto nxt : adj[cur])
				{
					if (p[cur] == nxt)	continue;
					q.push(nxt);
					p[nxt] = cur;
					depth[nxt] = depth[cur] + 1;
				}
			}
		}
		```

		```cpp
		#include <iostream>
		#include <stack>
		#include <vector>
		using namespace std;

		// DFS Example Code 1 - Filling Parent and Depth Arrays (Non-recursive)
		void dfs()
		{
			int root;
			cin >> root;
			vector<int> adj[10];
			int p[10];
			int depth[10];
			stack<int> s;
			s.push(root);
			while (!s.empty())
			{
				int cur = s.top();
				s.pop();
				cout << cur << ' ';

				for (auto nxt : adj[cur])
				{
					if (p[cur] == nxt)	continue;
					s.push(nxt);
					p[nxt] = cur;
					depth[nxt] = depth[cur] + 1;
				}
			}
		}
		```

		```cpp
		#include <iostream>
		#include <stack>
		#include <vector>
		using namespace std;

		// DFS Example Code 2 - Filling Parent and Depth Arrays (Recursive)
		vector<int> adj[10];
		int p[10];
		int depth[10];

		void dfs(int cur)
		{
			cout << cur << ' ';
			for (auto nxt : adj[cur])
			{
				if (p[cur] == nxt)	continue;
				p[nxt] = cur;
				depth[nxt] = depth[cur] + 1;
				dfs(nxt);
			}
		}
		// call dfs(1, 0);
		```

		```cpp
		// DFS Example Code 3 - Simple Traversal (Recursive)
		#include <iostream>
		#include <stack>
		#include <vector>
		using namespace std;

		vector<int> adj[10];
		int p[10];
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
		// call dfs(1, 0);
		```
