# ���� ����
���� ������ �˸�
* ���� �˻�, ���� ����, �� ����, ��� �˻�, ���� �ð� ���� ���� ��ǥ���� ���� ���� �˰��� ���� ����
* �ʸ��ེ ���α׷��� ���� ����Ͽ� ���� �ذ� ����
* ��Ƽ�����带 ����ϴ� C++ �ʸ��ེ ���̺귯���� ��� ����� ��� �� �ִ�.
```
���� ���� ������ �˰����� �־��� ������ ���� �κ� ������ ������,
������ �� �κ� ������ �ַ���� ���ϰ�, 
�� �κ� ���� �ַ���� ���ļ� ��ü ������ ���� �ַ���� ���ϴ� ���
```
* ���� ������ 3�ܰ�
    * ����(divide) : �־��� ������ ������ ������� �ذ��� �� �ִ� ���� �κ� ������ ������.
    * ����(conquer) : �� �κ� ������ ���� �ش��� ���Ѵ�.
    * ����(combine) : �� �κ� ������ �ش��� �����Ͽ� ��ü ������ ���� �ش��� ���Ѵ�.
## ���� ���� ����� C++ǥ�� ���̺귯�� �Լ�
* �Ʒ� �����ϴ� �Լ��� ������ ���� ������ �ʿ� ���� c++������ �Ʒ� ǥ ó�� �̸� ���ǵ� ������ �˰��� �Լ� ������
<table>
	<tr>
		<th>STL �Լ�</th>
		<th>�Լ� ����</th>
	</tr>
	<tr>
		<td>std::binary_search()</td>
		<td>���� �˻��� �̿��Ͽ� �����̳ʿ��� ���� �ϳ��� ã�´�.</td>
	</tr>
	<tr>
		<td>std::search()</td>
		<td>�����̳ʿ��� �Ϸ��� ���ҵ��� ã�´�.</td>
	</tr>
	<tr>
		<td>std::upper_bound()</td>
		<td>�����̳ʿ��� �־��� ������ ū ���Ұ� ��Ÿ���� �����ϴ� ��ġ�� �ݺ��ڸ� ��ȯ�Ѵ�.</td>
	</tr>
	<tr>
		<td>std::lower_bound()</td>
		<td>�����̳ʿ��� �־��� ������ ���� ���Ұ� ��Ÿ���� �����ϴ� ��ġ�� �ݺ��ڸ� ��ȯ�Ѵ�.</td>
	</tr>
	<tr>
		<td>std::partition()</td>
		<td>���� ������ �����ϰ�, �־��� �ǹ����� ���� ���Ҵ� �ǹ� �������� �ű�� �ǹ����� ū ���Ҵ� �ǹ� ���������� �ű��.</td>
	</tr>
	<tr>
		<td>std::partition_copy()</td>
		<td>���� ������ �����ϰ�, �� ����� ������ �� �迭�� ��ȯ��.</td>
	</tr>
	<tr>
		<td>std::is_partitioned()</td>
		<td>�־��� �ǹ��� �������� ������ �Ǿ� �ִ����� �˻�.</td>
	</tr>
	<tr>
		<td>std::stable_partition()</td>
		<td>���� ������ �����ϸ�, �� ��Ƽ�� ���Ҵ� ���� ������ ������.</td>
	</tr>
	<tr>
		<td>std::sort()</td>
		<td>�����̳� ���Ҹ� �����Ѵ�. ���������� ���� ���� �˰����� �����Ͽ� ����Ѵ�.</td>
	</tr>
	<tr>
		<td>std::stable_sort()</td>
		<td>�����̳� ���Ҹ� �����ϵ�, ���� ������ ���� ���ҿ� ���� ���� ������ ������� �ʵ��� ������.</td>
	</tr>
	<tr>
		<td>std::partial_sort()</td>
		<td>�����̳� ��ü�� �ƴ϶� �Ϻ� ������ ���ؼ� �����Ѵ�.</td>
	</tr>
	<tr>
		<td>std::merge()</td>
		<td>�� ���� �Է� �����̳ʸ� ��ģ��. �̶� �� �����̳��� ���� ������ �״�� �����ȴ�.</td>
	</tr>
	<tr>
		<td>std::nth_element()</td>
		<td>�����̳ʿ��� n��°�� ���� ���Ҹ� ��ȯ�Ѵ�.</td>
	</tr>
	<tr>
		<td>std::accumulate()</td>
		<td>�����̳� ������ ���� ���� ����Ѵ�. �� �Լ��� �ٸ� �ܺ� �Լ��� �����Ͽ� ���� ���� �ƴ� �ٸ� ������ ������ ���� �ִ�.</td>
	</tr>
	<tr>
		<td>std::transform()</td>
		<td>�����̳ʿ� �Լ��� �־�����, �����̳��� ��� ���ҿ� ���� �ش� �Լ��� �����Ͽ� ���� ������.</td>
	</tr>
	<tr>
		<td>std::reduce()</td>
		<td>������ ������ ���ҿ� ���� ���ེ ������ �����ϰ� ����� ��ȯ��.</td>
	</tr>
</table>


## ���� �˻�
* �� �ܰ迡�� ��ü �������� �Ϻο� ���ؼ��� �˻��� ����
* ���Ҹ� ã�ҰŴ� �Ǵ� range(�Ϻκ��� ������)�� �� ���� �κ����� ���� �� ���� �� �˻��� ������.
* **���� �˻��� ��κ��� ���� ���� �˰���� ���� �ٸ����� �ִ�.** 
    * �˻� ���������� �������� ���� range���� ���Ҹ� ã�� �� �ִٸ� ��ü ������������ ���Ҹ� ã�� �� �ִ�. => ��ü�� �Ϻο��� ���� �ش��� ��ü���� ���� �ش�� ����. ��, **���� ������ �ʿ����� ����**. �̷��� Ư���� ���� ������ �̿��Ͽ� �ذ��� �� �ִ� �ټ��� ��� �������� ��ġ ���� ����̴�.
```c++
	bool binary_search(int N, std::vector<int>& S)
	{
		auto first = S.begin();
		auto last = S.end();

		while (true)
		{
			// ���� �˻� ������ �߰� ���Ҹ� mid_element�� ����
			auto range_length = std::distance(first, last);
			auto mid_element_index = std::floor(range_length / 2);
			auto mid_element = *(first + mid_element_index);

			// mid_element�� N ���� ��
			if (mid_element == N)
				return true;
			else if (mid_element > N)
				std::advance(last, -mid_element_index);
			else
				std::advance(first, mid_element_index);

			// ���� �˻� ������ �ϳ��� ���Ҹ� ���� �ִٸ� false�� ��ȯ
			if (range_length == 1)
				return false;
		}
	}
```
## ���� ������ �̿��� ���� �˰���
* �ܺ� ���� : ��ǻ���� ���� �޸𸮿� �����Ͱ� �������� ���� ���¿��� ����Ǵ� ������ �ʿ�� ��. ���� �� ���� �������� ��ü �������� �Ϻθ� �޸𸮿� �÷����� ������ �� �ִ�.
    * ���� ����
### ���� ����
* ���� : ��뷮�� �����͸� �����ϴ� ��
* ���� ���ҷ� ������ ��ü ������ ���� ũ���� �κ��������� ���� ������ �����ϰ�, ���ĵ� �κ������� �������� �Ǵ� �������� ������ �����ϸ鼭 ��ġ�� ���
* ��ü �迭�� ���� ���� �κ� �迭�� ������ �۾��� �ݺ��ϸ�, �� �۾��� �� �κ� �迭�� �ϳ��� ���Ҹ� ���� �� ����. ���Ŀ��� **�ٽ� �迭�� ��ġ�� �۾��� �ݺ��ϸ� �̶� <span style="color: black; background-color: yellow;">������ �迭�� ���Ұ� ��������(��������)�� �����ϵ��� ����</span>**
![](./merge.jpg)
```c++
	template <typename T>
	std::vector<T> merge(std::vector<T>& arr1, std::vector<T>& arr2)
	{
		std::vector<T> merged;

		auto iter1 = arr1.begin();
		auto iter2 = arr2.begin();

		while (iter1 != arr1.end() && iter2 != arr2.end())
		{
			if (*iter1 < *iter2)
			{
				merged.emplace_back(*iter1);
				iter1++;
			}
			else
			{
				merged.emplace_back(*iter2);
				iter2++;
			}
		}

		if (iter1 != arr1.end())
		{
			for (; iter1 != arr1.end(); iter1++)
				merged.emplace_back(*iter1);
		}
		else
		{
			for (; iter2 != arr2.end(); iter2++)
				merged.emplace_back(*iter2);
		}

		return merged;
	}

	template <typename T>
	std::vector<T> merge_sort(std::vector<T> arr)
	{
		if (arr.size() > 1)
		{
			auto mid = size_t(arr.size() / 2);
			auto left_half = merge_sort<T>(std::vector<T>(arr.begin(),
				arr.begin() + mid));
			auto right_half = merge_sort<T>(std::vector<T>(arr.begin() + mid,
				arr.end()));

			return merge<T>(left_half, right_half);
		}

		return arr;
	}
```
### �� ����
* ���� : ��� ���� �ð��� ���̴� �� 
* **�⺻ ���̵��� ���� ���İ� ����.** ��, ���� �Է� �迭�� ���� ũ���� �κ� �迭�� ������, �� �κ� �迭�� ������ ��, �� ����� ���ļ� ��ü ���ĵ� �迭�� ������
* **<span style="color: black; background-color: yellow;">�ٸ� �� ������ �ٽ� ������ ������ �ƴ϶� �����̴�.</span>**
#### �� ������ ���� ���� ���
�Է� �迭�� �־����� �Է� �迭 �� �ǹ� ���� P�� �������� ���, �� ������ ���� ���� ������ ���� 2�ܰ�� �̷����
1. �Է� �迭�� �� ���� �κ� �迭 L�� R�� ������. L�� �Է� �迭���� P���� �۰ų� ���� ���Ҹ� �����ϴ� �κ� �迭�̰�, R�� �Է� �迭���� P���� ū ���Ҹ� �����ϴ� �κ� �迭�̴�.
1.  �Է� �迭�� L,P,R������ �籸����.

* **��ü �� ���� �˰���**
   1. �Է� �迭 A�� �� �� �̻��� ���Ҹ� ������ �ִٸ� A�� ���� ������ �����Ѵ�. �׷��� �κ� �迭 L(P���� �۰ų� ���� ���Ҹ� ����)�� R(P���� ū ����)�� �����ȴ�.
   2. 1�ܰ��� �Է����� L�� �����.
   3. 1�ܰ��� �Է����� R�� �����.
	* ���⼭ 2�ܰ�� 3�ܰ�� ���� ���꿡 ���� ������ �κ� �迭�� ��������� �����.
	* �̷��� ���� ������ ��������� �ݺ��Ҽ��� ��� ���Ұ� ���� ������������ ���ĵ�.
    ![](./quick.jpg)
```c++
	template <typename T>
	auto partition(typename std::vector<T>::iterator begin,
		typename std::vector<T>::iterator end)
	{
		// �� ���� �ݺ��ڸ� �����մϴ�.
		// �ϳ��� �ǹ��� ����Ű��, ������ ���� ������ ���۰� ������ ���Ҹ� ����ŵ�ϴ�.
		auto pivot_val = *begin;
		auto left_iter = begin + 1;
		auto right_iter = end;

		while (true)
		{
			// ������ ù ��° ���Һ��� �����Ͽ� �ǹ����� ū ���Ҹ� ã���ϴ�.
			while (*left_iter <= pivot_val && std::distance(left_iter, right_iter) > 0)
				left_iter++;

			// ������ ������ ���Һ��� �����Ͽ� �������� �ǹ����� ���� ���Ҹ� ã���ϴ�.
			while (*right_iter > pivot_val && std::distance(left_iter, right_iter) > 0)
				right_iter--;

			// ���� left_iter�� right_iter�� ���ٸ� ��ȯ�� ���Ұ� ������ �ǹ��մϴ�.
			// �׷��� ������ left_iter�� right_iter�� ����Ű�� ���Ҹ� ���� ��ȯ�մϴ�.
			if (left_iter == right_iter)
				break;
			else
				std::iter_swap(left_iter, right_iter);
		}

		if (pivot_val > *right_iter)
			std::iter_swap(begin, right_iter);

		return right_iter;
	}

	template <typename T>
	void quick_sort(typename std::vector<T>::iterator begin,
		typename std::vector<T>::iterator last)
	{
		// ���� ���Ϳ� �ϳ� �̻��� ���Ұ� �ִٸ�
		if (std::distance(begin, last) >= 1)
		{
			// ���� �۾��� ����
			auto partition_iter = partition<T>(begin, last);

			// ���� �۾��� ���� ������ ���͸� ��������� ����
			quick_sort<T>(begin, partition_iter - 1);
			quick_sort<T>(partition_iter, last);
		}
	}
```
* �� ������ ���� �ð��� �ǹ��� ��� �����ߴ°��� ���� �޶���. �ּ��� ���� �־��� �迭���� �߰� ��ġ�� ���Ҹ� �ǹ����� ����ϴ� ���

### ���� ���İ� �� ������ ������ �ð� ���⵵
<table>
	<tr>
		<th>�˰���</th>
		<th>�ּ��� ���</th>
		<th>���</th>
		<th>�־��� ���</th>
	</tr>
	<tr>
		<td>���� ����</td>
		<td>O(nlogn)</td>
		<td>O(nlogn)</td>
		<td>O(nlogn)</td>
	</tr>
	<tr>
		<td>�� ����</td>
		<td>O(nlogn)</td>
		<td>O(nlogn)</td>
		<td>O(n^2)</td>
	</tr>
</table>