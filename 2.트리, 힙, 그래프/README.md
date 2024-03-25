# Ʈ��, ��, �׷���

���� �ڷ� ����
## ���� �ڷ� ������ ǥ���� �� ���� ��ǥ���� ����
* ������ ������ ��ȯ ���Ӽ� ������ �ִ�.
### ������ ����
 * ������
 * ������ �Ϻ� ����(���� ���� ��)
 * �̷��� ������ �ذ� �ϱ� ���� Ʈ�� ���
### ��ȯ ���Ӽ�
* ģ�� ����
* �̷��� ������ �ذ��ϱ� ���� �׷��� ���

## Ʈ��
* ���� ��� ���̸� �����ϴ� ������ �̿��Ͽ� ������ ������.
    * ��� : �����Ͱ� ����� �κ�
    * ���� : ���� ��带 �մ� ��
#### ���� Ʈ��
* ������ ���� �ٸ� �� ���� ���(���� ���)�� ���� ��ũ�� ������.
* �Ʒ�ó�� ����ü�� �����ؼ� �ڵ� ����
```c++
struct node
{
	std::string position;
	node* first;
	node* second;
};
```

### Ʈ�� ��ȸ
���� ��带 �߽����� �����϶�!
#### ���� ��ȸ(preorder traversal)
* ���� ��带 ���� �湮 > ���� ����� ���� ���� ��� > ���� ����� ������ ���� ��� ������ �湮
* ���� : ���� ��带 ���� ��庸�� ���� �湮�Ѵٴ� ��!
```c++
	static void preOrder(node* start)
	{
		if (!start)
			return;

		std::cout << start->position << ", ";
		preOrder(start->first);
		preOrder(start->second);
	}
```
#### ���� ��ȸ(in-order traversal)
* ���� ��� > ���� ��� > ������ ���
```c++
	static void inOrder(node* start)
	{
		if (!start)
			return;

		inOrder(start->first);
		std::cout << start->position << ", ";
		inOrder(start->second);
	}
```
#### �Ŀ� ��ȸ(post-order traversal)
* ���� ��� > ������ ��� > ���� ���
* ��, �� �ڽ� ���� �湮
```c++
	static void postOrder(node* start)
	{
		if (!start)
			return;

		postOrder(start->first);
		postOrder(start->second);
		std::cout << start->position << ", ";
	}
```
### ���� ���� ��ȸ(level order traversal)
* Ʈ���� �� �� �������� �Ʒ� ��������, ���� ��忡�� ������ ��� ������ �湮
* ��, Ʈ���� ��Ʈ ������ **�ܰ躰��** ���ʴ�� �����ϴ� �Ͱ� ����.
```c++
	static void levelOrder(node* start)
	{
		if (!start)
			return;

		std::queue<node*> q;
		q.push(start);

		while (!q.empty())
		{
			int size = q.size();
			for (int i = 0; i < size; i++)
			{
				auto current = q.front();
				q.pop();

				std::cout << current->position << ", ";
				if (current->first)
					q.push(current->first);
				if (current->second)
					q.push(current->second);
			}

			std::cout << std::endl;
		}
	}
```
### �پ��� Ʈ�� ����
#### ���� �˻� Ʈ��(BST, Binary Search Tree)
* �θ� ���Ǵ� ������ ���� Ʈ���̴�.
* ������ ���� �Ӽ��� ����.
    * �θ� ����� �� >= ���� �ڽ� ����� ��
	* �θ� ����� �� <= ������ �ڽ� ����� ��
* �̿� ���� �Ӽ������� ���� �˻��� ���� ��Ʈ ������ ���ʴ�� ���� ���ϴ� ���, �� �ܰ踶�� �˻� ������ �������� �پ��.
* BST�� ������ ������ ������ ��� ��忡 �� ���� �ڽ� ��尡 ���� ���, **�� Ʈ���� ���̴� logN�� �ȴ�.**
* �̷� ���� BST�� �˻� �� ���� ������ O(log N)�� �ð� ���⵵�� ����. => �̷��� ������ ���� Ʈ���� ���� ���� Ʈ����� ��.
##### BST���� ���� �����ϱ�
* �ڽ� ��尡 ���� ��� : �ܼ��� �ش� ��带 ����
* �ڽ� ��尡 �ϳ��� �ִ� ��� : ��� ���� ��, �θ� ����� �����Ͱ� �ش� �ڽ� ��带 ����Ű���� ����
* �ڽ� ��尡 �� �� �ִ� ��� : ��� ���� ��, ���� ��带 �ļ� ���(successor)�� ��ü��.
    * **�ļ� ��� : ���� ��� �������� ū ���ڸ� ���� ��带 �ǹ�** => ��, ���� ���Һ��� ū ���ҵ� �߿��� ���� ���� ���Ҹ� �ǹ�!
#### Ʈ�� ������ �ð� ���⵵
* �˻��� ��� �̷������� �Ź� �˻� ������ �������� �پ��ٰ� ���� �ȴ�.
*  <span style="background-color: yellow; color: black;">N���� ��带 ������ �ִ� BST���� �˻��� �ʿ��� �ð� => T(N) = T(N/2) + 1 �������� ǥ��. �̸� �ð� ���⵵ ǥ������ T(N) = O(log N)</span>
    *  <span style="background-color: gray; color: black;">������ ! �׻� ��Ȯ���� �ʴ� => Ʈ�� ����� ���� ���� ������ ���� �����ǹǷ�, ����Ʈ���� �ƴ� ��� ��Ȯ X </span>
#### ���� Ʈ��(balaced tree)
* ������� ���� ������ Ʈ��
* ������ �˻��� �ð� ���⵵�� ����ȭ�Ϸ��� Ʈ���� ���̰� ����ȭ �Ǿ�� ��. => �̷��� �۾��� Ʈ�� ���� ���
* Ʈ���� ������ ��� ���ؼ��� ���� ���� �Ǵ� ���� �Ŀ��� Ʈ�� ������ �����ؾ� �� => �����Ǿ� ���⼺�� �پ�� ���� �˻� Ʈ���� ����-���� BST(height-balances BST)��� ��.
* Ʈ���� ������ ��� ���  : AVL Ʈ��, ����-�� Ʈ��
#### N-�� Ʈ��(N-ary tree)
* �� ��尡 N���� �ڽ��� ������ ��
```c++
struct nTree
{
	int data;
	std::vector<nTree*> children;
};
```
* ��ǻ�� �о߿��� N-�� Ʈ���� ����ϴ� ��ǥ���� ��
    * ��ǻ�� ���� �ý��� ���� : ������������ ��Ʈ(/)����  �����ؼ� �ټ��� ���ϰ� ������ ���� �� �ִ�.
	* �����Ϸ� : �߻� ���� Ʈ��
## ��
* Ư���� ������ Ʈ��
* ������ ���� �ð� ���⵵�� �����ؾ� ��.
    * O(1) : �ִ� ���ҿ� �ﰢ������ ������ �� �־�� ��.
	* O(log N) : ���� ���Կ� ���� �ð� ���⵵
	* O(log N) : �ִ� ���� ������ ���� �ð� ���⵵
* ���� ����/������ O(log N)�� �ð� ���⵵�� �����ϱ� ���� ���� ���� Ʈ�� ������ ����ؾ� ��!
    * <span style="background-color: yellow; color: black;">���� ���� Ʈ��  : ������ ������ ��带 �����ϰ�� ��� �� ���� �ڽ� ��尡 �ְ�, ������ ���������� ���ʺ��� ���ʴ�� ��尡 �ִ� Ʈ��</span>
* **���� ���� �߿��� �Һ���**�� ���� ���� Ʈ���� �����ؾ� �Ѵٴ� ��!!
* �ִ� �� : �׻� �ִ� ���Ұ� Ʈ���� ��Ʈ�� �ֵ���
* �ּ� �� : �׻� �ּ� ���Ұ� Ʈ���� ��Ʈ�� �ֵ���
###  �� ����
#### �� �ʱ�ȭ �ϱ�
* c++ ǥ���� �迭 �Ǵ� ������ �ݺ��ڸ� ���ڷ� �޾� ���� �����ϴ� std::make_heap() �Լ��� �����Ѵ�.
## �׷��� 
* �ϳ��� ��忡�� �ٸ� ���� �̵��ϴ� ��ΰ� ������ ����
* ��� �����ͻӸ� �ƴ϶� ���� �����͵� �����ؾ� ��.
* ���� �׷��� : ������ ����ġ�� ���� ��
    * ���θ� 
* ���� �׷��� : ������ ����ġ �ִ� ��
    * ���θ��� ���� �׷����� ǥ�������ν� �ִ� �Ÿ� ��� Ž������ �������� ��� ����
* ������ �׷���  : ���⼺�� ���� �׷���, ������ ��������� �ǹ�
* ���� �׷��� 
* <span style="background-color: yellow; color: black;">�׷��� Ž��</span>
    * �ʺ� �켱 Ž��(BFS)
	* ���� �켱 Ž��(DFS)
### ���� ��ķ� �׷��� ǥ��
* ����� �̿��ϸ� ��� ������ ������ ����ϴ� �޸𸮸� ����Ѵٴ� ���� �������̴�. => ��� ���� ������ ���� �޸� ��뷮�� ����
* �� ��尡 ���� ����Ǿ� ���� �ʴ��� ��� ��� ������ ���� ������ �����ؾ� ��.
```c++
struct graph
{
	std::vector<std::vector<int>> data;

	graph(int n)
	{
		data.reserve(n);
		std::vector<int> row(n);
		std::fill(row.begin(), row.end(), -1);

		for (int i = 0; i < n; i++)
		{
			data.push_back(row);
		}
	}

	void addEdge(const city c1, const city c2, int dis)
	{
		auto n1 = static_cast<int>(c1);
		auto n2 = static_cast<int>(c2);
		data[n1][n2] = dis;
		data[n2][n1] = dis;
	}

	void removeEdge(const city c1, const city c2)
	{
		auto n1 = static_cast<int>(c1);
		auto n2 = static_cast<int>(c2);
		data[n1][n2] = -1;
		data[n2][n1] = -1;
	}
};
```
### ���� ����Ʈ�� �׷��� ǥ��
* ���� ����Ǿ� �ִ� ����� ID�� �����ϴ� ���
```c++
struct graph
{
	std::vector<std::vector<std::pair<int, int>>> data;

	graph(int n)
	{
		data = std::vector<std::vector<std::pair<int, int>>>(n, std::vector<std::pair<int, int>>());
	}

	void addEdge(const city c1, const city c2, int dis)
	{
		auto n1 = static_cast<int>(c1);
		auto n2 = static_cast<int>(c2);
		data[n1].push_back({n2, dis});
		data[n2].push_back({n1, dis});
	}

	void removeEdge(const city c1, const city c2)
	{
		auto n1 = static_cast<int>(c1);
		auto n2 = static_cast<int>(c2);
		std::remove_if(data[n1].begin(), data[n1].end(), [n2](const auto& pair) {
			return pair.first == n2;
			});
		std::remove_if(data[n2].begin(), data[n2].end(), [n1](const auto& pair) {
			return pair.first == n1;
			});
	}
};
```