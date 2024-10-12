# DISKPART


## Создание разделов через Diskpart
Но, Я создаю разделы через GParted (из Live Linux).

```batch
DISKPART

list disk

rem Выбираем целевой диск (вместо X номер диска)
select disk X

rem Удаляем все данные с диска и переводим его в GPT
clean
convert gpt

rem Создаём EFI раздел размером в 100MB и задаём ему букву "S"
create partition efi size=100
format quick fs=fat32 label="Rabbit-EFI"
assign letter="S"

rem Создаём системный раздел (DiskC) и задаём ему букву "W"
create partition primary size=102400
format quick fs=ntfs label="Rabbit-Win"
assign letter="W"

rem Создаём третий раздел (DiskD) для данных, занимающий всё оставшееся пространство
create partition primary
format quick fs=ntfs label="Rabbit-Data"

exit
```


