- https://github.com/PaaaulZ/PhotoViewerOutOfMemoryNoMore
- https://github.com/lucidusdev/PhotoViewer-Out-Of-Memory-Dll-Patch

---

1. **Открой файл в HxD**: Запусти HxD, открой `ImagingEngine.dll`.
2. **Найди байтовый паттерн**:
    - В меню выбери **"Поиск" → "Поиск..."** (или нажми `Ctrl+F`).
    - В появившемся окне установи следующие параметры:
        - **Тип поиска**: "Hex-значение".
        - **Значение для поиска**: введи последовательность `85 C0 75` — `0D 03 15 86` .
        - "—" означает, что мы допускаем любой байт на этом месте.
    - Нажми **"ОК"** для поиска.
3. **Проверь результаты**: HxD должен найти первый совпадающий блок байтов.
4. **Измени байт**:
    - Когда ты найдёшь этот блок, замени байт `75` (который находится на третьей позиции от `85 C0`) на `EB`.
5. **Сохрани изменения**: После замены байта сохрани файл.