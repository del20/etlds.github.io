---
layout: post
title:  "How I Python LeetCode"
date:   2016-09-12 15:16:57 -0400
categories: live
comments: true
---
LeetCode and Me
======
I have solved [LeetCode][leetcode]'s Problems from top to bottom for more than 3 times couple years ago. Now the site becomes more sophisticated and collects a lot of new problems. It is time for me to go through it again to keep my brain running.

Why Python
======
I used Java to code these problems before, not because I am good at Java, conversely I am a newbie. I barely use Java for any other thing beside playing LeetCode. I use Java because it is plain and easy, every programmer would know it, so it would be no barrier between me and the interviewer when I am in the coding interview. Why I want to try python? I developed web application using ruby on rails for a while and find it really elegant. Writing ruby is just like writing English. I think Python, another interpreted language will give me the same experience (I was wrong!). Another reason is, Google is still my dream company.

Problem
======
This problem is called [Perfect Rectangle][perfect-rectangle]. Determine if rectangles all together form a exact cover of a rectangular region, no overlap, no missing area. This problem rated **"HARD"** because it is not related to any other problems. I don't like it and I don't think it is a good coding interview problem. If the candidate crack your problems in 10 minutes, and you still have time, you can try ask them this one.

Algorithm
======
The algorithm has couple parts
1. Keep tracking the most bottom-left corner and most top-right corner
2. Keep tracking the total area of all the rectangles that provided.
3. Put all the corners into a hash (key: x-y, value: type) and flag their type. I use "x-y" as key,  and bit flag for types (top-left, bottom-left, bottom-right, top-right).
4. Determine if overlap in loop. Determine if missing by counting single type corners and compare total area.

Pythonic Code Tips
======
{% highlight python linenos %}
import sys

class PerfectRectangle:
    def __init__(self):
        self.__corners = {}

    def isRectangleCover(self, rectangles):
        """Perfect Rectangle
        Determine if rectangels all together form a exact cover of a rectangular region

        Args:
            rectangles (List[List[int]]): [[bottom-left-x, bottom-left-y, top-right-x, top-right-y], ...]
            examples:
                rectangles = [
                  [1,1,3,3],
                  [3,1,4,2],
                  [3,2,4,4],
                  [1,3,2,4],
                  [2,3,3,4]
                ]

        Returns:
            bool: True or False
        """
        if len(rectangles) == 0 or len(rectangles[0]) == 0:
            return False

        # keep tracking the most bottom-left and top-right corners
        lx = ly = sys.maxsize
        rx = ry = -sys.maxsize
        # keep tracking the total area
        area_sum = 0

        for rect in rectangles:
            # keep tracking the most bottom-left and top-right corners
            lx, ly, rx, ry = min(lx, rect[0]), min(ly, rect[1]), max(rx, rect[2]), max(ry, rect[3])
            # keep tracking the total area
            area_sum += (rect[2] - rect[0]) * (rect[3] - rect[1])
            # bottom-left
            if self.__overlap("{}-{}".format(rect[0], rect[1]), 1):
                return False
            # bottom-right
            if self.__overlap("{}-{}".format(rect[2], rect[1]), 2):
                return False
            # top-left
            if self.__overlap("{}-{}".format(rect[0], rect[3]), 4):
                return False
            # top-right
            if self.__overlap("{}-{}".format(rect[2], rect[3]), 8):
                return False

        # single type corners' count
        count = len(filter(lambda x: x in [1, 2, 4, 8], self.__corners.values()))

        # Has and only has 4 single type corner and total area equal to width * height
        return count == 4 and area_sum == (rx - lx) * (ry - ly)

    def __overlap(self, corner, corner_type):
        """Check if current rectangle has SAME CONRNER overlap with the previous ones.

        Args:
            key (str): String that represent a corner in format 'x-y'
            corner_type (int): Coner type in [1,2,4,8]
            example:
                key: '2-3'
                corner_type: 1

        Returns:
            bool: True for SAME CONRNER overlap, False for no  SAME CONRNER overlap
        """
        tmp = self.__corners.get(corner, None)
        if tmp is None:
            tmp = corner_type
        elif tmp & corner_type:
            return True
        else:
            tmp |= corner_type
        self.__corners[corner] = tmp
        return False

{% endhighlight %}

Once you have the algorithm, code would be really simple. But there are some of the things I have learn to write pythonic code.

[Google Python Style Guide][googld-python-style-guide]
------
Google has a style guide every python programmer should follow. One thing I learn is the docstring in python. It use triple double quote to wrap the class or method's description, argument and return type. Someone who pick up your code or a 3 months later yourself would understand the code in a second.

Dictionary's get method
------
Yes, Python call it dictionary. The get method helps you get rid of if else statement when put a new entry in. This is what I do in Java a lot.

Instead of doing this...
{% highlight python linenos %}
total_sales = {}
for (product, price) in data:
    if product not in total_sales:
        total_sales[product] = 0
    total_sales[product] += price
{% endhighlight %}
We can do this...
{% highlight python linenos %}
total_sales = {}
for (product, price) in data:
    total_sales[product] = total_sales.get(product, 0)
{% endhighlight %}

Functional Programing
------
Functional Programing is powerful. It seems like you just tell the language what to do instead of tell it how to do it. But my opinion is, use it for simple case, and use sub function for complicated case. And also, in style guide, we have 80 characters limit on each line. That is why I recommend this.

Both ways work perfectly and pythonic. So I put them here for comparison.
{% highlight python linenos %}
count = len(filter(lambda x: x in [1, 2, 4, 8], self.__corners.values()))
{% endhighlight %}
{% highlight python linenos %}
count = len([x for x in self.__corners.values() if x in [1,2,4,8]])
{% endhighlight %}

What I don't like python
------
**indentation**

It drive me crazy sometime, even it saves you a `}` or `end`. I don't know how develops keep their file in sync by setting default indent a tab or four spaces.

**len()**

I don't like get size of array or tuple in this way. In Ruby we just do `arr.size` or `arr.count`

{% if page.comments %}
<div id="disqus_thread"></div>
<script>

/**
 *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
 *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables */
/*
var disqus_config = function () {
    this.page.url = PAGE_URL;  // Replace PAGE_URL with your page's canonical URL variable
    this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
(function() { // DON'T EDIT BELOW THIS LINE
    var d = document, s = d.createElement('script');
    s.src = '//etlds.disqus.com/embed.js';
    s.setAttribute('data-timestamp', +new Date());
    (d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
{% endif %}

[leetcode]: https://leetcode
[perfect-rectangle]: https://leetcode.com/problems/perfect-rectangle/
[googld-python-style-guide]: https://google.github.io/styleguide/pyguide.html
