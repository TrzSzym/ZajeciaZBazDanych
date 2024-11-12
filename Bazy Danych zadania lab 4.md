# Zadania lab4

## Zadanie 1

```sql

delete from postac where nazwa != "bjorn" and rodzaj="wiking" order by wiek desc limit 2;

```
```sql

alter table walizka drop foreign key walizka_ibfk_1;
alter table przetwory drop foreign key przetwory_ibfk_1;
alter table przetwory drop foreign key przetwory_ibfk_2;
alter table postac change id_postaci id_postaci int;
alter table postac drop primary key;

```

## Zadanie 2

```sql

alter table postac add pesel char(11);
alter table postac change pesel pesel char(11) primary key;
alter table postac change rodzaj rodzaj enum(""

```
```sql

alter table postac change rodzaj rodzaj enum("wiking", "ptak", "kobieta", "syrena");

```
```sql

insert into postac values ("92926123412", 25, "Gertruda Nieszczera", "syrena", "1999-12-12", "25", null, null);

```

## Zadanie 3

```sql

update postac set statek_nazwa="maria" where nazwa like "%a%";

```
```sql

update statek set max_ladownosc=(max_ladownosc*0.7) where data_wodowania like "19__-__-__" or data_wodowania like "2000-__-__";

```
```sql

alter table postac add check(wiek<=1000);

```

## Zadanie 4

```sql

alter table postac add check(wiek<=1000);

```
```sql

create table marynarz like postac;
insert into marynarz select * from postac where statek_nazwa is not null;

```

## Zadanie 5

```sql

update marynarz set statek_nazwa=null;

```
```sql

delete from marynarz where nazwa!="bjorn" and rodzaj="wiking" limit 1;

```
```sql

alter table postac drop foreign key postac_ibfk_1
delete from statek where nazwa_statku like "%"

```
```sql

drop table statek;

```
```sql

create table zwierz (
id int auto_increment primary key,
nazwa varchar(80),
wiek tinyint);

```
```sql

insert into zwierz select id_postaci, nazwa, wiek from postac where rodzaj="drozd";

```
