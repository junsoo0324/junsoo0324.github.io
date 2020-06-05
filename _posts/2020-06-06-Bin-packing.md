---
layout: single
title: Bin 문제풀이
time: 2020-06-06 01:30 +09:00
author: JunSoo
---

## 1.FirstFit

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



## 2.NextFit

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



## 3.BestFit

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



## 4.WorstFit

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