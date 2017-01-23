---
layout: post
title:  "FizzBuzz in rust"
date:   2014-03-24 22:41:11
comments: true
categories: rust
---

I've recently started learning [rust](http://www.rust-lang.org/) and
here's a rust implementation of the [FizzBuzz](http://c2.com/cgi/wiki?FizzBuzzTest)
test -


{% highlight rust %}
fn main() {
    let mut count: int = 1;
    let mut ans: ~str;
    
    while count < 101 {
        ans =
            if count % 15 == 0 { ~"FizzBuzz" }
            else if count % 3 == 0 { ~"Fizz" }
            else if count % 5 == 0 { ~"Buzz" }
            else { count.to_str() };

        println!("{}", ans);
        count += 1;
    }
}

{% endhighlight %}

[samebchase](http://codesurfers.net/~samuel/) pointed out this
interesting [post](http://composition.al/blog/2013/03/02/fizzbuzz-revisited/)
on the solving FizzBuzz using the patern matching capabilities of
rust. Rust's pattern matching is certainly powerful, especially the
destructuring property, which is sort of like unpacking in python.

Here's the same problem in python(which, incidentally, is exactly what I
wrote during my Mozilla interview) - 

{% highlight python %}
def fizzbuzz():
    for i in range(1, 101):
        ans = ""
        if i % 3 == 0:
            ans += "Fizz"
        if i % 5 == 0:
            ans += "Buzz"
        if ans == "":
            ans = i
        print ans
{% endhighlight %}

The python code just seems more elegant in my opinion. Or maybe my rust just sucks.
