# 재귀 (Recursion)

```cpp
BOJ_1629 곱셈

#include <iostream>
#define ll long long

using namespace std;

ll Recur(ll A, ll B, ll C) {
	if (B == 1)	return A % C; //Base Condition

	ll remainder = Recur(A, B / 2, C);

	if (B % 2 == 0)	return remainder * remainder % C; //짝수인 경우
	else //홀수인 경우
	{
		//return remainder * remainder * A % C;
		//이유는 reaminder의 최대값은 int 양의 최대값 -1, 대략적으로 10^9이고 이 두 수를 곱하면 최소 10^18
		//long long의 범위는 10^18이므로, reaminder의 제곱에 A를 곱할 경우 높은 확률로 오버플로우가 발생
		remainder = remainder * remainder % C;
		return remainder * A % C;
	}
}

int main(void) {
	ios::sync_with_stdio(false);
	cin.tie(NULL);

	ll A, B, C;
	cin >> A >> B >> C;

	cout << Recur(A, B, C);
}
```

```cpp
//BOJ - 1074 Z 바킹독(수정해야함) //이해는 했지만 내가 생각했던 거랑은 좀 다름
#include <iostream>
#include<algorithm>

using namespace std;
//사분면을 거르고 함수를 호출할 때마다 n-1을 하는 이유 : 2의 N승이니까 사각형을 2의 (N / 2)승으로 만들기 위함
// 이 과정을 Base Condition에 도달?할 때까지 함 
int func(int n, int r, int c)
{
	if (n == 0) return 0; //Base Condition에 도달했다는 것은 r, c까지 도달했다는 소리이므로 return 시작.
	int half = 1 << (n - 1); //비트 연산자
	if (r < half && c < half) return func(n - 1, r, c); //1번 사각형인 경우
	if (r < half && c >= half) return half * half + func(n - 1, r, c - half); //2번 사각형인 경우
	if (r >= half && c < half) return 2 * half * half + func(n - 1, r - half, c);//3번 사각형인 경우
	return 3 * half * half + func(n - 1, r - half, c - half);
}

int main()
{
	ios::sync_with_stdio(0);
	cin.tie(0);

	int n, r, c;
	cin >> n >> r >> c;
	cout << func(n, r, c);
}
 
//예시 1번 2 1 3
/*
* 1. 3번 사각형 (R, C) = (3, 1)
* half 1 << (2 - 1) ====>> 1을 1만큼 왼쪽으로 비트 이동 시키면 0001에서 0010으로 바뀐다. 그러므로 half = 2이다.
  if(3 >= 2 && 1 < 2)
  return 8 + func(1, 1, 1) 여기서 func의 호출은 타고 들어가는 느낌이다. 여기서 호출한 func의 리턴 값 + 8이 답인 것이다.
		 8 + 3(코드38번째 줄의 리턴 값) = 11이므로 최종적으로 11을 return 해준다.

  2. 4번 사각형 (R, C) = (1, 1)
  half 1 << (1 - 1) ====>> 1을 0만큼 왼쪽으로 비트 이동은 암것도 없으므로 half = 1이다
  if(1 >= 1 && 1 >= 1)
  return 3 * half * half + func(0, 0, 0) 3 + 0(코드40번째 줄의 리턴 값)

  3.BaseCondition 조건문이 참이 되므로 return 0; 0의 값은 38번째 줄로 감.
*/
```

```cpp
//BOJ - 11729 하노이 탑 이동 순서 (이해 X)
#include <iostream> 
using namespace std;
/*
* 1. n-1개의 원판을 기둥1 -> 기둥2
* 2. n번 원판을 기둥1 -> 기둥3
* 3. n-1개의 원판을 기둥2 -> 기둥3
* 
* 재귀식
* n-1개의 원판을 기둥 a -> 기둥 6 - a - b
* n번 원팔을 기둥a -> 기둥b
* n-1개의 원판을 기둥6-a-b -> b
*/
void func1(int a, int b, int n)
{
	if (n == 1) //Base Condition
	{
		cout << a << ' ' << b << '\n';
		return;
	}
	func1(a, 6 - a - b, n - 1);
	cout << a << " " << b << '\n';
	func1(6 - a - b, b, n - 1);
}
int main()
{
	int n;
	cin >> n;
	cout << (1 << n) - 1 << '\n';
	func1(1, 3, n);
}
```

```cpp
//BOJ - 17478 - 재귀함수가 뭔가요?
//띄어쓰기 못 찾아서 이틀을 어리바리...
#include <iostream>
using namespace std;

int i = 0;
bool plag, plag2;
void func1(int n)
{
	if (n == 0)	plag = true; //"라고 답변하였지."이라는 텍스트가 출력 되기 전까지를 체크하고 n번 반복하기 위함
	if (!plag)
	{
		for (int j = 0; j < i; j++)	cout << "____"; //_(4개)의 반복횟수는 함수의 호출횟수와 동일하므로 i로 호출횟수를 체크하여 반복
		cout << "\"재귀함수가 뭔가요?\"\n";
		for (int j = 0; j < i; j++)	cout << "____";
		cout << "\"잘 들어보게. 옛날옛날 한 산 꼭대기에 이세상 모든 지식을 통달한 선인이 있었어.\n";
		for (int j = 0; j < i; j++)	cout << "____";
		cout << "마을 사람들은 모두 그 선인에게 수많은 질문을 했고, 모두 지혜롭게 대답해 주었지.\n";
		for (int j = 0; j < i; j++)	cout << "____";
		cout << "그의 답은 대부분 옳았다고 하네. 그런데 어느 날, 그 선인에게 한 선비가 찾아와서 물었어.\"\n";
	}
	else//n번의 반복이 끝났으면 "라고 답변하였지." 텍스트를 반복하기 위해 return
	{
		return;
	}
	i++;//_*4개 출력을 제어하기 위함
	func1(--n);//n번 반복하기 위해 호출할 때마다 -1을 해줌

	if (plag) //n번의 반복이 끝났다면 실행.
	{
		if (!plag2)
		{
			for (int j = 0; j < i; j++)	cout << "____";
			cout << "\"재귀함수가 뭔가요?\"\n";
			for (int j = 0; j < i; j++)	cout << "____";
			cout << "\"재귀함수는 자기 자신을 호출하는 함수라네\"\n";
			for (int j = 0; j < i; j++)	cout << "____";
			cout << "라고 답변하였지.\n";
			plag2 = true;////"재귀함수가 뭔가요?", "재귀함수는 자기 자신을 호출하는 함수라네" 라는 멘트는 딱 한 번만 출력 되어야 하므로 이 멘트를 출력하였으면 plag2에 true를 표시해주어 중복 출력을 방지함
			i--;
		}
		else
		{
			for (int j = 0; j < i; j++)	cout << "____";
			cout << "라고 답변하였지.\n";
			i--;
		}
	}
}

int main()
{
	int n;
	cin >> n;
	cout << "어느 한 컴퓨터공학과 학생이 유명한 교수님을 찾아가 물었다.\n"; //시작멘트
	func1(n);
	cout << "라고 답변하였지."; //문제에서 입력의 범위를 1부터라고 말했으므로 함수가 종료된 이후에 호출 되도 무관함
	return 0;
}
```

```cpp
//BOJ - 11729 하노이 탑 이동 순서
#include <iostream>
using namespace std;
/*
* 1. n-1개의 원판을 기둥1 -> 기둥2
* 2. n번 원판을 기둥1 -> 기둥3
* 3. n-1개의 원판을 기둥2 -> 기둥3
* 
* 재귀식
* n-1개의 원판을 기둥 a -> 기둥 6 - a - b
* n번 원팔을 기둥a -> 기둥b
* n-1개의 원판을 기둥6-a-b -> b
* 
* 설명 들어보기 들어도 이해가 잘 안됨.
*/
void func1(int a, int b, int n)
{
	if (n == 1) //Base Condition
	{
		cout << a << ' ' << b << '\n';
		return;
	}
	func1(a, 6 - a - b, n - 1);
	cout << a << " " << b << '\n';
	func1(6 - a - b, b, n - 1);
}
int main()
{
	int n;
	cin >> n;
	cout << (1 << n) - 1 << '\n';
	func1(1, 3, n);
}
```

```cpp
//재귀 Recursion

#include<iostream>
using namespace std;

//			recursion(재귀)
/*
* : 하나의 함수에서 자기 자신을 다시 호출해 작업을 수행하는 알고리즘
* 
* 수학적 귀납법 : 1번 도미노가 쓰러짐 -> K번 도미노가 쓰러진다 -> K+1번 도미노가 쓰러지므로 참이다.
*				, 우리는 이러한 것으로 1번 쓰러짐 and K번 도미노가 쓰러짐 = 모든 도미노가 쓰러진다 라는 결론을 도출할 수 있음
* 
* 올바른 재귀 조건
* 1.특정 입력에 대해서는 자기 자신을 호출하지 않고 종료 되어야 한다. (Base Condition)
* 2.모든 입력은 Base Condition으로 수렴해야 한다.
* 
* 재귀 함수는 꽤 비용이 큰 연산이므로 메모리와 시간에서는 큰 손해를 본다.
* 
* 재귀 작성 요령
* 1. 함수의 인자로 어떤 것을 받고 어디까지 계산한 후 자기 자신에게 넘겨줄지 명확하게 정해야 함
* 2. 모든 재귀함수는 반복문으로 동일한 동작을 하는 함수를 만들 수 있음
* 3. 한 함수가 자기 자신을 여러 번 호출하면 비효율적일 수 있음 -> 37번째 줄 참고(피보나치 함수)
* 
*/

void func1(int N)
{
	if (N == 0) //Base condition
		return;
	func1(N--);
}

int func2(int N)
{
	if (N == 0) return 0;
	return N + func2(N - 1);
}

int fibo(int n)
{
	if (n <= 1)	return 1;
	return fibo(n - 1) + fibo(n - 2);
	//이 재귀는 시간복잡도가 지수함수 꼴로 터짐
	//왜냐? 이미 연산한 것을 반복함 향후 DP로 해결 가능한 부분도 존재
}

int main()
{
	int n;
	cin >> n;
	func1(n);
	func2(n);
	cout << n;
	return 0;
}
```