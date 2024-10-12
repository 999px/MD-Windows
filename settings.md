# Настройки

- [x] 031 
- [x] 032
- [x] 035
- [x] 036





## 003. Убрать из системного трея, безопасное отключение определенного устройства
```
reg.exe add HKLM\SYSTEM\CurrentControlSet\Services\storahci\Parameters\Device /f /v TreatAsInternalPort /t REG_MULTI_SZ /d XXX
```

Вместо XXX - нужно написать "Bus Number".



## ★ 004b. Активация, деактивация и отображение сведений о лицензии Windows
Устанавливает новый ключ
```
slmgr -ipk XXXXX-XXXXX-XXXXX-XXXXX-XXXXX
slui 4
```

Показывает наличие ключа и состояние лицензии
`slmgr /dli`

Показывает статус активации / дату окончания активации
`slmgr /xpr`

Показывает сведения о лицензии
`slmgr /dlv`

Удаляет ключ
`slmgr /upk`

Затем, удаляет ключ из реестра
`slmgr /cpky`

***
Активация по телефону: +372 686 8820
2 1 1 2 2 2 1
https://philka.ru/forum/topic/47487-aktivatciia-windows-10-7-8-81-vse-redaktcii-liubym-sposobom/
***



## 016. Установка Windows 11 на несовместимый компьютер
Нажимаем `Shift+F10`, вызываем `regedit` и:
```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\Setup\LabConfig]
"BypassTPMCheck"=dword:00000001
"BypassCPUCheck"=dword:00000001
;"BypassSecureBootCheck"=dword:00000001
;"BypassRAMCheck"=dword:00000001
;"BypassStorageCheck"=dword:00000001
```



## 017. Локальная учетная запись Windows 11 при установке
Нажимаем `Shift+F10` и вводим:
```
oobe\bypassnro
```

После нажатия ENTER компьютер перезагрузиться и появиться возможность создать локальную учётную запись.



## 018. Как скачать оригинальный ISO Windows 10, Windows 11 с сайта Майкрософт без программ
Нужно поменять Useragent на "мобильный".
- https://www.microsoft.com/ru-ru/software-download/windows10
- https://www.microsoft.com/ru-ru/software-download/windows11
***
Оригинальные версии Windows (nnmclub.to)
- https://nnmclub.to/forum/viewforum.php?f=504



## ★ 021. Сохранить резервную копию активации Windows и Office можно ручным способом
*ещё не проверял*

MANUAL BACKUP PROCESS:
1. Run Command Prompt as Administrator.
2. Type `net stop sppsvc` , and hit Enter.
3. Create a Copy of `C:\Windows\System32\spp\store` Folder.
4. Keep this File "**store**" somewhere else.
5. Replace the original "**store**" folder with the backup "**store**" folder (When you make a fresh installation). Choose: "REPLACE THE FILES IN THE DESTINATION"
6. Reboot Windows.
7. Done.



## ★ 022. Удаление раздела восстановления (Recovery) Windows с диска
1. Проверка состояния
	```
	reagentc /info
	```
    
2. После отключения среды восстановления, его раздел можно удалить так:
	```
	reagentc /disable
	```
	
3. Отключает среду восстановления Windows
	```
	diskpart
	list volume
	select volume N
	delete partition override
	exit
	```



## 023. Проверка системных файлов Windows
`sfc /scannow`
Эта команда выполнит проверку целостности всех системных файлов Windows и попытается их исправить в том случае, если были обнаружены какие-либо ошибки.
https://remontka.pro/sfc-scannow/


Ещё есть:
`dism /Online /Cleanup-image /Restorehealth` и `dism /Online /Cleanup-Image /ScanHealth`
они вроде проверяю системный файлы онлайн



## 024. восстановление загрузчика windwos
*ещё не всё изучил и проверил*

Выбор EFI раздела и отформатировать:
```
select volume N
format fs=fat32
```

Присвоение буквы Z этому разделу:
```
assign letter=Z
```

Скопировать туда загрузчик:
```
bcdboot C:\Windows /s Z: /f UEFI
```


## 028. Покажет сколько процентов диска уже зашифровано/разшифровано
*нужно лучше изучить тему*

Проверка статуса:
```
manage-bde -status
```

Расшифровывает том (Диск C:) и отключает защиту BitLocker:
```
manage-bde -off C:
```



## 029. Выбор VHD при установке Windows (diskpart)
`Shift+F10`

```
diskpart
list volume
select vdisk file="F:\win10.vhd"
attach vdisk
```



## 030. Создание разделов через DISKPART
```
; для запуска Diskpart
diskpart

; посмотреть номера дисков и узнать номер нужного
list disk

; вместо X номер нужного диска
select disk X

; зачистить всю существующею таблицу разделов
clean

; По умолчанию новая таблица создается в формате MBR, но для десяточки на UEFI нужно в GPT.
convert gpt

; Создание специального EFI раздела размером в 100 МБ. Размеры всегда в МБ указывается
create partition efi size=100

; Быстрое форматирование его в файловую систему Fat32 и назначение метки "EFI"
format quick fs=fat32 label="EFI"

; Создание раздела под систему. Укажи сам нужный тебе размер в МБ вместо 122880
create partition primary size=122880

; Быстрое форматирование его в файловую систему NTFS и назначение метки
format quick fs=ntfs label="PCNAME__SYSTEM"

; Теперь создаешь второй раздел без указания размера и он просто создастся на всё не размеченное пространство
create partition primary

; Быстрое форматирование его в файловую систему NTFS и назначение метки
format quick fs=ntfs label="PCNAME__DATA"

; Посмотреть что получилось в итоге
list partition

; Выход из Diskpart
exit
```



## 033. Не подключить автоматический внутренние диски (нужен для Windows 2 Go)
DISKPART

Вывод текущей политики
`san`

Не подключить автоматический внутренние диски
`san policy=OfflineInternal`

По умолчанию для обычного Windows
`san policy=OnlineAll`




## 034. Внесение изменении в offline реестр (реестр другой НЕ загруженной системы)
- В `regedit` выбираем `HKEY_LOCAL_MACHINE`
- В меню выбираем `Файл` → `Загрузить куст...`
- Открываем `*буква_диска*:\Windows\System32\config` и выбираем `SOFTWARE`
	- Могут быть загружены следующие кусты реестра
	  ```
	  HKEY_LOCAL_MACHINE\SAM      | \Windows\System32\config\SAM
	  HKEY_LOCAL_MACHINE\SECURITY | \Windows\System32\config\SECURITY
	  HKEY_LOCAL_MACHINE\SOFTWARE | \Windows\System32\config\SOFTWARE
	  HKEY_LOCAL_MACHINE\SYSTEM   | \Windows\System32\config\SYSTEM
	  HKEY_USERS\.DEFAULT         | \Windows\System32\config\DEFAULT
	  ```
- Называем загруженную ветвь `--offline--SOFTWARE`
- **— вносим нужные изменение —**
- В `regedit` выбираем загруженную ветвь `--offline--SOFTWARE`
- В меню выбираем `Файл` → `Выгрузить куст...`







