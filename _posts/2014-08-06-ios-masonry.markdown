---
layout: post
title:  "iOS Auto Layout using Masonry"
date:   2014-08-06 21:04:59
categories: technical
---

I kept telling myself I was going to use auto layout but could never bring myself to do it in the end. Maybe I just thought what I was currently doing was fine and I didn't need to change. I would always start a view and say "I'm going to use auto layout here for sure!" but then I found myself getting frustrated and I would just uncheck the auto layout checkbox. I then scrapped trying to use interface builder for my auto layout needs and went straight to code. But that wasn't pretty either. It was just too much code...

## But then I found [Masonry](https://github.com/Masonry/Masonry)
Masonry makes using Auto Layout fun! Yes I said it. Fun. I'm so glad I found a tool that made Auto Layout just make more sense. In short, Masonry is a wrapper for the Auto Layout framework to make constraint code more concise and readable.  Let's look at an example. If I wanted to add a UIImageView subview to my view and pin it to the edges of the view, it would look something like this:

{% highlight Objective-C %}
[imageView mas_makeConstraints:^(MASConstraintMaker *make) {
    make.edges.equalTo(superview);
}];
{% endhighlight %}

But you're probably saying, "Well that's simple, what if I wanted to do something more precise?" You can. For example, say you wanted this for the same UIImageView.

* 200 pts width and height
* Centered X
* Exactly 50 pts below a UILabel

The code would look something like this:

{% highlight Objective-C %}
[imageView mas_makeConstraints:^(MASConstraintMaker *make) {
    make.top.equalTo(label.mas_bottom).with.offset(50);
    make.centerX.equalTo(superview);
    make.height.equalTo(200);
    make.width.equalTo(200);
}];
{% endhighlight %}

The code is very readable and any iOS developer will immediately know what is going on with the constraints.

So far I have only scratched the surface of what Masonry can do and I am already having tons of fun. It has also allowed me to jump into Auto Layout a lot quicker. If you want to learn more about Masonry visit their [Github repo](https://github.com/Masonry/Masonry) and see what it can do for you!