---
layout: single
title: Generic-Algorism(롤 챔피언과 승률의 관계)
time: 2020-06-26 18:21 +0900
author: JunSoo
---



## GA (유전 알고리즘)

##### 롤 챔피언과 승률의 상관관계

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collections;
import java.util.Random;

public class Main {

    public static int MSE(int a, int b, int[] x, int[] y){
        int MSE = 0;
        for(int i = 0 ; i < y.length ; i ++){
            MSE += Math.pow(y[i] - (a*x[i] + b), 2);
        }
        return MSE;
    }
    //MSE 함수 구현

    public static int[] initA() {
        Random r = new Random();
        int[] a = new int[4];
        for(int i=0; i<4; i++) {
            a[i] = r.nextInt(31) + 1;
        }

        return a;
    }
    //랜덤으로 A를 4개 고름

    public static int[] initB() {
        Random r = new Random();
        int[] b = new int[4];
        for(int i=0; i<4; i++) {
            b[i] = r.nextInt(50) + 1;
        }

        return b;
    }
    //랜덤으로 B를 4개 고름

    public static int[] selection(int[] a,int[] b, int[] x, int[] y) {
        int sum = 0;
        int[] f = new int[a.length];
        for(int i=0; i < a.length; i++) {
            f[i] = MSE(a[i],b[i],x,y); //f[i]함수에 MSE 값 저장
            sum += f[i]; //f값의 합 만들기
        }

        double[] ratio = new double[a.length];
        for(int i=0; i < a.length; i++) {
            if(i==0) ratio[i] = (double)f[i]/(double)sum; //i=0 일때 비율 최대로
            else ratio[i] = ratio[i-1] + (double)f[i] / (double)sum; //i!=0 일때 비율 점차 줄이기
        }

        int[] ab = new int[a.length * 2];
        Random r = new Random();
        for(int i=0; i<a.length; i++) {
            double p = r.nextDouble();
            if(p < ratio[0]) {
                ab[i] = a[0];
                ab[i+a.length] = b[0];
            }
            else if(p < ratio[1]) {
                ab[i] = a[1];
                ab[i+a.length] = b[1];
            }
            else if(p < ratio[2]) {
                ab[i] = a[2];
                ab[i+a.length] = b[2];
            }
            else {
                ab[i] = a[3];
                ab[i+a.length] = b[3];
            }
        } //루프 돌려서 각 후보해 마다 뽑힐 확률 구하기

        return ab;
    }

    public static String int2String(String x) {
        return String.format("%8s", x).replace(' ', '0');
    }

    public static String[] crossOver(int[] x) {
        String[] arr = new String[x.length];
        for(int i=0; i<x.length; i+=2) {
            String bit1 = int2String(Integer.toBinaryString(x[i]));
            String bit2 = int2String(Integer.toBinaryString(x[i+1]));


            arr[i] = bit1.substring(0, 2) + bit2.substring(2, 5);
            arr[i+1] = bit2.substring(0, 2) + bit1.substring(2, 5);
        }

        return arr;
    }

    public static int invert(String x) {
        Random r = new Random();
        int a = Integer.parseInt(x, 2);
        for(int i=0; i<x.length(); i++) {
            double p = (double)3/ (double)100;
            if(r.nextDouble() < p) {
                a = 1 << i ^ a;
            }
        }
        return a;
    }

    public static int[] mutation(String[] x) {
        int[] arr = new int[x.length];
        for (int i=0; i<x.length; i++) {
            arr[i] = invert(x[i]);
        }
        return arr;
    }

    public static void main(String[] args) {
        //y= ax + b
        int[] a = initA();
        int[] b = initB();

        int[] x = {1,2,7,12,17,20,22}; //픽률
        int[] y = {46,47,48,49,50,21,52}; //승률
        int[] ab_MSE = new int[a.length];
        int a_f = 0;
        int b_f = 0;
        int min = 100000;

        for(int i=0; i<1000; i++) {
            int[] ab = selection(a,b,x,y);
            String[] cx = crossOver(ab);
            int[] mx = mutation(cx);

            for (int j = 0; j <a.length ; j++) {
                a[j] = mx[j];
                b[j] = mx[j+a.length];
            }

            for(int j = 0; j <a.length; j++) {
                ab_MSE[j] = MSE(mx[j], b[j], x, y);
                if (min > ab_MSE[j]) {
                    min = ab_MSE[j];
                    a_f = a[j];
                    b_f = b[j];
                }
            }

            }

        System.out.println( "y = " + a_f + "x + " + b_f );
        }
    }
```