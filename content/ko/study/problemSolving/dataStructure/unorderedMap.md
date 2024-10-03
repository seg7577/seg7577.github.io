# Unordered_map

- 개념
    - map 보다 더 빠른 탐색을 하기 위한 자료구조의 종류이다.
    - unorderd_map은 해쉬테이블로 구현한 자료구조이며 시간복잡도는 O(1)이다.
    - 우리가 흔히 사용하는 일반적인 map은 Binary Search Tree로 시간복잡도는 O(logN)이다.
    - unorderd_map은 중복된 데이터를 허용하지 않고 map에 비해 데이터가 많을 시 출동을 방지하며 좋은 성능을 보인다.
- 멤버함수
    - empty()
    → 비어있는지 확인하는 함수, 비었으면 return 1, else return 0이다.
    - size()
    → 맵의 크기를 확인하는 함수
    - operator []
    → 맵에서 key를 통해 value를 지정하는 operator
    → map_name[key] = value
    - find(key)
    → 맵에서 key에 해당하는 원소를 찾는 함수이다.
    - count(key)
    → 맵에서 key에 해당하는 원소의 갯수를 반환하는 함수이다.
    - insert({key, value})
    → 맵에서 pair<key, value>를 추가하는 함수이다.
    - erase(key)
    → 맵에서 key에 해당하는 원소를 제거하는 함수이다.
    - clear()
    → 맵을 초기화하는 함수이다.
    - operator =
    → 대입연산자 기능
- 개념 코드
    
    ```cpp
    #include <iostream>
    #include <string>
    #include <unordered_map>
    using namespace std;
    
    int main(){
        
        unordered_map<string,int> um;
        
        if(um.empty()){
            cout<<"unordered_map은 비어있습니다"<<endl;
        }
        
        um.insert(make_pair("key",1));
        um["banana"]=2;
        um.insert({"melon",3});
        
        cout<<"unordered_map의 크기는 "<<um.size()<<" 입니다"<<endl;
        
        // auto로 해도 무방
        for(pair<string,int> elem : um){
            cout<<"key : "<<elem.first<<" value : "<<elem.second<<endl;
        }
        
        // find 대신 count로 확인 가능
        if(um.find("banana")!=um.end()){
            um.erase("banana");
        }
        
        cout<<"unordered_map의 크기는 "<<um.size()<<" 입니다"<<endl;
        for(auto elem : um){
            cout<<"key : "<<elem.first<<" value : "<<elem.second<<endl;
        }
        
        return 0;
    }
    ```