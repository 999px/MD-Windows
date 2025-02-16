# Microsoft Store / UWP — Настройки

### Восстановление Microsoft Store в Windows LTSC
```
wsreset -i
```

~~Старый вариант: https://github.com/kkkgo/LTSC-Add-MicrosoftStore  
`LTSC-Add-MicrosoftStore-2019.zip` (MD5: B5FA5A65D85DB1C6533B5ABC4231CADE)~~


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

В Windows есть два типа UWP приложений:
- пользовательские тут: `C:\Program Files\WindowsApps\`
- системные приложения тут: `C:\Windows\SystemApps\`






# Microsoft Store — Apps


## Расширения

```markdown
### Расширения для изображений HEIF
### (HEIF Image Extensions)
*Microsoft Corporation*

- https://www.microsoft.com/store/productId/9PMMSR1CGPWG
- ms-windows-store://pdp/?ProductId=9PMMSR1CGPWG

> нужен для открытие HEIF изображений
> для .heic так же нужен **HEVC Video Extensions from Device Manufacturer**
> для .avif - **AV1 Video Extension**

> Win10 - нужен; Win11 - нужен;
```

```markdown
### AV1 Video Extension
*Microsoft Corporation*

- https://www.microsoft.com/store/productId/9MVZQVXJBQ9V
- ms-windows-store://pdp/?ProductId=9MVZQVXJBQ9V

> Без этого не открываются картинки .avif

> Win10 - нужен; Win11 - нужен;
```

```markdown
### Расширения для видео HEVC от производителя устройства
### (HEVC Video Extensions from Device Manufacturer)
*Microsoft Corporation*

- https://www.microsoft.com/store/productId/9N4WGH0Z6VHQ
- ms-windows-store://pdp/?ProductId=9N4WGH0Z6VHQ

> Без этого не открываются картинки .heic
> Устанавливаем .appx и потом уже обновляем из MS Store
> Microsoft.HEVCVideoExtension_1.0.33242.0_x64__8wekyb3d8bbwe.appx

> Win10 - нужен; Win11 - нужен;
```

```markdown
### Расширения для изображений Webp
### (Webp Image Extensions)
*Microsoft Corporation*

- https://www.microsoft.com/store/productId/9PG2DK419DRG
- ms-windows-store://pdp/?ProductId=9PG2DK419DRG

> Без этого не открываются картинки .webp

> Win10 - нужен; Win11 - нужен;
```

## Программы

```markdown
### App Installer
*Microsoft Corporation*

- https://www.microsoft.com/store/productId/9NBLGGH4NNS1
- ms-windows-store://pdp/?ProductId=9NBLGGH4NNS1

> нужен для LTSC
> WinGet в Microsoft Store называется - App Installer
```

```markdown
### Фотографии (Майкрософт)
### (Microsoft Photos)
*Microsoft Corporation*

- https://www.microsoft.com/store/productId/9WZDNCRFJBH4
- ms-windows-store://pdp/?ProductId=9WZDNCRFJBH4
```

```markdown
### Фрагмент и набросок
### (Snip & Sketch)
*Microsoft Corporation*

- https://www.microsoft.com/store/productId/9MZ95KL8MR0L
- ms-windows-store://pdp/?ProductId=9MZ95KL8MR0L
```

```markdown
### Камера Windows
### (Windows Camera)
*Microsoft Corporation*

- https://www.microsoft.com/store/productId/9WZDNCRFJBBG
- ms-windows-store://pdp/?ProductId=9WZDNCRFJBBG
```

```markdown
### Paint 3D
*Microsoft Corporation*

- https://www.microsoft.com/store/productId/9NBLGGH5FV99
- ms-windows-store://pdp/?ProductId=9NBLGGH5FV99
```

```markdown
### Медиаплеер Windows
### (Windows Media Player)
*Microsoft Corporation*

- https://www.microsoft.com/store/productId/9WZDNCRFJ3PT
- ms-windows-store://pdp/?ProductId=9WZDNCRFJ3PT
```

```markdown
### Paint
*Microsoft Corporation*

- https://www.microsoft.com/store/productId/9PCFS5B6T72H
- ms-windows-store://pdp/?ProductId=9PCFS5B6T72H
```