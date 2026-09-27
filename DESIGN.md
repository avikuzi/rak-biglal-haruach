# רק בגלל הרוח

Charcoal desk with one filled switch.

A dark forecast for Israeli wing-foilers. The page is warm ink on charcoal, type carries the hierarchy, and the only filled control is the next action. Green, yellow, and red appear only when they say something about the wind. Borders and a shift of surface separate regions. Nothing is purple, glass, or a gradient.

This file is the source of truth. If the interface and this brief disagree, change the interface. If a decision here is revised on purpose, update this file in the same change.

## Context

- **Platform:** static web, mobile-first. One file, `index.html`. The first screen has to work at 390px wide before it is tuned for a desktop.
- **Language:** Hebrew, `dir="rtl"`, `lang="he"`.
- **Feeling:** אמין · רגוע · מדויק.
- **5-second message:** "מתי ואיפה לצאת לגלוש השבוע, ולמה לסמוך על זה". A returning visitor gets that from the headline, the basis line, and the single action, without tapping.

## Numeric constraints

- **1 accent.** The action fill is `#f3f1ec`. Green, yellow, and red are wind meaning, not a second accent, and they never fill a button.
- **1 font family.** Heebo. Hebrew and numbers use the same family. `--font-en` is an alias of `--font-he`.
- **No heavy shadows.** `--shadow-none` on cards, buttons, and the header. A surface step and a hairline do the separating.
- **2 radii.** Pill `980px` for single-line controls and agreement pills. Card `8px` for panels. The agreement dot and the freshness dot are circles, not a third corner radius.
- **≤3 key figures and 1 primary action per screen.** The first screen's figures are the window, the wind, and the agreement. The filled button is `לראות את השעות`.

## References

Structural model: [Apple's style file](https://styles.refero.design/style/aecac5da-f397-4ddf-b71f-de1efc434cb8). Borrow the sheet, not the look.

**Take**

- A one-line essence, then exact tokens, then do/don't, then a short prompt per component.
- One accent, used for the primary action and the selected control.
- Two radii: a pill for buttons, one radius for cards.
- Borders and a background shift instead of drop shadows.
- A filled primary button and an outlined secondary.
- Type size carries hierarchy.

**Don't take**

- The light canvas, Apple blue, or SF Pro.
- Negative letter-spacing. Hebrew stays at `0`.
- Centered, full-bleed product photography, or a marketing hero at 56px.
- A second chromatic color for links, focus, or decoration.
- Purple, glass, gradient text, or emoji as icons.

## Color Palette

Action

Ink — `#f3f1ec` — `--color-action`

The single interactive fill. Primary button and the selected control (beach tab, level, day). Ink on charcoal, so the action is light, not a second hue. Do not use it as decoration, gradient text, or a glow.

Canvas — `#14161c` — `--color-action-ink`

Text and icons that sit on the filled action.

Meaning

Wind green — `#3faf7a` — `--color-wind-green`

In band, or models close (spread ≤ 3 kt). Never a button fill.

Wind yellow — `#f59e0b` — `--color-wind-yellow`

Caution: onshore, gusts over the cap, or a medium spread (≤ 6 kt).

Wind red — `#f07171` — `--color-wind-red`

Out of band, offshore, or the models disagree. Not a hover color for close or delete.

Status borders use these solid hues (`#3faf7a`, `#f59e0b`, `#f07171`). A 45% tint of the same hue is about 2:1 on charcoal and does not mark a card.

Neutrals

Canvas — `#14161c` — `--color-canvas`

Page background.

Elevated — `#1c1f27` — `--color-elevated`

Headline card, table header, unselected chips.

Raised — `#242830` — `--color-raised`

Hover surface. A background shift, not a shadow.

Ink — `#f3f1ec` — `--color-ink`

Primary text.

Ash — `#a39e94` — `--color-ash`

Secondary text, kickers, model names.

Mist — `#96928c` — `--color-mist`

Quiet captions. Light enough to clear 4.5:1 on the raised surface.

Line — `rgba(243, 241, 236, 0.12)` — `--color-line`

Hairline between figures, card borders.

Line strong — `rgba(243, 241, 236, 0.45)` — `--color-line-strong`

Outlined buttons. The composited edge clears 3:1 on canvas, elevated, and raised. The selected-hour ring is solid ash, not this alpha.

## Typography

One family: Heebo, for Hebrew and for numbers. Tracking stays `0`. Negative tracking is a Latin display trick and makes Hebrew look sparse. Do not import it, and do not add a second family for digits.

Weights: `400` body, `600` labels, buttons, and secondary figures, `700` the logo and the headline. Do not use `800` or `900` on new text.

| Role | Token | Size | Weight | Line height |
| --- | --- | --- | --- | --- |
| Caption, basis, pill | `--text-caption` | 12px | 600 | 1.4 |
| Body small, kicker, tabs | `--text-body-sm` | 14px | 400–600 | 1.45 |
| Body, primary button | `--text-body` | 16px | 400 / 600 | 1.5 |
| Week line | `--text-subheading` | 15px | 600 | 1.45 |
| Wind and agreement figures | `--text-figure-secondary` | 16px | 600 | 1.2 |
| Window figure | `--text-figure` | 28px (22px under 768px) | 700 | 1.2 |
| Headline | `--text-heading` | clamp(24px, 4vw, 34px); 22px under 768px | 700 | 1.3 |
| Logo | `--text-display` | 32px | 700 | 1.15 |

Family: `--font-he` = Heebo. `--font-en` aliases it.

## Spacing and shape

Base unit `4px`. Density is comfortable on a phone, tighter than a marketing page, because the headline, the basis, and the one button must sit above the fold at 390px.

| Name | Value | Token |
| --- | --- | --- |
| 4 | 4px | `--spacing-4` |
| 8 | 8px | `--spacing-8` |
| 12 | 12px | `--spacing-12` |
| 16 | 16px | `--spacing-16` |
| 20 | 20px | `--spacing-20` |
| 24 | 24px | `--spacing-24` |
| 40 | 40px | `--spacing-40` |
| Page max width | 1400px | `--page-max-width` |
| Section gap | 28px | `--section-gap` |
| Card padding | 16px | `--card-padding` |
| Element gap | 12px | `--element-gap` |

Two radii, plus the dot:

| Element | Value | Token |
| --- | --- | --- |
| Single-line buttons, tabs, agreement pills | 980px | `--radius-button` |
| Cards, panels, images, multi-line choices | 8px | `--radius-card` |
| Agreement dot, freshness dot | 50% | `--radius-dot` |

`--radius-sm` through `--radius-xl` alias `--radius-card`. Do not invent a third radius.

Shadows: `--shadow-none`. Hierarchy comes from type size and from canvas → elevated → raised. The sticky hour-label edge may keep a short directional shadow so the label stays readable while the table scrolls. That is not a card shadow.

## Surfaces

| Level | Name | Value | Purpose |
| --- | --- | --- | --- |
| 0 | Canvas | `#14161c` | Page |
| 1 | Elevated | `#1c1f27` | Headline card, summary card |
| 2 | Raised | `#242830` | Hover, pressed secondary |

Wind cells are meaning surfaces, not elevation: green `#0d3b32` / `#bbf7d0`, yellow `#3f3110` / `#fde68a`, red `#3f1d24` / `#fecdd3`.

## Components

### Headline card

Role: the first screen. One sentence, at most three figures, one action.

`--color-elevated` background, `1px solid var(--color-line)`, `--radius-card`, padding `--card-padding`, no shadow. Kicker in ash at `--text-body-sm` / 600. Title in ink at `--text-heading` / 700, aligned to the start. Three figures in one row: the window at `--text-figure`, wind and agreement at `--text-figure-secondary`, split by a hairline. Basis under them at `--text-caption`.

### Filled button

Role: the one primary action. `לראות את השעות`.

`--radius-button`, background `--color-action`, text `--color-action-ink`, `--text-body` / 600, padding `11px 22px`, min-height `44px`, no border, no shadow. Disabled: same button at 55% opacity, label `קודם בחרו חוף` or `קודם בחרו רמה`.

### Outlined button

Role: every other button. Refresh, guide, accessibility, close, an unselected tab.

`--radius-button`, transparent or `--color-elevated` fill, `1px solid var(--color-line-strong)`, text `--color-ink`, `--text-body-sm` / 600, min-height `44px`. Hover raises the fill to `--color-raised`. It does not become the filled action, and it does not turn red.

A selected beach, level, or day uses the filled treatment, because selection is the same job as the action fill: "this one."

Multi-line level choices keep `--radius-card` so a paragraph does not sit in a capsule. Unselected is outlined. Selected is filled.

### Hour table cell

Role: one hour, tappable, colored by the wind.

No radius on the cell. Row labels stay at the start; numbers stay centered in the column and use Heebo. The hour control has a pointer, a dotted underline, and `▾` / `▴`. In-band / caution / out-of-band use the cell tokens above, not a tint of the action ink. A selected hour gets an inset `2px` ring in `--color-ash`. Hover, on a fine pointer only, is a neutral wash `rgba(243, 241, 236, 0.1)`.

### Agreement pill

Role: say how close the models are. Not a button.

`--radius-button`, `--text-caption` / 600, padding `3px 10px`.

- Green, spread ≤ 3 kt: background `--color-wind-green-bg`, text `--color-wind-green-ink`, label `המודלים קרובים`
- Yellow, spread ≤ 6 kt: `--color-wind-yellow-bg` / `--color-wind-yellow-ink`, `פער בינוני`
- Red, otherwise or fewer than 2 models: `--color-wind-red-bg` / `--color-wind-red-ink`, `המודלים חלוקים`

Gusts that disagree by ≥ 8 kt: the yellow pill `המשבים חלוקים`.

### Model-detail panel

Role: the three models for the hour that was opened.

Sits under the hour table. Background `--color-canvas`, top corners square, bottom corners `--radius-card`, `1px solid var(--color-line)`, no shadow. Three equal cards on `--color-elevated` with `--radius-card`, because they are peers. A model inside the wind band gets a solid green border; outside, a solid red border. The name is ash at caption size. The wind number is Heebo. The note under the cards states the basis: how many models are in range, and the gust cap.

## Accessibility

WCAG 2.1 AA. These are requirements, not aspirations.

- **Body text ≥ 4.5:1.** Anything under 18px regular, including 12–16px captions, kickers, pills, and table numbers. Ink `#f3f1ec` on canvas is about 16:1. Ash `#a39e94` on the elevated card is about 6.2:1. Mist `#96928c` on the raised surface is about 4.8:1. Wind red as text is `#f07171`, about 5.1:1 on raised and about 4.9:1 on the error wash over canvas. Text that sits on a green, yellow, or red wash uses the lighter ink (`#6ee7b7`, `#fcd34d`, `#fca5a5`), not the solid hue.
- **Large text and UI ≥ 3:1.** Headlines and the window figure clear this easily. The focus ring is 2px `#f3f1ec`, about 14:1 on the card. The outlined button edge, `--color-line-strong` at 45% ink, is about 3.9:1 on raised. The selected-hour ring is solid ash, about 4.7:1 on a green cell. A status border (in-band, caution, out-of-band) is the solid wind hue, about 5.1:1 or better against raised. A 45% tint of that hue sat near 2:1 and is not a border.
- **Focus visible.** Every button and every tappable hour control shows that ring on `:focus-visible`, offset 3px. Do not remove it, and do not paint it in wind green, yellow, or red.
- **Targets ≥ 44px.** The primary button, the outlined header buttons, beach tabs, the hour control, and the wind number are at least 44px in both axes that the finger hits. Do not shrink them under a phone media query.

The hairline `--color-line` (12% ink) is a decorative divider between figures. It is about 1.4:1. It is not the boundary that identifies a control. Do not use it as the only outline of a button.

## Do

- Use `#f3f1ec` only as the filled action and the selected control. One fill, one job.
- Pair that filled button with outlined secondary actions. Do not stack two filled buttons.
- Let type size carry hierarchy: the window figure is larger than the wind and the agreement. At most three figures on the first screen.
- Separate surfaces with a hairline and a background step. Do not add a drop shadow to a card, a button, or the header.
- Use `980px` on single-line buttons and agreement pills, and `8px` on cards. Those are the only two radii, plus the two dots.
- Keep Hebrew at tracking `0`, weight at most `700`, aligned to the start.
- Show the basis next to every estimate, and name the real loading step.

## Don't

- Never introduce purple, violet, indigo, periwinkle, or a sky-blue accent.
- Never paint a button, a tab, or a link with wind green, yellow, or red. Those colors are the wind.
- Never use gradient text, a gradient wash, glass, or `backdrop-filter`.
- Never center the page. The hero, the cards, the footer, and empty states align to the start. Hour-table numbers are the exception: they center in the column.
- Never use a third radius, a pill on a multi-line card, or `50%` on anything except the agreement dot and the freshness dot.
- Never use emoji as icons, bullets, row markers, or card headers. Functional marks only: `▾` `▴` `↑` `✕` `↻` `↔`.
- Never add marketing filler: "רחף", "תובנות", "רוצה לראות", trophy language, or "פרופיל" as a name for the level.
- Never re-ask a saved level or spot.

## Agent prompt guide

Quick reference:

- text: `#f3f1ec`
- background: `#14161c`
- elevated card: `#1c1f27`
- border: `rgba(243, 241, 236, 0.12)`
- primary action: `#f3f1ec` fill, `#14161c` text, radius `980px`
- outlined action: `1px solid rgba(243, 241, 236, 0.45)`, transparent fill, radius `980px`
- meaning: `#3faf7a`, `#f59e0b`, `#f07171` — wind and agreement only

1. Headline card. Elevated `#1c1f27`, 8px radius, 16px padding, 1px line, no shadow, text aligned to the start. Kicker `מתחיל · שדות ים` at 14px / 600 in `#a39e94`. Title `החלון הבא שלך: שני 14:00–17:00, שדות ים` at clamp(24px, 4vw, 34px) / 700 in `#f3f1ec`. Three figures: `החלון` at 28px, `רוח` and `הסכמה` at 16px / 600, split by a hairline. Basis `חציון 3 מודלים · 2/3 מסכימים · עודכן HH:MM` at 12px.

2. Primary button. Pill, 980px radius, fill `#f3f1ec`, text `#14161c`, 16px / 600, padding 11px 22px, no border, no shadow. Label `לראות את השעות`.

3. Secondary button. Pill, 980px radius, transparent fill, 1px `rgba(243, 241, 236, 0.45)` border, text `#f3f1ec`, 14px / 600, min-height 44px. Label `רענון`. Hover fills `#242830`. Do not use green, yellow, or red.

4. Hour table cell. No radius. Heebo number, centered in the column. In-band cell `#0d3b32` / `#bbf7d0`. The hour control is a button with a dotted underline and `▾`. Selected state is an inset 2px ring `#a39e94`, not a new color.

5. Agreement pill. Pill, 980px radius, 12px / 600, padding 3px 10px. Green wash `rgba(63, 175, 122, 0.18)` and text `#6ee7b7`, label `המודלים קרובים`. Yellow and red use the matching wind tokens. The pill is not clickable.

6. Model-detail panel. Canvas `#14161c`, hairline, bottom radius 8px, no shadow. Three equal elevated cards. In-band card border `#3faf7a`. Out of band, `#f07171`. Name `ICON` in ash at 12px. Wind in Heebo. Note: `2 מתוך 3 מודלים בטווח הרוח`.

## CSS custom properties

Put new values in `:root` and consume `var(--…)`. Do not paste a raw hex into a component when a token exists. Accessibility modes override the legacy names (`--bg-primary`, `--text-primary`, `--green-ideal`, and the rest); the named colors point at those names, so a mode repaints the page.

```css
:root {
  --bg-primary: #14161c;
  --bg-secondary: #1c1f27;
  --bg-card-hover: #242830;
  --bg-table-row-alt: #191c23;
  --text-primary: #f3f1ec;
  --text-secondary: #a39e94;
  --text-muted: #96928c;
  --green-ideal: #3faf7a;
  --yellow-caution: #f59e0b;
  --red-danger: #f07171;

  --color-canvas: var(--bg-primary);
  --color-elevated: var(--bg-secondary);
  --color-raised: var(--bg-card-hover);
  --color-ink: var(--text-primary);
  --color-ash: var(--text-secondary);
  --color-mist: var(--text-muted);
  --color-action: var(--color-ink);
  --color-action-ink: var(--color-canvas);
  --color-line: rgba(243, 241, 236, 0.12);
  --color-line-strong: rgba(243, 241, 236, 0.45);
  --color-wind-green: var(--green-ideal);
  --color-wind-green-ink: #6ee7b7;
  --color-wind-yellow: var(--yellow-caution);
  --color-wind-yellow-ink: #fcd34d;
  --color-wind-red: var(--red-danger);
  --color-wind-red-ink: #fca5a5;
  --color-cell-green-bg: #0d3b32;
  --color-cell-green-ink: #bbf7d0;
  --color-cell-yellow-bg: #3f3110;
  --color-cell-yellow-ink: #fde68a;
  --color-cell-red-bg: #3f1d24;
  --color-cell-red-ink: #fecdd3;

  --font-he: 'Heebo', sans-serif;
  --font-en: var(--font-he);
  --font-weight-regular: 400;
  --font-weight-semibold: 600;
  --font-weight-bold: 700;
  --text-caption: 12px;
  --text-body-sm: 14px;
  --text-body: 16px;
  --text-subheading: 15px;
  --text-figure: 28px;
  --text-figure-secondary: 16px;
  --text-heading: 34px;
  --text-display: 32px;
  --tracking-none: 0;

  --spacing-unit: 4px;
  --spacing-4: 4px;
  --spacing-8: 8px;
  --spacing-12: 12px;
  --spacing-16: 16px;
  --spacing-20: 20px;
  --spacing-24: 24px;
  --spacing-40: 40px;
  --page-max-width: 1400px;
  --section-gap: 28px;
  --card-padding: 16px;
  --element-gap: 12px;

  --radius-button: 980px;
  --radius-card: 8px;
  --radius-dot: 50%;
  --shadow-none: none;
}
```

## Purpose and primary user

Israeli wing-foilers planning the week at a beach they already know. The first screen answers when and where the next usable window is, for their level.

The primary user is a **מתחיל**. Wind bands and the unsaved fallback (`activeLevel`, and `getWindBand` when a level is missing) use beginner: 11–18 קשר, gusts up to 22. A first visit with no saved prefs is asked for a spot and then a level. It is not shown a beginner forecast as theirs until both answers exist.

Returning visitors have both saved in `localStorage` key `wind_prefs_v1` as `{ level, beach }`.

## Core flow

**Returning visit.** Zero taps to know when and where.

- Headline: `החלון הבא שלך: {day} {HH}:00–{HH}:00, {spot}`
- Three figures: window, wind, agreement
- One filled button: `לראות את השעות`
- The hour table starts below that screen

**First visit** (`html[data-visit]` is `spot`, then `level`, then `done`).

1. `איפה גולשים?` with `נמצא את החלון הבא בחוף שתבחרו.` Button disabled: `קודם בחרו חוף`. No tab is pre-selected.
2. After a spot: `בחרת {spot}. מה הרמה שלך?` with `החלון יכלול רק שעות שהרוח בטווח של הרמה.` Button: `קודם בחרו רמה`.
3. After a level, save prefs and show the next window.

Forecast data may prefetch (`sdot-yam`). Do not present that prefetch as the visitor's choice.

Changing level or spot rewrites the headline and a week line, for example `למתחיל בשדות ים: 2 חלונות השבוע · הטוב ביותר שני`. One window: `חלון אחד השבוע · {day}`. None: `אין חלון השבוע`. While a new spot loads: `ל{level} {at}: מחפש את החלונות…`. Load failure: `…: לא הצלחנו לטעון`. `הטוב ביותר` is the longest window (hours, then ideal-rank, then earlier date).

## Terminology

Singular `שלך`. `בחרת` and `שלך` stay masculine. Say `חוף`, not ספוט. One Hebrew term per idea.

| Idea | Say | Do not say |
| --- | --- | --- |
| A continuous stretch of usable hours | **חלון** / **חלונות** | חלון גלישה, חלון מוגדר, חלון פעילות, חלון שמיש |
| One clock hour | **שעה** | a window |
| Count of hours that qualify | **שעות שמישות** | חלונות, when you mean hours |
| The displayed sustained wind | **רוח** | רוח ממוצעת |
| How the models are combined | **חציון** | as a synonym for wind |
| Gusts | **משבים**; one model's gust is **משב N** | a singular row label |
| Levels | **מתחיל**, **בינוני**, **מתקדם** | למתחילים on a status line |
| Journey line | **למתחיל** / **לבינוני** / **למתקדם** | למתחילים, פרופיל |
| Mediterranean spots | שדות ים, בת גלים, תל ברוך | תל ברוך / ת״א |
| Kinneret spots | גינוסר, ג'ינו / כפר נחום, דיימונד (צאלון), מעגן | a second marketing name |
| Kinneret tabs | `כנרת:` plus the short name | the short name alone |
| Models in the UI | **ICON**, **ECMWF**, **GFS** | DWD, NOAA, Open-Meteo in the header |
| Legal names | Footer only: ICON of DWD, ECMWF, GFS of NOAA, via Open-Meteo, CC BY 4.0 | in the header or a card title |
| Units | `{n} קשר`. Range `{a}–{b} קשר` | ק׳ |
| Time | `{HH}:00–{HH}:00` | `13:00 - 17:00` |

Helpers: `formatKnots`, `formatKnotRange`, `formatHour`, `formatHourSpan`, `spotName`, `modelShortName`. `formatKnots` returns `—` for a non-number. `spotAt()`: if the short name starts with ב, do not add another ב.

## Trust and interaction

Every estimate shows its basis: `חציון N מודלים · {support} · עודכן HH:MM`, or `נשמר HH:MM` from cache. The header is `עודכן HH:MM · ICON · ECMWF · GFS` after a fresh fetch, and `נתונים שמורים מ-HH:MM · ICON · ECMWF · GFS` from cache. A missing model is named.

An hour joins a window only when the median meets the band, direction is not offshore, and at least 2 of 3 models are in the wind band. The gust cap applies to the median.

Loading names the real step. No fake delay.

- Cache: `קורא תחזית שמורה…`
- Network: `מושך ICON, ECMWF ו-GFS…`, then each model as its series is read
- Before the consensus: `משווה מודלים…`
- After: `השוויתי N מודלים · N ימים · N שעות שמישות`

The loading state is a skeleton of the headline card plus that line. It leaves when the selected spot has rendered. Empty week: `אין חלון מתאים השבוע ב{spot}.` and `לראות את הימים`. Failed load: one sentence and `נסו שוב`. Filtered table with nothing left: `אין חלון ל{level} בתקופה זו. נסו לכבות את הסינון.`

If it can be tapped, it looks tappable. Refresh shows `מרענן…`, then the clock. Changing level or spot updates the headline. It does not toast "נשמר". Hover opens an hour only when `(hover: hover)` and `(pointer: fine)`. A click pins it.

The footer disclaimer stays: a planning aid, not a go/no-go for the water.
