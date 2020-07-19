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

### SQLite Nedir, Nasıl Kullanılır ?
Sqlite dosya tabanlı hafif database’ler içerisinde günümüzde en çok tercih edilenlerin başında geliyor. Özellikle mobil uygulamalar ve basit programlar söz konusu olduğunda koskoca DBMS (Veritabanı yönetim sistemi) kurmak yerine işimizi basitçe halletmemizi sağlayan sqlite bizi pek çok dertten kurtarıyor. Sqlite genel olarak uzaktan erişim ihtiyacı olmayan, kullanıcı doğrulaması gibi güvenlik gerektirmeyen sistemlerde tercih edilir. Mesela bir masaüstü program yaptınız, ya da Raspberry Pi gibi bir geliştirme kartı üzerinde yerel database kullanma ihtiyacınız doğdu. Sqlite sizi pek çok dertten kurtarır.

Şimdi C# ile SQlite kullanımı konusuna gelecek olursak, öncelikli olarak Visual Studio içerisinde nuget ile Sqlite’ı projemize dahil etmeliyiz.

```c#
SQLiteConnection.CreateFile("YeniVeriTabani.db");
```

 Yukarıdaki ifade “YeniVeriTabani” isminde bir tane database oluşturur. ancak dikkat edin, bu komutu her çalıştırdığınızda eskisini silip yenisini kurar. Bu arada eğer yol belirtmezseniz programı çalıştırıyorsanız dosyayı oraya oluşturur. Mesela debug modda compile edip çalıştırıyorsanız projenizin **%projeyolunuz%/bin/Debug/YeniVeriTabani.db** üzerine kurulum gerçekleşir.

###### Sadece Bir Kez Sqlite Dosya Oluşturma İşlemi

programınız her çalıştığında eski database’i silip yenisini kurarsa hiçbir veri tutamazsınız. Bu yüzden aynı dosya adı mevcut mu bunu kontrol etmemiz gerekir. Kodu birazcık geliştirelim;

```c#
if (!File.Exists("YeniVeriTabani.db"))
{
SQLiteConnection.CreateFile("YeniVeriTabani.db");
}
```

bu sefer kodu çalıştırdığımızda eğer aynı isimde veri tabanı yoksa oluşturacak. Varsa eskisini silmeden muhafaza edecek.

###### C# Sqlite Bağlantı Kurma

Sqlite Dosyamıza Bağlantı kurmak için öncelikli olarak iki tane **global değişken** oluşturalım.

```c#
public SQLiteConnection con = null;
```

**SqliteConnection** sınıfı nuget ile yüklediğimiz kütüphanenin içerisinde yer alır. Buradan türettiğimiz nesneyle bağlantı işlemlerimizi gerçekleştireceğiz. Şimdi C# Sqlite bağlantısı sağlamak için bir tane fonksiyon oluşturalım;

```c#
void baglan()
{
con = new SQLiteConnection("Data Source=YeniVeriTabani.db;Version=3;");
con.Open();
}
```

dikkat edin, con nesnesi global bir değişken. Bir sınıf içerisinde çalışırken global değişkene erişime dikkat etmeliyiz. Bu bağlantıyı çağırdığımızda Veritabanına bağlantıyı sağlamış oluyoruz.