# Настройки -- Суперкороткие

## 001. Гибернация
Отключение:
`powercfg -h off`

Если не работает гибернация можно попробовать так:
`powercfg /h /type full`



## 002. Собственный ярлык в Мой Компьютер
`%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Network Shortcuts`



## 007. Send To
`%USERPROFILE%\AppData\Roaming\Microsoft\Windows\SendTo`
или
`shell:sendto`



### 008. Информацию об общих ресурсах, активных сеансах и открытых файлах
`fsmgmt.msc`



### 011. Расположение StartMenu
Глобальная папка Пуск:
`C:\ProgramData\Microsoft\Windows\Start Menu`

Персональная папка Пуск:
`%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu`



### 013. Удаление службы
`sc delete "Имя службы"`



### 020. Каталог Центра обновления Майкрософт / Поиск и скачивание автономного установщика обновления Windows
- https://www.catalog.update.microsoft.com/
- https://www.catalog.update.microsoft.com/Search.aspx?q=KB5003637


### 026. Windows переменная среда
C:\Users\**USER_NAME**
`%USERPROFILE%`

C:\Users\**USER_NAME**\AppData\Roaming
`%APPDATA%`

Имя пользователя:
`C:\Users\%USERNAME%`