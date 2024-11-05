#Lab3 zadania
##zadanie 4

```sql

create table przetwory(
id_przetworu INT primary key,
rok_produkcji year default 1654,
id_wykonawcy INT,
zawartosc text,
dodatek text,
id_konsumenta INT,
foreign key (id_wykonawcy) references postac(id_postaci),
foreign key (id_konsumenta) references postac(id_postaci)
);
