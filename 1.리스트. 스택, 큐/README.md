# 리스트, 스택, 큐

선형 자료 구조, 최대 두가지 방향(순방향과 역방향)으로 자료를 순회할 수 있다.
## 리스트

### 연속된 자료 구조

- std::array
- std::vector
  - C 스타일 배열, std::array가 가지고 있는 **'고정 크기' 문제 해결**
  - push_back(), insert()함수의 단점 : 이들 함수가 추가할 원소를 먼저 임시로 생성한 후, 버퍼 내부 위치로 복사 또는 이동을 수행
  - emplace_back(), emplace() 함수 : 위와 같은 단점을 해결, 이 함수를 사용하면 새 원소 위치에 곧바로 객체가 생성되도록 최적화 됨

### 연결된 자료 구조

- std::forward_list
  - push_front(), insert_back() : 추가할 원소를 먼저 임시로 생성한 후, 버퍼 내부 위치로 복사 또는 이동을 수행
  - emplace_front(), emplace_after() : 추가적인 복사 필요X
  - 아주 기본적인 형태로 구현된 연결 리스트
  - 메모리를 적게쓰고 빠른 성능을 유지하기 위해 리스트 끝에 원소추가/역방향 이동/리스트 크기 반환 등의 기능 제공 X
  - 매우 적은 기능만 지원
- std::list
  - std::forward_list의 단점을 보완하기 위해 제공됨.
  - 양쪽 방향으로 연결된 연결 리스트 => 이중 연결 리스트 구조
  - std::forward_list에 비해 더 많은 기능을 제공하는 만큼 메모리를 좀 더 사용함.
  - 맨 마지막 원소와 리스트 크기를 따로 저장해서 push_back(), size() 같은 함수 지원

## 큐

- **std::deque**
  - 배열 기반과 연결 리스트 기반 컨테이너 방식이 섞여 있는 형태이며 각각의 장점을 적당히 가지고 있다.
  - push_front(), pop_front(), push_back(), pop_back() 동작이 O(1)
  - **모든 원소에 대한 임의 접근이 O(1)**
  - 덱 중간에 원소 삽입 또는 삭제는 O(n) 시간 복잡도로 동작, 실제로는 최대 n/2 단계로 동작(n은 덱의 크기)
  - **자료 구조가 벡터와 비슷하지만, 앞쪽과 뒤쪽으로 모두 확장할 수 있다는 점이 다르다.**

* std::queue
* std::priority_queue

  - 힙이라고 부르는 매우 유용한 구조를 제공함.
    ```
      힙은 컨테이너에서 가장 작은(또는 가장 큰) 원소에 빠르게 접근할 수 있는 자료구조
    ```

  * 최소/최대 원소에 접근하는 동작은 O(1)의 시간 복잡도를 가짐.
  * 원소 삽입은 O(log n)시간 복잡도로 동작
  * 원소 제거는 최소/최대 원소에 대해서만 가능
  * 유의해야 할 점은 최대 또는 최소 둘 중 하나에 대해서만 적용할 수 있으며, 최대와 최소에 한꺼번에 빠르게 접근할 수 없다.
    - 최대/최소 어느 것에 빠르게 접근할 것인지는 컨테이너 비교자에 의해 결정
    * 비교자는 기본적으로 std::less를 사용함. 그러므로 기본적으로 최대 힙으로 생성되며 최대 원소가 맨 위에 나타나게 됨을 의미
  * std::stack, std::queue와 달리 기본적으로 std::vector을 기본 컨테이너로 사용하며, 필요한 경우 변경 가능

## 스택

- std::stack

## ETC

- **컨테이너 어댑터** : std::stack은 std::deque로 만든 간단한 래퍼로서 스택 자료 구조에 필요한 인터페이스만을 제공함. 이러한 방식으로 만들어진 것을 컨테이너 어댑터라고 함.
  - std::stack, std::queue, std::priority_queue가 있다.
  * **어댑터에 대해서는 반복자를 지원하지 않는다**
    - 각가의 자료 구조에서 꼭 필요한 기능만 지원함. 스택, 큐, 우선순위 큐에서 모든 원소를 순회하는 작업을 할 필요가 없다. 언제든 특정 위치에 있는 원소 하나만 참조할 수 있으면 된다. 그래서 반복자를 지원 안함
