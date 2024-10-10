# Настройки

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




