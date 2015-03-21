#05.Sayýlar

Rubyde herþey nesne olduðu için Rubyde sayý oluþturmak için de Numeric sýnýfý kullanýlýr.

```
				    Numeric
			    ---| | | | |-------
			   /    /  |  \        \
			  /    /   |   \        \
			 /    /    |    \        \
	   Integer   Float | BigDecimal   Rational
	   /   \        Complex
 Fixnum    Bignum
 
```

Numeric sýnýfý yukarýdaki gibi alt sýnýflarý içerir.
Integer sýnýfý tamsayýlarý temsil etmek için kullanýlýr. Integer sýnýfý Fixnum ve Bignum adýnda iki sýnýf içerir.

```
p sayi = 2**30-1		#=> 1073741823
p sayi.class			#=> Fixnum

p sayi = 2**30			#=> 1073741824
p sayi.class			#=> Bignum
```

31bit içinde saklayabileceðimiz en büyük sayý 2**30-1 dir fixnum sýnýfýnda saklanýr sayý 1 artýrýldýðýnda fixnum sýnýrýný aþtýðý için Ruby otomatik olarak sayýyý bignum sýnýfýna geçirmiþtir.

Sayýnýn okunabilirliðini arttýrmak için ` _ ` kullanýlýr bu alt tire sayýnýn deyerini deðiþtirmeyecektir.

```
p sayi = 1_234_567_890		#=> 1234567890
```

> Bir sayýnýn bellekte kaç bayt yer kapladýðýný öðrenmek için ` size ` metodu kullanýlýr.

```
p 12.size	#=> 4
```

Sayý oluþtururken dikkat edilmesi gereken þeylerden biriside onluk sistemdeki bir sayýnýn sýfýr ile baþlamamasý gerektiðidir.
Bir sayýyý baþýnda sýfýr kullanarak yazarsak Ruby bu sayýyý sekizlik (octal) sistemde bir sayý larak algýlar.
Sayýnýn içerisinde 0..7 aralýðýnda rakamlar kullanýrsak ruby bunu otomatik olarak onluk sisteme çevirir 7'den büyük bir rakam kullanýldýðýnda
ise hata mesajý verir. Bununla beraber Ruby, ikilik (binary) ve onaltýlýk (hexdecimal) tabanýndaki sayýlarý da kullanmamýza imkan tanýr. 
Örnek olarak:

```
p sayi = 025			#=> 21
p sayi = 08

SyntaxError: (irb):2: Invalid octal digit
	from C:/Ruby/bin/irb:12:in '<main>'

p sayi = 0b10101100		#=> 172
p sayi = 0x1FB			#=> 507
p sayi = 0X1AB			#=> 427
	
```

Float sýnýfýný ise ondalýk sayýlarla çalýþmak için kullanýrýz.
```
sayi = 3.14159
p sayi.class		#=> Float
```

Bilimsel gösterim olarak bilinen yöntemin Rubyde kullanýmý þu þekildedir;

```
p sayi = 6.02e23		#=> 6.02e+23 
#(6.02*10^23) þeklinde ifade edilir.
```

Complex sýnýfý karmaþýk sayýlar üzerinde çalýþýrken kullanýlýr ``a+bi ` þeklinde tanýmlanýrlar ve kullanýlýrlar.

```
p Complex(1)			#=> (1+0i)
p Complex(3,4)			#=> (3+4i)
p Complex(3.1,8.2)		#=> (3.1+8.2i)
```
**Bir sayýyý karmaþýk sayýya çevirmek için `to_c` metodu kullanýlýr.**

Rational sýnýfý ile rasyonel sayýlarý sýnýfýmýza dahil ederiz. Ýlk parametre pay ikinci parametre ise paydadýr.
```
p Rational(1)					#=>(1/1)
p Rational(3,5)					#=>(3/5)
p Rational(20,36)				#=>(3/5)
p Rational(7,-5)				#=>(-7/5)
p Rational(0.1)					#=>(3602879701896397/36028797018963968)
p Rational('0.1')				#=>(1/10)
p Rational('2/3')				#=>(2/3)
p 0.3.rationalize				#=> (3/10)
```
Rasyonal sayý oluþturmak için bazý örnekler bu þekildedir. 3.satýrda rasyonal sayýnýn otomatik olarak sadeleþtiði görülebilir.
5.satýrda ise Float türünden bir sayýyý Rational türüne çevrildiðinde nasýl bir sonuç alacaðýný görüyoruz. Bu sonuç float türünden olan 
sayýlarýn hafýzada saklanma þeklinden kaynaklanmaktadýr. Dönüþümü tam sayý olarak yapmak istersek 6 ve 7. satýrlardaki gibi parametreyi metin olarak göndermeliyiz. Son satýrdaki metod ise alternatif olarak kullanýlabilir.

BigDecimal sýnýfý ise yüksek hassasiyet gerektiren iþlemler için kullanýlýr. Float tipinden olan sayýlarý bellekte saklanma þekillerinden kaynaklanan bazý problemler oluþabilir.
Aþþaðýdaki örnekteki gibi Float türünden sayýlarla çalýþmak zaman zaman sorun oluþturabilir.

```
p 0.5-0.4			#=> 0.09999999999999998
p 0.4-0.1			#=> 0.03000000000000004
```

Bu sorunu çözmek için BigDecimal türü kullanýlabilir. BigDecimal türü bir kütüphane olarak sunulmaktadýr  **require** anahtar kelimesini kullanarak
kodumuza dahil etmemiz gerekmektedir.

```
require "bigdecimal"
sayi1 = BigDecimal.new("0.5")			#=> 0.5E0
sayi2 = BigDecimal.new("0.4")			#=> 0.4E0
sayi3 = sayi1-sayi2						#=> 0.1E0
p sayi3.to_f							#=> 0.1
```