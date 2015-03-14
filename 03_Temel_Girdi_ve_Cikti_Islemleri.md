# 02.Temel Girdi ve ��kt� ��lemleri

## ��kt� ��lemleri Puts ve Print
puts metodu kendisinden sonra gelen metinleri yazar ve hemen arkas�ndan \n (yeni sat�r karakteri) ekler yani alt sat�ra ge�er.
print metodunun puts metodundan fark� \n karakterini eklememesidir.
Di�er bir farklar�ndan birtaneside puts metodu tampon belle�i hemen temizlerken prit metodu bunu yapmaz

## Girdi ��lemleri Gets
Kullan�c�dan bir bilgi giri�i bekledi�imizde kullan�lan metot gets metodudur.

```
print "Ad�n�z: "
ad = gets
print "Merhaba" , ad , "Ho�geldin!"
```
��kt� ��yle Olacakt�r;
```
Ad�n�z: Furkan
Merhaba Furkan
Ho�geldin!
```

bir sorun var gibi ad de�i�keninden sonra alt sat�ra ge�ti print ifadesinde \n karakteri kullanmad�k ve kullan�c�da girmedi asl�nda bu bir sorun de�ildir.
Gets metodu kullan�c�n�n girdi�i metnin sonuna  \n karakteri ekler bunu Rubynin **inspect** metodunu kullarak g�rebiliriz.

**Nedir bu inspect metodu?**.

Bu metod herhangibir nesneye ait detaylar� almam�za yard�mc� olur.

```
print ad.inspect		#Furkan\n
```
�eklinde bir ��kt� al�r�z yani yukardada belirtti�imiz gibi gets metodu kullan�c� girdisinden sonra \n karakterini eklemi�. Bundan nas�l m� kurtulacaks�n�z
**chop**  Keserek.

```
print "Ad�n�z: "
ad = gets.chop
print "Merhaba" , ad , "Ho�geldin!"
```
 
�eklinde de�i�tirdi�imizde ekran ��kt�s�
 
`Merhaba Furkan Ho�geldin!` �eklinde olacakt�r.

**chop** , **chomp** Metodlar�n� �nceleyelim.

```
cogul = "arabalar"
tekil = cogul.chomp "lar"
print tekil
```
Ekran ��kt�s� araba olacakt�r.
chomp ve chop farklar�;
chop metodu metnin en son karakterini siler.
chomp metodu metnin son karakteri \n  veya \r ise siler de�ilse hi�bir i�lem yapmaz 
```
ad = "Furkan"
yeni_ad_1 = ad.chop		#Furka
yeni_ad_2 = ad.chomp	#Furkan
```
�eklinde olacakt�r ekran ��kt�s�.
