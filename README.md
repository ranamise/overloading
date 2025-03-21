﻿# overloading
using System;

class Kapi { public int Sayisi { get; set; } }
class Pencere { public int Sayisi { get; set; } }
class Kasa { public string Turu { get; set; } }
class Marka { public string Adi { get; set; } }

class Araba
{
    public Marka Marka { get; set; }
    public string Model { get; set; }
    public Kapi Kapi { get; set; }
    public Pencere Pencere { get; set; }
    public Kasa Kasa { get; set; }
    public double Fiyat { get; set; }

    public Araba(Marka marka, string model, Kapi kapi, Pencere pencere, Kasa kasa, double fiyat)
    {
        Marka = marka;
        Model = model;
        Kapi = kapi;
        Pencere = pencere;
        Kasa = kasa;
        Fiyat = fiyat;
    }

    public void Yazdir()
    {
        Console.WriteLine($"Arabanın markası {Marka.Adi}, modeli {Model}, kapı sayısı {Kapi.Sayisi}, " +
            $"pencere sayısı {Pencere.Sayisi}, kasası {Kasa.Turu}, fiyatı {Fiyat:N0} TL’dir.");
    }
}

class Matematik
{
    public int Topla(int a, int b) => a + b;
    public double Topla(double a, double b) => a + b;
    public int Topla(int a, int b, int c) => a + b + c;
    public double Carp(double a, double b) => a * b;
    public int Carp(int a, int b) => a * b;
    public int Carp(int a, int b, int c) => a * b * c;
}

class GenericSinif<T>
{
    public T Veri { get; set; }
    public GenericSinif(T veri) { Veri = veri; }
    public void Yazdir() => Console.WriteLine($"Veri: {Veri}");
}

class Program
{
    static void Main()
    {
 
        Araba bmwX5 = new Araba(new Marka { Adi = "BMW" }, "X5", new Kapi { Sayisi = 4 }, new Pencere { Sayisi = 4 }, new Kasa { Turu = "Sedan" }, 2000000);
        bmwX5.Yazdir();

        Matematik mat = new Matematik();
        Console.WriteLine("Toplam (int): " + mat.Topla(5, 10));
        Console.WriteLine("Toplam (double): " + mat.Topla(5.5, 10.2));
        Console.WriteLine("Çarpma (int): " + mat.Carp(2, 3));
        Console.WriteLine("Çarpma (double): " + mat.Carp(2.5, 4.0));

        GenericSinif<int> sayi = new GenericSinif<int>(42);
        sayi.Yazdir();

        object kutu = sayi.Veri;
        int geriAlinanDeger = (int)kutu; 
        Console.WriteLine($"Unboxing Sonucu: {geriAlinanDeger}");
    }
}

// 3. Garbage Collector Açıklaması 
/*
Garbage Collector (Çöp Toplayıcı), C# dilinde belleği yönetmek için kullanılan bir mekanizmadır.
Kullanılmayan nesneleri otomatik olarak temizleyerek belleği verimli kullanmamızı sağlar.
Nesneler bellekten silindiğinde, sistem kaynakları serbest bırakılır.
C#’ta GC çalışmasını manuel olarak tetiklemek için GC.Collect() metodu kullanılabilir,
amatörce sık kullanımı performans sorunlarına yol açabilir.
*/
