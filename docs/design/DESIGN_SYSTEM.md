# Дизайн-система TesoroMap

Канон продукта: **[Devin Desktop](https://devin.ai/desktop)** — спокойный светлый SaaS, карта и панели читаются как рабочий инструмент, не как лендинг.

Референс-скрин: `assets` / Devin Sessions board.  
Refero-стиль по ссылке Cognitions ([styles.refero.design](https://styles.refero.design/style/cfab7b43-ed24-41e9-9272-c858700b865b)) описывает **Windsurf marketing (dark)** — для приложения не использовать. Допустимо только на отдельном маркетинговом лендинге (см. §10).

Токены в коде: [`tokens.css`](tokens.css).

---

## 1. Характер

| Да | Нет |
|----|-----|
| Светлая нейтральная оболочка | Тёмный «aurora» IDE на всём продукте |
| Тонкая линия, мало тени | Многослойные glow и неон |
| Карта — главный холст | Дашборд из карточек в первом вьюпорте |
| Pills для фильтров и CTA | Жирные градиентные кнопки |
| Линейные иконки | Эмодзи как UI |
| Один спокойный акцент (синий статуса) | Фиолетовые маркетинговые градиенты |

Первый экран продукта = **карта на весь вьюпорт** + тонкий chrome (как Циан по композиции, как Devin по материалам UI).

---

## 2. Цвет (chrome UI)

### Поверхности

| Token | Hex | Роль |
|-------|-----|------|
| `--tm-bg-app` | `#F4F4F5` | Фон приложения за панелями |
| `--tm-bg-sidebar` | `#F7F7F8` | Боковая панель |
| `--tm-bg-panel` | `#FFFFFF` | Карточки, попапы, sheet досье |
| `--tm-bg-muted` | `#EEEEF0` | Secondary button, track |
| `--tm-bg-hover` | `#E8E8EA` | Hover строк / меню |

### Текст

| Token | Hex | Роль |
|-------|-----|------|
| `--tm-text` | `#111113` | Заголовки, основной текст |
| `--tm-text-secondary` | `#5C5C66` | Метаданные, подписи |
| `--tm-text-tertiary` | `#8B8B96` | Timestamps, hints |
| `--tm-text-inverse` | `#FFFFFF` | Текст на primary |

### Границы и разделители

| Token | Hex | Роль |
|-------|-----|------|
| `--tm-border` | `#E4E4E7` | Карточки, инпуты |
| `--tm-border-strong` | `#D4D4D8` | Активный сегмент / focus ring soft |

### Акценты UI (не путать с легендой карты)

| Token | Hex | Роль |
|-------|-----|------|
| `--tm-accent` | `#2563EB` | Primary action, active tab, focus |
| `--tm-accent-soft` | `#EFF4FF` | Selected row / chip fill |
| `--tm-success` | `#16A34A` | Ready / ok слой |
| `--tm-warning` | `#D97706` | Waiting / degraded |
| `--tm-danger` | `#DC2626` | Ошибка источника |
| `--tm-info` | `#2563EB` | Running / sync |

Один chromatic accent для chrome — синий. Зелёный / оранжевый / красный только как **статус**, не как декорация.

---

## 3. Легенда карты (продуктовые цвета)

Отдельный набор от chrome. На карте важнее различимость типов сделки.

| Слой | Token | Hex (v0) | Геометрия |
|------|-------|----------|-----------|
| Участок (нейтраль) | `--tm-map-parcel` | `#64748B` + fill 18% | polygon |
| Торги | `--tm-map-tender` | `#7C3AED` | polygon / outline |
| Продажа | `--tm-map-sale` | `#2563EB` | point / polygon |
| Аренда | `--tm-map-lease` | `#0D9488` | point |
| Организация | `--tm-map-org` | `#CA8A04` | point |
| Дорога магистраль | `--tm-map-road-trunk` | `#334155` | line 3px |
| Дорога основная | `--tm-map-road-primary` | `#64748B` | line 2px |
| Дорога местная | `--tm-map-road-local` | `#A1A1AA` | line 1px |
| Выделение / focus | `--tm-map-focus` | `#F59E0B` | outline |

Фиолетовый **только** на слое торгов (семантика «гос»), не в кнопках UI.

---

## 4. Типографика

Devin Desktop = нейтральный геометрический sans. Для продукта:

| Роль | Family | Fallback |
|------|--------|----------|
| UI / body | **Geist Sans** или **Inter** | `ui-sans-serif, system-ui` |
| Mono (кадастровый номер, цены) | **Geist Mono** / **IBM Plex Mono** | `ui-monospace` |

Карта и цифры важнее «экспрессивного» display-шрифта. Display из Windsurf (`tomatoGrotesk`) — **не** для app shell.

### Шкала

| Token | Size / line / weight | Где |
|-------|----------------------|-----|
| `--tm-text-xs` | 12 / 16 / 400–500 | timestamps, badges |
| `--tm-text-sm` | 13 / 18 / 400 | мета в карточке |
| `--tm-text-md` | 14 / 20 / 400 | body панелей |
| `--tm-text-lg` | 15–16 / 22 / 500–600 | заголовок карточки объекта |
| `--tm-text-xl` | 18 / 26 / 600 | заголовок панели |
| `--tm-text-2xl` | 22 / 28 / 600 | редко, модалки |

Letter-spacing: чуть отрицательный на заголовках (`-0.01em`), на mono caps для номеров — нейтральный или `+0.02em`.

---

## 5. Форма, отступы, тень

### Radius

| Token | Value | Элемент |
|-------|-------|---------|
| `--tm-radius-sm` | `6px` | инпуты, мелкие chips |
| `--tm-radius-md` | `10px` | карточки объектов, колонки |
| `--tm-radius-lg` | `12px` | панели, модалки |
| `--tm-radius-pill` | `9999px` | primary/secondary buttons, filter pills, segmented |

Как у Devin: **pill = действия и фильтры**, **~10px = поверхности контента**.

### Spacing (база 4px)

`4 · 8 · 12 · 16 · 20 · 24 · 32 · 40 · 48`

- Padding карточки объекта: `12–16px`
- Gap в списках: `8px`
- Sidebar width: `240–280px`
- Sheet досье (desktop): `360–420px`

### Elevation

Тень минимальная — границы делают работу.

```css
--tm-shadow-sm: 0 1px 2px rgba(17, 17, 19, 0.04);
--tm-shadow-md: 0 4px 16px rgba(17, 17, 19, 0.06);
```

Модалки / popover — `md`. Карточки на доске / в списке — border, почти без тени.

---

## 6. Компоненты (как у Devin → как у нас)

| Devin | TesoroMap |
|-------|-----------|
| Left sidebar + main | Тонкий top/left chrome + **full-bleed map** |
| «New session» pill | «Обвести область» / «Новая область» |
| Segmented Board/List | Слои / Список объектов |
| Filter pills | Тип сделки, статус лота, категория org |
| Kanban card | Карточка участка / лота в списке области |
| Status + timestamp | Статус слоя (`ready/degraded`) + `fetched_at` |
| Blue unread dot | Непросмотренный лот / новое в контуре |

### Кнопки

- **Primary:** fill `--tm-accent`, text inverse, pill, height 32–36px  
- **Secondary:** fill `--tm-bg-muted`, text primary, pill  
- **Ghost:** transparent, border `--tm-border`  
- Не использовать градиенты на кнопках

### Инпуты / поиск

Height 32–36px, radius sm/md, border `--tm-border`, focus ring 2px `--tm-accent` at 30% opacity.

### Segmented control

Как Board/List: общая «дорожка» muted, активный сегмент белый + лёгкая тень/border.

### Карточка объекта

1. Заголовок (адрес / лот)  
2. Secondary: кадастровый номер mono  
3. Статус + цена  
4. Мета: источник · дата  

Без декоративных бейджей поверх карты (см. product UI rules: no hero overlays).

---

## 7. Layout продукта

```text
┌─ top bar: logo · search place · layers · account ─────────┐
│ ┌ map (100%) ──────────────────────────┬ dossier sheet ┐ │
│ │  draw · parcels · lots · orgs · roads │ facts/est/unk │ │
│ │                                       │ brief · advise│ │
│ └───────────────────────────────────────┴───────────────┘ │
└───────────────────────────────────────────────────────────┘
```

- Карта edge-to-edge под chrome.  
- Досье — боковой sheet поверх / beside, не «карточки в сетке» вместо карты.  
- Мобильный v1: карта full; sheet снизу (bottom sheet) в стиле тех же токенов.

---

## 8. Статусы и досье

| Kind | UI |
|------|-----|
| fact | нейтральный текст + source link |
| estimate | warning-tint chip «оценка» |
| unknown | tertiary text «неизвестно» — не выдумывать цифру |

Слои источника: точка/текст `ready` green · `loading` blue spinner · `degraded` orange · `empty` tertiary.

---

## 9. Motion

Как Devin: коротко и функционально.

- Sheet / popover: 150–200ms ease-out  
- Hover карточки: border/background, без прыжка scale  
- Спиннер sync слоя: линейный  
Не: параллакс карты, конфетти, aurora ribbons в app

---

## 10. Marketing (опционально, не app)

Если понадобится лендинг в семье Cognition/Windsurf Refero:

- Canvas `#011c42`, accent `#34e8bb`, pills 9999, cards radius 6  
- **Не смешивать** эти токены с map app shell  
- Отдельный CSS-файл `tokens.marketing.css`, не импортировать в приложение карты

---

## 11. Проверка перед UI-PR

- [ ] Светлый chrome, один синий accent  
- [ ] Кнопки/фильтры — pills; панели — ~10–12px radius  
- [ ] Карта — главный холст первого экрана  
- [ ] Кадастровый номер — mono  
- [ ] Легенда сделки ≠ цвет кнопок  
- [ ] Нет Windsurf navy / teal glow в продукте  
- [ ] Нет purple-on-white marketing градиентов в chrome  

---

## 12. Источники

- Product UI: [devin.ai/desktop](https://devin.ai/desktop) + скрин Sessions board  
- Marketing-only reference: [Refero Windsurf style](https://styles.refero.design/style/cfab7b43-ed24-41e9-9272-c858700b865b)  
- Продуктовый цикл: [`../product/analysis-loop.md`](../product/analysis-loop.md)  
- Архитектура UI: [`../architecture/ARCHITECTURE.md`](../architecture/ARCHITECTURE.md) §9  
