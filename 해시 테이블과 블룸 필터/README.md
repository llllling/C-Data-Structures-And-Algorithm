# 해시 테이블과 블룸 필터
* 대용량 데이터를 다루는 응용 프로그램에서 발생할 수 있는 룩업 관련 문제에 대해 이해할 수 있다.
* <span style="background-color: yellow; color: black;">룩업(lookup, 조회)</span> : 특정 원소가 컨테이너에 있는지 확인하거나 또는 컨테이너에서 특정 키에 해당하는 값을 찾는 작업을 의미
*  모든 원소를 선형으로 검토하여 원하는 값을 찾는 작업은 일반적으로 매우 많은 시간이 소요됨. => 저장된 데이터가 많아질수록 검색 시간은 크게 증가함.
## 해시 테이블
* 해싱 : 각각의 데이터를 가급적 고유한 숫자 값으로 표현하고, 나중에 같은 숫자 값을 사용하여 데이터의 유무를 확인하거나 또는 해당 숫자에 대응하는 원본 데이터를 추출하는 작업
* 해시 함수  : 주어진 데이터로부터 고유한 숫자 값을 계산하는 함수
### 체이닝 
* 다수의 키가 같은 해시 값을 갖는 경우 충돌 문제 발생
* 체이닝이란 => 해시 테이블의 특정 위치에서 하나의 키를 저장하는 것이 아니라 하나의 연결 리스트를 저장한다.
    * 벡터 대신 연결리스트를 사용하는 이유 : 특정 위치의 원소를 빠르게 삭제하기 위함

```c++
class hash_map
{
	std::vector<std::list<int>> data;

	public:
		hash_map(size_t n)
		{
			data.resize(n);
		}

		void insert(uint value)
		{
			int n = data.size();
			data[value % n].push_back(value);
			std::cout << value << "을(를) 삽입했습니다." << std::endl;
		}

		bool find(uint value)
		{
			int n = data.size();
			auto& entries = data[value % n];
			return std::find(entries.begin(), entries.end(), value) != entries.end();
		}

		void erase(uint value)
		{
			int n = data.size();
			auto& entries = data[value % n];
			auto iter = std::find(entries.begin(), entries.end(), value);

			if (iter != entries.end())
			{
				entries.erase(iter);
				std::cout << value << "을(를) 삭제했습니다." << std::endl;
			}
		}
	};
}
```
* 삽입 함수의 시간 복잡도 O(1)
* 룩업과 삭제는 데이터 크기와 해시 테이블 크기에 따라 상당히 느릴 수 있다. 
    * 예를 들어 모든 키가 같은 해시 값을 가질 경우, 룩업 연산은 연결 리스트에서 선형 검색을 수행한느 것과 같으므로 O(N)의 시간 복잡도를 가짐.</span>
* <span style="background-color: yellow; color: black;">만약 해시 테이블이 저장할 키 개수에 비해 매우 작다면 충돌이 많이 발생, 리스트는 평균적으로 더 길어짐.
* <span style="background-color: yellow; color: black;">반면에, 너무 큰 해시 테이블을 가지고 있다면 실제 데이터는 듬성듬성 존재하게 되므로 메모리 낭비가 발생</span>
* 응용프로그램 동작 시나리오를 고려하여 해시 테이블 크기를 적절히 조절해야 한다. => 이를 위한 수식을 하나 정의할 수 있다.
#### 부하율 
* 해시 테이블에서 각각의 리스트에 저장되는 키의 평균 개수를 나타냄.
```
         전체 키 개수
부하율 = -------------
        해시 테이블 크기
```
* 만약 키 개수가 해시 테이블 크기와 같다면 부하율은 1 => 매우 이상적인 상태로, 모든 연산이이 O(1)에 가깝게 작동하고 모든 메모리 공간을 적절하게 활용함.
* 부하율이 1보다 작으면 리스트당 키가 하나도 저장되지 않은 경우가 있다는 것이고, 메모리 낭비될 수 있음.
* 부하율이 1보다 크면 리스트의 평균 길이가 1보다 크다는 의미. 검색, 삭제 등의 함수가 약간 느리게 동작할 수 있다.
* 부하율은 항상 O(1) 시간 복잡도로 계산할 수 있음.