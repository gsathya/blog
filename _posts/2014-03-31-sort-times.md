---
layout: post
title:  "Sort Times"
date:   2014-03-31 11:34:57
categories: puzzles
---

[Problemotd](http://www.problemotd.com/) had a fun litle
[problem](http://www.problemotd.com/problem/sort-times/) today. I
suggest you try it out before reading further. Spoilers ahead!

Most of the solutions on the comments of that page use sorting to
solve it. This is suboptimal since sorting takes O(nlogn). The key
thing to note here is that there is an upper bound on the maximum
value in the input list -- 23. Therefore, we can use count sort to
"sort" this in O(n) running time with constant space(array of size
24).

Here's the code in python -

{% highlight python %}
ip = [2,1,12,3,16,19,23]
array = [0]*24
ans = []

for i in ip:
    array[i]+=1

for id, i in enumerate(array[12:]):
    for t in range(i):
        ans.append(id+12)

for id, i in enumerate(array[:12]):
    for t in range(i):
        ans.append(id)

print ans
{% endhighlight %}
