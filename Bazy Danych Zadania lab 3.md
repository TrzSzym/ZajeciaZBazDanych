# Lab3 zadania
## zadanie 4

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

Insert Into przetwory values (
default,
default,
1,
'Bigos',
default,
3);

 ```

## zadanie 5

```sql

Insert Into postac values
(default, 'Raban', 'Wiking', '1999-10-20', 25),
(default, 'Maciej', 'Wiking', '1789-09-01', 235),
(default, 'Zdziś', 'Wiking', '644-11-02', 255),
(default, 'Miś', 'Wiking', '641-12-12', 255),
(default, 'Demogorgon', 'Wiking', '647-12-13', 255);

```
```sql
create table statek(
nazwa_statku varchar(100) primary key,
rodzaj_statku enum('kajak', 'żaglowiec', 'kuter'),
data_wodowania date,
max_ladownosc INT(255) unsigned);

```
```sql

insert into statek values
('Maria', 'Kajak', '0645-12-12', 222),
('Monte', 'Kuter', '1555-05-05', 24321);

```
```sql

alter table postac add funkcja varchar(50);

```
```sql

update postac set funkcja="kapitan" where id_postaci=1;

```
```sql

alter table postac add statek_nazwa varchar(50), add foreign key (statek_nazwa) references statek(nazwa_statku);

```
```sql

update postac set statek_nazwa='maria' where rodzaj='wiking' or rodzaj='ptak';
update postac set statek_nazwa='monte' where id_postaci=9 or id_postaci=6 or id_postaci=4;

```
```sql

delete from izba where nazwa_izby='spizarnia';

```
```sql

drop table izba;

```
