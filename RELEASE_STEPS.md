# Как выложить проект на GitHub и сделать релиз

## 1. Создать репозиторий на GitHub

1. Зайдите на [github.com](https://github.com) → **New repository**.
2. Имя, например: `Ender3V2S1-20260106` или `Ender3-SpritePro-Firmware`.
3. Выберите **Public**, **не** добавляйте README / .gitignore (репозиторий пустой).
4. Нажмите **Create repository**.

## 2. Подключить remote и отправить код

В папке проекта выполните (подставьте свой логин и имя репозитория):

```bash
git remote add origin https://github.com/ВАШ_ЛОГИН/ИМЯ_РЕПОЗИТОРИЯ.git
git branch -M main
git push -u origin main
```

## 3. Обновить ссылки в README

В файле `README.md` замените `YOUR_GITHUB_USERNAME` на ваш логин GitHub в двух местах (ссылки на Releases и на клонирование). Затем:

```bash
git add README.md
git commit -m "Fix GitHub username in README"
git push
```

## 4. Создать релиз с бинарником прошивки

1. На странице репозитория: **Releases** → **Create a new release**.
2. **Choose a tag:** введите, например, `v1.0.0` → **Create new tag**.
3. **Release title:** например, `v1.0.0 — Ender 3 + Sprite Pro, без зонда`.
4. В **Description** можно вставить:
   - Конфиг: Ender 3, плата 4.2.2, Sprite Pro, только механические концевики, MESH_BED_LEVELING, русский язык.
   - Файл прошивки только для **STM32F103RET6** (Creality 4.2.2).
5. В блок **Attach binaries** перетащите файл прошивки:
   - из папки `release\`: `firmware-20260220-160049.bin`
   - или из `.pio\build\STM32F103RE_creality\` после сборки `pio run -e STM32F103RE_creality`.
6. Нажмите **Publish release**.

Готово: репозиторий публичный, в Releases лежит бинарник прошивки для вашей конфигурации.
