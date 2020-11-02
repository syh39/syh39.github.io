---
title:  "[백준 2502번] 떡먹는 호랑이 (실버 1)"
excerpt: ""

categories:
  - Algorithm
  - Math
tags:
  - Algorithm
  - Math
last_modified_at: 2020-11-3 
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
---

---




### 문제 화면

![BOJ](/assets/images/BOJ/www.acmicpc.net_problem_2502.jpg)



문제 링크 : <https://www.acmicpc.net/problem/2502> 



### 문제 풀이

이 문제는 식을 세우고 나서 코드로 구현하는게 핵심인 문제이다. 

 

#### 제출 코드

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
      if(((arr[D][0]*A) + (arr[D][1]*B) == K) && B>=A){
        cout << A << endl;
        cout << B << endl;

        return 0;
      }
    }
  }
}
```






