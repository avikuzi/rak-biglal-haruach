# רק בגלל הרוח

Charcoal desk with one filled switch.

A dark forecast for Israeli wing-foilers. The page is warm ink on charcoal, type carries the hierarchy, and the only filled control is the next action. Green, yellow, and gray appear only when they say whether the wind is suitable. Borders and a shift of surface separate regions. Nothing is purple, glass, or a gradient.

This file is the source of truth. If the interface and this brief disagree, change the interface. If a decision here is revised on purpose, update this file in the same change.

## Context

- **Platform:** static web, mobile-first. One file, `index.html`. The first screen has to work at 390px wide before it is tuned for a desktop.
- **Language:** Hebrew, `dir="rtl"`, `lang="he"`.
- **Feeling:** אמין · רגוע · מדויק.
- **5-second message:** "מתי ואיפה לצאת לגלוש השבוע". A returning visitor gets that from the headline, the wind, and the single action, without tapping. The update time is in the header.

## Numeric constraints

- **1 accent.** The action fill is `#f3f1ec`. Green, yellow, and gray are wind suitability, not a second accent, and they never fill a button. Green is מתאים, yellow is זהירות, gray is לא מתאים.
- **1 font family.** Heebo. Hebrew and numbers use the same family. `--font-en` is an alias of `--font-he`.
- **No heavy shadows.** `--shadow-none` on cards, buttons, and the header. A surface step and a hairline do the separating.
- **2 radii.** Pill `980px` for single-line controls and agreement pills. Card `8px` for panels. The agreement dot and the freshness dot are circles, not a third corner radius.
- **≤3 key figures and 1 primary action per screen.** The first screen's figures are the window, the wind, and `תנאי גלישה טובים`. The filled button is `לראות את השעות`.

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

Wind gray — `#b7b3aa` — `--color-wind-gray`

Not suitable: out of the wind band, or offshore. Not a hover color for close or delete. Model agreement is not a color.

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

Ash — `#b3aea4` — `--color-ash`

Secondary text, kickers, model names. Light enough for 4.5:1 on `#313846` (about 5.3:1) and on `#3c3f44` (about 4.8:1), and about 7.5:1 on the elevated card.

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
| Caption, basis, pill | `--text-caption` | 13px | 600 | 1.4 |
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

Wind cells are meaning surfaces, not elevation: green `#0d3b32` / `#bbf7d0` (מתאים), yellow `#3f3110` / `#fde68a` (זהירות), gray `#3a3e46` / `#f3f1ec` (לא מתאים).

## Components

### Headline card

Role: the first screen. One sentence, at most three figures, one action.

`--color-elevated` background, `1px solid var(--color-line)`, `--radius-card`, padding `--card-padding`, no shadow. Kicker in ash at `--text-body-sm` / 600. Title in ink at `--text-heading` / 700, aligned to the start: `{when}, {HH}:00–{HH}:00` with the week chevron on that line. Under it, the wind at `--text-figure-secondary` and one conditions label `תנאי גלישה טובים`. The label uses the green wash and green ink only. It does not name a model gap and it does not switch to yellow or gray. Basis under them at `--text-caption`.

### Filled button

Role: the one primary action. `לראות את השעות`.

`--radius-button`, background `--color-action`, text `--color-action-ink`, `--text-body` / 600, padding `11px 22px`, min-height `44px`, no border, no shadow. It is not shown while a beach or a level is still missing. That state is a 14px ash helper, not a dimmed button. The filled button appears when it can open the hours: `לראות את השעות`, `לראות את הימים`, or `נסו שוב`.

### Outlined button

Role: every other button. Refresh, guide, accessibility, close, an unselected tab.

`--radius-button`, transparent or `--color-elevated` fill, `1px solid var(--color-line-strong)`, text `--color-ink`, `--text-body-sm` / 600, min-height `44px`. Hover raises the fill to `--color-raised`. It does not become the filled action, and it does not turn red.

A selected beach, level, or day uses the filled treatment, because selection is the same job as the action fill: "this one."

The level choice is one segmented control: pill radius, three equal labels, centered. Unselected segments are transparent on the elevated fill. The selected segment uses the filled treatment. The longer definition stays in `מה מגדיר את הרמה?`.

### Hour table cell

Role: one hour, tappable, colored by the wind.

No radius on the cell. Row labels stay at the start; numbers stay centered in the column and use Heebo. The hour control has a pointer, a dotted underline, and `▾` / `▴`. In-band / caution / out-of-band use the cell tokens above, not a tint of the action ink. A selected hour gets an inset `2px` ring in `--color-ash`. Hover, on a fine pointer only, is a neutral wash `rgba(243, 241, 236, 0.1)`.

### Conditions label

Role: on a window that already passed the 2-of-3 rule, say the conditions are good. Not a button, and not a model-agreement grade.

`--radius-button`, `--text-caption` / 600, padding `3px 10px`. One style: background `--color-wind-green-bg`, text `--color-wind-green-ink`, label `תנאי גלישה טובים`. No spread number, no `המודלים קרובים` / `פער בינוני` / `המודלים חלוקים`. The headline and each week-list row use this label. `הטוב ביותר` stays a separate ink marker on the best row. The green ink `#6ee7b7` on the 18% green wash over the elevated card is about 8:1, and about 7.3:1 on the raised best row. Both clear WCAG 2.1 AA for 13px text (4.5:1).

### Model agreement

Role: say how close the models are, on the hour table and in the model-detail panel. Not a button. Not a color. Not used as a grade on the headline or the week list.

Ash text at caption size. No dot.

- Spread ≤ 3 kt and three models: `שלוש התחזיות קרובות`. Two models: `התחזיות קרובות`.
- Spread ≤ 6 kt: `התחזיות לא זהות`.
- Otherwise, or fewer than two models: `התחזיות חלוקות`.

Gusts that disagree by ≥ 8 kt: the same ash text, `המשבים חלוקים`.

### Model-detail panel

Role: the three models for the hour that was opened.

Sits under the hour table. Background `--color-canvas`, top corners square, bottom corners `--radius-card`, `1px solid var(--color-line)`, no shadow. Three equal cards on `--color-elevated` with `--radius-card`, because they are peers. A model inside the wind band gets a solid green border; gusts over the cap or onshore get a solid yellow border; outside the band or offshore, a solid gray border. The name is ash at caption size. The wind number is Heebo. The note under the cards states the basis: how many models are in range, and the gust cap. Agreement under the hour is ash text, not a colored pill.

## Accessibility

WCAG 2.1 AA. These are requirements, not aspirations.

- **Body text ≥ 4.5:1.** Anything under 18px regular, including 13–16px captions, kickers, pills, and table numbers. Info text is at least 13px. Body copy is at least 14px. Ink `#f3f1ec` on canvas is about 16:1. Ash `#b3aea4` on the elevated card is about 7.5:1, and it still clears 4.5:1 on `#313846` and `#3c3f44`. Mist `#96928c` on the raised surface is about 4.8:1. Unsuitable gray text `#e6e2d8` on canvas is about 12:1, and on a gray cell `#3a3e46` the ink `#f3f1ec` is about 9.5:1. Text that sits on a green or yellow wash uses the lighter ink (`#6ee7b7`, `#fcd34d`), not the solid hue.
- **Large text and UI ≥ 3:1.** Headlines and the window figure clear this easily. The focus ring is 2px `#f3f1ec`, about 14:1 on the card. The outlined button edge, `--color-line-strong` at 45% ink, is about 3.9:1 on raised. The selected-hour ring is solid ash, about 4.7:1 on a green cell. A status border (in-band, caution, out-of-band) is the solid wind hue, about 5.1:1 or better against raised. A 45% tint of that hue sat near 2:1 and is not a border.
- **Focus visible.** Every button and every tappable hour control shows that ring on `:focus-visible`, offset 3px. Do not remove it, and do not paint it in wind green, yellow, or red. Programmatic focus on `main#mainContent` after the intro does not paint that ring. The shell is not a keyboard control.
- **Targets ≥ 44px.** The primary button, the outlined header buttons, beach tabs, the hour control, and the wind number are at least 44px in both axes that the finger hits. Do not shrink them under a phone media query.

The hairline `--color-line` (12% ink) is a decorative divider between figures. It is about 1.4:1. It is not the boundary that identifies a control. Do not use it as the only outline of a button.

## Do

- Use `#f3f1ec` only as the filled action and the selected control. One fill, one job.
- Pair that filled button with outlined secondary actions. Do not stack two filled buttons.
- Let type size carry hierarchy: the window figure is larger than the wind and the conditions label. At most three figures on the first screen.
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

1. Headline card. Elevated `#1c1f27`, 8px radius, 16px padding, 1px line, no shadow, text aligned to the start. Kicker `מתחיל · שדות ים` at 14px / 600 in `#b3aea4`. Title `מחר, 14:00–17:00` at clamp(24px, 4vw, 34px) / 700 in `#f3f1ec`, with `▾` on the same control. The clock span is `bdi dir="ltr"`, so it reads start-then-end from left to right. Under it: `רוח` and the range, gusts when they sit above the wind, and the label `תנאי גלישה טובים` in the green wash. No model-count line and no median line on this card.

2. Primary button. Pill, 980px radius, fill `#f3f1ec`, text `#14161c`, 16px / 600, padding 11px 22px, no border, no shadow. Label `לראות את השעות`.

3. Secondary button. Pill, 980px radius, transparent fill, 1px `rgba(243, 241, 236, 0.45)` border, text `#f3f1ec`, 14px / 600, min-height 44px. Label `רענון`. Hover fills `#242830`. Do not use green, yellow, or red.

4. Hour table cell. No radius. Heebo number, centered in the column. In-band cell `#0d3b32` / `#bbf7d0`. The hour control is a button with a dotted underline and `▾`. Selected state is an inset 2px ring `#b3aea4`, not a new color.

5. Conditions label on the headline and the week list. Pill, 980px radius, 13px / 600, padding 3px 10px. Green wash `rgba(63, 175, 122, 0.18)` and text `#6ee7b7`, label `תנאי גלישה טובים`. One style. Hour-table agreement is ash text, for example `שלוש התחזיות קרובות` or `התחזיות חלוקות`. It is not clickable.

6. Model-detail panel. Canvas `#14161c`, hairline, bottom radius 8px, no shadow. Three equal elevated cards. In-band card border `#3faf7a`. Out of band, `#f07171`. Name `ICON` in ash at 13px. Wind in Heebo. Note: `2 מתוך 3 מודלים בטווח הרוח`.

## CSS custom properties

Put new values in `:root` and consume `var(--…)`. Do not paste a raw hex into a component when a token exists. Accessibility modes override the legacy names (`--bg-primary`, `--text-primary`, `--green-ideal`, and the rest); the named colors point at those names, so a mode repaints the page.

```css
:root {
  --bg-primary: #14161c;
  --bg-secondary: #1c1f27;
  --bg-card-hover: #242830;
  --bg-table-row-alt: #191c23;
  --text-primary: #f3f1ec;
  --text-secondary: #b3aea4;
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
  --color-cell-gray-bg: #3a3e46;
  --color-cell-gray-ink: #f3f1ec;

  --font-he: 'Heebo', sans-serif;
  --font-en: var(--font-he);
  --font-weight-regular: 400;
  --font-weight-semibold: 600;
  --font-weight-bold: 700;
  --text-caption: 13px;
  --content-max-width: 960px;
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

Israeli wing-foilers planning the week at a beach they already know. The first screen answers whether today works at their beach, and names the next window when it does not.

The primary user is a **מתחיל**. Wind bands and the unsaved fallback (`activeLevel`, and `getWindBand` when a level is missing) use beginner: 11–18 קשר, gusts up to 22. A first visit with no saved prefs opens on מתחיל at שדות ים.

The choice is `{ level, beach }` in `localStorage` key `wind_prefs_v1`. Priority is a valid `?beach=` or `?level=` query, then the saved value, then the default (מתחיל, שדות ים). An id that is not in the beach or level list is ignored. `localStorage` reads and writes are wrapped in try/catch.

## Core flow

**Returning visit.** Zero taps to know when and where.

- Headline opens on today. If today has a usable window: `היום, {HH}:00–{HH}:00`. Before sunset, if today has no window, or today's window has already ended while daylight remains, and a later day has a window: the headline stays `אין תנאים לגלישה היום` or `החלון של היום נגמר`. Under it, one full-width button: `לחלון הבא: מחר ({weekday}) {HH}:00–{HH}:00` when that day is tomorrow, otherwise `לחלון הבא: {weekday} {HH}:00–{HH}:00`. The button selects that day and scrolls to its hours. There is no grey `לא היום` caption under that headline. Before sunset, if the forecast has no window left: headline `אין תנאים לגלישה היום` when today truly has no wind, plus plain text `אין חלון גלישה בימים הקרובים`, and no button. After sunset, once today's daylight hours are over: if a later window exists, the headline is `ערב טוב. החלון הבא: מחר {HH}:00–{HH}:00` when that day is tomorrow, otherwise `ערב טוב. החלון הבא: יום {weekday} {HH}:00–{HH}:00`, and the same full-width button stays under it. If the forecast has no window left after sunset: `ערב טוב. אין תנאים בימים הקרובים.` and no button.
- Under the headline, one line names up to two other beaches that have a window today for the selected level: `היום יש תנאים ב:` and the beach names. A good window is a green chip. If no other beach has a good window, up to two caution windows (`אפשר לגלוש, בזהירות`) show as muted amber chips. If neither exists, the line is hidden. Rank is longest window, then strongest suitable wind. Tapping a name switches to that beach, scrolls to the card, and toasts `עברנו ל…`. A verified live camera is a separate 44px button on that chip and opens in a new tab. Beaches without a verified camera have no button. The line reads forecasts already in `forecastCache`.
- The spot and level stay in the kicker. Under a today-window: the wind range, gusts when they sit above the wind, and the label `תנאי גלישה טובים` or `אפשר לגלוש, בזהירות`. A caution label can add a short reason: `רוח מהים אל החוף`, `רוח חלשה`, or `משבים חזקים`. The model-count and median lines are not on this card. The update time stays in the header. A text link `לשנות חוף או רמה` opens the beach chips and the level control. It does not repeat the kicker.
- One filled button: `לראות את השעות`. It opens the hour table. Time ranges and other numeric ranges (wind, gusts, knots, degrees) are isolated left-to-right (`bdi dir="ltr"`), including the week list, the hour table, and the model comparison.
- The hour table is collapsed behind `פירוט שעה־שעה`. A week-list row opens it and jumps to that hour.

**First visit** opens straight on today's window for מתחיל at שדות ים (`html[data-visit]` is `done`). The beach chips and the level control stay collapsed behind `לשנות חוף או רמה` until that link is tapped. Beach chips are 44px tall, 8px apart. The level control is one segmented pill, at most 480px wide and 44px tall, with the label centered. A change is saved immediately.

The hero and the summary card stop at `--content-max-width` (960px). The disclaimer stops at 70ch. Footer source links have a 44px hit area.

Forecast data may prefetch (`sdot-yam`). Do not present that prefetch as the visitor's choice.

Changing level or spot rewrites the one headline to today's window for that choice. If today has more than one window, the headline uses the longest. If today has none during daylight, the headline stays `אין תנאים לגלישה היום`. After sunset it uses the evening line from the returning-visit bullet. While a new spot loads: `מחפש זמן טוב לגלישה…`. Load failure: `לא הצלחנו לטעון את התחזית ל{spot}.`

When that line names a day it is a button: underlined, a small `▾` beside the phrase (`▴` when open), `aria-expanded`, and a 44px target. Open, it lists every window from `listWeekWindows`, in week order: day and date, `{HH}:00–{HH}:00`, the range of the hourly median wind and gust, and the label `תנאי גלישה טובים`. The list's accessible name is `זמנים טובים לגלישה`. The best window is marked `הטוב ביותר` on a raised row, not with a second filled button. A row opens `פירוט שעה־שעה`, selects that day, and pins the window's first hour. Loading and an empty week stay plain text, with no chevron.

The hour table, its day filter, and its summary start collapsed. The control is `פירוט שעה־שעה`, a button with `aria-expanded`. It is not stored. There is no seasons guide on the page. The accessibility statement is a footer link, `הצהרת נגישות`, that opens a short dialog: one commitment sentence, one support line (keyboard, screen reader, text size via the נגישות toolbar), the contact `aviku.vaad@gmail.com`, and an update date. Escape closes it, and Tab stays inside it. The floating נגישות toolbar stays.

The beach guide (`מדריך חופים ותנאי כניסה`) names the facing in 8-point Hebrew (`חוף שפונה למערב`), not degrees. Degrees stay in a tooltip only. An open beach is four short rows: `רוח טובה:`, `כניסה:`, `מתאים ל:`, and `שים לב:` when there is one hazard. Longer notes sit behind `עוד`. Getting up on the foil is `ריחוף על הפויל`. The week heading is `השבוע`.

The day summary under the hour table is one scan, not an essay. Body copy in that block is at least 16px. The model line (`ICON · ECMWF · GFS · HH:MM`) may be 13px. At most one caution line is visible, for example `זהירות: הרוח נושבת מהים אל החוף.` The longer note sits behind `למה?`. `בקצרה` is a single line of time, wind, and wing size. It does not repeat the lead sentence or the caution. `לפני היציאה` is one short line.

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

Helpers: `formatKnots`, `formatKnotRange`, `formatHour`, `formatHourSpan`, `spotName`, `modelShortName`. `formatKnots` returns `—` for a non-number.

## Trust and interaction

The first card does not repeat how the models were combined. That basis lives in the hour table and its explanations: `חציון N מודלים · {support} · עודכן HH:MM`, or `נשמר HH:MM` from cache. The header is `עודכן HH:MM · ICON · ECMWF · GFS` after a fresh fetch, and `נתונים שמורים מ-HH:MM · ICON · ECMWF · GFS` from cache. A missing model is named.

An hour joins a window only when the median meets the band, direction is not offshore, and at least 2 of 3 models are in the wind band. The gust cap applies to the median.

Loading names the real step. No fake delay.

- Cache: `קורא תחזית שמורה…`
- Network: `מושך ICON, ECMWF ו-GFS…`, then each model as its series is read
- Before the consensus: `משווה מודלים…`
- After: `השוויתי N מודלים · N ימים · N שעות שמישות`

The loading state is a skeleton of the headline card plus that line. It leaves when the selected spot has rendered. Empty week: `אין חלון מתאים השבוע ב{spot}.` and `לראות את הימים`. Failed load: one sentence and `נסו שוב`. Filtered table with nothing left: `אין חלון ל{level} בתקופה זו. נסו לכבות את הסינון.`

If it can be tapped, it looks tappable. Refresh shows `מרענן…`, then the clock. Changing level or spot updates the headline. It does not toast "נשמר". Hover opens an hour only when `(hover: hover)` and `(pointer: fine)`. A click pins it.

The footer disclaimer stays: a planning aid, not a go/no-go for the water.
