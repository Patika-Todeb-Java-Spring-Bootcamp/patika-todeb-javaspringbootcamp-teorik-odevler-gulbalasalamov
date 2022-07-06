### HOMEWORK ANSWERS RELATED TO SPRING & SPRING BOOT CONCEPTS 

---

#### Q1 - What do IOC and DI mean?

---

**Inversion of Control (IoC)**: Kontrolun ters cevrilmesi, el degistirmesi anlamaini tasir. 
Ancak bu kavrami anlamak icin once *control flow*'un ne demek oldugunu bilmek gerekir. 
Kontrolden kasit akisin kontrolunu yapmak, bir uygulamadaki akisin adimlarini, ne zaman neyi nerede cagiracagimizi, bunlari kontrol etmektir.

Uygulamalar kendi akislarini kontrol eder. Ne zaman bir obje olusturacagini, ne zaman o objenin uzerinde methodlar cagiracagini, exceptionlar firlatacagini, sequence halinde bilir. 
Bu standart control flowdur. Application kendi akislarinin sahibidir.

IOC , bir applicationin sahip oldugu akis kontrolunu elinden birakmasi, karsi tarafa vermesidir. Temelde frameworkler tarafindan uygulanan bir mekanizmadir.
Dolayisiyla Framework bir application tarafgindan extend edildiginde, calistirilip ayaga kaldirildigi zaman, kontrolu ele alir, ve hangi nesneleri nasil ve ne zaman olusturacagini,
hangi objeleri olusturacagini, objeler arasinda nasil dependenciler oldugunu ve nasil yonetecinigini (DI ile) ve hangi exceptionlari olustracagini, hangi eventleri firlatacagini butun bunlara karar veren yapi Framework'in kendisidir. 
Iste buna IOC denir .

sdsd

---

#### Q2 