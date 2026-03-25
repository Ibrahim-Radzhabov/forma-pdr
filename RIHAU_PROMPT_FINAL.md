# RIHAU — Premium Architectural Glazing Website

## Как использовать

Этот промпт разбит на **2 этапа**:
- **ЭТАП 1** — отправляешь первым. Агент проектирует архитектуру, утверждаешь.
- **ЭТАП 2** — отправляешь после утверждения. Агент пишет код.
- **systems.json** — создай заранее и положи в `/data/systems.json` перед запуском этапа 2.

---

# ═══════════════════════════════════════
# ЭТАП 1 — АРХИТЕКТУРА И ДИЗАЙН-СИСТЕМА
# ═══════════════════════════════════════

```
Brand:            Rihau
Location:         Moscow
Segment:          Upper-premium architectural glazing
Main clients:     Private houses, villas, terraces, architects, designers
Core products:    Panoramic glazing, sliding portals, aluminum systems, façade glazing
Visual tone:      Dark, restrained, architectural, tactile, editorial luxury
Conversion:       Consultation + estimate by plan/photo/messenger
Language:         Russian (all UI and copy)
```

## VISUAL REFERENCES

Study these before proposing anything:
- https://www.skywayroofglazing.co.uk — architectural glazing, editorial calm
- https://www.iqglassuk.com — premium product catalog, clean presentation
- https://www.coutureoutdoor.com — luxury outdoor living, spatial elegance
- https://www.schueco.com — system-level premium, engineering trust
- https://topframing.ru — Russian premium glazing, modern execution

Target feeling: **architectural restraint + luxury residential warmth + engineering trust**.

## TARGET AUDIENCE

Affluent homeowners 30–60, architects, interior designers.
They want confidence, not pressure. Premium look = trust signal.
They distrust mass-market contractors and noisy sales tactics.
First visit often from WhatsApp link on mobile — conversion must work there.

## COPY GUIDE

Write like: architectural consultation, precision, clean geometry, spatial comfort.
Never like: "лучшие цены", "номер один", "успей купить", "от производителя", "акция".

Example headings:
- "Хорошее остекление — это не про профиль. Это про пространство, свет и пропорции."
- "Свет, масштаб и геометрия — как часть архитектуры."

Example review:
- "После замены стало действительно тише, особенно ночью. Монтаж аккуратный, откосы сделали чисто."

Example card tagline:
- "Бесшовный переход между интерьером и террасой"
- "Максимум света при минимальной ширине профиля"

## ANTI-PATTERNS (hard rules)

Never use:
- Aggressive sales banners, red/orange promo labels, "скидка 70%"
- Bright blue corporate gradients, cheap stock photos
- Mass-market window company layouts, e-commerce marketplace aesthetics
- Retail language: "от производителя", "самые дешёвые", "акция месяца"
- Inline base64 images, single giant HTML file

## YOUR TASK FOR STAGE 1

Do NOT write any code yet. Instead, deliver:

### 1. Concept (3 sentences max)
What is the brand feeling? What makes it different from typical glazing sites?

### 2. Design system
Propose and confirm:

| Token            | Suggested value                          |
|------------------|------------------------------------------|
| `--bg`           | `#0a0a0a` deep warm black                |
| `--bg-card`      | `#141414` elevated surfaces              |
| `--bg-alt`       | `#1a1a1a` section alternation            |
| `--text`         | `#e8e2d8` warm ivory                     |
| `--text-muted`   | `#8a8278` secondary text                 |
| `--accent`       | `#c9a96e` muted champagne/brass          |
| `--accent-hover` | `#d4b97d` lighter gold on hover          |
| `--border`       | `rgba(255,255,255,0.08)` subtle dividers |

Typography:
- Headlines: Cormorant Garamond (serif), 500 weight
- Body/UI: Inter (sans-serif), 400 weight
- Labels: Inter uppercase, 2px tracking

Spacing: `4, 8, 12, 16, 24, 32, 48, 64, 96, 128px`
Breakpoints: `480 / 768 / 1024 / 1280 / 1440px`

If you disagree with any value — propose an alternative with reasoning.

### 3. Information architecture

Confirm or improve this section order:

| #  | Section                      | Funnel job                |
|----|------------------------------|---------------------------|
| 1  | Fixed nav                    | Orientation + quick CTA   |
| 2  | Hero                         | Attention + positioning   |
| 3  | Trust metrics bar            | Instant credibility       |
| 4  | Architectural storytelling   | Reframe value             |
| 5  | Solution categories          | Show breadth              |
| 6  | Key advantages               | Differentiation           |
| 7  | Flagship systems             | Aspiration                |
| 8  | Catalog grid (from JSON)     | Selection                 |
| 9  | Guided selector              | Decision help             |
| 10 | Process (6 steps)            | Reduce anxiety            |
| 11 | Portfolio (6–9 projects)     | Social proof              |
| 12 | Before/after proof module    | Emotional conviction      |
| 13 | Testimonials                 | Peer trust                |
| 14 | FAQ                          | Objection handling + SEO  |
| 15 | Contact + form + map         | Conversion                |
| 16 | Footer                       | Legal + secondary nav     |

### 4. Hero content
Propose exact: label, H1, subheadline, CTA1 text, CTA2 text.

### 5. CTA strategy
Map every CTA placement with type (primary/secondary/soft) and text.

### 6. Product taxonomy review
I will provide `/data/systems.json` with 20–30 entries.
For now, confirm these category groups make sense:
- Панорамные системы (5–6 entries)
- Раздвижные системы (4–5)
- Террасы и веранды (3–4)
- Фасады и входные группы (3–4)
- Специальные решения (4–5)

### 7. Key risks or suggestions
Flag anything that could fail or should be reconsidered.

**Wait for my approval before proceeding to Stage 2.**

---

# ═══════════════════════════════════════
# ЭТАП 2 — ГЕНЕРАЦИЯ КОДА
# ═══════════════════════════════════════

(Отправлять ПОСЛЕ утверждения архитектуры из этапа 1)

## PREREQUISITES

Before generating code, ensure:
1. `/data/systems.json` exists with 20–30 product entries
2. Design system is confirmed from Stage 1
3. Section order is confirmed from Stage 1

## FILE STRUCTURE

```
/rihau
  index.html              ← all 16 sections
  /styles
    main.css              ← full design system + responsive
  /scripts
    app.js                ← nav, fade-in, accordion, selector, mobile CTA
    catalog.js            ← reads systems.json, renders grid, filtering
  /data
    systems.json          ← ALREADY EXISTS, do not recreate
  /assets
    /images               ← CSS gradient placeholders
    /icons
  README.md
```

## CODE CONSTRAINTS (hard limits)

| File                      | Max lines |
|---------------------------|-----------|
| `index.html`              | 600       |
| `main.css`                | 1000      |
| `app.js` + `catalog.js`   | 800 total |

- No frameworks, no build tools
- Semantic HTML5 + modern CSS + Vanilla JS
- Real `<img loading="lazy">` — no base64
- No inline styles longer than 1 property

## IMAGES

Use CSS gradient placeholders:
```css
.img-placeholder {
  background: linear-gradient(135deg, #1a1a1a 0%, #2a2520 50%, #1a1a1a 100%);
  aspect-ratio: 16/9;
}
```
Add `<!-- TODO: replace with real photo -->` comments on every placeholder.

## REQUIRED COMPONENTS

### Navigation
- Fixed top, blur background on scroll
- Logo left, links center, CTA right
- Mobile: burger menu with accessible overlay (aria-expanded, focus trap)
- Clickable phone number visible on desktop

### Hero
- Full-screen with confirmed content from Stage 1
- Background: CSS gradient placeholder (not base64)
- Overlay: linear-gradient(to top, #0a0a0a, transparent 60%) + radial warm glow
- 2 CTA buttons: primary filled + secondary ghost

### Trust metrics
- Clean grid: 4–6 metrics
- Large numbers (accent color) + descriptive labels
- Examples: "10+ лет", "500+ объектов", "гарантия на монтаж"

### Storytelling block
- Editorial heading + 3–5 benefit points
- Theme: "Остекление — это не про профиль. Это про пространство, свет и пропорции."

### Flagship systems block
- 3–4 large editorial cards, visually distinct from catalog grid
- Full-width image placeholder + overlay text
- Featured categories: sliding portals, panoramic corner systems, terrace glazing, façade solutions
- Each card: category name + one aspirational line + "Подробнее" link to catalog section
- This section must feel editorial and aspirational, NOT like a product grid

### Catalog
- Rendered from `/data/systems.json` via `catalog.js`
- Category filter chips
- Elegant card grid (badge, name, tagline, 3 specs, use case, CTA)
- No comparison tables

### Guided selector
- 3–4 step chip-based questionnaire
- Output: 2–4 recommended categories
- Pure CSS + JS, no external dependencies

### Process
- 6 steps, horizontal on desktop, vertical on mobile
- Step number (accent) + title + one-line description

### Portfolio
- 6–9 project cards with: type, context, solution, tags
- CSS gradient image placeholders

### Proof module
- **CSS-only before/after slider using clip-path**
- Drag handle with accent color
- Touch support for mobile
- Labels "ДО" / "ПОСЛЕ"
- No canvas, no video, no frame sequences, no scroll hijacking

### Testimonials
- 3–4 cards: quote, name + initial, project context
- Restrained tone, specific details

### FAQ
- Accordion with `aria-expanded`, keyboard accessible
- 10–12 questions covering: cost, timeline, systems, guarantees, process

### Contact section
- Form: имя, телефон, тип объекта (select), комментарий (textarea)
- File upload placeholder
- CTA: "Обсудить проект"
- Reassurance text below form
- WhatsApp + Telegram links (placeholder href)
- Phone (placeholder)
- Yandex Map embed placeholder
- Privacy consent checkbox: "Согласен на обработку персональных данных"

### Sticky mobile CTA
- Visible below 768px after scrolling past hero
- Phone button + "Написать" (messenger) button

### Footer
- Logo, nav links, contacts, messengers, copyright
- Privacy policy link (placeholder)

## RESPONSIVE

Must work on: 1440+ / 1280 / 1024 / 768 / 480 and below.
Mobile: burger menu, preserved hierarchy, no cramped spacing, usable filters.

## ACCESSIBILITY

- Correct heading hierarchy (one H1)
- aria-labels on interactive elements
- alt text on all images (descriptive placeholders)
- Visible focus states
- Skip-to-content link
- `prefers-reduced-motion` — disable all animations
- Form labels and error states
- FAQ accordion keyboard support

## SEO / STRUCTURED DATA

```html
<title>Rihau — Премиальное архитектурное остекление · Москва</title>
<meta name="description" content="Панорамное, раздвижное и фасадное остекление
для частных домов, террас и современных интерьеров. Алюминиевые системы,
проектирование, монтаж под ключ.">
<link rel="canonical" href="https://rihau.ru">
```

Schema.org JSON-LD: `ProfessionalService` + `FAQPage`
Open Graph: title, description, type, image, url, locale=ru_RU
Twitter card: summary_large_image
Favicon: inline SVG

## MOTION

- Fade-in + translate-up (20px) via Intersection Observer, threshold 0.1
- `--transition-fast: 0.2s ease`
- `--transition-base: 0.4s cubic-bezier(0.25, 0, 0.2, 1)`
- Hover transitions on cards and buttons
- No bouncy, flashy, or scroll-hijacking animations

## CTA STRATEGY

| Location            | Type      | Text                    |
|---------------------|-----------|-------------------------|
| Hero                | Primary   | Обсудить проект         |
| Hero                | Secondary | Смотреть проекты        |
| After categories    | Primary   | Получить расчёт         |
| Inside selector     | Primary   | Подобрать решение       |
| After portfolio     | Soft      | Обсудить проект         |
| Final section       | Primary   | Запросить консультацию  |
| Sticky mobile       | Primary   | Позвонить / Написать    |

## DELIVERABLES

1. `index.html` — complete, all 16 sections
2. `main.css` — full design system + responsive
3. `app.js` — nav, fade-in, accordion, selector, sticky CTA
4. `catalog.js` — JSON loading, filtering, card rendering
5. `README.md` — concept, structure, how to run, how to edit content

## SELF-CHECK BEFORE DELIVERY

Before submitting code, review every section and ask:
1. Would this page look out of place next to schueco.com? If yes — redo it.
2. Does any section feel like a "window company template"? If yes — redo it.
3. Does any copy sound like "от производителя" or "лучшие цены"? If yes — rewrite.
4. Is there any section with no visual rhythm (wall of text, no spacing)? If yes — fix.
5. On mobile 375px: is every CTA reachable, every form usable, nav accessible? If no — fix.

## QUALITY BAR

Desktop: editorial, spacious, gallery-like.
Mobile: premium, accessible, conversion-ready.
Copy: calm, competent, architectural Russian. No lorem ipsum.
Code: clean, modular, maintainable, performant.

The result must feel like a **boutique architectural glazing studio**, not a contractor page.

---

# ═══════════════════════════════════════
# ШАБЛОН systems.json
# ═══════════════════════════════════════

Создай этот файл заранее в `/data/systems.json`:

```json
[
  {
    "id": "panoramic-aluminum",
    "category": "panoramic",
    "name": "Панорамные алюминиевые окна",
    "tagline": "Максимум света при минимальной ширине профиля",
    "badge": "Панорама",
    "specs": [
      "Профиль от 35 мм",
      "Стеклопакет до 52 мм",
      "Теплоизоляция: Uf 1.3 Вт/м²·K"
    ],
    "useCase": "Частные дома, пентхаусы, современные интерьеры",
    "image": "assets/images/panoramic-aluminum.jpg"
  },
  {
    "id": "sliding-portal",
    "category": "sliding",
    "name": "Раздвижные порталы",
    "tagline": "Бесшовный переход между интерьером и террасой",
    "badge": "Раздвижные",
    "specs": [
      "Створка до 3×3 м",
      "Вес створки до 400 кг",
      "Порог от 20 мм"
    ],
    "useCase": "Террасы, выходы в сад, панорамные гостиные",
    "image": "assets/images/sliding-portal.jpg"
  }
]
```

Заполни 20–30 записей по категориям:
- `"panoramic"` — 5–6 шт
- `"sliding"` — 4–5 шт
- `"terrace"` — 3–4 шт
- `"facade"` — 3–4 шт
- `"special"` — 4–5 шт
