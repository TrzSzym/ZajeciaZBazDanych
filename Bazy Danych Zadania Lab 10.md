# Lab 10

## Zadanie 1

```sql

select imie, nazwisko, year(data_urodzenia) from pracownik

```
## Zadanie 2

```sql

select imie, nazwisko, (2025-year(data_urodzenia)) as "Wiek" from pracownik

```

## Zadanie 3

```sql

select distinct(d.nazwa), count(p.dzial) as "Liczba pracownikow dzialu" from pracownik p left join dzial d on p.dzial=d.id_dzialu  group by (d.nazwa)

```

## Zadanie 4

```sql

select distinct(k.nazwa_kategori), count(t.kategoria) as "liczba produktów" from towar t left join kategoria k on k.id_kategori=t.kategoria group by k.nazwa_kategori

```

## Zadanie 5

```sql

select distinct(k.nazwa_kategori), group_concat(nazwa_towaru SEPARATOR ", ") as "liczba produktów" from towar t left join kategoria k on k.id_kategori=t.kategoria group by k.nazwa_kategori

```

## Zadanie 6

```sql

select round((sum(pensja)/count(id_pracownika)), 2) as "Srednia pensja w firmie" from pracownik

```

## Zadanie 7

```sql

select round(avg(pensja), 2) as srednie_zarobki from pracownik where (2025-year(data_zatrudnienia))>=5

```

## Zadanie 8

```sql

select t.nazwa_towaru as towar, count(p.id_pozycji) as ilosc_zamowien from pozycja_zamowienia p inner join towar t on p.towar = t.id_towaru group by t.nazwa_towaru order by ilosc_zamowien desc limit 10;

select distinct(t.nazwa_towaru) as towar, sum(towar*ilosc) as ilosc_zamowien from pozycja_zamowienia p inner join towar t on p.towar = t.id_towaru group by t.nazwa_towaru order by ilosc_zamowien desc limit 10;

```

## Zadanie 9

```sql

select z.numer_zamowienia,  sum(p.ilosc*t.cena_zakupu) as "Łączny koszt zamowienia" from zamowienie z 
inner join pozycja_zamowienia p on p.zamowienie=z.id_zamowienia 
inner join towar t on t.id_towaru=p.towar
where z.data_zamowienia like "2017-01-__" or z.data_zamowienia like "2017-02-__" or z.data_zamowienia like "2017-03-__" group by z.numer_zamowienia 

```

## Zadanie 10

```sql

select p.id_pracownika, concat(p.imie, " ", p.nazwisko) as "imie i nazwisko", sum(poz.cena) from zamowienie z 
inner join pracownik p on z.pracownik_id_pracownika = p.id_pracownika 
inner join pozycja_zamowienia poz on poz.zamowienie=z.id_zamowienia group by id_pracownika

```

## Zadanie 11

```sql

select distinct(d.nazwa), min(p.pensja), max(p.pensja) from pracownik p inner join dzial d on d.id_dzialu=p.dzial group by d.nazwa

```

## Zadanie 12

```sql

select k.pelna_nazwa, z.id_zamowienia, sum(p.ilosc*p.cena) as "Wartosc" from zamowienie z inner join klient k on k.id_klienta=z.klient
inner join pozycja_zamowienia p on p.zamowienie=z.id_zamowienia group by id_zamowienia order by Wartosc desc limit 10

```

## Zadanie 13

```sql

select distinct(year(z.data_zamowienia)) as "Rok", round(sum(p.ilosc*p.cena), 2) as "Przychod" from zamowienie z 
inner join pozycja_zamowienia p on p.zamowienie=z.id_zamowienia 
group by Rok order by przychod desc

```

## Zadanie 14

```sql

select sum(p.cena*p.ilosc) from zamowienie z 
inner join pozycja_zamowienia p on p.zamowienie=z.id_zamowienia
inner join status_zamowienia s on s.id_statusu_zamowienia=z.status_zamowienia
where s.nazwa_statusu_zamowienia like "anulowane"

```

## Zadanie 15

```sql

select distinct(a.miejscowosc) as "miasto", count(z.id_zamowienia) as "ilosc zamowien", sum(p.ilosc*p.cena) as "suma wartosci zamowien" from zamowienie z
inner join pozycja_zamowienia p on p.zamowienie=z.id_zamowienia
inner join klient k on k.id_klienta=z.klient
inner join adres_klienta a on a.klient=k.id_klienta
inner join typ_adresu t on t.id_typu=a.typ_adresu
where t.nazwa like "podstawowy" group by miasto

```

## Zadanie 16

```sql

select sum(p.ilosc*(p.cena-t.cena_zakupu)) as "dochód" from pozycja_zamowienia p
inner join towar t on t.id_towaru=p.towar
inner join zamowienie z on z.id_zamowienia=p.zamowienie
inner join status_zamowienia s on s.id_statusu_zamowienia=z.status_zamowienia
where s.nazwa_statusu_zamowienia like "zrealizowane"

```

## Zadanie 17

```sql

select distinct(year(data_zamowienia)) as "rok",  sum(p.ilosc*(p.cena-t.cena_zakupu)) as "dochód" from pozycja_zamowienia p
inner join towar t on t.id_towaru=p.towar
inner join zamowienie z on z.id_zamowienia=p.zamowienie
inner join status_zamowienia s on s.id_statusu_zamowienia=z.status_zamowienia
where s.nazwa_statusu_zamowienia like "zrealizowane"
group by rok

```
