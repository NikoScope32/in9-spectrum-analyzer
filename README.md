# IN-9 Spectrum Analyzer

8-канальный аудио спектроанализатор на газоразрядных индикаторах ИН-9.

## Возможности

- 7-полосный анализатор спектра (MSGEQ7)
- 8 ламп ИН-9
- Датчик CO2/температуры/влажности (SCD41)
- Часы реального времени (DS3231)
- WiFi + веб-интерфейс
- NTP синхронизация

## Прошивка через браузер

**[👉 Открыть Web Flash](https://NikoScope32.github.io/in9-spectrum-analyzer/web/)**

Требуется браузер Chrome, Edge или Opera.

## Железо

- ESP32-S3-DevKitC-1 (WROOM-1-N16R8)
- ИН-9 × 8
- MSGEQ7 модуль
- MCP4728 × 2
- MGE340 × 8
- SCD41
- DS3231
- HV PSU 12V→150V (MC34063 + IRF840)

## Сборка прошивки

```bash
cd firmware
pio run
```

После сборки скопировать бинарники в `web/`:
- `.pio/build/esp32-s3-devkitc-1/bootloader.bin`
- `.pio/build/esp32-s3-devkitc-1/partitions.bin`
- `.pio/build/esp32-s3-devkitc-1/firmware.bin`
- `boot_app0.bin` (из PlatformIO packages)

## Лицензия

MIT