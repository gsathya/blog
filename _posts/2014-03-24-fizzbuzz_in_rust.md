---
layout: post
title:  "FizzBuzz in rust"
date:   2014-03-24 22:11:11
comments: true
categories: rust
---

I've recently started learning [Rust](http://www.rust-lang.org/) and here's a Rust implementation of the [FizzBuzz](http://c2.com/cgi/wiki?FizzBuzzTest) test. 


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

[samebchase](http://codesurfers.net/~samuel/) pointed out this interesting [post](http://composition.al/blog/2013/03/02/fizzbuzz-revisited/) on the solving FizzBuzz using the patern matching capabilities of Rust. Rust's pattern matching is certainly powerful, especially the destructuring property, which is sort of like unpacking in Python.
