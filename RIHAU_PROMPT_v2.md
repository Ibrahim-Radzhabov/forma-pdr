# RIHAU — Premium Architectural Glazing Website Prompt (v2)

## QUICK BRIEF (read this first)

```
Brand:            Rihau
Location:         Moscow
Segment:          Upper-premium architectural glazing
Main clients:     Private houses, villas, terraces, architects, designers
Core products:    Panoramic glazing, sliding portals, aluminum systems, façade glazing
Visual tone:      Dark, restrained, architectural, tactile, editorial luxury
Conversion:       Consultation + estimate by plan/photo/messenger
Language:         Russian
```

## VISUAL REFERENCES (match this feeling)

Study these sites before writing any code:
- https://www.skywayroofglazing.co.uk — architectural glazing, editorial calm
- https://www.iqglassuk.com — premium product presentation, catalog clarity
- https://www.coutureoutdoor.com — luxury outdoor living, spatial elegance
- https://www.schueco.com — system-level premium, clean engineering
- https://topframing.ru — Russian premium glazing, modern execution

Match the intersection of: **architectural restraint + luxury residential warmth + engineering trust**.

---

## ROLE

You are a world-class digital art director, luxury UX architect, and senior front-end engineer. Build a production-ready premium website.

---

## ANTI-PATTERNS (hard rules)

Never use:
- Aggressive sales banners, red/orange promo labels, "скидка 70%"
- Bright blue corporate gradients
- Cheap stock photos (builder helmets, fake smiles)
- Mass-market window company layouts
- Cluttered comparison tables on first screen
- E-commerce marketplace aesthetics
- Retail language: "от производителя", "самые дешёвые", "акция месяца"
- Inline base64 image delivery
- Single giant HTML file

---

## 1. DESIGN SYSTEM

### Palette
| Token          | Value                                    |
|----------------|------------------------------------------|
| `--bg`         | `#0a0a0a` deep warm black                |
| `--bg-card`    | `#141414` elevated surfaces              |
| `--bg-alt`     | `#1a1a1a` section alternation            |
| `--text`       | `#e8e2d8` warm ivory                     |
| `--text-muted` | `#8a8278` secondary text                 |
| `--accent`     | `#c9a96e` muted champagne/brass          |
| `--accent-hover`| `#d4b97d` lighter gold on hover         |
| `--border`     | `rgba(255,255,255,0.08)` subtle dividers |

### Typography
| Element        | Font                          | Weight | Size range     |
|----------------|-------------------------------|--------|----------------|
| H1 hero        | Cormorant Garamond (serif)    | 500    | 56–72px        |
| H2 sections    | Cormorant Garamond            | 500    | 36–48px        |
| H3 cards       | Cormorant Garamond            | 500    | 22–28px        |
| Body           | Inter or Manrope (sans-serif) | 400    | 15–17px        |
| UI/labels      | Inter, uppercase, tracking 2px| 500    | 11–13px        |
| CTA buttons    | Inter, uppercase, tracking 2px| 600    | 13–14px        |

### Spacing scale
`4, 8, 12, 16, 24, 32, 48, 64, 96, 128px`

### Motion
- `--transition-fast: 0.2s ease`
- `--transition-base: 0.4s cubic-bezier(0.25, 0, 0.2, 1)`
- `--transition-slow: 0.8s cubic-bezier(0.25, 0, 0.2, 1)`
- Fade-in + translate-up (20px) via Intersection Observer
- `prefers-reduced-motion: reduce` — disable all motion

### Breakpoints
`480px / 768px / 1024px / 1280px / 1440px`

---

## 2. INFORMATION ARCHITECTURE

Build in this exact order. Each section solves one job in the funnel:

| #  | Section                    | Funnel job                    |
|----|----------------------------|-------------------------------|
| 1  | Fixed nav                  | Orientation + quick CTA       |
| 2  | Hero                       | Attention + positioning       |
| 3  | Trust metrics bar          | Instant credibility           |
| 4  | Architectural storytelling | Reframe value                 |
| 5  | Solution categories        | Show breadth                  |
| 6  | Key advantages             | Differentiation               |
| 7  | Flagship systems           | Aspiration                    |
| 8  | Catalog grid (20–30)       | Selection                     |
| 9  | Guided selector            | Decision help                 |
| 10 | Process (6 steps)          | Reduce anxiety                |
| 11 | Portfolio (6–9 projects)   | Social proof                  |
| 12 | Proof module (BA/comfort)  | Emotional conviction          |
| 13 | Testimonials               | Peer trust                    |
| 14 | FAQ                        | Objection handling + SEO      |
| 15 | Contact + form + map       | Conversion                    |
| 16 | Footer                     | Legal + secondary nav         |

---

## 3. HERO

- Full-screen, premium architectural photo background
- Multi-layer overlay (linear gradient + radial warm glow)
- Left-aligned editorial composition

Content:
```
label: АРХИТЕКТУРНОЕ ОСТЕКЛЕНИЕ · МОСКВА
H1:    Свет, масштаб и геометрия — как часть архитектуры.
sub:   Панорамные, раздвижные и фасадные светопрозрачные решения
       для частных домов, террас и современных интерьеров.
CTA1:  [Обсудить проект]     — filled accent
CTA2:  [Смотреть проекты]    — ghost border
```

---

## 4. PRODUCT TAXONOMY (20–30 entries)

Organize into these groups. Each entry = one catalog card.

```
ПАНОРАМНЫЕ СИСТЕМЫ (5–6)
  - Панорамные алюминиевые окна
  - Узкопрофильные архитектурные окна
  - Угловое остекление
  - Безрамные панорамные решения
  - Остекление с минимальным профилем

РАЗДВИЖНЫЕ СИСТЕМЫ (4–5)
  - Раздвижные порталы
  - Подъёмно-сдвижные системы (HS)
  - Параллельно-сдвижные системы (PSK)
  - Складные системы (гармошка)

ТЕРРАСЫ И ВЕРАНДЫ (3–4)
  - Террасное остекление
  - Остекление веранд
  - Остекление зимних садов
  - Раздвижное остекление террас

ФАСАДЫ И ВХОДНЫЕ ГРУППЫ (3–4)
  - Фасадное остекление
  - Витражные конструкции
  - Входные группы
  - Стеклянные двери и порталы

СПЕЦИАЛЬНЫЕ РЕШЕНИЯ (4–5)
  - Шумоизоляционные системы
  - Энергоэффективные системы
  - Солнцезащитные решения
  - Дизайнерские оттенки профиля
  - Нестандартные архитектурные решения
```

### Card structure:
```
[Badge: "Панорама" | "Тишина" | "Тепло" | "Минимальный профиль" | ...]
Название системы
Позиционирующая строка (1 предложение)
───
• Спецификация 1
• Спецификация 2
• Спецификация 3
Применение: частные дома, террасы...
───
[Получить расчёт]
```

---

## 5. GUIDED SELECTOR

"Какое решение подойдёт вашему объекту?"

Step-by-step or chip-based selector:
1. Тип объекта: дом / квартира / терраса / пентхаус / коммерческий
2. Приоритет: панорама / тепло / тишина / дизайн / масштаб проёма
3. Нужна ли раздвижная система: да / нет / не знаю
4. Важен ли минимальный профиль: да / нет

Output: 2–4 recommended system groups with links to catalog.

---

## 6. PROCESS (6 steps)

```
01  Консультация         — обсуждение задачи, бюджета, сроков
02  Замер и анализ        — точный замер, анализ проёмов и конструктива
03  Подбор системы        — конфигурация, цвет, фурнитура, стеклопакет
04  Проектирование        — чертежи, согласование, привязка к архитектуре
05  Производство          — изготовление по спецификации
06  Монтаж и сдача        — установка, отделка, проверка, гарантия
```

---

## 7. CONTACT / LEAD FORM

```
Fields:
  - Имя
  - Телефон
  - Тип объекта (select)
  - Что нужно остеклить (textarea)
  - Прикрепить план/фото (file upload placeholder)

CTA: "Обсудить проект"

Reassurance:
  - Свяжемся в ближайшее время
  - Можно отправить план или фото
  - Без навязчивых продаж
```

Messengers: WhatsApp + Telegram (placeholder links)
Phone: placeholder
Address: placeholder
Map: Yandex Maps embed placeholder

---

## 8. CTA STRATEGY

| Location              | CTA type  | Text                    |
|-----------------------|-----------|-------------------------|
| Hero                  | Primary   | Обсудить проект         |
| Hero                  | Secondary | Смотреть проекты        |
| After categories      | Primary   | Получить расчёт         |
| Inside selector       | Primary   | Подобрать решение       |
| After portfolio       | Soft      | Обсудить проект         |
| Final section         | Primary   | Запросить консультацию  |
| Sticky mobile         | Primary   | Позвонить / Написать    |

---

## 9. SEO / STRUCTURED DATA

```html
<title>Rihau — Премиальное архитектурное остекление · Москва</title>
<meta name="description" content="Панорамное, раздвижное и фасадное остекление
для частных домов, террас и современных интерьеров. Алюминиевые системы,
проектирование, монтаж под ключ.">
```

Schema.org: `ProfessionalService` + `FAQPage`
Open Graph: title, description, image, url, locale=ru_RU
Canonical, favicon, twitter:card

---

## 10. TECHNICAL SPEC

### Structure
```
/rihau
  index.html
  /styles
    main.css
  /scripts
    app.js
    catalog.js
  /data
    systems.json        ← 20–30 product entries
  /assets
    /images             ← placeholder gradient images
    /icons
  README.md
```

### Constraints
- `index.html` < 600 lines
- `main.css` < 1000 lines
- `app.js` + `catalog.js` < 800 lines total
- No frameworks, no build tools, semantic HTML + CSS + Vanilla JS
- Real `<img loading="lazy">` for all images
- Mobile burger menu (accessible)
- Sticky mobile CTA bar
- FAQ accordion with aria-expanded
- Intersection Observer for fade-in
- `prefers-reduced-motion` support

### Images
Use CSS gradient placeholders that feel architectural:
```css
.img-placeholder {
  background: linear-gradient(135deg, #1a1a1a 0%, #2a2520 50%, #1a1a1a 100%);
  aspect-ratio: 16/9;
}
```
Add `<!-- TODO: replace with real photo -->` comments.

---

## 11. DELIVERABLES

1. Project concept (2–3 sentences)
2. Complete `index.html` with all 16 sections
3. `main.css` — full design system
4. `app.js` — nav, fade-in, accordion, selector, scroll
5. `catalog.js` — filtering, rendering from JSON
6. `systems.json` — 20–30 entries
7. `README.md` — concept, structure, how to run, how to edit

---

## 12. QUALITY BAR

The result must feel like a **boutique architectural glazing studio**, not a contractor page.

Desktop: editorial, spacious, gallery-like.
Mobile: premium, accessible, conversion-ready.
Copy: calm, competent, architectural Russian.
Code: clean, modular, maintainable, performant.

Start by:
1. Proposing concept (3 sentences)
2. Confirming design system
3. Defining product taxonomy
4. Then generating code
