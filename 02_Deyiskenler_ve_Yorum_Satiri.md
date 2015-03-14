# 02.De�i�kenler ve Yorum Sat�r�

### Yorum Sat�r�

Yorum Sat�r� Olu�turabilmek ��in Diez (#) karakteri kullan�l�r.

```
# bu tek sat�rl�k bi yorum sat�r�d�r
```

�ok Sat�rl�k  yorumlar i�in 

```
=begin
�ok 
sat�rl�
yorumlar
=end
```

�eklinde Kullan�l�r.

### De�i�kenler

De�i�ken isimleri k���k yada b�y�k harf , alt tire (_),$,@,@@ karakterlerinden birisiyle ba�lamak zorundad�r.

##### De�i�ken �rnekleri
```
Ge�erli �simlendirme                  Ge�ersiz �simlendirme
toplam			#Yerel De�i�ken            	-sayi
kULLANici_Adi	#Yerel De�i�ken				sen&ben
_Yakit_Tipi		#Yerel De�i�ken				veri#Tipi
$altif_no		#Global De�i�ken			2_B_OR_Not_2_b
@adres_bilgisi	#�rnek De�i�keni			@gmail.com
@@sinif_adi		#S�n�f De�i�keni			@@cok iyi
PI_SAYISI		#Sabit						AVAGADRO_SABITI*
```
##### De�i�kenlere De�er Atamak

Genellikle ` = ` kullan�l�r.

Rubi'nin �zelliklerinden birtanesi **Paralel De�i�ken Atama**d�r.

```
a,b,c = 1,2,3
# a = 1 oldu
# b = 2 oldu
# c = 3 oldu
```
�ki de�i�kenin de�erini birbiriyle de�i�tirmek zorunda kald���m�z durumlarda ba�ka bir programlama diliyle yap�lmaya kalksak ge�ici bir de�i�ken 
ou�turmam�z gerekecek ona bir de�eri eklememiz gerekecekti �u �ekilde;

```
gecici = a
a = b
b = gecici
```
�eklinde a'n�n de�eri ile b'nin de�erlerini de�i�tirmi� olduk ama bunu Ruby'de paralel atamay� kullanarak;

```
a,b = b,a
```

�eklinde Yapabiliriz.

#### De�i�ken T�rleri
##### Yerel De�i�kenler
		Yerel De�i�kenler sadece tan�mland�klar� blok i�erisinde kullan�labilirler. Mesela bir d�ng� i�inde tan�mlanan bir yerel de�i�ken d�ng� d���nda eri�ilemez.
		** Yerel De�i�kenler K���k Harf ya da Alt Tire (_) Karakteriyle Ba�lamak Zorundad�r.**

		```
		sayac = 0
		_sayac = 4
		ornek_degisken = "�rnek"
		```

		** Yerel De�i�kenleri Tan�mlad���m�z Anda �lk De�erini Vermek Zorunday�z Aksi Taktirde Yorumlay�c� Bu Tan�mlamalara Bir De�i�ken Tan�mlamas� Yerine Metod �a�r�s� Olarak Alg�lar ve undefined method (tan�mlanmam�� metod) hatas� verir.
		
##### Global De�i�kenler
		Global de�i�kenler yerel de�i�kenlerin aksine nerede tan�mland�klar�na bak�lmaks�z�n t�m program boyunca kullan�labilirler.
		Global de�i�kenler tan�mlan�rken isminin ba��nda ` $ ` (dolar) i�areti bulunmal�d�r.
		Global de�i�kenin tan�mland��� anda ilk de�erinin verilmemesi durumunda yorumlay�c� bunu **nill** (bo�) olarak de�erlendirir. Dolay�s�yla ilk de�er vermek zorunlu de�ildir.
	
	##### S�n�f De�i�keni
		S�n�f de�i�keninin isminin ba��nda iki adet ` @ ` karakteri bulunur ve bu s�n�f�n t�m �rnek nesneleri taraf�ndan kullan�labilirdir.
		** Yerel de�i�kenler gibi olu�turulduklar� anda ilk de�eri verilmelidir. **
		```
		@@toplam  = 0
		```
	##### �rnek De�i�kenleri
		S�n�f de�i�kenlerine benzer ancak bu de�i�kenler o s�n�ftan t�remi� olan ge�erli �rnek taraf�ndan eri�ibilirdirler. �simlerinin ba��nda ` @ ` karakteri bulunur.
		** Yorumlay�c� ilk de�er verilmesi konusunda Global de�i�kenlere davrand��� gibi davran�r yani nill olarak alg�lan�r **
		```
		@isim  = "Furkan"		
		```
	##### Sabitler
		Program boyunca de�erinin de�i�meyece�ini d���nd���m�z de�i�kenleri sabit olarak adland�rabiliriz. Sabit isimleri b�y�k harfle ba�lamak zorundad�rlar. Genellikle t�m� b�y�k harfle yaz�l�r.
		```
		KDV_ORANI = 0.18
		KARBOM_ATOM_NO = 6
		```
	##### Semboller
		Di�er dillerde olmayan semboller Ruby'e �zeldir.
		Semboller metinlere �ok benzerler. Aralar�ndaki en b�y�k fark;
		Metinler her olu�turuldu�unda i�eri�i ayn�da olsa bellekte yeni bir String nesnesi olu�turulur ama semboller bellekte sadece bir kez olu�turulurlar ve t�m oturum boyunca burada sabittirler.
		Ruby de her nesnenin bir kimli�i vard�r bu kimlik bilgisine ` object_id ` metodu ile eri�iriz.
		```
		puts "Metin".object_id	#23432596
		puts "Metin".object_id	#23223846
		```
		G�r�ld��� gibi ayn� karakterleri i�erdikleri halde her metin i�in yeni bir nesne olu�turulur. �imdi ayn� �rne�i semboller i�in yapal�m.
		** Semboller : (iki nokta �st �ste) karakteriyle ba�larlar. (baz� durumlar hari�).
		
		```
		puts :metin.object_id		#548932
		puts :metin.object_id		#548932
		```
		�eklinde sonu� alm�� olduk.
		
##### K�saca De�i�kenler

| **�lk Karakterler**	| **De�i�ken T�r�** |
| --------------------- |:-----------------:|
| a-z veya alt tire (_) | Yerel De�i�ken    |
| $         			| Global De�i�ken   |
| @@   					| S�n�f De�i�keni   |
| @   					| �rnek De�i�keni   |
| A-Z   				| Sabit			    |
| :  					| Semboller		    |
		
	