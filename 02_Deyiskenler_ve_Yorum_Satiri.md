# 02.Deðiþkenler ve Yorum Satýrý

### Yorum Satýrý

Yorum Satýrý Oluþturabilmek Ýçin Diez (#) karakteri kullanýlýr.

```
# bu tek satýrlýk bi yorum satýrýdýr
```

Çok Satýrlýk  yorumlar için 

```
=begin
çok 
satýrlý
yorumlar
=end
```

Þeklinde Kullanýlýr.

### Deðiþkenler

Deðiþken isimleri küçük yada büyük harf , alt tire (_),$,@,@@ karakterlerinden birisiyle baþlamak zorundadýr.

##### Deðiþken Örnekleri
```
Geçerli Ýsimlendirme                  Geçersiz Ýsimlendirme
toplam			#Yerel Deðiþken            	-sayi
kULLANici_Adi	#Yerel Deðiþken				sen&ben
_Yakit_Tipi		#Yerel Deðiþken				veri#Tipi
$altif_no		#Global Deðiþken			2_B_OR_Not_2_b
@adres_bilgisi	#Örnek Deðiþkeni			@gmail.com
@@sinif_adi		#Sýnýf Deðiþkeni			@@cok iyi
PI_SAYISI		#Sabit						AVAGADRO_SABITI*
```
##### Deðiþkenlere Deðer Atamak

Genellikle ` = ` kullanýlýr.

Rubi'nin özelliklerinden birtanesi **Paralel Deðiþken Atama**dýr.

```
a,b,c = 1,2,3
# a = 1 oldu
# b = 2 oldu
# c = 3 oldu
```
Ýki deðiþkenin deðerini birbiriyle deðiþtirmek zorunda kaldýðýmýz durumlarda baþka bir programlama diliyle yapýlmaya kalksak geçici bir deðiþken 
ouþturmamýz gerekecek ona bir deðeri eklememiz gerekecekti þu þekilde;

```
gecici = a
a = b
b = gecici
```
þeklinde a'nýn deðeri ile b'nin deðerlerini deðiþtirmiþ olduk ama bunu Ruby'de paralel atamayý kullanarak;

```
a,b = b,a
```

Þeklinde Yapabiliriz.

#### Deðiþken Türleri
##### Yerel Deðiþkenler
		Yerel Deðiþkenler sadece tanýmlandýklarý blok içerisinde kullanýlabilirler. Mesela bir döngü içinde tanýmlanan bir yerel deðiþken döngü dýþýnda eriþilemez.
		** Yerel Deðiþkenler Küçük Harf ya da Alt Tire (_) Karakteriyle Baþlamak Zorundadýr.**

		```
		sayac = 0
		_sayac = 4
		ornek_degisken = "Örnek"
		```

		** Yerel Deðiþkenleri Tanýmladýðýmýz Anda Ýlk Deðerini Vermek Zorundayýz Aksi Taktirde Yorumlayýcý Bu Tanýmlamalara Bir Deðiþken Tanýmlamasý Yerine Metod Çaðrýsý Olarak Algýlar ve undefined method (tanýmlanmamýþ metod) hatasý verir.
		
##### Global Deðiþkenler
		Global deðiþkenler yerel deðiþkenlerin aksine nerede tanýmlandýklarýna bakýlmaksýzýn tüm program boyunca kullanýlabilirler.
		Global deðiþkenler tanýmlanýrken isminin baþýnda ` $ ` (dolar) iþareti bulunmalýdýr.
		Global deðiþkenin tanýmlandýðý anda ilk deðerinin verilmemesi durumunda yorumlayýcý bunu **nill** (boþ) olarak deðerlendirir. Dolayýsýyla ilk deðer vermek zorunlu deðildir.
	
	##### Sýnýf Deðiþkeni
		Sýnýf deðiþkeninin isminin baþýnda iki adet ` @ ` karakteri bulunur ve bu sýnýfýn tüm örnek nesneleri tarafýndan kullanýlabilirdir.
		** Yerel deðiþkenler gibi oluþturulduklarý anda ilk deðeri verilmelidir. **
		```
		@@toplam  = 0
		```
	##### Örnek Deðiþkenleri
		Sýnýf deðiþkenlerine benzer ancak bu deðiþkenler o sýnýftan türemiþ olan geçerli örnek tarafýndan eriþibilirdirler. Ýsimlerinin baþýnda ` @ ` karakteri bulunur.
		** Yorumlayýcý ilk deðer verilmesi konusunda Global deðiþkenlere davrandýðý gibi davranýr yani nill olarak algýlanýr **
		```
		@isim  = "Furkan"		
		```
	##### Sabitler
		Program boyunca deðerinin deðiþmeyeceðini düþündüðümüz deðiþkenleri sabit olarak adlandýrabiliriz. Sabit isimleri büyük harfle baþlamak zorundadýrlar. Genellikle tümü büyük harfle yazýlýr.
		```
		KDV_ORANI = 0.18
		KARBOM_ATOM_NO = 6
		```
	##### Semboller
		Diðer dillerde olmayan semboller Ruby'e özeldir.
		Semboller metinlere çok benzerler. Aralarýndaki en büyük fark;
		Metinler her oluþturulduðunda içeriði aynýda olsa bellekte yeni bir String nesnesi oluþturulur ama semboller bellekte sadece bir kez oluþturulurlar ve tüm oturum boyunca burada sabittirler.
		Ruby de her nesnenin bir kimliði vardýr bu kimlik bilgisine ` object_id ` metodu ile eriþiriz.
		```
		puts "Metin".object_id	#23432596
		puts "Metin".object_id	#23223846
		```
		Görüldüðü gibi ayný karakterleri içerdikleri halde her metin için yeni bir nesne oluþturulur. Þimdi ayný örneði semboller için yapalým.
		** Semboller : (iki nokta üst üste) karakteriyle baþlarlar. (bazý durumlar hariç).
		
		```
		puts :metin.object_id		#548932
		puts :metin.object_id		#548932
		```
		Þeklinde sonuç almýþ olduk.
		
##### Kýsaca Deðiþkenler

| **Ýlk Karakterler**	| **Deðiþken Türü** |
| --------------------- |:-----------------:|
| a-z veya alt tire (_) | Yerel Deðiþken    |
| $         			| Global Deðiþken   |
| @@   					| Sýnýf Deðiþkeni   |
| @   					| Örnek Deðiþkeni   |
| A-Z   				| Sabit			    |
| :  					| Semboller		    |
		
	