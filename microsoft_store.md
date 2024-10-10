# Microsoft Store / UWP — Настройки

### Восстановление Microsoft Store в Windows LTSC
```
wsreset -i
```
<s>
Старый вариант  
Раньше использовал `LTSC-Add-MicrosoftStore-2019.zip`  
(MD5: B5FA5A65D85DB1C6533B5ABC4231CADE)  
Скачал его отсюда: https://github.com/kkkgo/LTSC-Add-MicrosoftStore
</s>
    

### Список всех установленных приложений UWP (Universal Windows Platform)

```powershell
Get-AppxPackage

# Более удобном виде
Get-AppxPackage | select Name, NonRemovable, PackageFullName
```

### Удаления приложения

```powershell
Remove-AppxPackage <PackageFullName>
```

### Скачать .APPX файл из Microsoft Store

- https://store.rg-adguard.net/

<aside>
💡 В Windows есть два типа UWP приложений:

- пользовательские тут: `C:\Program Files\WindowsApps\`
- системные приложения тут: `C:\Windows\SystemApps\`
</aside>