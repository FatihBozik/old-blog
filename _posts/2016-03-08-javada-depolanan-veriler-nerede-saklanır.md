---
layout: post
title: Java'da Depolanan Veriler Nerede Saklanır?
tags: [java, heap, stack]
comments: true
---

## Değişkenler

Java'da **primitif** ve **referans** değişkeni olmak üzere 2 tip değişken vardır.

### Primitive değişkenler (primitive variable)
Primitive değişkenler değerlerini kendi üzerlerinde taşırlar. Bunlar 8 tipten biri olabilir `byte`, `short`, `int`, `long`, `char`, `float`, `double`, `boolean`.

<!-- more -->

### Referans değişkeni (reference variable)
Referans değişken bir nesneyi işaret eder (C/C++ programcıları bunları C'deki **pointer**lara benzetebilir). Referans değişkenlerine örnek olarak herhangi bir sınıf tipindeki değişkenleri verebiliriz. Örnek `Date date`, `String str`.

Primitive değişkenler ve referans değişkenleri nerede ve nasıl tanımlandığıyla ilgili olarak

* **class variable :** Sınıfa ait değişken,
* **instance variable :** Nesneye ait değişken, 
* **local variable** : Metodun içinde tanımlanan değişken (metod parametreleri de dahil) olabilirler.

##Veriler Nerede Saklanır?
* Tüm nesneler **heap**de depolanır. Örnek değişkenler(instance variables) de nesneye ait olduklarından **heap**de depolanır.

* Tüm local değişkenler **yığın (stack)**da depolanır.

* Sınıf değişkenleri (yani static tanımlanmış değişkenler) Java 7'de heap bölgesi içinde yer alan **PermGen (Permanent Generation)** adı verilen özel bir alanda depolanıyorlardı. Java 8 ile birlikte PermGen alanı kaldırıldı. JDK 1.8 HotSpot JVM, sınıf metadatalarını **Metaspace** alanında depoluyor. Bu alan Java Process Heap(Native Memory) alanında yer alıyor. Özetlersek static tanımlanmış değişkenler Java 8 de native memory içinde Metaspace alanında. Java 7 de heap bölgesi içinde yer alan PermGen alanında depolanıyor.

<img style="max-width: 45%;" align="left" src="/images/javada-depolanan-veriler-nerede-saklanır/permgen.png" alt="Oracle HotSpot Heap Structure" height="auto">

<img style="max-width: 45%;" align="right" src="/images/javada-depolanan-veriler-nerede-saklanır/metaspace.png" alt="JDK 1.8 Oracle HotSpot Heap Structure" height="auto">

<br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>

## Analiz

Örnek bir kod üzerinden anlatmak gerekirse, 

{% highlight java %}
import java.util.Date;

public class Test {
    int g = 3;
    static int h = 10;
    Integer i = 12;
    MyClass myClass2 = new MyClass();
    static MyClass myClass3 = new MyClass();
    static Integer j = 11;

    public static void main(String args[]) {
        double a = 5.4;
        Double b = 18.0;
        MyClass myClass = new MyClass();
        myClass.setName("fatih");
    }
}

class MyClass {
    int age = 10;
    static int number = 15;
    Date myDate = new Date();
    String name;
    static String str = "String Deneme";

    public void setName(String param) {
        this.name = param;
    }
}
{% endhighlight %}

* `g`, `i`, `myClass2` değişkenleri instance variable olduklarından bu değişkenler oluşturulmaz (programımızda hiç Test nesnesi oluşturmadık). Hiç bir yerde depolanmaz. Dolayısıyla initialization(ilk değer atamaları) da yapılmaz. `myClass2 referans değişkeninin göstereceği MyClass nesnesi` de oluşturulmaz. `i referans değişkeninin göstereceği Integer nesnesi` de oluşturulmaz.

* `h`, `j`, `myClass3` değişkenleri sınıf değişkeni olduklarından native memorydeki **metaspace** alanında depolanır (Java 8 için). `myClass3 referans değişkeninin gösterdiği MyClass nesnesi` heapte depolanır. Aynı şekilde `j nesnesinin gösterdiği Integer nesnesi` **heap**te depolanır.

* `a`, `b` ve `myClass` local değişken olduklarından **stack**te depolanır.

* b referans değişkeninin gösterdiği `Double nesnesi` **heap**te depolanır.

* myClass referans değişkeninin gösterdiği `MyClass nesnesi` **heap**te depolanır.

* `age`, `myDate`, `name` değişkenleri instance variable olduklarından nesne ile birlikte **heap**te depolanır. myDate referans değişkeninin gösterdiği `Date nesnesi` **heap**te depolanır. Aynı şekilde name referans değişkeninin göstereceği nesne **heap**te depolanır (new ile oluşturulmadığından dolayı heap içinde **string constant pool** denilen alanda bulunur).

* `number`, `str` sınıf değişkenleri native memorydeki **metaspace** alanında depolanır. str referans değişkeninin gösterdiği `String nesnesi` **heap**te depolanır. (heap içinde **string constant pool** denilen alanda)

* `param` local değişken olduğundan **stack**te depolanır.

* `args` local değişkeni **stack**te depolanır.

* setName methoduna gönderilen argümanda `"fatih"` bir nesne olduğundan heap alanında depolanır. (**string constant pool** denilen alanda)