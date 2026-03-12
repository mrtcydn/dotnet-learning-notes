
## Tanım

- .NET frameworkünün çalışmasını yöneten sistemdir. C# veya başka bir .NET dili ile yazılan kod doğrudan makine kodu olarak çalışmaz. Önce farklı aşamalardan geçer ve CLR bu süreci yönetir.
- Kısaca ; .NET uygulamasının işletim sistemi ile arasındaki yönetici katmandır.
---
## Amacı

- Kodun güvenli çalışmasını sağlamak
- Memory yönetimini otomatize etmek
- Farklı .NET dillerinin birlikte çalışmasını sağlamak
- Performansı optimize etmek
---
## Not

- C#'da derleme yapıldığında gerçek bir makine kodu oluşmaz. Derleyici **'Roslyn'** bir ara dile çevirir. Buna **[IL](02-il)** denir. 
---
## Diyagram

<img src="../diagrams/dotnet-architecture.png" alt="dotnet architecture" width="367">

- Compile Time = kodun derlenip .dll ve .exe oluşturulan kısım.
- Run Time = .exenin çalıştığı zaman oluşturulan makine kod işlenme kısmı
---
## Çalışma Mantığı

```csharp
Console.WriteLine("Hello World"); // kodu yazılır
```  

- C# Compiler bunu Intermediate Language (IL) koduna çevirir.
- CLR gönderilir
- [JIT](03-jit) IL kodunu makine koduna çevirir
- CPU çalıştırır
---
## CLR Neleri Yönetir?

1)  **[Garbage Collector](04-garbage-collector)** 
   - Memory temizliği yapar. Artık kullanılmayan objeleri otomatik siler.

```csharp 
var user = new User(); 
```  

2) **[Memory Management](05-memory-management)**
  - [Stack ve Heap](10-stack-heap)
  - Object allocation

2) **[Exception Handling](06-expection-handling)**
 - Hata yönetimi yapar.
```csharp
try
{
}
catch(Exception ex)
{
}
```  

4) **[Type Safety](07-type-safety)**
 - Yanlış tür kullanımını engeller
```csharp	
int x = "hello";  // hata
```  

5) **[Security](08-security)**
 - Kodun güvenliğini sağlar

5) **[Thread Management](09-thread-management)**
 - Multi-thread işlenlerini yönetir.

