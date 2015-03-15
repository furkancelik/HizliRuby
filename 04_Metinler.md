#04.Metinler

##Metin Olu�turma

###String.new metodu
Rubyde her�ey nesne oldu�u i�in metinlerde String s�n�f� ile olu�turulurlar.

` metin = String.new		#=> "" `

�rnekteki gibi new metoduna parametre g�ndermedi�imiz i�in bo� bir metin olu�tu. (varsay�lan olarak bo�tur).

```
 metin = String.new("Metin Olu�turmay� ��reniyorum.")
 puts metin		#=>Metin Olu�turmay� ��reniyorum.
 ```
 Parametre g�ndererek metni olu�turmu� olduk.
 
###T�rnak ��areti Kullanarak Metin Olu�turmak
Metin olu�turulurken en �ok tercih edilen y�ntem t�rnak i�areti y�ntemidir.
tek t�rnak ve �ift t�rnak kullanarak metin olu�turabiliriz.

```
tek_tirnak  = 'Yeni Metin Olu�turdum.'		#=> "Yeni Metin Olu�turdum."
cif_tirnak  = "Yeni Metin Olu�turdum."		#=> "Yeni Metin Olu�turdum."
```
Bu �rnekte iki kullan�m aras�nda hi�bir fark yoktur. Ama ikisidenayn� �ey de�ildir fark kar��m�za metin ifadelerine kod par�ac��� g�m�l�nce ortay a��k�yor.

�ncelikle nedir bu kod par�aca�� g�mme?

```
corba = 'Mercimek'
mesaj = 'En Sevdi�im �orba,' + corba + ' �orbas�d�r.'
puts mesaj		#=> En Sevdi�im �orba, Mercimek �orbas�d�r.
```

**Art� Operat�r� (+)** Ruby Dilinde metinleribirle�tirmek i�in kullan�l�r.

Bir di�er y�ntem

```
corba = 'Mercimek'
mesaj = "En Sevdi�im �orba, #{corba} �orbas�d�r."
puts mesaj		#=> En Sevdi�im �orba, Mercimek �orbas�d�r.
```
G�r�ld��� gibi iki �rnekte ayn� i�i yap�yor. Ama ` #{} ` karakterini kullan�nca 2.�rnek daha rahat okunabiliyor ve gereksiz i�lemlerden ar�nd�r�lm�� oluyor.

**#{} Karakteri ney mi?**
Bu karakterin kullan�m� Ruby yorumlay�c�s�na s�sl� parantez aras�nda bir kod g�m�l� oldu�unu s�yl�yor. B�ylece yorumlay�c� String �rne�ini olu�turmadan �nce
bu kodu yorumluyor ve geri sonucu (nesneyi) ilgili yerde kullan�yor.
` #{} ` Karakteri aras�nda her t�rl� kod par�as�n� kullabiliriz. Bu karakter aras�nda bir s�n�f bile tan�mlan�p kullan�labilir.

�imdi tek t�rnak ve �ift t�rnak kullan�m� aras�ndaki farka bakacak olursak;

```
ad = 'Furkan'
tek_tirnak 	= 'Ho�geldin, #{ad}!'		#=> "Ho�geldin, \#{ad}!
cift_tirnak = "Ho�geldin, #{ad}!"		#=> "Ho�geldin, Furkan!
```
G�r�ld��� gibi tek t�rnak kullanarak t�rnak i�erisine kodlar�m�z� g�memiyoruz.
Sonu� olarak metnin i�inde kod par�as� g�m�lecekse �ift t�rnak kullanmal�y�z.

###Kullan�c� Tan�ml� Metin S�n�rlay�c� �le Metin Olu�turmak
Bir di�er metin olu�turma y�ntemi kullan�c� tan�ml� metin s�n�rlay�c�n�n kullan�lmas�d�r.
Bu s�n�rlay�c� ` %Q ` ve ` %q ` Karakteriyle temsil edilir.
�rnek olarak:

```
%Q{metin ifadesi}
```

yada 

```
%q{metin ifadesi}
```

Buradaki Q harfi **�ift t�rna��** q harfi ise **tek t�rna��** temsil eder.

```
ad = "Furkan"
metin1 = %Q{Ho�geldin, #{ad}!}		#=> Ho�geldin, Furkan!
metin2 = %q{Ho�geldin, #{ad}!}		#=> Ho�geldin, #{ad}!
```

> %Q metin s�n�rlay�c�s� yerine sadece % metin s�n�rlay�c�s�da kullan�labilir

Metin s�n�rlay�c�s� karakteri olarak sadece s�sl� parantez ` { } ` kullanmak zorunlu de�ildir.
onun yerine istedi�imiz ba�ka bir s�n�rlay�c� karakter belirleyebiliriz. Bu karakterin harf olmamas� yada Ruby i�in �zel anlam� olmamas� gerekir (# karakteri gibi).
�nemli olan s�n�rlay�c� ba��nda kullan�lan karakter ile s�n�rlay�c� sonlanmal�d�r �rnek olarak ` %Q[metin] ` , ` %<metin> ` , ` %q(metin) ` gibi.

> %Q ve %q karakterinden hemen sonra (bo�luk b�rakmadan) s�n�rlay�c� karakter girilmelidir.

##Heredoc Kullan�m�

�ok sat�rl� ve i�erisinde t�rnak i�aretleri ge�en metinler olu�turulurken kullan�lan bir y�ntemdir. Ruby php gibi pek �ok programlama dilinde mevcuttur.
Ruby'de kullan�m �u �ekildedir;

```
<<METIN
	#metinler buraya yaz�lacak...
METIN
```

�ncelikle ` << ` karakteri ile METIN (s�n�rlay�c� kelime) aras�nda bo�luk olmamal�d�r.
METIN olarak adland�r�lan k�s�m istenilen herhangibir kelime , metin olabilir.
�lk s�rada belirtti�imiz METIN ifadesi �unu s�ylemektedir bu ifadeyi bir daha g�rd���nde orada metin bitmi�tir.
En sondaki METIN sat�r�n en ba��nda olmal�d�r bo�luk olmamal�d�r ama bu durumda bir zorunluluk yoktur s�n�rlay�c� biti�ini girintili olarak yazmak istersek �u �ekide kullanabiliriz.

```
<<-METIN
		#metinler buraya yaz�lacak...
	METIN
```

G�r�ld��� gibi ` << ` karakteriyke s�n�rlay�c� metin aras�nda tire (-) i�areti konulmal�d�r.

**Heredoc kullan�m� i� i�e olarak da kullanabiliriz**

```
metin = <<METIN1 , <<METIN2
	Merhaba
METIN1
D�nya
METIN2

puts metin
```

program �al��t�r�l�nca a��a��daki ��kt�y� verecektir.

```
Merhaba
D�nya
```

S�n�rlay�c� ifadeleri i� i�e kullan�rken tan�mlama yapmak i�in en ba�ta ka� tane olacaksa s�ras�yla yazmak ve aras�na virg�l koymal�y�z.
METIN1 s�n�rlay�c�s� sonlanmak i�in ondan sonra a�t���m�z METIN2 s�n�rlay�c�s�n�n sonlanmas�n� bekleyecektir yani sa�dan sola s�n�rlay�c�lar� sonland�rmal�y�z.
Asl�nda burda olu�turdu�umuz METIN1 ve METIN2 aras�na virg�l koyarak olu�turuldu�u i�in bunlar bir diziye aktar�lm�� oldular daha detayl� bakmak i�in

```
puts metin.inspect		#=>["Merhaba\n","D�nya\n"]
```
�eklinde ��kt� al�n�r.


##�zel Karakter ve Karakter Gizleme

```
metin = '�stanbul'u dinliyorum g�zlerim kapal�'
print metin
```

yukar�daki kod hata verecektir ��nk� ilk t�rnak i�areti a��ld�ktan sonra ki ilk t�rnak i�aretine kadar metin olarak yorumlar
'�stanbul' yani buraya kadar metin olarka yorumlar ondan sonraki metinlere anlam veremez ve hata verir bu durumdan kurtulmak i�in
kullanaca��m�z karakter **ters b�l�** karakteridir ( ` \ ` ).

Do�rusu:
```
metin = '�stanbul\'u dinliyorum g�zlerim kapal�'
print metin
```
�eklinde g�ncelledi�imizde sorunsuzca �al��acakt�r 

** \ ifadesini nas�l metin olarak yazd�raca��m?**

Ters b�l� karakterini metin olarka yazd�rmak i�in yine \ karakteriyle ka�ma i�lemi yapmal�y�z yani.

```
metin = " \" \\ \" Karakterini Kullanmak.";
print metin		#=> " \ " Karakterini Kullanmak
```

G�r�ld��� gibi " ifadesinden ka�mak i�in de \ kulland�k \ karakterinden ka�mak i�inde \ kulland�k.

**Baz� �zel Karakterler**

| Ters B�l� G�sterimi   | A��klama		 										|
| --------------------- | ----------------------------------------------------- |
| \a 					| Konsol Uygulamalar�nda "bip" sesi ��kmas�n� sa�lar  	|
| \b  					| Geriye do�ru bir karakter silme (backspace tu�u)		|
| \f 					| Form Besleme 											|
| \e 					| Escape Tu�u 											|
| \n 					| Yeni Sat�r 											|
| \r 					| Enter Tu�u 											|
| \s 					| Bo�lul 												|
| \t 					| Sekme (Tab) 											|
| \v 					| Dikey Sekme - (\n ve \t birle�imi) 					|


##Metinlerle Birlikte �al��mak

Rubyde bir metnin uzunlu�unu (toplam karakter say�s�n�) ��renmek i�in length ve size metodu kullan�l�r

```
metin = "metnin say�s�nu bul ruby"
puts metin.length		#=> 24
puts metin.size			#=> 24
```

**count metodu kullan�m�**
count metodu ile metin i�inde arad���m�z karakterden ka� tane var onu ��renebiliriz.
Tek bir parametre ile kullan�ld���nda metin i�inde her bir harften ka� tane oldu�unu hesaplar
�ki parametre ile kullan�l�rsa parametrelerdeki harflerin kesi�imini al�r ve bu kesi�imdeki harflerden ka� tane oldu�unu sayar.
E�er ikinci parametrenin ba��nda ^ i�areti bulunuyorsa bu ifadeye negatiflik katar. �lk parametredeki harflerden ikinci parametredeki harfler ��kart�l�r ve kalan harflerden metin i�inde ka� tane oldu�u say�l�r.
�ki karakter aras�nda tire (-) i�areti konuluyorsa bu karakterlerden bir seri olu�turulup seriye dahil olan t�m karakterler say�l�r.

```
#Metin i�inde ka� tane e var?
metin = "Bu bir test metnidir."
puts metin.count "e"		#=>2

#te metnini t ve e olmak �zere iki par�aya ay�r�yor 
#ve her bir harfin ka� tane oldu�unu sayarak topluyor.

puts metin.count "te"		#=>5

#te ve tr metinlerinin kesi�imini al�yor 
#te ve tr metinlerinin kesi�imi t harfi olur

puts metin.count "te","tr"		#=>3

#a��a��daki ifade ise t,e,sharflerinden 3 harflerini ��kart�yor
#geriye t ve s harfleri kal�yor.

puts metin.count "test","^e"		#=>4

#a��a��da ise t harfinden ka� tane oldu�unu buluyor 
#ve m den r ye kadar olan harflerden de
#(m,n,o,p,r) ka� tane oldu�unu bulup topluyor

puts metin.count "tm-r"		#=>7
```


##Metinleri Birle�tirme
�rnekle a��klayal�m

```
ad = "Furkan"
soyad = "�elik"

puts ad + " " + soyad		#=>Furkan �elik

ad2 = "Hasan"
soyad2 = "�elik"

puts ad2 << " " << soyad2		#=>Furkan �elik
```
` + ` ve ` << ` metodlar� ayn� i�lemi yap�yor gibi g�z�ksede aralar�nda bir fark vard�r

` + ` metodunu kulland�ktan sonra ad ve soyad de�i�kenlerinin de�eri de�i�mezken ` << ` metodunu kulland�ktan sonra
ad2 de�i�keninin de�eri Hasan de�il Hasan �elik oldu.

Ba�ka bir �rnekle inceleyelim

```
gobek_adi = "Bekir"
ad = "Furkan"
soyad = "�elik"

gobek_adi << ad << soyad

puts gobek_adi		#=>Bekir Furkan �elik
puts ad				#=>Furkan
puts soyad			#=>�elik
```

G�r�ld��� gibi ` << ` operat�r� en ba�taki de�i�kenin de�erini de�i�tirdi ve di�erlerinin de�erini de�i�tirmedi 

**concat metodu**

Metinleri birle�timenin bir di�er yolu da concat metodudur.

```
a = "Merhaba"
b = "nas�ls�n"
c = "iyi misin?"

puts a.concat(b).concat(c)		#=>Merhaba nas�ls�n iyi misin?
puts a							#=>Merhaba nas�ls�n iyi misin?
puts b							#=>nas�ls�n
puts c							#=>iyi misin?
```

�rne�e bak�ld���nda concat metodunun ` << ` metodu ile ayn� i�lemi yapt��� g�r�lmektedir.

**Farkl� bir birle�tirme y�ntemi**

�rnek �zerinde inceleyelim

```
ad = "Furkan"
metin = "Merhaba " "#{ad}" ", ho� geldin!"
print metin		#=>Merhaba Furkan, ho� geldin!
```
Arada + ya da ba�kabir operat�r yok!
Birde bunu inceleyelim

```
ad = "Furkan"
metin  = "Merhaba" , "#{ad}", ", ho� geldin"
print metin		#=>Merhaba Furkan, ho� geldin!
``` 

�ki �rnek aras�ndaki tek fark metinler aras�na , (virg�l) koymam�z oldu.

` print metin.inspect `
dedi�imizde ekran ��kt�s�
` #=> "[\"Merhaba \",\"Furkan\",\", ho� geldin!\"]" `
G�r�ld��� gibi metin burda string de�il bir dizi olmu�.

##B�y�k/K���k Harf D�n���m�

**B�y�k harfe �evirme upcase**

```
metin = "merhaba"
print metin.upcase		#=>"MERHABA"
print metin				#=>"merhaba"
```

G�r�ld��� gibi upcase metodu kullan�larak metin harfleri b�y�k harfe �evrildi ama de�i�ken bu durumdan etkilenmedi bunun i�in Rubyde �zel metodlar var 
bunlar bang diye adland�r�l�yor ve metod uygulan�nca de�i�kenimizin de�erine etki ediyor. �u �ekilde inceleyebiliriz.

```
metin = "merhaba"
print metin.upcase!		#=>"MERHABA"
print metin				#=>"MERHABA"
```

upcase! metodunu kulland�k ! ile biten metodlar bang! metodlar�d�r bunlar dedi�im gibi de�i�kenin de�erini etkilerler metin de�i�kenimiz yeni de�erini alm�� oldu.

**K���k harfe �evirme downcase**

```
metin = "MERHABA"
print metin.downcase		#=>"merhaba"
print metin.downcase!		#=>"merhaba"
#downcase! metodu ile de�i�kenimizin de�erini etkilemi� oluyoruz.
print metin					#=>"merhaba"
```

**swapcase Metodu**

swapcase metodu ile b�y�k harfleri k���k harflere k���k harfleri b�y�k harflere d�n��t�r�yoruz.

```
metin = "mErHaBa"
print metin.swapcase		#=>"MeRhAbA"
print metin.swapcase!		#=>"MeRhAbA"
print metin					#=>"MeRhAbA"
```



**capitalize Metodu**

capitalize metodu ile metnin sadece ilk harfini b�y�k di�erlerini k���k yapabiliriz.

```
metin = "bu Birinci c�mle. Bu ikinci."
print metin.capitalize		#=>"Bu birinci c�mle. bu ikinci."
print metin.capitalize!		#=>"Bu birinci c�mle. bu ikinci."
print metin					#=>"Bu birinci c�mle. bu ikinci."
```


##Alfabe D��� Karakter Temizleme
Bazen metin i�indeki alfabe d��� karakterlerin temizlenmesi gerekir (\f,\n,\r,\s,\t) bo�luk karakterleri gibi.
bunun i�in 3 metod vard�r.

**lstrip** metnin sadece sol taraf�ndaki alfabe d��� karakterleri temizler.
**rstrip** metnin sadece sa� taraf�ndaki alfabe d��� karakterleri temizler.
**strip** metodu her iki tarafdaki alfabe d��� karakterleri temizler.

```
metin = "   \t Merhaba   \r\n"
puts metin.lstrip.inspect		#=>"Merhaba   \r\n"
puts metin.rstrip.inspect		#=>"   \t Merhaba"
puts metin.strip.inspect		#=>"Merhaba"
```

##Ba�ka T�rden Veriyi Metne D�n��t�rme

Herhangibir t�rden veriyi metne d�n��t�rmek i�in **to_s** metodundan faydalan�l�r.

```
5.to_s							#=> "5"
false.to_s						#=> "false"
[1,2,"elma","armut"].to_s		#=> "12elmaarmut"
puts :sembol.to_s				#=> "sembol"
PI = "3.1415"					#PI ad�nda sabit tan�mland�
puts PI.to_s					#=> "3.14"
```

##Metni Diziye D�n��t�rmek

Bir metin ifadesi belirli bir karakterlerle (bo�luk, virg�l, nokta vb.) ayr�lm�� bir bi�imde ise ve bu ifadeyi diziye d�n��t�rmek istersek **split** metodu kullan�l�r.

E�er ay�r�c� karakter bo�luk ise split metoduna herhangibir parametre g�ndermemize gerek yoktur.

```
metin = "Karpuz Muz Elma Armut"
metin.split			#=>["Karpuz","Muz","Elma","Armut"]
```

E�er bo�luk d���nda bir ay�r�c� karakter kullan�lm��sa bu karakterin parametre olarak girilmesi gerekiyor.

```
metin = "Karpuz*Muz*Elma*Armut"
metin.split('*')			#=>["Karpuz","Muz","Elma","Armut"]
```

>Diziyi tekrar metin haline d�n��t�rmek istedi�imizde yada herhangibir diziyi belirli bir karakterle metne d�n��t�rmek i�in **join** metodu kullan�l�r.
>join metodu dizilere tan�ml� bir metottur metinlerde join metodu kullan�l�rsa hata al�n�r.

```
metin = "Karpuz*Muz*Elma*Armut"
metin.split('*')			#=>["Karpuz","Muz","Elma","Armut"]
metin.join('+')				#=>Karpuz+Muz+Elma+Armut
```


>Rubyde Metinlerle birlikte kullan�labilecek 100'den fazla metod mevcuttur
>T�m metodlar i�in http://ruby-doc.org/core-2.2.1/String.html adresine bakabilirsiniz.

