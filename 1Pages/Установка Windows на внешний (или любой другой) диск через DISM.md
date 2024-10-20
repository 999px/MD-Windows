# Установка Windows на внешний (или любой другой) диск через DISM

- https://www.isumsoft.com/windows-10/make-external-hard-drive-bootable-windows-10.html
- https://www.bootdev.ru/2018/07/Installing-Windows-on-USB-drive.html
***


### 1 Этап.
Сначала создаём на устройстве где будет установлен Windows Два раздела (я для этого буду использовать GParted) - **EFI** и раздел для самой **Windows**.

НО, для раздела EFI пока не ставим флаги `boot` и `esp` , а то тупой DISKPART не даст установить букву этому раздела, если он на съемном устройстве. по этому оставляем там пока флаг `msftdata` .


### 2 Этап.
- Ставим установочный диск Windows.
- Назовём раздел EFI на съемной носители буквой - **S**.
- А раздел для Windwos на съемном носители буквой - **W**.
- Пусть к файлу `F:\sources\install.wim` , вместо `F` пишем правильную букву.

Получает информацию о всех доступных индексах в образе `install.wim` 

```
dism /get-imageinfo /imagefile:"F:\sources\install.wim"
```

Указываем нужные `index` и букву диска где будет установлен Windows.

```
dism /apply-image /imagefile:"F:\sources\install.wim" /index:4 /applydir:W:\
```

Создаём EFI файл на EFI разделе

```
bcdboot W:\Windows /s S: /f UEFI
```


