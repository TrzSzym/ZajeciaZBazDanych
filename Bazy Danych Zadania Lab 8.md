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

## Zadanie 4

```sql

create table system_alarmowy (
id_alarmu int auto_increment primary key,
wiadomosc Varchar(255)
);

```
```sql

create trigger alarm_tesciowa
after insert on wyprawa
for each row
begin
	declare uczestnicy varchar(255);
    declare dziadek varchar(255);
    
    set uczestnicy = (select k.nazwa from wyprawa w inner join uczestnicy u on w.id_wyprawy = u.id_wyprawy
    inner join kreatura k on u.id_uczestnika = k.idKreaury where w.id_wyprawy = new.id_wyprawy);
    set dziadek = (select s.nazwa from wyprawa w inner join etapy_wyprawy e on w.id_wyprawy=e.id_wyprawy
    inner join sektor s on e.id_sektora = s.id_sektora where w.id_wyprawy = new.id_wyprawy);
		if uczestnicy like "%tesciowa%" then
			if dziadek like "%dziadka%" then
				insert into system_alarmowy(wiadomosc) values ("TESCIOWA NADCHODZI !!!!!");
            end if;
		end if;
end; //

```
