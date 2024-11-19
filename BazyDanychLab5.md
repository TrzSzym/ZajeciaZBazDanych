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
