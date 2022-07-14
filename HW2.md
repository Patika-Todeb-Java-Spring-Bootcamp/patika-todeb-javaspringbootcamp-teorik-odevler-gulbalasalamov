### HOMEWORK ANSWERS RELATED TO SPRING & SPRING BOOT CONCEPTS 

---

#### Q1 - What do IOC and DI mean?

---

**Inversion of Control (IoC)**: 
Kontrolun ters cevrilmesi, el degistirmesi anlamaini tasir. 
Ancak bu kavrami anlamak icin once kontrol akisinin (control flow) ne demek oldugunu bilmek gerekir. 
Kontrolden kasit bir uygulamadaki akisin adimlarini, ne zaman neyi nerede cagiracagimizi ve bunlari kontrol edebilmektir.

Uygulamalar kendi akislarini kontrol eder. Ne zaman bir obje olusturacagini, ne zaman o objenin uzerinde methodlar cagiracagini, exceptionlar firlatacagini, sequence halinde bilir. 
Bu standart control flowdur. Application kendi akislarinin sahibidir.

IOC , bir applicationin sahip oldugu akis kontrolunu elinden birakmasi, karsi tarafa vermesidir. 
Temelde frameworkler tarafindan uygulanan bir mekanizmadir.
Dolayisiyla Framework bir application tarafindan extend edildiginde, calistirilip ayaga kaldirildigi zaman, kontrolu ele alir, ve hangi nesneleri nasil ve ne zaman olusturacagini,
hangi objeleri olusturacagini, objeler arasinda nasil dependenciler oldugunu ve nasil yonetecinigini Dependency Injection (DI) ve hangi exceptionlari olustracagini, 
hangi eventleri firlatacagini butun bunlara karar veren yapi Framework'in kendisidir. 
Iste buna IoC denir .

IoC, Spring'de kullanilan temel prensiptir ve Spring MVC, Security, Core veya DAO, ne entegrasyonu kullanilirsa kullanilsin, IoC prensibiyle calisacaktir.

**Dependency Injection (DI)**: Spring’in kendi dokumantasyonu da DI ile IoC’yi ayni gorme egilimindedir. DI , IoC ile implemente edilir.
Yani objeleri olustur ve bu objeleri baska bir objeye injecte eder. 
Bunun icin kontrolun bu objeleri olusturan yapida olmasi lazim gerekir, yani Springde olmasi lazim. 
Dolayisiyla DI, IoC ile basarilir. Bu baglamda IoC , DI‘ in arka tarafindaki felsefedir. DI, IoC ile elde ettigimiz seylerden birisidir.

Ancak not etmek gerekir ki birbiriyle ayni seyler degildir. Biz DI olmasa bile IoC ile farkli yapilari implemente edebiliriz. 
Ama sunun da farkinda olmak gerekir ki Spring’den bahsettigimiz zaman objenin lifecycleini yonetmek, eventler olusturmak, 
Aspect Orieented Programming (AOP), butun bunlar herhalukarda obje olusturup onlari birbirine gecirmeyi,
wiringi, gerektirdigi icin cogunlukla insanlar IoC dendigi zaman DI olarak algilamaktadirlar, her nakadar ayni olmasada.

---

#### Q2 - What are Spring Bean Scopes?

---
Spring bize bean oluşturma ve beanlerin yasam dongulerini kontrolmek icin yetkin bir kontrole sahip olma imkani verir. 

Scopes kavramindan once Spring Framework'unde bean'in ne demek oldugunu kavramakta fayda vardir. 
Spring’in IoC containeri tarafindan yonetilen objelere `bean` deriz. 
Spring IoC bean objelerini olusturur, assemble eder yani bir araya getirir, wire eder, ve bir sekilde hayat dongulerini yonetir. 
Spring’in yonetecegi bean’leri ve dependencyleriyle alakali bilgileri, configuration meta data ile birlikte biz container’a saglariz. 
Container’da bu configuration meta datayi kullanarak bizim islerimizi gorur. 
Spring tarafindan olusturulmamis beanler Spring tarafindan yonetilmezler.

Scope olayi ise declare edilmis bir beanden hangi durumlarda nasil obje olusturulacagini belirlemek icin kullanilir. 

| Scope | Açıklama                                                                             |
|----|--------------------------------------------------------------------------------------|
| Singleton | Varsayılan olarak her bean Singleton’dur. Bu Bean’den sadece bir tane üretilir.      |
| Protoype | Bean’e istek geldiğinde oluşturulur. Her istekte farklı bir instance oluşturulur.    |
| Request | Web uygulamaları için kullanılır. Her HTTP isteği geldiğinde instance oluşturulur.   | 
| Session | Web uygulamaları için kullanılır. Her HTTP session oluştuğunda instance oluşturulur. |
| Application | ssd |
| WebSocket | WebSocket'e sahip instancelardir. Tipik olarak Singleton ozellik gosterirler.        |

https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-factory-scopes

---

#### Q3 - What does @SpringBootApplication do?

----

Bu anotasyon @Configuration,  @EnbaleAutoConfiguration, @ComponentScan  anotasyonlarının üçünü de içeren temel bir anotasyondur.

Uygulamalarin beanlerini tanimlandirip yapilandirir, beanleri otomatik tarayip bulur ve ekstra konfigurasyonlari yapar 

 - @Configuration


https://docs.spring.io/spring-boot/docs/current/api/org/springframework/boot/autoconfigure/SpringBootApplication.html


