# Lab 7

## Zadanie 1

```sql

insert into kreatura select * from wikingowie.kreatura

create talbe uczestnicy select * from wikingowie.uczestnicy;
create table etapy_wyprawy select * from wikingowie.etapy
create table sektor select * from wikingowie.sektor
create talbe wyprawa select * from wikingowie.wyprawa

```
```sql

select kreatura.nazwa from kreatura inner join uczestnicy on kreatura.idKreatury=uczestnicy.id_uczestnika where id_uczestnika is null;

```
```sql

select wyprawa.nazwa, sum(ekwpinuek.ilosc) from wyprawa inner join uczesstnicy on wyprawa.id_wyprawy = uczestnicy.id_wyprawy
inner join kreatura on kreatura.idKreatury = uczestnicy.id_uczestnika
right join ekwipunek on ekwipunek.idKreatury=kreatura.idKreatury
where wyprawa.nazwa is not null group by nazwa;
  
```

## Zadanie 2

```sql

select wyprawa.nazwa, count(uczestnicy.id_uczestnika), group_concat(distinct kreatura.nazwa) from wyprawa join uczestnicy on uczestnicy.id_wyprawy=wyprawa.id_wyprawy
join kreatura on uczestnicy.id_uczestnika = kreatura.idKreatury group by wyprawa.nazwa;

```
```sql

select distinct wyprawa.nazwa, wyprawa.data_rozpoczecia, etapy_wyprawy.kolejnosc, sektor.nazwa, kreatura.nazwa from etapy_wyprawy
inner join sektor on etapy_wyprawy.sektor = sektor.id_sektora
inner join wyprawa on etapy_wyprawy.idWyprawy= wyprawa.id_wyprawy
inner join kreatura on kreatura.idKreatury= wyprawa.kierownik
oredr by wyprawa.data_rozpoczecia, etapy _wyprawy.kolejnosc;

```

## Zadanie 3

```sql

select s.nazwa, count(e.sektor) from sektor s left join etapy_wyprawy e on s.id_sektora=e.sektor group by sektor.nazwa;

```
```sql

select k.nazwa, if(count(u.id_uczestnika)>0,'bral udzial w wyprawie', 'nie bral udzialu w wyprawie') from uczestnicy u right join kreatura k on k.idKreatury = u.id_uczestnika group by k.nazwa;

```

## Zadanie 4

```sql



```
