=ODEV 1=
Merhabalar,

Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1.1-film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
1.2-film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
1.3-film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
1.4-customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
1.5-film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
Kolay Gelsin.


1.1-        SELECT title, description FROM film;

1.2-        SELECT * FROM film
            WHERE length > 60 AND length < 75;

1.3-        SELECT * FROM film
            WHERE rental_rate = 0.99 AND (replacement_cost = 12.99 OR replacement_cost = 28.99);

1.4-        SELECT last_name FROM customer
            WHERE first_name = 'Mary';
            
1.5-        SELECT * FROM film
            WHERE NOT length > 50 AND NOT (rental_rate = 2.99 OR rental_rate = 4.99);

=ODEV 2=
Merhabalar,

Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

2.1-film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
2.2-actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
2.3-film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)
Kolay Gelsin.




2.1-        SELECT * FROM film
            WHERE replacement_cost BETWEEN 12.99 AND 16.99;

2.2-        SELECT first_name, last_name FROM actor WHERE first_name
            IN ('Penelope','Nick','Ed');

2.3-        SELECT * FROM film WHERE rental_rate
            IN (0.99, 2.99, 4.99)
            AND replacement_cost IN (12.99, 15.99, 28.99);

=ODEV 3=
Merhabalar,

Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

3.1-country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
3.2-country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
3.3-film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
3.4-film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
Kolay Gelsin.


3.1-        SELECT country FROM country
            WHERE country LIKE 'A%a' ;

3.2-        SELECT country FROM country
            WHERE LENGTH(country) >= 6 AND country LIKE '%n';

3.3-        SELECT title FROM film
            WHERE (title ILIKE '%t%t%t%t%');


3.4-        SELECT * FROM film
            WHERE title LIKE 'C%'
            AND length > 90 AND rental_rate = 2.99;

=ODEV 4=
Merhabalar,

Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

4.1-film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
4.2-film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
4.3-film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
4.4-country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
4.5-city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?
Kolay Gelsin.



4.1-        SELECT DISTINCT replacement_cost FROM film;

4.2-        SELECT COUNT(DISTINCT replacement_cost)
            AS replacement_costs
            FROM film;

4.3-        SELECT DISTINCT COUNT (title) FROM film
            WHERE title LIKE 'T%'
            AND rating = 'G';

4.4-        SELECT COUNT (country) FROM country
            WHERE LENGTH(country) = 5;

4.5-        SELECT COUNT(*)
            FROM city
            WHERE city LIKE '%r' OR city LIKE '%R';
