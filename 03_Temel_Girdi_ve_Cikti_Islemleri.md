# 02.Temel Girdi ve Çýktý Ýþlemleri

## Çýktý Ýþlemleri Puts ve Print
puts metodu kendisinden sonra gelen metinleri yazar ve hemen arkasýndan \n (yeni satýr karakteri) ekler yani alt satýra geçer.
print metodunun puts metodundan farký \n karakterini eklememesidir.
Diðer bir farklarýndan birtaneside puts metodu tampon belleði hemen temizlerken prit metodu bunu yapmaz

## Girdi Ýþlemleri Gets
Kullanýcýdan bir bilgi giriþi beklediðimizde kullanýlan metot gets metodudur.

```
print "Adýnýz: "
ad = gets
print "Merhaba" , ad , "Hoþgeldin!"
```
Çýktý Þöyle Olacaktýr;
```
Adýnýz: Furkan
Merhaba Furkan
Hoþgeldin!
```

bir sorun var gibi ad deðiþkeninden sonra alt satýra geçti print ifadesinde \n karakteri kullanmadýk ve kullanýcýda girmedi aslýnda bu bir sorun deðildir.
Gets metodu kullanýcýnýn girdiði metnin sonuna  \n karakteri ekler bunu Rubynin **inspect** metodunu kullarak görebiliriz.

**Nedir bu inspect metodu?**.

Bu metod herhangibir nesneye ait detaylarý almamýza yardýmcý olur.

```
print ad.inspect		#Furkan\n
```
þeklinde bir çýktý alýrýz yani yukardada belirttiðimiz gibi gets metodu kullanýcý girdisinden sonra \n karakterini eklemiþ. Bundan nasýl mý kurtulacaksýnýz
**chop**  Keserek.

```
print "Adýnýz: "
ad = gets.chop
print "Merhaba" , ad , "Hoþgeldin!"
```
 
Þeklinde deðiþtirdiðimizde ekran çýktýsý
 
`Merhaba Furkan Hoþgeldin!` Þeklinde olacaktýr.

**chop** , **chomp** Metodlarýný Ýnceleyelim.

```
cogul = "arabalar"
tekil = cogul.chomp "lar"
print tekil
```
Ekran Çýktýsý araba olacaktýr.
chomp ve chop farklarý;
chop metodu metnin en son karakterini siler.
chomp metodu metnin son karakteri \n  veya \r ise siler deðilse hiçbir iþlem yapmaz 
```
ad = "Furkan"
yeni_ad_1 = ad.chop		#Furka
yeni_ad_2 = ad.chomp	#Furkan
```
Þeklinde olacaktýr ekran çýktýsý.
