---
layout: single
title: FFT 알고리즘
time: 2020-05-17 18:00 +0900
author: JunSoo
---

# 1 . FFT 알고리즘이란

##### 고속 푸리에 변환(FFT) 알고리즘 : 

이산 푸리에 변환(DFT)과 역변환을 빠르게 계산 하기 위한 알고리즘

기존 이산 푸리에 변환의 속도에 비해 FFT 알고리즘을 이용하면 획기적으로 시간 복잡도를 줄일 수 있다는 장점이있다.



# 2 . 이산 푸리에 변환(DFT)  

##### 이산 푸리에 변환(Discrete Fourier Transform) : 

시간 영역의 이산 신호를 주파수 영역의 이산 신호로 변환하는 것을 뜻한다.

이산적인 입력 신호에 대한 푸리에 변환이다.

 먼저, n-1차 다항식 f(x)는 n개의 서로 다른 (x, f(x)) 값을 알고 있을 시 유일하게 결정된다.

만약 이 n개의 x값과 각각에 해당하는 함숫값 사이의 변환이 굉장히 빠르다면 , 전체적으로 다항식의 곱을 빠르게 계산할 수 있다.



어떤 0 이상의 정수 p에 대해, **n = 2^p**라고 일반화한다.

또한, 위에서 말한 서로 다른 n개의 점의 x좌표들은 n승을 할 시 1이 되는 n개의 서로 다른 복소해들을 가져온다. 즉 **x^n = 1**인 서로 다른 n개의 해를 구해서 x로 쓴다.



이 x를 x_1이라 하고 x_k = (x_1)^k라 하여 모든 0 ≤ k < n 에 대해 각 값을 계산하면 n개의 값이 나오게 된다. 

이때 x_k는 

![img](https://blogfiles.pstatic.net/MjAxOTA4MzBfMzMg/MDAxNTY3MTQxMzk2MjUx.WIIEWwrkxbcTtfNzHCjm65hGNIh1PzAuEG8fOk6gZb0g.0yeyHuE75lijYSuC-unDCgHyo0MpJId3rGr9S8zxwDYg.PNG.kks227/2.png?type=w3)

 위 식과 같이 나오게 되고, 성립함을 알 수 있다.

![img](https://blogfiles.pstatic.net/MjAxOTA4MzBfMTk1/MDAxNTY3MTQzNzAyNzE4.nsVtF6XzE-FPbA7_fBg3I5ajfuQhEFYnRWYwWAeYHbEg.G5PX8wpP3F-9GwJzoBOC2uEj4XSH8eMhXQ4JGpYI1xMg.PNG.kks227/5.png?type=w3)



이때 n = 8일 때는 시각적으로 이렇게 표현할 수 있는데, 가로축이 실수부분, 세로축이 허수부분이라고 생각하시면 되겠습니다.

여기서 x_k = - x_(k+n/2), 즉 서로 반대편에 있는 값들끼리 서로 부호만 반대인 상황이 일어납니다.

DFT는 즉, 이 각각의 f(x)의 계수 <a0, a1, ... , a(n-1)>을 <f(x_0), f(x_1), ... , f(x_(n-1))>로 변환하는 것이다.



.

# 3 . 고속 푸리에 변환 (FFT) 

2에서 설명한 이산 푸리에 변환의 시간 복잡도를 개선하기 위해  분할정복을 통해 보완한 알고리즘이다.

분할정복이 들어가는 알고리즘을 대부분 FFT라고 하기 때문에

주로 알려져 있는 FFT 할고리즘은 쿨리-튜키 알고리즘이다.

n1 + n2 =n인 ,  n 크기의 DFT를 분할해 n1, n2 크기의 두 DFT로 나타 낸 후 결과를 O(n)시간에 합치는 방식으로

이 알고리즘은 주로  x^n = 1인 해들을 이용해 계산을 실시한다.



![img](https://blogfiles.pstatic.net/MjAxOTA4MzBfMTY3/MDAxNTY3MTQyOTE1MDgw.NQx1WRooXiK_KdRY9klrBeYWYwbI-v1nsgjhdpcuudcg.kxAedXcKRe5TtliT-YyeqJh2eS0FNemWHrybeVeHF1Yg.PNG.kks227/3.png?type=w3) 



n이 짝수일 때, 다항식 f(x)를 저렇게 두 개의 다항식으로 쪼갤 수 있다. 짝수차항만을 담은 것과 홀수차항만을 담은 것으로. 또한, 만약 우리가 어떤 x값 쌍을 w와 -w로 뽑는다면

<img src="https://blogfiles.pstatic.net/MjAxOTA4MzBfNzgg/MDAxNTY3MTQzMTc3MzQ2.qcEFCMQQZXxH2i3STzYUQBN3OQ9uajanxfDqIjZFwnkg.6V-pIr3S69NG8ujzXTjOwEAyXvTRolc4_v7AxeKB2REg.PNG.kks227/4.png?type=w3" alt="img" style="zoom:50%;" />

f_even(w^2)와 f_odd(w^2), 이 두 값만 구해온다면 즉석에서 아주 빠르게 f(w)와 f(-w)를 구할 수 있게된다.



# 4. DFT 와 FFT의 시간복잡도 차이

위의 DFT와 FFT가 생소하기 때문에 쉽게 예를 들어 다항식의 곱을 볼때

최고차항이 n-1인 두 다항식은 원래부터 **O(n^2)**의 시간복잡도를 가진다.

DFT는 바로, 이 각각의 f(x)의 계수 <a0, a1, ... , a(n-1)>을 <f(x_0), f(x_1), ... , f(x_(n-1))>로 변환하는 것을 말합니다. 한 함숫값을 구하는 데 **O(n)**의 시간이 걸리므로 기본적으로 DFT에는 **O(n^2)**의 시간이 걸리게 되지만,



그러나 FFT로 계산한다면 

**다항식의 곱을 구하는 데 걸리는 총 시간**

:  **DFT O(nlogn) + 함숫값끼리의 곱 O(n) + IDFT O(nlogn)** 를 합한 값이 되게 되고,

BIg-O 표기법에 의해 시간복잡도는 결국 O(nlogn)이 되게된다.



이에 비해 FFT는 짝수와 홀수의 수열을 따로 짝수의 수열과 홀수의 수열로 나눠 계산하기 때문에 

O(N log N)의 시간복잡도를 가지게 되고,

FFT는 DFT에 비해 더 빠른 계산이 가능하게 된다.

