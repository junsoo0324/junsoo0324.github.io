---
layout: single
title: greedy algorithm
time: 2020-04-26 16:00:00 +0900
author: JunSoo
---



## # 그리디(Greedy) 알고리즘

###### 그리디 알고리즘은 최적화 문제를 해결하는 알고리즘이다.

###### 최적화 문제는 가능한 해들 중에서 가장 좋은(최대 또는 최소) 해를 찾는 문제이다. 

###### 그리디 알고리즘은 욕심쟁이 방법, 탐욕적 방법, 탐욕 알고리즘 등으로 불리기도 한다.

###### 그리디 알고리즘은 (입력) 데이터 간의 관계를 고려하지 않고 수행 과정에서 '욕심내어' 최소값 또는 최댓값을 가진 데이터를 선택한다

###### 이러한 선택을 '근시안적'인 선택이라고 말하기도 한다. 

###### 그리디 알고리즘은 근시안적인 선택으로 부분적인 최적해를 찾고, 이들을 모아서 문제의 최적해를 찾는다.

###### 또한 그리디 알고리즘은 일단 한번 선택하면, 이를 절대로 번복하지 않는다.

###### 즉,선택한 데이터를 버리고 다른 것을 취하지 않는다.

###### 이러한  특성 때문에 대부분의 그리디 알고리즘들은 매우 단순하며, 또한 제한적인 문제들만이 그리디 알고리즘으로 해결된다.



## # 그리디 알고리즘 문제들

#### 1.동전 거스름돈

#### 2.최소 신장 트리

#### 3.최단 경로 찾기

#### 4.부분 배낭 문제

#### 5.집합 커버 문제

#### 6.작업 스케줄링

#### 7.허프만 압축



###### 책에서 소개된 문제들은 위에서 표현했다

###### 신박한 그리디 알고리즘 문제를 찾아야 하기에 인터넷을 뒤져보던 도중 

###### 백준이라는 사이트에서 모두의 마블이라는 문제를 보게 되었다.



## 문제

###### 영관이는 게임을 좋아한다. 별의별 게임을 다 하지만 그 중에서 제일 좋아하는 게임은 모두의 마블이다. 어김없이 오늘도 영관이는 학교 가는 버스에서 캐릭터 합성 이벤트를 참여했다.

###### 이번 이벤트는 다음과 같다. 순서가 매겨진 여러 장의 카드가 있다. 각각의 카드는 저마다 레벨이 있다.

###### 카드 A에 카드 B를 덧붙일 수 있다. 이때 붙이는 조건은 다음과 같다.

1. ###### 두 카드는 인접한 카드여야 한다.

2. ###### 업그레이드 된 카드 A의 레벨은 변하지 않는다.

###### 카드 합성을 할 때마다 두 카드 레벨의 합만큼 골드를 받는다.

###### 영관이가 골드를 최대한 많이 받을 수 있게 여러분이 도와주자.

###### 예를 들어, c1, c2, c3로 연속된 카드 3개가 있고 각각 레벨이 40,30,30 이라고 하자.

###### 이 카드들을 합치는 과정에서, 먼저 c3에 c2를 합쳐 임시 카드 x1을 만든다. x1의 레벨은 30이고 획득 골드는 60이다. 그 다음엔 c1에 x1을 합쳐 카드 x2를 만들면 레벨이 40이고 70만큼의 골드를 획득할 수 있다. 이때, 영관이가 획득한 골드는 70+60 = 130이다.

###### 다른 방법으로 c1에 c2를 덧붙인 카드 x1을 만들면, x1의 레벨은 40이고 획득한 골드는 70이다.

###### x1에 c3를 덧붙인 카드 x2의 레벨은 40이고 획득 골드는 70이다. 이때, 영관이가 획득한 골드는 70 + 70 = 140이다. 이외에 더 많은 골드를 받는 방법이 없으므로 140이 획득할 수 있는 최대 골드이다.



## #입력값

###### 카드의 개수 n(0 < n ≤ 1,000)이 주어진다.

##### 다음 줄에 각각 카드의 레벨 Li가 순서대로 주어진다. (0 < Li ≤ 100,000)





## #출력값

###### 영관이가 받을 수 있는 골드의 최댓값을 출력한다.





## #예제 입력

```java
3
40 30 30
```





## #예제 출력

```java
140
```





## ##풀이

```java
import java.util.*; 
import java.io.*; 

public class Main {
	private static BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
    public static void main (String args[]) throws IOException { 
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in)); 
        br.readLine(); String str1[] = br.readLine().split(" "); 
        int max = 0; 
        int maxIndex = 0; 
        int result = 0; 
        for (int i = 0; i < str1.length; i++) { 
            int level = Integer.parseInt(str1[i]); 
            if (max < level) { max = level; maxIndex = i; } result += level; } 
        result += max * (str1.length - 2); 
        bw.write(String.valueOf(result)); 
        bw.flush(); 
    } 
}

```





