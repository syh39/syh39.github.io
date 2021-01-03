---
title:  "[백준 2502번] 떡먹는 호랑이"
excerpt: ""

categories:
  - Algorithm
tags:
  - Algorithm
  - Math
  - Silver Level
last_modified_at: 2020-11-3 
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
---


### 문제 화면

![BOJ](/assets/images/BOJ/2502/www.acmicpc.net_problem_2502.jpg)



문제 링크 : <https://www.acmicpc.net/problem/2502> 



### 문제 풀이

이 문제는 식을 세우고 나서 코드로 구현하는게 핵심인 문제이다. 첫째 날에 준 떡의 개수 A와 둘째 날에 준 떡의 개수 B에 따라서 나머지 3~30일차에 준 떡의 개수가 결정되기 때문에 A와 B에 관하여 식을 세우면 된다. 

즉, 첫째 날에 A개의 떡을 주고 둘째 날에 B개의 떡을 주었다면 셋째 날에는 A+B개의 떡을 주게 된다. 

넷째 날의 경우 둘째 날에 준 떡의 개수와 셋째 날에 준 떡의 개수를 더한 값이기 때문에 B+A+B = A+2B가 된다. 

다섯 째 날의 경우 셋째 날에 준 떡의 개수와 넷째 날에 준 떡의 개수를 더한 값이기 때문에 A+B+A+2B=2A+3B가 된다.  

> 구상

![BOJ](/assets/images/BOJ/2502/1.jpg) {:height="50%"}



> 코드 테스트 결과

![BOJ](/assets/images/BOJ/2502/2.jpg) {: width="100" height="100"}



따라서 위의 공식은 n = n-1 + n-2 가 되고 A와 B는 각각 배열로 저장할 수 있다. 

위의 구조를 그대로 배열로 구현하려면 2차배열이 좋을 것 같아서 31행, 2열짜리 배열을 만들었다. 각 행은 날을 나타내고 열은 0열은 A, 1열은 B로 나타냈다. 헷갈릴까봐 30행이 아닌 31행으로 만들고 1일 -> 1행으로 만들었다. 그리고 처음 두 날은 각각 A=1, B=0 / A=0, B=1로 초기화 해주고 3일차부터 30일차까지 반복문으로 값을 넣어주었다. 

식을 완성하고 나서 날(D)과 떡의 개수(K)를 입력 받고 나서 이중포문으로 각각 A와 B를 대입해서 K와 일치하는 순간 답을 출력하도록 하였다. 

 

### 제출 코드

```c++
#include <iostream>

using namespace std;

int main() {
  int arr[31][2];
  int D, K;
  arr[1][0] = 1;
  arr[1][1] = 0;
  arr[2][0] = 0;
  arr[2][1] = 1;

  for(int i = 3 ; i < 31 ; i++) {
    arr[i][0] = arr[i-1][0] + arr[i-2][0]; // A식
    arr[i][1] = arr[i-1][1] + arr[i-2][1]; // B식

  }
  cin >> D >> K ;

  for(int A = 1 ; A <=K ; A++) {
    for(int B = A ; B <=K ; B++) {
      if((arr[D][0]*A) + (arr[D][1]*B) == K){
        cout << A << endl;
        cout << B << endl;

        return 0;
      }
    }
  }
}
```



### 결론

이번 문제는 수학적인 공식을 만들고 어떻게 코드로 구현할 수 있는지를 물어보는 문제인 것 같았다. 문제 이해는 쉬웠지만 코드로 구현하는 부분에서 헤맸던 것 같다. 


