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

- C#'da derleme yapıldığında gerçek bir makine kodu oluşmaz. Derleyici **'Roslyn'** bir ara dile çevirir. Buna **[[02-Intermediate Language (IL)]]** denir. 
---
## Diyagram

![[Net Mimarisi.png|368]]
- Compile Time = kodun derlenip .dll ve .exe oluşturulan kısım.
- Run Time = .exenin çalıştığı zaman oluşturulan makine kod işlenme kısmı
---
## Çalışma Mantığı

```csharp
Console.WriteLine("Hello World"); // kodu yazılır
```  

- C# Compiler bunu Intermediate Language (IL) koduna çevirir.
- CLR gönderilir
- [[03-Just-In Time Compiler(JIT)]] IL kodunu makine koduna çevirir
- CPU çalıştırır
---
## CLR Neleri Yönetir?

1)  [[Garbage Collector]] 
   - Memory temizliği yapar. Artık kullanılmayan objeleri otomatik siler.

```csharp 
var user = new User(); 
```  

2) [[Memory Management]]
  - [[Stack ve Heap]]
  - Object allocation

3) [[Exception Handling]]
 - Hata yönetimi yapar.
```csharp
try
{
}
catch(Exception ex)
{
}
```  

4) [[Type Safety]]
 - Yanlış tür kullanımını engeller
```csharp	
int x = "hello";  // hata
```  

5) **[[Security]]**
 - Kodun güvenliğini sağlar

6) [[Thread Management]]
 - Multi-thread işlenlerini yönetir.

