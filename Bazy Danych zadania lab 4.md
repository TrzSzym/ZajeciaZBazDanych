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
