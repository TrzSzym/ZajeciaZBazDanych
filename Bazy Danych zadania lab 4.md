# Zadania lab4

##Zadanie 1

``sql

delete from postac where nazwa != "bjorn" and rodzaj="wiking" order by wiek desc limit 2;

```
```sql

alter table walizka drop foreign key walizka_ibfk_1;
alter table przetwory drop foreign key przetwory_ibfk_1;
alter table przetwory drop foreign key przetwory_ibfk_2;
alter table postac change id_postaci id_postaci int;
alter table postac drop primary key;

```
