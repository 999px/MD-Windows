# Настройки ####################################################################

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
   ```batch
   DISKPART
   
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

Присвоение буквы "S" этому разделу:
```
assign letter=S
```

Скопировать туда загрузчик:
```
bcdboot C:\Windows /s S: /f UEFI
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






********************************************************************************
<br /><br />

# Отключение служб (services.msc) ##############################################
**Отображаемое имя // Имя службы**

- Сервер // LanmanServer [по умолчанию: Автоматически] -- Отключена
   - Другие компьютеры не смогут подключаться к твоим общим папкам и принтерам.

- Logitech LampArray Service // logi_lamparray_service [по умолчанию: Автоматически] -- Отключена



********************************************************************************
<br /><br />

# Настройки -- Суперкороткие ###################################################

### Гибернация
- Отключение: `powercfg -h off`
- Если не работает гибернация можно попробовать так: `powercfg /h /type full`


### Собственный ярлык в Мой Компьютер
`%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Network Shortcuts`


### Send To
`%USERPROFILE%\AppData\Roaming\Microsoft\Windows\SendTo`
или
`shell:sendto`


### Информацию об общих ресурсах, активных сеансах и открытых файлах
`fsmgmt.msc`


### Расположение меню "Пуск" (Start Menu)
- Глобальная папка Пуск: `C:\ProgramData\Microsoft\Windows\Start Menu`
- Персональная папка Пуск: `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu`


###  Удаление службы
`sc delete "Имя службы"`


### Каталог Центра обновления Майкрософт / Поиск и скачивание автономного установщика обновления Windows
- https://www.catalog.update.microsoft.com/
- https://www.catalog.update.microsoft.com/Search.aspx?q=KB5003637


### Windows переменная среда
```
C:\Users\**USER_NAME**                  | `%USERPROFILE%`
C:\Users\**USER_NAME**\AppData\Roaming  | `%APPDATA%`
Имя_Пользователя                        | `C:\Users\%USERNAME%`
```


### Добавление разделителя в классическое "контекст меню"
Пример:
```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Classes\*\shell\Получить Hash]
"SeparatorBefore"=""
"SeparatorAfter"=""
```









********************************************************************************
<br /><br />

# Настройки -- DISKPART ########################################################
- Но, Я создаю разделы через GParted (из Live Linux).
- Вызод консоли на этапе установки Windows - `Shift + F10`
- Чтобы в Windows показывал вместо 399 GB - 400 GB, я указываю размер раздела на 1 MB больше.


## Создание разделов через Diskpart
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
create partition primary size=102401
format quick fs=ntfs label="Rabbit-Win"
assign letter="W"

rem Создаём третий раздел (DiskD) для данных, занимающий всё оставшееся пространство
create partition primary
format quick fs=ntfs label="Rabbit-Data"

rem Смотри что получилось в итоге
list partition
list volume

exit
```



## Выбор VHD при установке Windows (diskpart)
```batch
DISKPART

list volume

select vdisk file="F:\_VHD\win10-test.vhdx"
attach vdisk
```




