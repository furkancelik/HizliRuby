#04.Metinler

##Metin Oluþturma

###String.new metodu
Rubyde herþey nesne olduðu için metinlerde String sýnýfý ile oluþturulurlar.

` metin = String.new		#=> "" `

Örnekteki gibi new metoduna parametre göndermediðimiz için boþ bir metin oluþtu. (varsayýlan olarak boþtur).

```
 metin = String.new("Metin Oluþturmayý Öðreniyorum.")
 puts metin		#=>Metin Oluþturmayý Öðreniyorum.
 ```
 Parametre göndererek metni oluþturmuþ olduk.
 
###Týrnak Ýþareti Kullanarak Metin Oluþturmak
Metin oluþturulurken en çok tercih edilen yöntem týrnak iþareti yöntemidir.
tek týrnak ve çift týrnak kullanarak metin oluþturabiliriz.

```
tek_tirnak  = 'Yeni Metin Oluþturdum.'		#=> "Yeni Metin Oluþturdum."
cif_tirnak  = "Yeni Metin Oluþturdum."		#=> "Yeni Metin Oluþturdum."
```
Bu örnekte iki kullaným arasýnda hiçbir fark yoktur. Ama ikisidenayný þey deðildir fark karþýmýza metin ifadelerine kod parçacýðý gömülünce ortay açýkýyor.

Öncelikle nedir bu kod parçacaðý gömme?

```
corba = 'Mercimek'
mesaj = 'En Sevdiðim Çorba,' + corba + ' Çorbasýdýr.'
puts mesaj		#=> En Sevdiðim Çorba, Mercimek Çorbasýdýr.
```

**Artý Operatörü (+)** Ruby Dilinde metinleribirleþtirmek için kullanýlýr.

Bir diðer yöntem

```
corba = 'Mercimek'
mesaj = "En Sevdiðim Çorba, #{corba} Çorbasýdýr."
puts mesaj		#=> En Sevdiðim Çorba, Mercimek Çorbasýdýr.
```
Görüldüðü gibi iki örnekte ayný iþi yapýyor. Ama ` #{} ` karakterini kullanýnca 2.örnek daha rahat okunabiliyor ve gereksiz iþlemlerden arýndýrýlmýþ oluyor.

**#{} Karakteri ney mi?**
Bu karakterin kullanýmý Ruby yorumlayýcýsýna süslü parantez arasýnda bir kod gömülü olduðunu söylüyor. Böylece yorumlayýcý String örneðini oluþturmadan önce
bu kodu yorumluyor ve geri sonucu (nesneyi) ilgili yerde kullanýyor.
` #{} ` Karakteri arasýnda her türlü kod parçasýný kullabiliriz. Bu karakter arasýnda bir sýnýf bile tanýmlanýp kullanýlabilir.

Þimdi tek týrnak ve çift týrnak kullanýmý arasýndaki farka bakacak olursak;

```
ad = 'Furkan'
tek_tirnak 	= 'Hoþgeldin, #{ad}!'		#=> "Hoþgeldin, \#{ad}!
cift_tirnak = "Hoþgeldin, #{ad}!"		#=> "Hoþgeldin, Furkan!
```
Görüldüðü gibi tek týrnak kullanarak týrnak içerisine kodlarýmýzý gömemiyoruz.
Sonuç olarak metnin içinde kod parçasý gömülecekse çift týrnak kullanmalýyýz.

###Kullanýcý Tanýmlý Metin Sýnýrlayýcý Ýle Metin Oluþturmak
Bir diðer metin oluþturma yöntemi kullanýcý tanýmlý metin sýnýrlayýcýnýn kullanýlmasýdýr.
Bu sýnýrlayýcý ` %Q ` ve ` %q ` Karakteriyle temsil edilir.
Örnek olarak:

```
%Q{metin ifadesi}
```

yada 

```
%q{metin ifadesi}
```

Buradaki Q harfi **çift týrnaðý** q harfi ise **tek týrnaðý** temsil eder.

```
ad = "Furkan"
metin1 = %Q{Hoþgeldin, #{ad}!}		#=> Hoþgeldin, Furkan!
metin2 = %q{Hoþgeldin, #{ad}!}		#=> Hoþgeldin, #{ad}!
```

> %Q metin sýnýrlayýcýsý yerine sadece % metin sýnýrlayýcýsýda kullanýlabilir

Metin sýnýrlayýcýsý karakteri olarak sadece süslü parantez ` { } ` kullanmak zorunlu deðildir.
onun yerine istediðimiz baþka bir sýnýrlayýcý karakter belirleyebiliriz. Bu karakterin harf olmamasý yada Ruby için özel anlamý olmamasý gerekir (# karakteri gibi).
Önemli olan sýnýrlayýcý baþýnda kullanýlan karakter ile sýnýrlayýcý sonlanmalýdýr Örnek olarak ` %Q[metin] ` , ` %<metin> ` , ` %q(metin) ` gibi.

> %Q ve %q karakterinden hemen sonra (boþluk býrakmadan) sýnýrlayýcý karakter girilmelidir.

##Heredoc Kullanýmý

Çok satýrlý ve içerisinde týrnak iþaretleri geçen metinler oluþturulurken kullanýlan bir yöntemdir. Ruby php gibi pek çok programlama dilinde mevcuttur.
Ruby'de kullaným þu þekildedir;

```
<<METIN
	#metinler buraya yazýlacak...
METIN
```

Öncelikle ` << ` karakteri ile METIN (sýnýrlayýcý kelime) arasýnda boþluk olmamalýdýr.
METIN olarak adlandýrýlan kýsým istenilen herhangibir kelime , metin olabilir.
Ýlk sýrada belirttiðimiz METIN ifadesi þunu söylemektedir bu ifadeyi bir daha gördüðünde orada metin bitmiþtir.
En sondaki METIN satýrýn en baþýnda olmalýdýr boþluk olmamalýdýr ama bu durumda bir zorunluluk yoktur sýnýrlayýcý bitiþini girintili olarak yazmak istersek þu þekide kullanabiliriz.

```
<<-METIN
		#metinler buraya yazýlacak...
	METIN
```

Görüldüðü gibi ` << ` karakteriyke sýnýrlayýcý metin arasýnda tire (-) iþareti konulmalýdýr.

**Heredoc kullanýmý iç içe olarak da kullanabiliriz**

```
metin = <<METIN1 , <<METIN2
	Merhaba
METIN1
Dünya
METIN2

puts metin
```

program çalýþtýrýlýnca aþþaðýdaki çýktýyý verecektir.

```
Merhaba
Dünya
```

Sýnýrlayýcý ifadeleri iç içe kullanýrken tanýmlama yapmak için en baþta kaç tane olacaksa sýrasýyla yazmak ve arasýna virgül koymalýyýz.
METIN1 sýnýrlayýcýsý sonlanmak için ondan sonra açtýðýmýz METIN2 sýnýrlayýcýsýnýn sonlanmasýný bekleyecektir yani saðdan sola sýnýrlayýcýlarý sonlandýrmalýyýz.
Aslýnda burda oluþturduðumuz METIN1 ve METIN2 arasýna virgül koyarak oluþturulduðu için bunlar bir diziye aktarýlmýþ oldular daha detaylý bakmak için

```
puts metin.inspect		#=>["Merhaba\n","Dünya\n"]
```
Þeklinde çýktý alýnýr.


##Özel Karakter ve Karakter Gizleme

```
metin = 'Ýstanbul'u dinliyorum gözlerim kapalý'
print metin
```

yukarýdaki kod hata verecektir çünkü ilk týrnak iþareti açýldýktan sonra ki ilk týrnak iþaretine kadar metin olarak yorumlar
'Ýstanbul' yani buraya kadar metin olarka yorumlar ondan sonraki metinlere anlam veremez ve hata verir bu durumdan kurtulmak için
kullanacaðýmýz karakter **ters bölü** karakteridir ( ` \ ` ).

Doðrusu:
```
metin = 'Ýstanbul\'u dinliyorum gözlerim kapalý'
print metin
```
Þeklinde güncellediðimizde sorunsuzca çalýþacaktýr 

** \ ifadesini nasýl metin olarak yazdýracaðým?**

Ters bölü karakterini metin olarka yazdýrmak için yine \ karakteriyle kaçma iþlemi yapmalýyýz yani.

```
metin = " \" \\ \" Karakterini Kullanmak.";
print metin		#=> " \ " Karakterini Kullanmak
```

Görüldüðü gibi " ifadesinden kaçmak için de \ kullandýk \ karakterinden kaçmak içinde \ kullandýk.

**Bazý Özel Karakterler**

| Ters Bölü Gösterimi   | Açýklama		 										|
| --------------------- | ----------------------------------------------------- |
| \a 					| Konsol Uygulamalarýnda "bip" sesi çýkmasýný saðlar  	|
| \b  					| Geriye doðru bir karakter silme (backspace tuþu)		|
| \f 					| Form Besleme 											|
| \e 					| Escape Tuþu 											|
| \n 					| Yeni Satýr 											|
| \r 					| Enter Tuþu 											|
| \s 					| Boþlul 												|
| \t 					| Sekme (Tab) 											|
| \v 					| Dikey Sekme - (\n ve \t birleþimi) 					|


##Metinlerle Birlikte Çalýþmak

Rubyde bir metnin uzunluðunu (toplam karakter sayýsýný) öðrenmek için length ve size metodu kullanýlýr

```
metin = "metnin sayýsýnu bul ruby"
puts metin.length		#=> 24
puts metin.size			#=> 24
```

**count metodu kullanýmý**
count metodu ile metin içinde aradýðýmýz karakterden kaç tane var onu öðrenebiliriz.
Tek bir parametre ile kullanýldýðýnda metin içinde her bir harften kaç tane olduðunu hesaplar
Ýki parametre ile kullanýlýrsa parametrelerdeki harflerin kesiþimini alýr ve bu kesiþimdeki harflerden kaç tane olduðunu sayar.
Eðer ikinci parametrenin baþýnda ^ iþareti bulunuyorsa bu ifadeye negatiflik katar. Ýlk parametredeki harflerden ikinci parametredeki harfler çýkartýlýr ve kalan harflerden metin içinde kaç tane olduðu sayýlýr.
Ýki karakter arasýnda tire (-) iþareti konuluyorsa bu karakterlerden bir seri oluþturulup seriye dahil olan tüm karakterler sayýlýr.

```
#Metin içinde kaç tane e var?
metin = "Bu bir test metnidir."
puts metin.count "e"		#=>2

#te metnini t ve e olmak üzere iki parçaya ayýrýyor 
#ve her bir harfin kaç tane olduðunu sayarak topluyor.

puts metin.count "te"		#=>5

#te ve tr metinlerinin kesiþimini alýyor 
#te ve tr metinlerinin kesiþimi t harfi olur

puts metin.count "te","tr"		#=>3

#aþþaðýdaki ifade ise t,e,sharflerinden 3 harflerini çýkartýyor
#geriye t ve s harfleri kalýyor.

puts metin.count "test","^e"		#=>4

#aþþaðýda ise t harfinden kaç tane olduðunu buluyor 
#ve m den r ye kadar olan harflerden de
#(m,n,o,p,r) kaç tane olduðunu bulup topluyor

puts metin.count "tm-r"		#=>7
```


##Metinleri Birleþtirme
Örnekle açýklayalým

```
ad = "Furkan"
soyad = "Çelik"

puts ad + " " + soyad		#=>Furkan Çelik

ad2 = "Hasan"
soyad2 = "Çelik"

puts ad2 << " " << soyad2		#=>Furkan Çelik
```
` + ` ve ` << ` metodlarý ayný iþlemi yapýyor gibi gözüksede aralarýnda bir fark vardýr

` + ` metodunu kullandýktan sonra ad ve soyad deðiþkenlerinin deðeri deðiþmezken ` << ` metodunu kullandýktan sonra
ad2 deðiþkeninin deðeri Hasan deðil Hasan Çelik oldu.

Baþka bir örnekle inceleyelim

```
gobek_adi = "Bekir"
ad = "Furkan"
soyad = "Çelik"

gobek_adi << ad << soyad

puts gobek_adi		#=>Bekir Furkan Çelik
puts ad				#=>Furkan
puts soyad			#=>Çelik
```

Görüldüðü gibi ` << ` operatörü en baþtaki deðiþkenin deðerini deðiþtirdi ve diðerlerinin deðerini deðiþtirmedi 

**concat metodu**

Metinleri birleþtimenin bir diðer yolu da concat metodudur.

```
a = "Merhaba"
b = "nasýlsýn"
c = "iyi misin?"

puts a.concat(b).concat(c)		#=>Merhaba nasýlsýn iyi misin?
puts a							#=>Merhaba nasýlsýn iyi misin?
puts b							#=>nasýlsýn
puts c							#=>iyi misin?
```

Örneðe bakýldýðýnda concat metodunun ` << ` metodu ile ayný iþlemi yaptýðý görülmektedir.

**Farklý bir birleþtirme yöntemi**

Örnek üzerinde inceleyelim

```
ad = "Furkan"
metin = "Merhaba " "#{ad}" ", hoþ geldin!"
print metin		#=>Merhaba Furkan, hoþ geldin!
```
Arada + ya da baþkabir operatör yok!
Birde bunu inceleyelim

```
ad = "Furkan"
metin  = "Merhaba" , "#{ad}", ", hoþ geldin"
print metin		#=>Merhaba Furkan, hoþ geldin!
``` 

Ýki örnek arasýndaki tek fark metinler arasýna , (virgül) koymamýz oldu.

` print metin.inspect `
dediðimizde ekran çýktýsý
` #=> "[\"Merhaba \",\"Furkan\",\", hoþ geldin!\"]" `
Görüldüðü gibi metin burda string deðil bir dizi olmuþ.

##Büyük/Küçük Harf Dönüþümü

**Büyük harfe çevirme upcase**

```
metin = "merhaba"
print metin.upcase		#=>"MERHABA"
print metin				#=>"merhaba"
```

Görüldüðü gibi upcase metodu kullanýlarak metin harfleri büyük harfe çevrildi ama deðiþken bu durumdan etkilenmedi bunun için Rubyde özel metodlar var 
bunlar bang diye adlandýrýlýyor ve metod uygulanýnca deðiþkenimizin deðerine etki ediyor. þu þekilde inceleyebiliriz.

```
metin = "merhaba"
print metin.upcase!		#=>"MERHABA"
print metin				#=>"MERHABA"
```

upcase! metodunu kullandýk ! ile biten metodlar bang! metodlarýdýr bunlar dediðim gibi deðiþkenin deðerini etkilerler metin deðiþkenimiz yeni deðerini almýþ oldu.

**Küçük harfe çevirme downcase**

```
metin = "MERHABA"
print metin.downcase		#=>"merhaba"
print metin.downcase!		#=>"merhaba"
#downcase! metodu ile deðiþkenimizin deðerini etkilemiþ oluyoruz.
print metin					#=>"merhaba"
```

**swapcase Metodu**

swapcase metodu ile büyük harfleri küçük harflere küçük harfleri büyük harflere dönüþtürüyoruz.

```
metin = "mErHaBa"
print metin.swapcase		#=>"MeRhAbA"
print metin.swapcase!		#=>"MeRhAbA"
print metin					#=>"MeRhAbA"
```



**capitalize Metodu**

capitalize metodu ile metnin sadece ilk harfini büyük diðerlerini küçük yapabiliriz.

```
metin = "bu Birinci cümle. Bu ikinci."
print metin.capitalize		#=>"Bu birinci cümle. bu ikinci."
print metin.capitalize!		#=>"Bu birinci cümle. bu ikinci."
print metin					#=>"Bu birinci cümle. bu ikinci."
```


##Alfabe Dýþý Karakter Temizleme
Bazen metin içindeki alfabe dýþý karakterlerin temizlenmesi gerekir (\f,\n,\r,\s,\t) boþluk karakterleri gibi.
bunun için 3 metod vardýr.

**lstrip** metnin sadece sol tarafýndaki alfabe dýþý karakterleri temizler.
**rstrip** metnin sadece sað tarafýndaki alfabe dýþý karakterleri temizler.
**strip** metodu her iki tarafdaki alfabe dýþý karakterleri temizler.

```
metin = "   \t Merhaba   \r\n"
puts metin.lstrip.inspect		#=>"Merhaba   \r\n"
puts metin.rstrip.inspect		#=>"   \t Merhaba"
puts metin.strip.inspect		#=>"Merhaba"
```

##Baþka Türden Veriyi Metne Dönüþtürme

Herhangibir türden veriyi metne dönüþtürmek için **to_s** metodundan faydalanýlýr.

```
5.to_s							#=> "5"
false.to_s						#=> "false"
[1,2,"elma","armut"].to_s		#=> "12elmaarmut"
puts :sembol.to_s				#=> "sembol"
PI = "3.1415"					#PI adýnda sabit tanýmlandý
puts PI.to_s					#=> "3.14"
```

##Metni Diziye Dönüþtürmek

Bir metin ifadesi belirli bir karakterlerle (boþluk, virgül, nokta vb.) ayrýlmýþ bir biçimde ise ve bu ifadeyi diziye dönüþtürmek istersek **split** metodu kullanýlýr.

Eðer ayýrýcý karakter boþluk ise split metoduna herhangibir parametre göndermemize gerek yoktur.

```
metin = "Karpuz Muz Elma Armut"
metin.split			#=>["Karpuz","Muz","Elma","Armut"]
```

Eðer boþluk dýþýnda bir ayýrýcý karakter kullanýlmýþsa bu karakterin parametre olarak girilmesi gerekiyor.

```
metin = "Karpuz*Muz*Elma*Armut"
metin.split('*')			#=>["Karpuz","Muz","Elma","Armut"]
```

>Diziyi tekrar metin haline dönüþtürmek istediðimizde yada herhangibir diziyi belirli bir karakterle metne dönüþtürmek için **join** metodu kullanýlýr.
>join metodu dizilere tanýmlý bir metottur metinlerde join metodu kullanýlýrsa hata alýnýr.

```
metin = "Karpuz*Muz*Elma*Armut"
metin.split('*')			#=>["Karpuz","Muz","Elma","Armut"]
metin.join('+')				#=>Karpuz+Muz+Elma+Armut
```


>Rubyde Metinlerle birlikte kullanýlabilecek 100'den fazla metod mevcuttur
>Tüm metodlar için http://ruby-doc.org/core-2.2.1/String.html adresine bakabilirsiniz.

