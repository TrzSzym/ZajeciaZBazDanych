# Zadania Lab 5
## Zadanie 1
```sql

create table kreatura select * from wikingowie.kreatura;
create table zasob select * from wikingowie.zasob;
create table ekwipunek select * from wikingowie.ekwipunek;

```
```sql

select * from zasob;

```
```sql

select * from zasob where rodzaj like "jedzenie";

```
```sql

select zasob.idZasobu, zasob.ilosc from ekwipunek, zasob where idKreatury like "1" or "3" or "5"

```

## Zadanie 2
```sql

select * from kreatura where rodzaj!="wiedzma" and udzwig>=50;

```
```sql

select * from zasob where waga>2 and waga<5

```
```sql

select * from kreatura where nazwa like "%or%" and udzwig>30 and udzwig<70;

```

## Zadanie 3
```sql

select * from zasob where dataPozyskania like "____-08-__" or "____-07-__"

```
```sql

select * from zasob where rodzaj is not null order by waga

```
```sql

select * from kreatura where dataUr is not null order by dataUr limit 5;

```

## Zadanie 4
```sql

select distinct rodzaj from zasob

```
```sql

select concat(nazwa,"-",rodzaj) as "nazwa - rodzaj" from kreatura where rodzaj like "wi%"

```
```sql

select nazwa, concat(ilosc*waga) as "waga calkowita" from zasob where year(dataPozyskania)>=2000 and year(dataPozyskania)<=2007

```

## Zadanie 5
```sql

select nazwa, concat(ilosc*waga*0.7) as "Masa netto jedzenia", concat(ilosc*waga*0.3) as "odpad" from zasob

```
```sql

select * from zasob where rodzaj is null

```
```sql

select distinct rodzaj from zasob where nazwa like "ba%" or nazwa like "%os" order by rodzaj

```
