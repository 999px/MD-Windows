# Как создать радел через Diskpart

НО, Я создаю раздел через GParted (из Live Linux)

`SHIFT` + `F10`

```Batch 
DISKPART

list disk

rem Выбираем целевой диск
select disk X

clean
convert gpt

rem Создаем EFI раздел размером в 100 MB
create partition efi size=100
format quick fs=fat32 label="EFI"
assign letter="S"

rem Создаем Диск Це.
create partition primary size=102400
format quick fs=ntfs label="Windows"
assign letter="W"

rem Создаем третий раздел занимающий все оставшееся пространство диска (Диск Дэ)
create partition primary
format quick fs=ntfs label="MyData"
```