# Сконвертировать LTSC в IoT LTSC + HWID-лицензия

- https://windows64.net/453-windows-10-iot-ltsc-hwid.html

***


## Windows 10 LTSC 21H2 -> IoT LTSC 21H2
1. Устанавливаете **Windows 10 LTSC 21H2**.
2. Когда система установлена, то от имени Администратора вводите:
   ```batch
   slmgr.vbs -ipk QPM6N-7J2WJ-P88HH-P3YRH-YY74H
   ```
3. Она переключит редакцию на **IoT LTSC 21H2**.
4. Затем нужно активизировать систему **HWID активатором**.

Если вы будете переустанавливать систему, то точно так же установить **LTSC 21H2**, введите
```powershell
slmgr.vbs -ipk QPM6N-7J2WJ-P88HH-P3YRH-YY74H
```

но активатор уже использовать не нужно будет. Система активируется сама, после ввода этого ключа.



## Windows 11 IoT LTSC 24H2
Для Win 11 LTSC
https://massgrave.dev/hwid

```
- IoT Enterprise LTSC 2024	IoTEnterpriseS
`slmgr.vbs -ipk CGK42-GYN6Y-VD22B-BX98W-J8JXD`
```

https://github.com/massgravel/Microsoft-Activation-Scripts

