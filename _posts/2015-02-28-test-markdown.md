---
layout: post
title: Test_title
subtitle: Test_subtitle
categories: test
tags: [test]
---

You can write regular [markdown](http://markdowntutorial.com/) here and Jekyll will automatically convert it to a nice webpage.  I strongly encourage you to [take 5 minutes to learn how to write in markdown](http://markdowntutorial.com/) - it'll teach you how to transform regular text into bold/italics/headings/tables/etc.

**Test bold text**

## Test secondary heading

Test table:

| col_0 | col_1 | col_2 |
| :------ |:--- | :--- |
| Five | Six | Four |
| Ten | Eleven | Nine |
| Seven | Eight | Six |
| Two | Three | One |

Test_image

![Crepe](https://ifh.cc/g/L0T0Xu.jpg)
Samseong station


code chunk:

~~~
var foo = function(x) {
  return(x + 5);
}
foo(3)
~~~

code with syntax highlighting

```javascript
var foo = function(x) {
  return(x + 5);
}
foo(3)
```


And here is the same code with syntax highlighting:

```javascript
var foo = function(x) {
  return(x + 5);
}
foo(3)
```

code with line numbers:

{% highlight javascript linenos %}
var foo = function(x) {
  return(x + 5);
}
foo(3)
{% endhighlight %}

## Boxes
You can add notification, warning and error boxes like this:

### Notification

{: .box-note}
**Note:** This is a notification box.

### Warning

{: .box-warning}
**Warning:** This is a warning box.

### Error

{: .box-error}
**Error:** This is an error box.
