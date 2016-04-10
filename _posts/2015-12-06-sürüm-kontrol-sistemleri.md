---
layout: post
title: Sürüm Kontrol Sistemleri(Version Control Systems) Hakkında
tags: [version control systems, git]
comments: true
---

Sürüm kontrol sistemleri, dosyalar üzerinde yaptığımız değişiklikleri kayıt altına almamıza ve daha sonra bu kayıtlara geri dönebilmemize olanak sağlayan sistemlerdir.

<!-- more -->

Sürüm kontrol sistemlerini kullanarak

* projenin geçmişteki bir sürümüne erişebilir,
* yapılan değişiklikleri karşılaştırabilir,
* bir dosya üzerinde en son kimin değişiklik yaptığını görebilir,
* bir hata yaptığımızda hataları geri alabiliriz.

<br/>
## Sürüm Kontrol Sistemlerinin Tarihçesi

### Yerel Sürüm Kontrol Sistemleri(Local Version Control Systems)

Dosyalardaki bütün değişiklikleri(dosya sürümlerini) veritabanına kaydeden sürüm kontrol sistemleridir.

<img style="max-width: 100%;" src="/images/sürüm-kontrol-sistemleri/local version control systems.png" alt="Local Control Systems" height="auto">

<br/>
### Merkezi Sürüm Kontrol Sistemleri(Centralized Version Control Systems)

İlerleyen zamanlarda programcıların birlikte çalışması ihtiyacı önemli bir sorun olarak karşımıza çıktı. Bu sebeple `Merkezi Sürüm Kontrol Sistemleri`(CVS, Subversion ve Perforce) adı verilen sürüm kontrolüne alınan bütün dosyaların bir sunucuda tutulduğu sistemler geliştirildi. Bu sistemde kullanıcılar sunucudan istedikleri dosyaları seçerek(checkout) kullanırlar.

<img style="max-width: 100%;" src="/images/sürüm-kontrol-sistemleri/centralized version control systems.png" alt="Centralized Version Control Systems" height="auto">

<br/>
### Dağıtık Sürüm Kontrol Sistemleri(Distributed Version Control Systems)

Yerel ve merkezi kontrol sistemlerinin ikisinde de sürüm kontrolüne alınan dosyalar tek bir bilgisayarda tutulduğundan yedekleme yapılmadığı takdirde merkezi veritabanının sabit diskinde meydana gelebilecek bir hata tüm projenin kaybedilmesine yol açabiliyordu. Bu sorunun çözebilmek için `Dağıtık Sürüm Kontrol Sistemleri`(Git, Mercurial) geliştirildi. Bu sistemlerde istemciler dosyaların yalnızca belelk kopyalarını almakla kalmazlar. Yazılım havuzunu(repository) kopyalarlar. Kullanıcıların yaptığı her seçme işlemi(checkout) bütün verinin yedeklenmesiyle sonuçlanır.

<img style="max-width: 100%;" src="/images/sürüm-kontrol-sistemleri/distributed version control systems.png" alt="Distributed Version Control Systems" height="auto">

<br/><br/>

**Kaynaklar:**<pre>1. [Chacon, S. 2009. Pro Git (1st edition)](http://www.amazon.com/Pro-Git-Scott-Chacon/dp/1430218339)
2. [Başlangıç Sürüm kontrolü hakkında](https://git-scm.com/book/tr/v1/Ba%C5%9Flang%C4%B1%C3%A7-S%C3%BCr%C3%BCm-Kontrol%C3%BC-Hakk%C4%B1nda)</pre>
