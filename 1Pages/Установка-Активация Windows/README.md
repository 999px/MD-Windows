# Установка-Активация Windows

## Общее
- **TPM** - Отключить
- **Secure Boot** - Включить
- Размер раздела указываю на 1MB больше, чтобы было 100GB вместо 99.9GB



<br /><br />
## Обычная установка
1. Создаём разделы через **Gparted** - [IMG](i/004.jpg)

2. В **новом устновщике** Windows 11 24H2 выбрать --> `Предыдущая версия настройки`  
   *(новый установщик автоматический создаёт **MSR-раздел** (msftres))*

3. В установщике Windows 11, чтобы обойти ограничение TPM запускаем файл:  
   [+Win11-InstallNoTPM-v1.reg](+Win11-InstallNoTPM-v1.reg)

4. Во время OOBE (первоначальной настройки) - конвертируем "LTSC" в "IoT LTSC".  
   [+IoT_LTSC.md](+IoT_LTSC.md)

5. Во время OOBE - отключаем автоматическое шифрование дисков:  
   [+OOBE-Disable_Device_AutoEncryption-v1.reg](+OOBE-Disable_Device_AutoEncryption-v1.reg)





<br /><br />
## Если нужно установить на **VHD**
```
DISKPART

list vol

select vdisk file="F:\_VHD\Win11ltsc.vhdx"
attach vdisk
```





<br /><br />
## Или через DISM

1. Запускаем установщик Windows и сразу нажимает `Shift + F10`.  
   Назначаем буквы для дисков: **"EFI" --> S** , **"Disk C" --> W**.
   ```
   DISKPART
   
   list disk
   sel disk X
   
   list part
   sel part X
   
   assign letter=S
   assign letter=W
   
   list vol
   
   exit
   ```

2. **install.wim** - на установочном диске ( `F:\sources\install.wim` ).
   
3. Получаем информацию о всех доступных **индексах** в образе `install.wim`:
   ```
   dism /get-imageinfo /imagefile:"F:\sources\install.wim"
   ```

4. Указываем нужный **индекс** (index) и **букву диска** (applydir) где будет установлен Windows:
   ```
   dism /apply-image /imagefile:"F:\sources\install.wim" /index:4 /applydir:W:\
   ```

5. Создаём EFI на EFI разделе:
   ```
   bcdboot W:\Windows /s S: /f UEFI
   ```








<br /><br />
## Активация - HWID Activation (только один раз)
Если цифровая лицензию уже есть (или другая нужная лицензия) - пропускаем.  
Если нет, будем использовать **MAS** - https://massgrave.dev/

> MAS Latest Release  
> Last Release - v2.7 (6-Sep-2024)
> - https://github.com/massgravel/Microsoft-Activation-Scripts
> - https://dev.azure.com/massgrave/_git/Microsoft-Activation-Scripts
> - https://git.activated.win/massgrave/Microsoft-Activation-Scripts

- "LTSC" версия должна быть сконвертирована в "IoT LTSC".
- Чтобы скачать, открываем репозитории на GitHub и нажимает на `Code` → `Download ZIP`.
- Открываем `Microsoft-Activation-Scripts-master.zip` и запускаем оттуда: `MAS\All-In-One-Version-KL\MAS_AIO.cmd`  
  ![img](i/002.png)
- Выбираем - `[1]` HWID.

После получения цифровой лицензии можно отформатировать и переустановить систему. Лицензия сохраниться.  
**NB!** После переустановки "LTSC", его нужно вначале снова сконвертировать в "IoT LTSC".





*****************************************************
<br /><br />


## В качестве информации

- Windows 11 LTSC по умолчанию создаёт такие разделы:  
  ![img](i/001.png)













