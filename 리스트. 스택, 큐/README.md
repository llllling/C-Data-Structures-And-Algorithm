# 리스트, 스택, 큐
## 연속된 자료 구조 
* std::array 
* std::vector
	* C 스타일 배열, std::array가 가지고 있는 '고정 크기' 문제 해결
	* push_back(), insert()함수의 단점  :  이들 함수가 추가할 원소를 먼저 임시로 생성한 후, 버퍼 내부 위치로 복사 또는 이동을 수행
	* emplace_back(), emplace() 함수 : 위와 같은 단점을 해결, 이 함수를 사용하면 새 원소 위치에 곧바로 객체가 생성되도록 최적화 됨
## 연결된 자료 구조
* std::forward_list
	* push_front(), insert_back() : 추가할 원소를 먼저 임시로 생성한 후, 버퍼 내부 위치로 복사 또는 이동을 수행
	* emplace_front(), emplace_after() : 추가적인 복사 필요X