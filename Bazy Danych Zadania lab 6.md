# Zadania lab 6

## Zadanie 1
```sql

select avg(waga) from kreatura where rodzaj like "wiking";

```
```sql

select distinct(rodzaj), avg(waga) as "średnia waga", count(rodzaj) as "liczba" from kreatura group by rodzaj; 

```
```sql

select distinct(rodzaj), avg(concat(2024-year(dataUr))) as "sredni wiek" from kreatura group by rodzaj; 

```

## Zadanie 2

```sql

select rodzaj, sum(waga) from zasob group by rodzaj;

```
```sql

select distinct(nazwa), avg(waga) from zasob where ilosc>=4 group by nazwa having avg(waga)>10;

```
```sql

select distinct(rodzaj), (count(nazwa)) as "ilosc nazw" from zasob where ilosc>1 group by rodzaj;

```

## Zadanie 3

```sql

select distinct(kreatura.nazwa), sum(ekwipunek.ilosc) from ekwipunek inner join kreatura on ekwipunek.idKreatury=kreatura.idKreatury group by nazwa;

```
```sql

select distinct(kreatura.nazwa), group_concat(zasob.nazwa SEPARATOR", ") as "zasoby" from ekwipunek
inner join kreatura on ekwipunek.idKreatury=kreatura.idKreatury
inner join zasob on ekwipunek.idZasobu=zasob.idZasobu group by kreatura.nazwa;

```
```sql

select kreatura.idKreatury, kreatura.nazwa from kreatura left join ekwipunek on kreatura.idKreatury=ekwipunek.idkreatury where ekwipunek.idKreatury is null;

```

## Zadanie 4

```sql

select distinct(kreatura.nazwa), group_concat(zasob.nazwa SEPARATOR", ") as "zasoby" from ekwipunek
inner join kreatura on ekwipunek.idKreatury=kreatura.idKreatury
inner join zasob on ekwipunek.idZasobu=zasob.idZasobu where kreatura.dataur like "167_-__-__" and kreatura.rodzaj like "wiking" group by kreatura.nazwa;

```
```sql

select kreatura.nazwa from ekwipunek
inner join kreatura on ekwipunek.idKreatury=kreatura.idKreatury
inner join zasob on ekwipunek.idZasobu=zasob.idZasobu 
where zasob.rodzaj like "jedzenie"
order by kreatura.dataUr desc
limit 5

```
```sql

select concat(k1.nazwa,"-",k2.nazwa) from kreatura k1 join kreatura k2 on k1.idKreatury + 5=k2.idKreatury order by k1.idKreatury

```

## Zadanie 5

```sql

select distinct(kreatura.nazwa), avg(zasob.waga) from ekwipunek
inner join kreatura on ekwipunek.idKreatury=kreatura.idKreatury
inner join zasob on ekwipunek.idZasobu=zasob.idZasobu 
where kreatura.rodzaj not like "wąż" or "małpa"
group by kreatura.nazwa
having sum(ekwipunek.ilosc)<30

```
```sql

nie wiem :(

```
