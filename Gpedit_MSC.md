# gpedit.msc

## G001. Windows 10 Enterprise: Отключить данные диагностики и использования
`Конфигурация компьютера`
→ `Административные шаблоны`
→ `Компоненты Windows`
→ `Сборки для сбора данных и предварительные сборки`

Windows 10
- Разрешить телеметрию **[Включена]**
  - 0-Безопасность (только для предприятий)

Windows 11
- Разрешить сбор диагностических данных **[Включена]**
  - Сбор диогностических данных отключен (не рекомендуется)


## G003. Отключить Autorun и Autoplay
`Конфигурация компьютера` 
→ `Административные шаблоны` 
→ `Компоненты Windows` 
→ `Политики автозапуска` 

- Выключение автозапуска **[Включена]**
  - Все устройства



## G004. Отключить обновления Windows 10
`Конфигурация компьютера`
→ `Административные шаблоны`
→ `Компоненты Windows`
→ `Центр обновления Windows`

- Настройка автоматического обновления **[Отключено]**

Закройте редактор, после чего зайдите в параметры системы и выполните проверку наличия обновлений (это нужно, чтобы изменения вступили в силу, сообщают, что иногда срабатывает не сразу).
При этом, при ручной проверке - обновления найдутся, но в будущем автоматически поиск и установка выполняться не будут.



## G005. Разрешение использования BitLocker без совместимого TPM
`Конфигурация компьютера`
→ `Административные шаблоны`
→ `Компоненты Windows`
→ `Шифрование диска BitLocker`
→ `Диски операционной системы`

- Этот параметр политики позволяет настроить требование дополнительной проверки подлинности при запуске **[Включена]**



## G006. Отключить автоматическую перезагрузку Windows 10
`Конфигурация компьютера`
→ `Административные шаблоны`
→ `Компоненты Windows`
→  `Центр обновления Windows`

- Не выполнять автоматическую перезагрузку при автоматической установке обновлений, если в системе работают пользователи **[Включено]**



## G007. Отключение установку\обновление драйвера для определённого устройства
Скопировать "ИД оборудования" из Диспетчере устройств.
(Пример: PCI\VEN_10DE&DEV_1D10&SUBSYS_09181028)

Потом:
`Конфигурация компьютера`
→ `Административные шаблоны`
→ `Система`
→ `Установка устройства`
→ `Ограничения на установку устройства`

- Запретить установку устройств с указанными кодами устройств **[Включено]**

нажать на кнопку `Показать...` и добавите туда "ИД оборудования"



## G008. Отключить автоматическое получение драйверов из Центра обновлений (Windows 11)
`Конфигурация компьютера`
→ `Административные шаблоны`
→ `Компоненты Windows`
→ `Центр обновления Windows`
→ `Управление обновлениями, предложенными Центром обновления Windows` 

- Не включать драйверы в обновления Windows **[Включено]**

***
источник: https://remontka.pro/disable-drivers-automatic-update-windows/



## G009. Отключить встроенное средство Windows для запись оптических дисков
`Конфигурация пользователя`
→ `Административные шаблоны`
→ `Компоненты Windows`
→ `Проводник` 

- Удалить возможности записи компакт-дисков **[Включено]**






