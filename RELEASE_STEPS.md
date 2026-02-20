# Как сделать релиз

Релизы настроены через **GitHub Actions**: при пуше тега вида `v*` автоматически собирается прошивка и создаётся релиз с прикреплённым `firmware.bin`.

## Шаги

1. **Убедиться, что все изменения закоммичены и запушены:**
   ```bash
   git status
   git push origin main
   ```

2. **Создать тег и отправить его на GitHub:**
   ```bash
   git tag v1.0.0
   git push origin v1.0.0
   ```

3. **Готово.** На [Actions](https://github.com/NiXbi-L/Ender3-SpritePro-Firmware/actions) запустится workflow **Release Firmware**: он соберёт прошивку и создаст [Release](https://github.com/NiXbi-L/Ender3-SpritePro-Firmware/releases) с тегом `v1.0.0` и файлом `firmware.bin`.

Следующие релизы — теги `v1.0.1`, `v1.1.0` и т.д.:

```bash
git tag v1.0.1
git push origin v1.0.1
```

## Ручной релиз (без тега)

Если нужно выложить бинарник вручную: соберите локально `pio run -e STM32F103RE_creality`, затем на странице репозитория **Releases** → **Create a new release** → укажите тег, описание и прикрепите файл из `.pio/build/STM32F103RE_creality/firmware-*.bin`.
