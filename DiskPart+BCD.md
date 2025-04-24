## 001. Добавить в загрузчик Windows новую запись для загрузки VHDX файла

1. Подключить VHDX диск с Windows (жедательно в режиме readonly)

2. Добавь запись в загрузчик
```
bcdedit /copy {current} /d "Windows 11 VHDX"

bcdedit /set {новый-ID} device vhd=[locate]\путь\к\файлу.vhdx
bcdedit /set {новый-ID} osdevice vhd=[locate]\путь\к\файлу.vhdx
```

([locate] — автоматически найдет VHDX при загрузке)

3. Просмотре резултата
```
bcdedit /v
```

### Удалить запись
```
bcdedit /delete {ID}
```






