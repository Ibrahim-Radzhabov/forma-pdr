# AGENTS.md — Инструкция для AI-агентов

## Проект
**FORMA PDR** — лендинг премиальной PDR-студии (беспокрасочное удаление вмятин) в Москве. Один HTML-файл, zero dependencies.

## Критические правила

1. **НЕ трогать scroll-driven анимацию кадров** — frame sequence логика timing-sensitive, изменения ломают синхронизацию скролла и кадров.
2. **НЕ добавлять внешние зависимости** — ни npm, ни CDN, ни Google Fonts. Проект полностью self-contained.
3. **НЕ менять порядок секций** — навигация и smooth-scroll завязаны на id-якоря (`#process`, `#services`, `#gallery`, `#reviews`, `#contacts`, `#before-after`).
4. **НЕ удалять CSS-переменные** — дизайн-система построена на `--gold`, `--dark*`, `--text`, `--muted`, `--space-*`. Все стили ссылаются на них.
5. **Плейсхолдеры помечены `XXXXXXXXXX`** — телефон, URL, ID мессенджеров, Метрики. Не путать с реальными данными.

## Стек и ограничения
- **Стек**: HTML5, CSS3, Vanilla JS. Всё inline в одном файле `forma_landing_v3.html` (~1565 строк, ~840 KB).
- **Кадры анимации**: 64 внешних JPEG (`frames/frame_000.jpg` — `frame_063.jpg`). Загружаются батчами по 8. Прелоадер уходит после первых 8.
- **Hero-фон**: `hero-forma.jpg` (275 KB JPEG), preload в `<head>`, CSS `background-image`.
- **Шрифты**: Georgia (заголовки) + Arial (UI) — системные, без загрузки.

## Архитектура файла

```
forma_landing_v3.html
├── <head>
│   ├── Meta: charset, viewport, title, description
│   ├── SEO: canonical, OG (7 тегов), Twitter Card (4 тега)
│   ├── Schema.org: AutoRepair + WebSite (2 JSON-LD блока)
│   ├── Preload: hero-forma.jpg
│   ├── Preconnect: yandex.ru
│   └── <style> (~750 строк CSS)
│       ├── :root (цвета + spacing scale 8px)
│       ├── Skip-to-content
│       ├── Nav (fixed, compact on scroll)
│       ├── Hero (bg-image + overlays)
│       ├── Stats, Frame sequence, BA-slider
│       ├── Services (card glow ::after), Why (SVG icons)
│       ├── Process (3-col grid), Gallery, Reviews (quote ::before)
│       ├── Contacts (form styles), Footer
│       ├── Fade-in, Preloader, Noise overlay
│       ├── @media prefers-reduced-motion
│       └── @media 480px / 900px / 1440px+
├── <body>
│   ├── Skip-to-content link
│   ├── Preloader (#preloader)
│   ├── <header> → <nav> (burger + mobile overlay + sticky CTA)
│   ├── <main id="main-content">
│   │   ├── Hero (.hero)
│   │   ├── Stats (.stats) — 4 числа
│   │   ├── Frame Sequence (.frame-seq-section) — 64 кадра, 500vh scroll space
│   │   ├── Before/After (.ba-section) — 2 base64 img, clip-path slider
│   │   ├── Services (.services-section) — 5 карточек + CTA карточка
│   │   ├── Why FORMA (.why-section) — 4 пункта с SVG-иконками
│   │   ├── Process (.process-section) — 5 шагов, 3-col grid
│   │   ├── Gallery (.gallery-section) — 6 placeholder-дивов
│   │   ├── Reviews (.reviews-section) — 3 карточки
│   │   └── Contacts (.contacts-section) — форма + карта iframe
│   ├── </main>
│   └── <footer>
└── <script> (~350 строк JS)
    ├── Frame array (generated, 64 items)
    ├── Preloader + progressive loading
    ├── Scroll-driven frame sequence (RAF)
    ├── BA slider (mouse + touch + keyboard + ARIA)
    ├── Яндекс.Метрика (conditional, YM_ID=0)
    ├── IntersectionObserver fade-in
    ├── Nav compact on scroll
    ├── Burger menu
    ├── Sticky CTA
    ├── Card glow (desktop mousemove)
    └── Contact form validation
```

## Дизайн-система

### Цвета
| Переменная | Значение | Назначение |
|-----------|----------|------------|
| `--gold` | `#c9a96e` | Акцент, CTA, иконки, бордеры |
| `--gold2` | `#e8c98a` | Hover-состояние gold |
| `--dark` | `#0a0a0a` | Основной фон |
| `--dark2` | `#111111` | Фон чётных секций |
| `--dark3` | `#1a1a1a` | Фон карточек |
| `--text` | `#e8e4df` | Основной текст |
| `--muted` | `#888` | Вторичный текст |

### Spacing (8px base)
`--space-xs: 8px`, `--space-sm: 16px`, `--space-md: 24px`, `--space-lg: 32px`, `--space-xl: 48px`, `--space-2xl: 64px`, `--space-3xl: 96px`, `--space-4xl: 128px`

### Типографика
- Заголовки: `Georgia, serif`, `font-weight: 400`
- UI/body: `Arial, sans-serif`
- Акцент в заголовках: `<em>` → `color: var(--gold); font-style: normal`
- Section tag: 12px, uppercase, letter-spacing 4px, gold

## Ключевые паттерны

### Добавление новой секции
1. Создать `<section class="new-section" id="new-id" aria-label="...">` внутри `<main>`
2. Обернуть контент в `<div class="container">`
3. Добавить `.section-tag` + `.section-title` для единообразия
4. Добавить `fade-in` класс на элементы для анимации появления
5. Чередовать фон: `--dark` / `--dark2`
6. Добавить якорь в nav если нужно

### Стилизация кнопок
- Primary: `.btn-primary` (gold bg, чёрный текст)
- Ghost: `.btn-ghost` (прозрачный, белый border)
- Оба имеют `:hover`, `:active` (scale 0.97), `:focus-visible` (gold outline)

### Card glow эффект
Используется на `.service-card` и `.review-card`. Требует:
- `position: relative; overflow: hidden; --mouse-x: 50%; --mouse-y: 50%;` на карточке
- `::after` с `radial-gradient` по `var(--mouse-x/y)`
- JS listener `mousemove` обновляет CSS-переменные
- Отключен на touch-устройствах (`'ontouchstart' in window`)

## Файлы проекта

| Файл | Статус | Описание |
|------|--------|----------|
| `forma_landing_v3.html` | Основной | Лендинг — HTML + CSS + JS |
| `hero-forma.jpg` | Используется | Фон hero (275 KB) |
| `hero-forma.png` | Исходник | Оригинал hero (1.5 MB), не подключён |
| `frames/frame_*.jpg` | Используется | 64 кадра scroll-анимации |
| `frames_base64.js` | Артефакт | Не используется, можно удалить |
| `test_video*.mp4` | Артефакт | Исходные видео, не используются |
| `*.md` (кроме AGENTS.md) | Документация | Архитектура, промпты, чеклисты |

## Что осталось сделать
- [ ] Заменить `XXXXXXXXXX` на реальные данные (телефон, URL, ID Метрики, мессенджеры)
- [ ] Реальные фото в галерею (заменить `.gallery-placeholder` на `<img>`)
- [ ] Реальные фото в BA-slider (заменить base64 заглушки)
- [ ] Реальные отзывы клиентов
- [ ] Подключить бэкенд формы (Telegram-бот или email API)
- [ ] Убрать ватермарку Veo с кадров анимации (перегенерировать или обработать)
- [ ] Политика конфиденциальности + consent по 152-ФЗ
- [ ] Деплой: домен, SSL, CSP-заголовки, HSTS, robots.txt, sitemap.xml
- [ ] Конвертация hero-forma.jpg в WebP/AVIF
- [ ] Опционально: минификация, разделение CSS/JS в отдельные файлы

## Запуск
```bash
# Вариант 1: открыть напрямую
open forma_landing_v3.html

# Вариант 2: локальный сервер (нужен для корректной загрузки frames/)
python3 -m http.server 8080
# Открыть http://localhost:8080/forma_landing_v3.html
```
