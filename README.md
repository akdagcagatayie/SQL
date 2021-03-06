# SQL

### PostgreSQL - dvdrental

<br>
<hr>

## Ödev 1

<br>

> 1.film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız. 

>`SELECT title,description FROM film;`


<br>

> 2.film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.

> `SELECT * FROM film WHERE length>60 AND length<75;`

<br>

> 3.film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.

> `SELECT * from film WHERE rental_rate = 0.99 AND(replacement_cost = 12.99 OR replacement_cost = 28.99);`

<br>

> 4.customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

> `SELECT last_name FROM customer WHERE first_name = 'Mary';`

<br>

> 5.film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

> `SELECT * FROM film where length < 50 and NOT(rental_rate = 2.99 OR rental_rate = 4.99);`

<hr>

## Ödev-2

<br>

>1.film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)

> `SELECT * FROM film where replacement_cost BETWEEN 12.99 AND 16.99;`


<br>

>2.actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

> `SELECT first_name,last_name from actor WHERE first_name IN ('Penelope','Nick','Ed');`



<br>

>3.film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

> `SELECT * FROM film WHERE rental_rate IN(0.99, 2.99, 4.99) AND replacement_cost IN(12.99, 15.99, 28.99);`

<br>
<hr>

## Ödev-3

<br>

>1.country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

> `SELECT * FROM country WHERE country LIKE 'A%a';`

<br>

>2.country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

> `SELECT * FROM country WHERE country LIKE '_____%n';`

<br>

>3.film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

> `SELECT * FROM film WHERE title ILIKE '%T%T%T%T%';`

<br>


>4.film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

> `SELECT * from film WHERE title LIKE 'C%' AND length >90 AND rental_rate = 2.99;`

<br>
<hr>

## Ödev 4

<br>

>1.film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

> `SELECT DISTINCT(replacement_cost) FROM film;`

<br>

>2.film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

> `SELECT COUNT(DISTINCT(replacement_cost)) FROM film;`

<br>

>3.film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

> `SELECT COUNT(*) FROM film WHERE title LIKE 'T%' and rating = 'G';`

<br>

>4.country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

> `SELECT COUNT(*) FROM country WHERE country LIKE '_____';`

<br>

>5.city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?

> `SELECT COUNT(*) FROM city WHERE city ILIKE '%R';`

<br>
<hr>

## Ödev 5

<br>

>1.film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

>`SELECT * FROM film WHERE title LIKE '%n' ORDER BY length DESC 
LIMIT 5;`

<br>

>2.film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.

> `SELECT * FROM film WHERE title LIKE '%n' ORDER BY length ASC
OFFSET 5
LIMIT 5;`

<br>


>3.customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.


>`SELECT * FROM CUSTOMER WHERE store_id=1 ORDER BY last_name DESC LIMIT 4;`


<br>
<hr>

## Ödev 6

<BR>

>1.film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

>`select avg(rental_rate) from film;`

<br>

>2.film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?

>`SELECT COUNT(*) FROM film where title LIKE 'C%';`

<br>

>3.film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

>`SELECT MAX(length) FROM film where rental_rate = 0.99;`

<br>

>4.film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

>`SELECT COUNT(DISTINCT(replacement_cost)) FROM film where length > 150;`


<br>
<hr>

## Ödev 7

<br>

>1.film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

> `SELECT rating , COUNT(*) FROM film
GROUP BY rating;`

<br>

>2.film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

> `SELECT replacement_cost,COUNT(*) FROM film
GROUP BY replacement_cost
HAVING COUNT(*)>50;`

<br>

>3.customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir? 

>`SELECT store_id,COUNT(*) FROM customer
group by store_id;`


<br>


>4.city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.

> `SELECT country_id,COUNT(*) FROM city
group by country_id
order by COUNT(*) DESC
LIMIT 1;`

<br>
<hr>

## Ödev 9

<br>

>1.city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

> `SELECT city.city,country.country FROM city
INNER JOIN country
ON city.country_id = country.country_id;`

<br>

>2.customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

> `SELECT payment.payment_id,customer.first_name, customer.last_name FROM payment
INNER JOIN customer
ON payment.customer_id = customer.customer_id`

<br>

>3.customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

> `SELECT rental.rental_id , customer.first_name,customer.last_name FROM rental
INNER JOIN customer 
ON rental.customer_id = customer.customer_id;`

<br>
<hr>

## Ödev 10

<br>

>1.city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.

>`SELECT city.city , country.country FROM city
LEFT JOIN country
ON city.country_id = country.country_id`

<br>

>2.customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.

>`SELECT payment.payment_id,customer.first_name, customer.last_name FROM payment
RIGHT JOIN customer
ON payment.customer_id = customer.customer_id`

<br>

>3.customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.

>`SELECT rental.rental_id , customer.first_name,customer.last_name FROM rental
full JOIN customer 
ON rental.customer_id = customer.customer_id`

<br>
<hr>

## Ödev 12

<br>

>1.film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?

>`SELECT COUNT(*) FROM film
WHERE length > 
(
	SELECT AVG(length) from film
); `

<br>

>2.film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?

>`SELECT COUNT(*) FROM film WHERE rental_rate =
(
	SELECT MAX(rental_rate) FROM film
);`

<br>

>3.film tablosunda en düşük rental_rate ve en düşük replacement_cost değerlerine sahip filmleri sıralayınız.

>``SELECT COUNT(*) FROM filmWHERE rental_rate =(SELECT MIN      (rental_rate) FROM fil>)AND replacement_cost = (SELECT MIN(replacement_cost) From film); ``


<br>

>4.payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.

>``SELECTpayment.customer_id,customer.first_namecustomerlast_name,COUNT(payment.customer_id) FROM payment INNER JOIN customer
ON payment.customer_id = customer.customer_id
GROUP BY payment.customer_id,customer.first_name,customer.last_name
ORDER BY COUNT(payment.customer_id) DESC;
; ``

<br>
<hr>