---
title: 📜MAP(맵) 2022-09~2022-12
hide_date: true
reading_time: false
date: 2022-09-01
---

- 맵(Map)은 **키(key)**와 **값(value)**의 쌍으로 이루어진 데이터를 저장하는 자료구조입니다. 각 키는 유일하며, 이를 통해 대응되는 값을 효율적으로 검색, 삽입, 삭제할 수 있습니다. 맵은 다양한 프로그래밍 언어에서 제공되며, 상황에 따라 해시 테이블(Hash Table)이나 이진 탐색 트리(Binary Search Tree)로 구현됩니다.
    - map contaniner는 노드 기반으로 이루어져 있는 균형 이진 트리 구조이다.
    - map은 key와 value로 이루어져 있으며 pair 객체 형태로 저장된다.
    - Unique Key : key는 고유한 값이므로 중복이 불가능하다.(만약 중복 key를 사용하고 싶다면 multimap에서 사용 가능)
    - Ordered - map도 set과 마찬가지로 삽입이 되면서 자동으로 정렬이 된다. (default는 less/오름차순이다.)
    
    ![그림14](/images/dataStructureImages/image14.jpg)
    
- 사용 방법
    - 기본 생성 방법 → map <Data type1, Data type2> 변수이름;
        
         → ex) map <int, int> m1;
                   map <string, int> m2;
        
    - map<int> m (pred);
    → pred를 ㅇ통해 정렬기준 (오름, 내림)을 세울 수 있다.
    
- 주요 멤버함수
    - iterator(반복자)
    → begin() : beginning iterator를 반환
        
        → end() : end iterator를 반환
        
    - 추가 및 삭제
        
        → insert (make_pair(key, value)) : map에 원소를 pair 형태로 추가
        
        → erase (key) : map에서 key(키값^)에 해당하는 워소 삭제
        
        → clear() : map의 원소들 모두 삭제
        
    - 조회
        
        → find(key) : key(키값)에 해당하는 iterator를 반환
        
        → count(key) : key(키값)에 해당하는 원소들 (value)의 개수를 반환
        
    - 기타
        
        → empty() : map이 비어있으면 true 아니면 false를 반환
        
        → size() : map 원소들의 수를 반환
        
- 기본 구현 코드
    
    ```cpp
    #include <iostream>
    #include <map>
    
    using namespace std;
    
    int main(void){
    	map<int, string> m;
    	m.insert(pair<int, string>(1, "one"));
    	m.insert(pair<int, string>(2, "two"));
    	m.insert(pair<int, string>(3, "three"));
    	m.insert(pair<int, string>(4, "four"));
    	
    	map<int, string>::iterator iter;
    	for(iter = m.begin(); iter != m.end(); iter++){
    		cout << (*iter).first << ", " << (*iter).second << endl;
    	}
    	
    	map<int, int> m2;
    	m2[9] = 123;
    	m2[3] = 532;
    	m2[4] = 999;
    	
    	map<int, int>::iterator iter2;
    	for(iter2 = m2.begin(); iter2 != m2.end(); iter2++){
    		cout << iter2->first << ' ' << iter2->second << endl;
    	}
    }
    //output
    1, one
    2, two
    3, three
    4, four
    3 532
    4 999
    9 123
    ```