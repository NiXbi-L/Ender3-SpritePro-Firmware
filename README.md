# Professional Firmware — форк под Ender 3 + Sprite Pro (без зонда)

Публичный форк [mriscoc/Ender3V2S1](https://github.com/mriscoc/Ender3V2S1) (Professional Firmware, ProUI, DWIN) с конфигурацией под **Creality Ender 3** с экструдером **Sprite Pro** и **только механическими концевиками** (без BLTouch/CR-Touch).

---

## Конфигурация принтера

| Параметр | Значение |
|----------|----------|
| **Принтер** | Creality Ender 3 (базовая платформа) |
| **Плата** | Creality 4.2.2 (STM32F103RET6) |
| **Экструдер** | Sprite Pro (прямой привод, до 300 °C) |
| **Драйвер E** | TMC2208 Standalone |
| **Конечники** | Только механические X, Y, Z (без датчика уровня) |
| **Калибровка стола** | MESH_BED_LEVELING (ручная сетка, без зонда) |
| **Язык интерфейса** | Русский |
| **Дисплей** | DWIN (ProUI) |

### Геометрия и лимиты

- **Стол:** 245×250 мм (X_BED_SIZE × Y_BED_SIZE)
- **Рабочая зона:** X 5…248, Y 5…248, Z 0…250 мм (запас от механики, без упора в концы)
- **Парковка сопла:** `(X_MAX_POS - 10, Y_MAX_POS - 10, 20)` — вперёд в пределах лимитов
- **E-steps:** 424.9 (Sprite Pro)
- **Макс. температура горячего конца:** 300 °C

### Что отключено в этой сборке

- BLTouch / CR-Touch и любой зонд
- Z_SAFE_HOMING и USE_PROBE_FOR_Z_HOMING — калибровка Z только по механическому концевику Z
- UBL (UBL заменён на MESH_BED_LEVELING)
- Калибровка стола зондом (BED_TRAMMING_USE_PROBE отключён)

---

## Установка прошивки

1. Скачайте последний [Release](https://github.com/NiXbi-L/Ender3-SpritePro-Firmware/releases) и файл `firmware.bin`.
2. Положите `.bin` на отформатированную SD-карту (FAT32), вставьте в принтер и включите питание.
3. После прошивки переименуйте или удалите файл с карты (чтобы при следующем включении прошивка не ставилась заново).

**Важно:** Подходит только для платы **4.2.2** с чипом **STM32F103RET6**. Для других плат/чипов нужна своя сборка.

---

## Сборка из исходников (PlatformIO)

```bash
# Клонировать репозиторий
git clone --recursive https://github.com/NiXbi-L/Ender3-SpritePro-Firmware.git
cd Ender3-SpritePro-Firmware

# Сборка прошивки под 4.2.2 (STM32F103RE)
pio run -e STM32F103RE_creality
```

Готовый бинарник: `.pio/build/STM32F103RE_creality/firmware-*.bin`.

---

## Базовый проект и лицензия

- Основа: [mriscoc/Ender3V2S1](https://github.com/mriscoc/Ender3V2S1) (Professional Firmware).
- Marlin — [marlinfw.org](https://marlinfw.org/), лицензия GPL.

Прошивка и файлы предоставляются «как есть», без гарантий. Установка и использование на свой риск.
