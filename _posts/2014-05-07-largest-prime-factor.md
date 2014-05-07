---
layout: post
title: "一个寻找最大素因子的算法"
description: ""
category: 
tags: ["Project Euler", "Algorithms"]
---
{% include JB/setup %}

被[Project Euler](http://projecteuler.net/problems)的第三题卡住了...题目如下:

>The prime factors of 13195 are 5, 7, 13 and 29.
>What is the largest prime factor of the number 600851475143 ?

我的brute force的代码就不贴了, 反正跑不出结果... 在网上搜到一个答案并提交后, 进到这道题的讨论区里, 发现@bitRAKE的一个非常简短的代码(原代码是C, 我改为了python):
<!--more-->
{% highlight python linenos %}
def largest_prime_factor(n):
    divisor = 2
    while n > 1:
        if n % divisor == 0:
            n /= divisor
            divisor -= 1
        divisor += 1
    return divisor
{% endhighlight %}

第一反应就是竟然不用判断是否素数?! 一番思考后, 才理清了这里面的原理.

任意一个大于1的正整数N都能写成<code>N = P<sub>1</sub> * P<sub>2</sub> * ... * P<sub>i</sub></code>. 其中<code>P<sub>1</sub></code>到<code>P<sub>i</sub></code>为从小到大排列的素数, 相邻的两个数可能相等(如`4 = 2 * 2`). 于是<code>P<sub>i</sub></code>就是我们要找的最大素因子.

显然, 要找到<code>P<sub>i</sub></code>, 只需计算<code>N / (P<sub>1</sub> * P<sub>2</sub> * ... * P<sub>i - 1</sub>)</code>就可以了, 以此类推, 需要依次找到<code>P<sub>1</sub></code>, <code>P<sub>2</sub></code>..., 废话...
