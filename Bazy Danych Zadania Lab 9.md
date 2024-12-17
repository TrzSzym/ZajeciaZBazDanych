# Lab 9

## Zadanie 1.1

```sql

select nazwisko from pracownik order by nazwisko

```
```sql

select imie, nazwisko, pensja from pracownik where year(data_urodzenia)>1979;

```
```sql

select * from pracownik where pensja>=3500 and pensja<=5000

```
```sql

select t.nazwa_towaru from stan_magazynowy s inner join towar t on s.towar=t.id_towaru where s.ilosc>10;

```
```sql

select nazwa_towaru from towar where nazwa_towaru like "A%" or nazwa_towaru like "B%" or nazwa_towaru like "C%"

```
```sql

select * from klient where czy_firma!=1;

```
```sql

select * from zamowienie order by data_zamowienia desc limit 10 

```
```sql

select * from pracownik order by pensja limit 5

```
```sql

select * from towar where nazwa_towaru not like "%a%" order by cena_zakupu desc limit 10 

```
```sql

select * from towar t inner join stan_magazynowy s on s.towar=t.id_towaru
inner join jednostka_miary j on j.id_jednostki=s.jm where j.nazwa="szt"
order by t.nazwa_towaru, t.cena_zakupu desc

```
```sql

create table towary_powyzej_100 (select * from __firma_zti.towar where cena_zakupu>=100);

```
```sql

create table pracownik_50_plus (select * from __firma_zti.pracownik where year(data_urodzenia) <= 1974)

```

## Zadanie 1.2

```sql

select p.imie, p.nazwisko, d.nazwa from pracownik p inner join dzial d on p.dzial=d.id_dzialu

```
```sql

select t.nazwa_towaru, k.nazwa_kategori, s.ilosc from towar t inner join stan_magazynowy s on t.id_towaru=s.towar
inner join kategoria k on k.id_kategori=t.kategoria order by s.ilosc desc

```
```sql

select * from zamowienie z inner join status_zamowienia s on z.status_zamowienia=s.id_statusu_zamowienia
 where s.nazwa_statusu_zamowienia like "anulowane"

```
```sql

select  * from klient k inner join adres_klienta a on k.id_klienta=a.klient where a.miejscowosc like "Olsztyn"

```
```sql

select * from jednostka_miary j where j.id_jednostki not in (select distinct(jm) from stan_magazynowy)

```
```sql

SELECT z.numer_zamowienia, t.nazwa_towaru, p.ilosc, p.cena from pozycja_zamowienia p
inner join zamowienie z on z.id_zamowienia=p.zamowienie
inner join towar t on p.towar=t.id_towaru
where year(z.data_zamowienia) like "2018"

```
```sql



```
