---
title: 📜이진 탐색(Binary Search) 2022-09~2022-12
hide_date: true
reading_time: false
date: 2022-09-01
---
- 정렬된 배열에서만 사용할 수 있는 알고리즘입니다. 이진 탐색을 사용하려면 배열이 오름차순 또는 내림차순으로 정렬되어 있어야 합니다.
이진 탐색은 배열의 가운데에 있는 값을 먼저 확인한 다음, 찾고자 하는 값과 비교합니다. 이때, 가운데 값이 찾고자 하는 값보다 크면 왼쪽 절반을, 작으면 오른쪽 절반을 탐색 범위로 줄여 탐색을 이어나갑니다.
이렇게 배열의 범위를 절반씩 좁혀가면서 탐색하기 때문에 시간 복잡도가 매우 효율적입니다.

- lower_bound의 개념 <algorithm> stl을 사용하여 쓸 수 있음 lower_bound
    - 용도 : 찾으려는 key 값보다 같거나 큰 숫자가 배열 몇 번째에서 처음 등장 하는지 찾기 위함
        사용 조건 : 탐색을 진행할 배열 혹은 벡터는 오름차순 정렬되어 있어야 사용 가능함
    - 원리 : 배열 혹은 벡터를 끝까지 탐색하면서 key 값의 이상의 숫자가 처음으로 나오는 위치의 주소를 반환한다.
        -> 아래 코드 처럼 인덱스의 위치를 알고 싶다면 배열 혹은 벡터의 첫번째 주소를 가리키는 값을 lower_bound의 반환값에 대해 빼면 key 값이 처음으로 나오는 인덱스 번호를 알 수 있다.
    - 예시코드
        ```cpp
        //배열을 이용한 코드
        int main()
        {
            int arr[6] = { 1, 2, 3, 4, 5, 6 };
            cout << "lower_bound(6) : " << lower_bound(arr, arr + 6, 6) - arr;
            
        
            //output : 5
        }
        //벡터를 이용한 코드
        int main()
        {
        
            vector<int> arr = { 1,2,3,4,5,6,6,6 };
            cout << "lower_bound(6) : " << lower_bound(arr.begin(), arr.end(), 6) - arr.begin();
        
            // 결과 -> lower_bound(6) : 5
        
            return 0;
        }
        ```
    
    - upper_bound의 개념
        - <algorithm> stl을 이용하여 사용 가능
        용도 : 찾으려는 key 값을 초과하는 숫자가 배열 몇 번째에서 처음 등장하는지 찾기 위함
        사용 조건 : 탐색을 진행할 배열 혹은 벡터는 오름차순 정렬되어 있어야 함
        원리 : 처음부터 끝까지 탐색하면서 3을 처음으로 초과하는 숫자가 나오는 위치의 엔덱스 번호를 반환하는 예제이다.
        
        ```cpp
        
        //배열을 이용한 코드
        int main()
        {
            int arr[10] = { 1, 2, 3, 4, 6, 7, 8, 9, 10, 11 };
            cout << "upper_bound(6) : " << upper_bound(arr, arr + 6, 6) - arr;
        
            //output : 5
        }
        //벡터를 이용한 코드
        int main() 
        {
        
            vector<int> arr = { 1,3,5,5,7,8,8,10,10,11,13 };
            cout << "5 이상 11 이하의 갯수 : " << upper_bound(arr.begin(), arr.end(), 11) - lower_bound(arr.begin(), arr.end(), 5);
        
            return 0;
        }
        ```