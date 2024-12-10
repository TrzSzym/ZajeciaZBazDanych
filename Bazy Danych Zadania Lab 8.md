# Lab 7

## Zadanie 1

```sql

delimiter //
Create trigger tr_kreatura_before_insert
BEFORE INSERT ON kreatura
for each row
begin
	if new.waga < 0 then
		set new.waga = 0;
	end if;
end //
delimiter //
create trigger tr_kreatura_before_udpate
before update on kreatura
for each row
begin
	if new.waga < 0 then
		set new.waga = 0;
    end if;
end;//

delimiter ;

```

## Zadanie 2

```sql

create table archiwum_wypraw (id_wyprawy INT, nazwa VARCHAR(30), data_rozpoczecia DATE , data_zakonczenia date , kierwonik varchar(30));

DELIMITER //
create trigger tr_delete_wyprawa
after delete on wyprawa
for each row
begin
	insert into archiwum_wypraw values (old.id_wyprawy,
    old.nazwa,
    old.data_rozpoczecia,
    old.data_zakonczenia,
    (select k.nazwa from kreatury kinner join wyprawa w on  k.idKreatury=w.kierownik where k.idKreatury=old.w.kierownik));
end //

```

## Zadanie 3

```sql

DELIMITER $$
create procedure eliksir_sily(in ID INT)
begin
	update kreatura set udzwig=(udzwig*1.2) where id_kreatury = ID;
end $$

delimiter ;

```
```sql

delimiter //
create function DUZE(tekst varchar(100))
returns VARCHAR(100)
BEGIN
RETURN upper(tekst);
end //

delimiter ;

```
