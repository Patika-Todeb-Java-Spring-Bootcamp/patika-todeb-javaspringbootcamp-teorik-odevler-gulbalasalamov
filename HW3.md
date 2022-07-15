### Homework 3 

This homework covers answers for the questions about the following topics:

- GIT
- Fundamentals of Spring and Spring Boot
- Comparison of Spring and Spring Boot
- Spring Boot annotations

Answers to questions are in **Turkish**.

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

Bu anotasyon @Configuration,  @EnableAutoConfiguration, @ComponentScan  anotasyonlarının üçünü de içeren temel bir anotasyondur.

Uygulamalarin beanlerini tanimlandirip yapilandirir, beanleri otomatik tarayip bulur ve ekstra konfigurasyonlari yapar.

 - `@Configuration`: Tanimlandigi sinifin bean tanimlamalari icin kaynak oldugunu ve Spring IoC container tarafindan kullanilacagini belirtir.
 - `@EnableAutoConfiguration`: Spring Boot'un jar dependency, classpath ve bizler tarafindan tanimlanmis objeleri otomatik olarak olusturup kaydetmesini saglar.
 - `@ComponentScan`: Spring'in Spring tarafindan yonetilen bilesenleri bulmasi icin kullanilir.
XML tabanli konfigurasyonda <context: component-scan> taginin yaptigi isi yapar. @Autowired annotationlarin calismasi icin eklenir. Boylece configuration, controller, service ve dahasi bilesenler aranir. 
@ComponentScan anotasyonu @Configured anatasyonuyla beraber kullanilir ve aranacak bilesenlerin packagelarinin yeri gosterilir.


https://docs.spring.io/spring-boot/docs/current/api/org/springframework/boot/autoconfigure/SpringBootApplication.html

----

#### Q4 - Why Spring Boot over Spring?

----

Spring Boot, production seviyesinde Spring tabanlı uygulamalar oluşturmayı kolaylaştırır ve çok az Spring konfigürasyonuna ihtiyaç duyar.

Spring Boot'un esas aldigi hedefler:

- Tüm Spring geliştirmeleri için daha hızlı ve geniş çapta erişilebilir bir başlangıç deneyimi sağlamak,
- Varsayılan gereklilik ve dependency'lerin optimize edilerek eklenmesi, 
- Gömülü sistem sunucuları, guvenlik, durum kontrolleri vb buyuk projeler icin kullanisli ozellikler saglamasi
- XML tabanli yapilandirma ve konfigurasyona ihtiyac duymamak 

Spring Boot'un Spring'e kiyasla avantajlarina daha derinlemesine bakarsak:

- Java -jar komutuyla calistirilabilecek standalone bagimsiz uygulamalar yaratmak,
- Tomcat, Jetty vb gomullu sunucularin yardimiyla web uygulamarini test edebilmek,
- Maven konfigurasyonunu basitlestirmek icin varsayilan starter bir pom.xml dosyasi ile gelmesi
- Production-ready ozellikleri barindirmasi
- XML ayarlarina gerek duymamak
- Gelistirme ve test icin CLI tool icermesi
- Bir cok plug-in'e sahip olmasi
- Boilerplate kodlar, XML konfigurasyon ve anastosyanlarini minimize etmesi
- Uretkenligi artirma

Özetlemek gerekirse Spring Boot, standart Spring Framework'unun tüm işlevlerini içerir ve aynı zamanda uygulama geliştirmeyi çok daha kolay hale getirir. 
Spring ile karşılaştırıldığında, tüm Spring Boot öznitelikleri otomatik olarak yapılandırıldığından, bir uygulamayı çok daha kısa sürede hazır hale getirip çalıştırabiliriz.

https://spring.getdocs.org/en-US/spring-boot-docs/getting-started/getting-started-introducing-spring-boot.html

----

#### Q5 - What is Singleton and where to use it?

----

Spring Frameworku ApplicationContext ile yuklendigi zaman bir bean olusturur ve eger ontanimli scope degistirilmemisse bunu Singleton olarak yapar.

Singleton aslinda bir yazilim mimarisi pattern’idir ve tekil anlami tasir. Bir siniftan tek bir nesne olusmasini enforce ediyorsak, 
ister programatik olarak, ister farkli toollarla ki Spring de bunlardan birisidir, sadece tek bir nesne olusturulsun baska nesne olusturulmasin istiyorsak bu mimariye Singleton deriz. 

Teknik olarak bakarsak Singleton adinin da cagristiracagi uzere 1 tane olan demek, unique olan demek, tek olan demek 
dolayisiyla Spring'de Singleton olarak tanimladigimiz zaman ya da defeaultta biraktigimiz zaman 
@Component ile anatotate edilse veya klasik XMLde de konmus olsa sinifiyla, id siyle , aliasiyle, 
biz her gereken yerde yeni bir nesne olusturmayacak, bir tane olusturup bunu her yerde kullanacagiz. 
Dolayisiyla tek bir instancei olan seye singleton deriz.

Singletonlar multi-thread servis objeleri icin siklikla kullanilir. Web ortamlari icin request ve session scopelari vardir.

----

#### Q6 - Explain @RestController annotation in Sprint boot?

@RestController anatasyonu `@Controller` ve `@ResponseBody` anatasyonlarinin birlesimidir.
Controller, Spring icerisinde uzun zamandir bulunan bir yapi. RestController ise Spring 4.0 ile geldi.
Temel amaci ilgili sınıftaki bütün metodların birer REST EndPoint'lerini (servis noktası) uretmeyi saglamak.
Kolayligi ise bu islem icin Controller ve ResponseBody notasyonlarini tek seferde vermesi.
Bu sayede REST controller olmasını isteyeceğimiz her metoda @ResponseBody yazmaktan da kurtulmuş oluyoruz.

RestController sinifinin metotlarinda kullanilan anatasyonlar

- @GetMapping : Get istegi
- @PostMapping : Post istegi
- @DeleteMapping : Delete istegi 
- @PathVariable : Methodlara gecilen parametreler

RestController donen datanin direkt JSON/XML olmasini otomatik saglayabiliyor. 

https://docs.spring.io/spring-boot/docs/2.0.9.RELEASE/reference/html/getting-started-first-application.html#getting-started-first-application-annotations

----

#### Q7 - What is the primary difference between Spring and Spring Boot?

----

Spring, Java EE'ye gore daha lightweight bir uygulama gelistirme framework'udur. 
Spring, mimari olarak bakildigi zaman frameworkleri iceren frameworklerden olusur. Uygulama gelistirmek icin bir cok framework bulunur (JSP, Hibernate vb)

Spring Boot ise Spring tabanli bir framework olup esas olarak REST API gelistirmek icin kullanilir.

Spring'in Java EE'den en temel farki getirdigi Dependency Injection (DI) ozelligidir. 
Spring Boot'un ise en temel farki Autoconfiguration (otomatik konfigurasyon) ile Spring'in on yuklemesini otomatik yapilandirmasidir. 

Spring Boot frameworkleri sayesinde developerlar development suresini ve sarfedilen eforu azaltabilir, uretkenligi artirabilir.

----

#### Q8 - Why to use VCS?

----

Version Control System (VCS) yazılımların versiyonlarının takip edildiği sürüm takip sistemidir.
Git bunlardan en populer olanıdır. Git, yazılım geliştirme sırasında kaynak koddaki değişiklikleri izler.
Programcılar arasındaki çalışmaları koordine etmek için tasarlanmıştır. 
Hız, veri bütünlüğü ve dağıtılmış, doğrusal olmayan iş akışları için destek içerir.

Git bir yazılım iken GitHub ve GitLab ornegin 
Git hizmeti verebilen web tabanlı grafik arayüzü olan bir Git depo barındırma hizmetidir.

GitHub vb servisler kullanmak Git deneyimini artirir ve ekstra avantajlar da saglar:

- Kisisel calisma ve projeleri sergilemek, genis kitlelere yayilmak
- Acik kaynakli projelere destek olmak
- Var olan proje, bilgi ve dokumanlara kolay erisim
- Markdown ile dokumantayon




