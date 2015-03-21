#05.Say�lar

Rubyde her�ey nesne oldu�u i�in Rubyde say� olu�turmak i�in de Numeric s�n�f� kullan�l�r.

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

Numeric s�n�f� yukar�daki gibi alt s�n�flar� i�erir.
Integer s�n�f� tamsay�lar� temsil etmek i�in kullan�l�r. Integer s�n�f� Fixnum ve Bignum ad�nda iki s�n�f i�erir.

```
p sayi = 2**30-1		#=> 1073741823
p sayi.class			#=> Fixnum

p sayi = 2**30			#=> 1073741824
p sayi.class			#=> Bignum
```

31bit i�inde saklayabilece�imiz en b�y�k say� 2**30-1 dir fixnum s�n�f�nda saklan�r say� 1 art�r�ld���nda fixnum s�n�r�n� a�t��� i�in Ruby otomatik olarak say�y� bignum s�n�f�na ge�irmi�tir.

Say�n�n okunabilirli�ini artt�rmak i�in ` _ ` kullan�l�r bu alt tire say�n�n deyerini de�i�tirmeyecektir.

```
p sayi = 1_234_567_890		#=> 1234567890
```

> Bir say�n�n bellekte ka� bayt yer kaplad���n� ��renmek i�in ` size ` metodu kullan�l�r.

```
p 12.size	#=> 4
```

Say� olu�tururken dikkat edilmesi gereken �eylerden biriside onluk sistemdeki bir say�n�n s�f�r ile ba�lamamas� gerekti�idir.
Bir say�y� ba��nda s�f�r kullanarak yazarsak Ruby bu say�y� sekizlik (octal) sistemde bir say� larak alg�lar.
Say�n�n i�erisinde 0..7 aral���nda rakamlar kullan�rsak ruby bunu otomatik olarak onluk sisteme �evirir 7'den b�y�k bir rakam kullan�ld���nda
ise hata mesaj� verir. Bununla beraber Ruby, ikilik (binary) ve onalt�l�k (hexdecimal) taban�ndaki say�lar� da kullanmam�za imkan tan�r. 
�rnek olarak:

```
p sayi = 025			#=> 21
p sayi = 08

SyntaxError: (irb):2: Invalid octal digit
	from C:/Ruby/bin/irb:12:in '<main>'

p sayi = 0b10101100		#=> 172
p sayi = 0x1FB			#=> 507
p sayi = 0X1AB			#=> 427
	
```

Float s�n�f�n� ise ondal�k say�larla �al��mak i�in kullan�r�z.
```
sayi = 3.14159
p sayi.class		#=> Float
```

Bilimsel g�sterim olarak bilinen y�ntemin Rubyde kullan�m� �u �ekildedir;

```
p sayi = 6.02e23		#=> 6.02e+23 
#(6.02*10^23) �eklinde ifade edilir.
```

Complex s�n�f� karma��k say�lar �zerinde �al���rken kullan�l�r ``a+bi ` �eklinde tan�mlan�rlar ve kullan�l�rlar.

```
p Complex(1)			#=> (1+0i)
p Complex(3,4)			#=> (3+4i)
p Complex(3.1,8.2)		#=> (3.1+8.2i)
```
**Bir say�y� karma��k say�ya �evirmek i�in `to_c` metodu kullan�l�r.**

Rational s�n�f� ile rasyonel say�lar� s�n�f�m�za dahil ederiz. �lk parametre pay ikinci parametre ise paydad�r.
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
Rasyonal say� olu�turmak i�in baz� �rnekler bu �ekildedir. 3.sat�rda rasyonal say�n�n otomatik olarak sadele�ti�i g�r�lebilir.
5.sat�rda ise Float t�r�nden bir say�y� Rational t�r�ne �evrildi�inde nas�l bir sonu� alaca��n� g�r�yoruz. Bu sonu� float t�r�nden olan 
say�lar�n haf�zada saklanma �eklinden kaynaklanmaktad�r. D�n���m� tam say� olarak yapmak istersek 6 ve 7. sat�rlardaki gibi parametreyi metin olarak g�ndermeliyiz. Son sat�rdaki metod ise alternatif olarak kullan�labilir.

BigDecimal s�n�f� ise y�ksek hassasiyet gerektiren i�lemler i�in kullan�l�r. Float tipinden olan say�lar� bellekte saklanma �ekillerinden kaynaklanan baz� problemler olu�abilir.
A��a��daki �rnekteki gibi Float t�r�nden say�larla �al��mak zaman zaman sorun olu�turabilir.

```
p 0.5-0.4			#=> 0.09999999999999998
p 0.4-0.1			#=> 0.03000000000000004
```

Bu sorunu ��zmek i�in BigDecimal t�r� kullan�labilir. BigDecimal t�r� bir k�t�phane olarak sunulmaktad�r  **require** anahtar kelimesini kullanarak
kodumuza dahil etmemiz gerekmektedir.

```
require "bigdecimal"
sayi1 = BigDecimal.new("0.5")			#=> 0.5E0
sayi2 = BigDecimal.new("0.4")			#=> 0.4E0
sayi3 = sayi1-sayi2						#=> 0.1E0
p sayi3.to_f							#=> 0.1
```