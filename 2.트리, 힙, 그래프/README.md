# 트리, 힙, 그래프

비선형 자료 구조
## 선형 자료 구조로 표현할 수 없는 대표적인 문제
* 계층적 문제와 순환 종속성 문제가 있다.
### 계층적 문제
 * 조직도
 * 대학의 일부 과정(과목에 관한 것)
 * 이러한 문제를 해결 하기 위해 트리 사용
### 순환 종속성
* 친구 관계
* 이러한 문제를 해결하기 위해 그래프 사용

## 트리
* 노드와 노드 사이를 연결하는 에지를 이용하여 계층을 구성함.
    * 노드 : 데이터가 저장된 부분
    * 에지 : 노드와 노드를 잇는 선
#### 이진 트리
* 각각의 노드는 다른 두 개의 노드(하위 노드)에 대한 링크를 가진다.
* 아래처럼 구조체를 정의해서 코드 구현
```c++
struct node
{
	std::string position;
	node* first;
	node* second;
};
```

### 트리 순회
현재 노드를 중심으로 생각하라!
#### 전위 순회(preorder traversal)
* 현재 노드를 먼저 방문 > 현재 노드의 왼쪽 하위 노드 > 현재 노드의 오른쪽 하위 노드 순으로 방문
* 전위 : 상위 노드를 하위 노드보다 먼저 방문한다는 뜻!
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
#### 중위 순회(in-order traversal)
* 왼쪽 노드 > 현재 노드 > 오른쪽 노드
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
#### 후외 순회(post-order traversal)
* 왼쪽 노드 > 오른쪽 노드 > 현재 노드
* 즉, 두 자식 먼저 방문
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
### 레벨 순서 순회(level order traversal)
* 트리의 맨 위 레벨부터 아래 레벨까지, 왼쪽 노드에서 오른쪽 노드 순서로 방문
* 즉, 트리의 루트 노드부터 **단계별로** 차례대로 나열하는 것과 같다.
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
### 다양한 트리 구조
#### 이진 검색 트리(BST, Binary Search Tree)
* 널리 사용되는 형태의 이진 트리이다.
* 다음과 같은 속성이 있음.
    * 부모 노드의 값 >= 왼쪽 자식 노드의 값
	* 부모 노드의 값 <= 오른쪽 자식 노드의 값
* 이와 같은 속성때문에 원소 검색을 위해 루트 노드부터 차례대로 값을 비교하는 경우, 각 단계마다 검색 범위가 절반으로 줄어듬.
* BST가 마지막 레벨을 제외한 모든 노드에 두 개의 자식 노드가 있을 경우, **이 트리의 높이는 logN이 된다.**
* 이로 인해 BST의 검색 및 삽입 동작은 O(log N)의 시간 복잡도를 가짐. => 이러한 형태의 이진 트리를 완전 이진 트리라고 함.
##### BST에서 원소 삭제하기
* 자식 노드가 없는 경우 : 단순히 해당 노드를 삭제
* 자식 노드가 하나만 있는 경우 : 노드 삭제 후, 부모 노드의 포인터가 해당 자식 노드를 가리키도록 조정
* 자식 노드가 두 개 있는 경우 : 노드 삭제 후, 현재 노드를 후속 노드(successor)로 대체함.
    * **후속 노드 : 현재 노드 다음으로 큰 숫자를 가진 노드를 의미** => 즉, 현재 원소보다 큰 원소들 중에서 가장 작은 원소를 의미!
#### 트리 연산의 시간 복잡도
* 검색의 경우 이론적으로 매번 검색 범위가 절반으로 줄어든다고 보면 된다.
*  <span style="background-color: yellow; color: black;">N개의 노드를 가지고 있는 BST에서 검색에 필요한 시간 => T(N) = T(N/2) + 1 수식으로 표현. 이를 시간 복잡도 표현으로 T(N) = O(log N)</span>
    *  <span style="background-color: gray; color: black;">하지만 ! 항상 정확하지 않다 => 트리 모양이 원소 삽입 순서에 따라 결정되므로, 균형트리가 아닌 경우 정확 X </span>
#### 균형 트리(balaced tree)
* 편향되지 않은 상태의 트리
* 원소의 검색의 시간 복잡도를 최적화하려면 트리의 높이가 최적화 되어야 함. => 이러한 작업을 트리 균형 잡기
* 트리의 균형을 잡기 위해서는 원소 삽입 또는 삭제 후에는 트리 구성을 조정해야 함 => 조정되어 편향성이 줄어든 이진 검색 트리를 높이-균형 BST(height-balances BST)라고 함.
* 트리의 균형을 잡는 방법  : AVL 트리, 레드-블랙 트리
#### N-항 트리(N-ary tree)
* 각 노드가 N개의 자식을 가지는 것
```c++
struct nTree
{
	int data;
	std::vector<nTree*> children;
};
```
* 컴퓨터 분야에서 N-항 트리를 사용하는 대표적인 예
    * 컴퓨터 파일 시스템 구조 : 리눅스에서는 루트(/)부터  시작해서 다수의 파일과 폴더를 가질 수 있다.
	* 컴파일러 : 추상 구문 트리
## 힙
* 특별한 형태의 트리
* 다음과 같은 시간 복잡도를 만족해야 함.
    * O(1) : 최대 원소에 즉각적으로 접근할 수 있어야 함.
	* O(log N) : 원소 삽입에 대한 시간 복잡도
	* O(log N) : 최대 원소 삭제에 대한 시각 복잡도
* 원소 삽입/삭제에 O(log N)의 시간 복잡도를 만족하기 위해 완전 이진 트리 구조를 사용해야 함!
    * <span style="background-color: yellow; color: black;">완전 이진 트리  : 마지막 레벨의 노드를 제외하고는 모두 두 개의 자식 노드가 있고, 마지막 레벨에서는 왼쪽부터 차례대로 노드가 있는 트리</span>
* **힙의 가장 중요한 불변성**은 완전 이진 트리를 유지해야 한다는 점!!
* 최대 힙 : 항상 최대 원소가 트리의 루트에 있도록
* 최소 힙 : 항상 최소 원소가 트리의 루트에 있도록
###  힙 연산
#### 힙 초기화 하기
* c++ 표준은 배열 또는 벡터의 반복자를 인자로 받아 힙을 구성하는 std::make_heap() 함수를 제공한다.
## 그래프 
* 하나의 노드에서 다른 노드로 이동하는 경로가 여러개 존재
* 노드 데이터뿐만 아니라 에지 데이터도 저장해야 함.
* 비가중 그래프 : 에지에 가중치가 없는 것
    * 도로망 
* 가중 그래프 : 에지에 가중치 주는 것
    * 도로망을 가중 그래프로 표현함으로써 최단 거리 경로 탐색같은 문제에서 사용 가능
* 무방향 그래프  : 방향성이 없는 그래프, 에지가 양방향임을 의미
* 방향 그래프 
* <span style="background-color: yellow; color: black;">그래프 탐색</span>
    * 너비 우선 탐색(BFS)
	* 깊이 우선 탐색(DFS)
### 인접 행렬로 그래프 표현
* 행렬을 이용하면 노드 개수의 제곱에 비례하는 메모리를 사용한다는 점이 문제점이다. => 노드 개수 증가에 따라 메모리 사용량이 증가
* 두 노드가 서로 연결되어 있지 않더라도 모든 노드 사이의 에지 정보를 저장해야 함.
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
### 인접 리스트로 그래프 표현
* 직접 연결되어 있는 노드의 ID만 저장하는 방식
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