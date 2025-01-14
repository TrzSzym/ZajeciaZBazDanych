# Zadanie 1
## 1
```sql
create table student(
	id_studenta int primary key auto_increment,
    imie varchar(100) not null,
    nazwisko varchar(100) not null,
    rok_studiow tinyint unsigned,
    data_urodzenia date
)
```
## 2
```sql
create table kierunek(
	id_kierunku int primary key auto_increment,
    nazwa_kierunku varchar(200) not null
)
```
## 3
```sql
create table student_na_kierunku(
	student int,
    kierunek int,
	constraint fk_student
    foreign key (student) references student(id_studenta)
    on delete set null,
    constraint fk_kierunek
    foreign key (kierunek) references kierunek(id_kierunku)
    on delete set null
)
```
## 4
```sql 
create table przedmiot(
	id_przedmiotu int primary key auto_increment,
    nazwa_przedmiotu varchar(200) not null,
    opis longtext
) 
```
## 5
```sql
create table kierunek_has_przedmiot(
	kierunek int not null,
    przedmiot int not null,
    obowiazkowy bool default 1,
	foreign key (kierunek) references kierunek(id_kierunku),
    foreign key (przedmiot) references przedmiot(id_przedmiotu),
    constraint pk_khp primary key (kierunek, przedmiot)
)
```
## 6
```sql
insert into student (id_studenta, imie, nazwisko, rok_studiow, data_urodzenia)
values(null, 'Marcin', 'Pakuła', 1, '2004-09-02')
insert into student (id_studenta, imie, nazwisko, rok_studiow, data_urodzenia)
values(null, 'Szymon', 'Trzpil', 1, '2004-10-28')
insert into student (id_studenta, imie, nazwisko, rok_studiow, data_urodzenia)
values(null, 'Jan', 'Kowalski', 3, '2002-03-11')
insert into student (id_studenta, imie, nazwisko, rok_studiow, data_urodzenia)
values(null, 'Adam', 'Rumiń0ski', 2, '1999-02-22')

insert into kierunek(id_kierunku, nazwa_kierunku)
values(null, 'informatyka'), (null, 'dietetyka')

insert into student_na_kierunku(student, kierunek)
values(1, 1), (2, 1), (3, 2), (3, 1)

insert into  przedmiot(id_przedmiotu, nazwa_przedmiotu, opis)
values(null, 'Podstawy logiki i teorii mnogości', 'Przedmiot podejmujący problemy logiczne
w matematyce i informatyce'),
(null, 'Anatomia', 'Przedmiot opisujący antamonię człowieka'),
(null, 'Przedmioty humanizujące', 'Przedmiot opierający się na naukach etycznych/filozoficznych'),
(null, 'bazy danych', 'Przedmiot praktyczny zawierający wiedzę nt. tworzenia i korzystania z
baz danych')

insert into kierunek_has_przedmiot(kierunek, przedmiot, obowiazkowy)
values(1, 1, 1), (2, 2, 1), (1, 3, 0), (1, 4, 1)
```
## 7
```sql
alter table przedmiot modify opis varchar(800) default 'brak opisu'
```
## 8
```sql

```
## 9
```sql
alter table kierunek_has_przedmiot
add semestr text not null,
add rok_studiow int unsigned not null 

update kierunek_has_przedmiot set semestr = '2024Z' where kierunek = 1;
update kierunek_has_przedmiot set semestr = '2021Z' where kierunek = 2;
update kierunek_has_przedmiot set rok_studiow = 2 where kierunek = 1;
update kierunek_has_przedmiot set rok_studiow = 1 where kierunek = 2;
update kierunek_has_przedmiot set rok_studiow = 3 where kierunek = 2;
update kierunek_has_przedmiot set rok_studiow = 1 where kierunek = 1;
```
## 10
```sql

```
