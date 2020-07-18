## Task Nedir ?

Task, yapılması gereken bazı işleri temsil eden bir nesnedir. Task, işin tamamlanıp tamamlanmadığını ve işlemin bir sonuç döndürürse, size sonucu verir. Task sınıfı, bir değer döndürmeyen ve genellikle zaman uyumsuz olarak yürütülen tek bir işlemi temsil eder. Task nesneler, ilk olarak .NET Framework 4 ' te tanıtılan görev tabanlı zaman uyumsuz düzenin merkezi bileşenlerinden biridir. Bir Task nesnesi tarafından gerçekleştirilen iş, genellikle ana uygulama iş parçacığı üzerinde zaman uyumsuz olarak değil, bir iş parçacığı havuzu iş parçacığında zaman uyumsuz olarak yürütülebildiğinden, bir görevin durumunu öğrenmek için, Status özelliğini ve IsCanceled, IsCompletedve IsFaulted özelliklerini de kullanabilirsiniz. En yaygın olarak, görevin gerçekleştireceği işi belirtmek için bir lambda ifadesi kullanılır.

###### Task Ne Zaman Gereklidir ?

Paralel olarak bir şey yürütmek istediğinizde kullanılabilir. 'Async' ve 'await' anahtar kelimelerini kullanarak bir işte Asenkron uygulama kolaydır.

## Thread Nedir ?

Aynı process ortamında birden fazla iş yürütme imkanı sağlar. Bir process’in çalışmaya başlaması ile birlikte bir thread (main thread) oluşturulur ve process içerisinde birden fazla (multi-thread ) oluşturulabilir.

###### Thread Ne Zaman Gereklidir ?

Uygulamanın aynı anda birkaç görevi gerçekleştirmek için gerekli olduğu zaman geldiğinde ihtiyaç duyarız.

### Task vs Thread

- Thread sınıfı, Windows’ta bir 'thread' oluşturmak ve değiştirmek için kullanılır. Task, bazı eşzamansız işlemleri temsil eder ve görevleri eşzamansız ve paralel olarak çalıştırmak için bir dizi API olan 'Task Parallel Library (Görev Paralel Kitaplığı’nın) bir parçasıdır.
- Task bir sonuç döndürebilir. Bir threadde sonucu döndürmek için doğrudan bir mekanizma yoktur.
- Task, iptal belirteçleri kullanılarak iptal işlemini destekler. Ancak Thread değil.
- Bir task’in aynı anda birden çok işlemi olabilir. Thread’lerin aynı anda yalnızca bir görevi olabilir.
- Task, Thread’den daha üst düzey bir kavramdır.

## Thread vs Process

Thread yapıları işletim sistemi işlemlerine benzemektedir. OS içerisinde işlemler birbirine paralel olarak çalışmaktadır. Thread yapısında ise, threadler bir process içerisinde birbirlerine paralel olarak çalışmaktadırlar. İşlemler birbirlerine tamamen izoledir. Threadler birbirlerine tamamen izole değillerdir. Aynı hafızayı paylaşırlar bundan dolayı birlikte çalışan threadler arasından veriler rahatça paylaşılmaktadır.

## Task vs Parallel

Paralel programlama ile sistemin CPU performansı gibi özellikler ön plandadır ve tüm çalışan thread yapıları tek bir işlemi yapmak için çalışır. Belirli bir task’ı birden fazla thread kullanarak hızlıca tamamlamaktır. Task’ı tamamlamak için birden fazla kaynak kullanmak olarak düşünebiliriz.

## Extension Nedir ?

Kelime anlamı genişletilebilir metod olan Extension Method'lar C#3.0 ile hayatımıza girmiştir ve yaptığı iş itibatiyle kullanım açısından son derece faydalı metodlardır. Tek cümleyle özetlemek gerekirse class ve struct yapılarını modify etmeden ilgili struct yada class'için extension metodlar eklememizi sağlar.

- Bizi sürekli aynı kodları yazmaktan kurtarır.
- Statik metodlar ve statik classlardan oluşur.Referans olarak oluşturduğumuz obje üzerinden çağrılır.
- Extension metodlar statik metodlar ve statik classlardan oluşmaktadır. Fakat referans olarak oluşturduğunuz obje üzerinden çağrılırlar.
- Extension metodların aldığı ilk parametre, bu metodun hangi nesne üzerinde çalışacağını belirtir. Ve alacağı ilk parametrenin önüne "this" anahtar kelimesi getirilir. Böylece metodun bu nesne üzerinde işlem yapacağı belirtilmiş olur.
- Extension metodların kullanımı da çok kolaydır. Extension metodları kullanacağınız kaynak koda, using anahtar kelimesini kullanarak eklediğinizde bu metodlarınızı kullanabilirsiniz.



