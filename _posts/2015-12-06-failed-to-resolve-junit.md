---
layout: post
title: "Failed to resolve: junit:junit:4.12"
tags: [android studio gradle error, junit error]
comments: true
---

###Hata
Ubuntu işletim sisteminde Android Studio'da yeni bir proje oluşturduğumda karşılaştığım bir hata.

<img style="max-width: 100%;" src="/images/failed-to-resolve-junit/junit error.png" alt="Grandle junit hatası" height="auto">

<!-- more -->

###Çözüm
`../AndroidStudioProjects/{ProjectName}/app/build.gradle` dosyası aşağıdaki gibi düzenlenir.
{% highlight groovy %}
android {
    ...
    repositories {
        maven { url 'http://repo1.maven.org/maven2' }
    }
}
{% endhighlight %}
<<<<<<< HEAD

~~~
markdown: kramdown
mathjax: true
~~~

Here is an example MathJax inline rendering \\( 1/x^{2} \\), and here is a block rendering: 
\\[ \frac{1}{n^{2}} \\]
=======
>>>>>>> 0b471e5a7f0976f99288d2c0e2cb684e0454758b
