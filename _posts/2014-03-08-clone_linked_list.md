---
layout: post
title:  "Clone a linked list"
date:   2014-03-08 19:11:11
comments: true
categories: programming puzzles
---

One of my labmates recently interviewed with Google and we were
discussing the questions. One particular question was pretty interesting -

Given a linked list with a next pointer and a random pointer(points to
a random element in the linked list). Clone the linked list.

The approach I've taken requires `O(n)` time and `O(n)` space. Although,
there's another approach that takes constant space, I'm pretty sure
this would've been good enough for a 30 minute interview. I'll probably
code the other approach next time.

The algorithm is pretty much -

* Clone the original linked list
* While cloning, use a dictionary to create a mapping such that key =
  reference to original node, value = reference to the new node
* Loop through the original list again
    * Set random pointer of every node in the new list using the
      dictionary
  
Here's the python code -

{% highlight python %}
class Node:
    def __init__(self, val):
        self.val = val
        self.next = None
        self.rand = None

def clone(old):
    if not old:
        return

    old_copy = old
    root = Node(old.val)
    prev = root
    temp = None

    old = old.next

    mapping = {}
    
    while old:
        temp = Node(old.val)
        mapping[old] = temp
        
        prev.next = temp
        prev = temp
        old = old.next

    old = old_copy
    temp = root

    while old:
        temp.rand = mapping[old.rand]
        temp = temp.next
        old = old.next

    return root
{% endhighlight %}
