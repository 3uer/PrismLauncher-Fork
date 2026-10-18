# ForkerLauncher — Дорожная карта

Форк [Prism Launcher](https://github.com/PrismLauncher/PrismLauncher) с улучшенным UI,
плавными анимациями и полной поддержкой Linux (Arch) и Windows.

## Этап 1 — Ребрендинг (ветка `feature/rebrand`)

- [ ] `CMakeLists.txt` — имя проекта, имя exe-файла
- [ ] `program_info/` — название приложения, организация, копирайты
- [ ] `program_info/org.prismlauncher.PrismLauncher.desktop.in` → свой .desktop файл (Linux)
- [ ] Иконки: `program_info/*.svg`, `prismlauncher.ico`, `prismlauncher.icns`
- [ ] Строки в коде: `launcher/Application.cpp` и другие места с "Prism Launcher"
- [ ] README.md — новое описание проекта
- [ ] Свои API-ключи (Microsoft OAuth, CurseForge) — ключи Prism использовать нельзя!

## Этап 2 — Кастомная тема оформления

Темы лежат в `launcher/ui/themes/` — это Qt Style Sheets (QSS, почти как CSS) + JSON-манифест.

- [ ] Изучить структуру существующих тем (например `launcher/ui/themes/flat/`)
- [ ] Цветовая палитра ForkerLauncher, акцентный цвет
- [ ] Тёмная + светлая тема
- [ ] Свои иконки для темы
- [ ] Сделать тему по умолчанию

## Этап 3 — Плавные анимации

Инструменты Qt: `QPropertyAnimation`, `QGraphicsOpacityEffect`, `QEasingCurve::OutCubic`.
Код UI: `launcher/ui/`, кастомные виджеты: `launcher/ui/widgets/`.

- [ ] Плавное появление окон и диалогов (fade-in)
- [ ] Анимация наведения на карточки инстансов
- [ ] Плавное переключение страниц настроек
- [ ] Анимация прогресс-баров

## Этап 4 — Сборка Linux + Windows

### Linux (Arch)
```bash
sudo pacman -S base-devel cmake qt6-base qt6-5compat qt6-svg qt6-imageformats qt6-tools \
    zlib quazip-qt6 c-ares tomlplusplus extra-cmake-modules scdoc ghc-filesystem
git clone --recursive https://github.com/3uer/PrismLauncher-Fork.git
cd PrismLauncher-Fork
cmake -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build -j$(nproc)
```

### Windows
- [ ] GitHub Actions (воркфлоу уже есть в `.github/workflows/`) для автосборки .exe/.msi

## Этап 5 — Новые функции

- [ ] Список идей уточняется (предлагай!)

## Важно помнить

- Лицензия GPLv3 — код должен оставаться открытым
- Нельзя использовать бренд "Prism Launcher" и их API-ключи в публичных сборках
- Основная разработка — в ветке `develop`, как и в апстриме
