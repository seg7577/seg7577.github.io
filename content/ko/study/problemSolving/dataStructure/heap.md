# Heap

- 개념
    
    [https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FVCP5n%2FbtqSPE4E2hn%2F2G7f8scOqnpXFfJEN0bZLk%2Fimg.png](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FVCP5n%2FbtqSPE4E2hn%2F2G7f8scOqnpXFfJEN0bZLk%2Fimg.png)
    
    → heap은 이진 트리 자료구조이다.
    
    → i번째 노드의 자식 노드는 i * 2 + 1번째 노드와  i * 2 + 2번째 노드가 된다.
    
    → i번째 노드의 부모 노드는 (i - 1) / 2번째 노드가 된다.
    
    → 부모노드는 항상 자식 노드보다 작거나 같다. or 크거나 같다.
    
    → 위 사진의 트리를 보면 부모노드는 자식 노드 보다 작은 규칙이 있다. 이러한 구조를 **최소힙**이라고 한다. 만약 부모 노드가 자식 노드 보다가 큰 경우 **최대힙**이라고 한다.