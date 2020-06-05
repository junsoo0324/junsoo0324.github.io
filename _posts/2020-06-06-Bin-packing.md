---
layout: single
title: Bin 문제풀이
time: 2020-06-06 01:30 +09:00
author: JunSoo
---

# 통 채우기 문제

통 채우기 문제는 n개의 물건이 주어지고, 통의 용량이 C일때 주어진 모든 물건을 가장 적은 수의 통에 채우는 문제이다.

물건을 통에 넣는 방법은 그리디 방법으로 구할 수 있는데, 그 중에서도 '무엇에 욕심을 낼 것인가'에 따라서 다음과 같이 4종류로 분류할 수 있다. 





## 1.First Fit

##### First Fit(최초적합)은 첫번째 통부터 물건을 차례대로 살펴보며 가장 먼저 여유가 있는 통에 새 물건을 넣는 방식이다.







## 코딩

![ff](https://user-images.githubusercontent.com/62889378/83906957-77d04d00-a79f-11ea-8557-f59147d46582.PNG)



```java
import java.lang.reflect.Array;
import java.util.ArrayList;

public class FirstFit implements Fit{
    @Override
    public void fit(ArrayList<Bin> arr, Item item) {

        for (int i = 0; i < arr.size(); i++) {
            Bin bin = arr.get(i);
            if(bin.check(item)) {
                bin.add(item);
                return;
            }
        }

        Bin bin = new Bin();
        if(bin.check(item)) bin.add(item);
        arr.add(bin);
    }
}
```



## 2. Next Fit

##### Next Fit(다음 적합)은 직전에 물건을 넣은 통에 여유가 있으면 새 물건을 넣는다.







## 코딩

![nf](https://user-images.githubusercontent.com/62889378/83906954-769f2000-a79f-11ea-8c2a-4a0a8857e3bc.PNG)

```java
import java.util.ArrayList;

public class NextFit implements Fit{

    @Override
    public void fit(ArrayList<Bin> arr, Item item) {

        for (int i = 0; i < arr.size(); i++) {
            Bin bin = arr.get(arr.size()-1);
            if(bin.check(item)) {
                bin.add(item);
                return;
            }
        }

        Bin bin = new Bin();
        if(bin.check(item)) bin.add(item);
        arr.add(bin);

    }

}
```



## 3. Best Fit

##### BestFit(최선 적합)은 기존의 통 중에서 새 물건이 들어가면 남는 부분이 가장 적은 통에 새 물건을 넣는다.







## 코딩

![bf](https://user-images.githubusercontent.com/62889378/83906946-72730280-a79f-11ea-8f4d-09bc0f2de62c.PNG)

```java
import java.util.ArrayList;

public class BestFit implements Fit{

    @Override
    public void fit(ArrayList<Bin> arr, Item item) {

        int remain = 10;
        int rN = -1;
        for (int i = 0; i < arr.size(); i++) {
            Bin bin = arr.get(i);
            if (bin.check(item)) {

                if (remain < bin.remainCapacity - item.size)
                    remain = remain;
                else if (remain > bin.remainCapacity - item.size) {
                    remain = (bin.remainCapacity - item.size);
                    rN = i;
                } else
                    remain = remain;

            }
        }

        Bin bin;
        if (rN == -1) {
            bin = new Bin();
            if (bin.check(item)) bin.add(item);
            arr.add(bin);
        } else {
            bin = arr.get(rN);
            bin.add(item);
        }

    }

}
```



## 4. Worst Fit

##### Worst Fit(최악 적합)은 기존의 통 중에서 새 물건이 들어가면 남는 부분이 가장 큰 통에 새 물건을 넣는다.







## 코딩

![wf](https://user-images.githubusercontent.com/62889378/83906956-77d04d00-a79f-11ea-985a-2c4e10c137d4.PNG)

```java
import java.util.ArrayList;

public class WorstFit implements Fit{

    @Override
    public void fit(ArrayList<Bin> arr, Item item) {

        int remain = -1;
        int rN = 10;
        for (int i = 0; i < arr.size(); i++) {
            Bin bin = arr.get(i);
            if (bin.check(item)) {

                if (remain > bin.remainCapacity - item.size)
                    remain = remain;
                else if (remain < bin.remainCapacity - item.size) {
                    remain = (bin.remainCapacity - item.size);
                    rN = i;
                } else
                    remain = remain;

            }
        }

        Bin bin;
        if (rN == 10) {
            bin = new Bin();
            if (bin.check(item)) bin.add(item);
            arr.add(bin);
        } else {
            bin = arr.get(rN);
            bin.add(item);
        }

    }

}
```