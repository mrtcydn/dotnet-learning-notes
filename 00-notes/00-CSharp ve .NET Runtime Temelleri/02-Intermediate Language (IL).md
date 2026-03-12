# Tanım

- .Net dillerinin derlendikten sonra dönüştürüldüğü ara koddur.
-  C# , F# , VB.NET gibi diller doğrudan makine koduna değil, önce IL'e çevrilir.
- Bu IL kodu daha sonra [[01-Common Language Runtime (CLR)]] tarafından çalıştırılır.
---
# Amacı

- .NET dillerini platformdan bağımsız yapmak
- Tüm .NET dillerinin aynı runtime üzerinde çalışmasını sağlamak
- Kodun optimize edilmesini sağlamak
- Güvenli çalıştırma ortamı oluşturmak
---
# Diyagram

![[Net Mimarisi.png|356]]

---
# C# Kodunun IL'e Çevrilmesi

```csharp
int x = 10;  
int y = 20;  
int result = x + y;  
Console.WriteLine(result);
```
Derlendikten sonra IL'e benzer bir şey oluşur:
```il
ldc.i4.s 10  
stloc.0  
  
ldc.i4.s 20  
stloc.1  
  
ldloc.0  
ldloc.1  
add  
stloc.2  
  
ldloc.2  
call void [System.Console]System.Console::WriteLine(int32)
```

---
# IL Nerede Saklanır?

- IL kodu **assembly** içinde saklanır.
- Assembly = .dll  , .exe
- İçerisinde şunlar vardır; 
	- IL kodu
	- Metadata
	- Assembly manifest

---
# Metadata Nedir?

IL yanında şu bilgiler bulunur:
- class bilgileri
- method bilgileri
- property bilgileri
- type bilgileri

---
# IL Nasıl Görülür?

IL'i incelemek için birkaç araç vardır.
##### 1) ILDasm
.NET SDK içinde gelir.

#### 2) ILSpy
Çok popüler bir araçtır.

Özellikleri:
- DLL içini açar
- IL gösterir
- Decompile yapar

#### 3) dnSpy
Debug ve IL inceleme aracı.

---

# ÖZET

- IL, .NET dillerinin compile edildiği **ara koddur**
- IL, **platform bağımsızdır**
- CLR tarafından çalıştırılır
- [[03-Just-In Time Compiler(JIT)]]  tarafından **machine code'a çevrilir**
- Assembly içinde **IL + Metadata** bulunur
- IL **stack tabanlıdır**
