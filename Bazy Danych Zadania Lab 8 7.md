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



```
