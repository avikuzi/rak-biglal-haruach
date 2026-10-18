# רק בגלל הרוח

A light summer desk, with one dark switch.

A light forecast for Israeli Wingfoil riders. The page is warm ink on sand, with a hint of light sky at the top. White cards sit on a soft shadow. The first thing on screen is the next window, the beach, and the level, in large type. Green, muted amber, and gray appear only when they say whether the wind is suitable. Nothing is purple, and nothing pulses or blinks.

This file is the source of truth. If the interface and this brief disagree, change the interface. If a decision here is revised on purpose, update this file in the same change.

## Context

- **Platform:** static web, mobile-first. The page is `index.html`. The weekly video is `video-of-week.json`. The first screen has to work at 390px wide before it is tuned for a desktop.
- **Language:** Hebrew, `dir="rtl"`, `lang="he"`.
- **Feeling:** אמין · רגוע · מדויק.
- **5-second message:** "מתי, איפה, ובאיזו רמה". A returning visitor gets that from the headline and the two selectors, without tapping. The update time is in the header.

## Numeric constraints

- **1 accent.** The action fill is ink `#1c1917`, with sand text `#f6f1e8`. Green, muted amber, and gray are wind suitability, not a second accent, and they never fill a button. Green is מתאים, muted amber is זהירות, gray is לא מתאים. Do not use bright yellow `#f59e0b`.
- **1 font stack.** `-apple-system, BlinkMacSystemFont, 'SF Pro Text', 'SF Pro', 'Heebo', sans-serif`. Hebrew and numbers use the same stack. `--font-en` is an alias of `--font-he`. Heebo stays loaded as the fallback.
- **Soft card shadows.** White cards use `0 10px 28px rgba(60, 48, 30, 0.08)`. Buttons stay flat. The header may use a short shadow. Do not add a glow, a pulse, or a blink.
- **2 radii.** Pill `980px` for single-line controls and agreement pills. Card `8px` for panels. The agreement dot and the freshness dot are circles, not a third corner radius.
- **≤3 key figures and 1 primary action per screen.** The first screen's figures are the window and the wind. `תנאי גלישה טובים` stays on the week-list row. The filled button is `לראות את השעות`.

## References

Structural model: [Apple's style file](https://styles.refero.design/style/aecac5da-f397-4ddf-b71f-de1efc434cb8). Borrow the sheet, not the look.

**Take**

- A one-line essence, then exact tokens, then do/don't, then a short prompt per component.
- One accent, used for the primary action and the selected control.
- Two radii: a pill for buttons, one radius for cards.
- White cards with a soft shadow on a warm sand page.
- A filled primary button and an outlined secondary.
- Type size carries hierarchy. The next window is the largest type on the page.

**Don't take**

- A dark charcoal canvas, or a purple or indigo accent.
- Negative letter-spacing. Hebrew stays at `0`.
- Centered product photography, or a pulsing animation.
- A second chromatic color for links, focus, or decoration. Sky blue is only the faint page wash.
- Purple, glass, gradient text, bright yellow, or emoji as icons.

## Color Palette

Action

Ink — `#1c1917` — `--color-action`

The single interactive fill. Primary button and the selected control (beach tab, level, day). Dark ink on the light page. Do not use it as decoration, gradient text, or a glow.

Sand — `#f6f1e8` — `--color-action-ink`

Text and icons that sit on the filled action.

Meaning

Wind green — `#3faf7a` — `--color-wind-green`

In band, or models close (spread ≤ 3 kt). Never a button fill.

Wind amber — `#8a5a12` — `--color-wind-yellow`

Caution: onshore, or gusts over the cap. Muted amber only. Never bright yellow.

Wind gray — `#6b6560` — `--color-wind-gray`

Not suitable: out of the wind band, or offshore. Not a hover color for close or delete. Model agreement is not a color.

Practice label — `#1e4a45` — `--color-practice-ink`

Ink for `רוח חלשה, טוב לתרגול` on the light page. It is a label, not a fourth wind-cell color, and it does not fill a button. No pulse.

Status borders use the solid hues (`#157a45`, `#8a5a12`, `#b42318`).

Neutrals

Canvas — `#f6f1e8` — `--color-canvas`

Page background. The body wash runs from `#e7f3f8` (a hint of sky) through `#f7f3ea` into `#f4efe6` (sand). That wash is not an accent and not a control.

Elevated — `#ffffff` — `--color-elevated`

Headline card, table, and other cards. Soft shadow, not a dark surface.

Raised — `#eef3f8` — `--color-raised`

Hover surface.

Ink — `#1c1917` — `--color-ink`

Primary text. About 15:1 on white and on the sand canvas.

Ash — `#44403c` — `--color-ash`

Secondary text. About 9:1 on white.

Mist — `#57534e` — `--color-mist`

Quiet captions. About 7:1 on white and on sand. Clears 4.5:1.

Line — `rgba(28, 25, 23, 0.12)` — `--color-line`

Hairline between figures, card borders.

Line strong — `rgba(28, 25, 23, 0.42)` — `--color-line-strong`

Outlined buttons. The edge clears 3:1 on white and on sand.

## Typography

One stack: system UI, then SF Pro, then Heebo, for Hebrew and for numbers. Tracking stays `0`. Negative tracking is a Latin display trick and makes Hebrew look sparse. Do not add a second family for digits.

Weights: `400` body, `600` labels, buttons, and secondary figures, `700` the logo and the headline. Do not use `800` or `900` on new text.

| Role | Token | Size | Weight | Line height |
| --- | --- | --- | --- | --- |
| Caption, basis, pill | `--text-caption` | 13px | 600 | 1.4 |
| Body small, kicker, tabs | `--text-body-sm` | 14px | 400–600 | 1.45 |
| Body, primary button | `--text-body` | 16px | 400 / 600 | 1.5 |
| Week line | `--text-subheading` | 15px | 600 | 1.45 |
| Wind and agreement figures | `--text-figure-secondary` | 16px | 600 | 1.2 |
| Window figure | `--text-figure` | 28px | 700 | 1.2 |
| Headline | the next window | clamp(34px, 5.6vw, 56px); 32px under 768px | 700 | 1.15 |
| Logo | `--text-display` | 32px | 700 | 1.15 |

Family: `--font-he` = `-apple-system, BlinkMacSystemFont, 'SF Pro Text', 'SF Pro', 'Heebo', sans-serif`. `--font-en` aliases it.

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
| Card padding | 28px (22px 16px under 768px on the hero) | `--card-padding` |
| Element gap | 12px | `--element-gap` |

Two radii, plus the dot:

| Element | Value | Token |
| --- | --- | --- |
| Single-line buttons, tabs, agreement pills | 980px | `--radius-button` |
| Cards, panels, images, multi-line choices | 8px | `--radius-card` |
| Agreement dot, freshness dot | 50% | `--radius-dot` |

`--radius-sm` through `--radius-xl` alias `--radius-card`. Do not invent a third radius.

Card shadow: `0 10px 28px rgba(60, 48, 30, 0.08)` on white cards. Hierarchy still comes first from type size. The sticky hour-label edge may keep a short directional shadow so the label stays readable while the table scrolls. Buttons do not glow.

## Surfaces

| Level | Name | Value | Purpose |
| --- | --- | --- | --- |
| 0 | Canvas | `#f6f1e8` | Page, with the sky-to-sand wash |
| 1 | Elevated | `#ffffff` | Headline card, summary card |
| 2 | Raised | `#eef3f8` | Hover, pressed secondary |

Wind cells are meaning surfaces, not elevation: green `#e5f4ec` / `#0c4f2e` (מתאים), amber `#f6edd9` / `#5c3d0e` (זהירות), gray `#eceae6` / `#2c2926` (לא מתאים).

## Components

### Headline card

Role: the first screen. One sentence, at most three figures, one action.

White card, soft shadow, `--radius-card`, generous padding. The kicker `חלון הגלישה הבא` is centered, ash, 16px / 600. The title is centered, ink, clamp(34px, 5.6vw, 56px) / 700 (32px under 768px): `{beach} · {when} {HH}:00–{HH}:00`, with the week chevron on that line. The same `{beach} ·` prefix is on the evening line and on `אין תנאים לגלישה היום`. Under the title, two large buttons: `חוף: {name}` and `רמה: {name}`. The chip lists stay collapsed until a button is tapped. Under those buttons, Mediterranean beaches show one compact line, `המים 27° · חולצת לייקרה`. That line is a caption, not a fourth key figure, and it stays short so the wind and `לראות את השעות` remain above the fold at 390px. The closed drawer `לבוש לפי המים` sits at the bottom of this card, after the Windguru link. Level definitions sit in a closed `<details>` drawer, `מה מגדיר את הרמה?`. For מחדד, the practice tag may sit under the title. The wind figure follows. The conditions label is not repeated under the headline. A verified Windguru page is a small ash text link at the footer of this card, `לבדיקה ב־Windguru`, min-height 44px, new tab. Beaches without a verified page have no link.

### Sea temperature

Role: today's sea temperature for the Mediterranean coast, plus one clothing line. Not a wind figure, and not a live buoy.

One value for the Israeli coast, from Open-Meteo Marine `sea_surface_temperature` at the nearest grid point to שדות ים (`32.49`, `34.89`, `cell_selection=sea`). The displayed degree is the noon hour for today in Jerusalem, rounded to the nearest integer. The clothing follows that integer. The line is `המים {n}° · {clothing}`. The closed drawer holds the four approved rows and a 13px source note: the date, Open-Meteo Marine, the returned grid point, and that this is a daily model estimate, not a buoy reading. The same number is used for תל ברוך. כנרת hides the block, because the lake is not this reading. A failed fetch hides the block and does not change the wind forecast.

| Water | Clothing |
| --- | --- |
| מעל 24° (25° and up) | חולצת לייקרה |
| 22–24° | שורטי או חליפה דקה |
| 20–22° (20° and 21°) | חליפת 3/2 |
| מתחת ל־20° | חליפת 4/3 ונעליים |

22° and 24° stay in the warmer band. The table labels stay as approved, including `20–22°`. The matching row uses the raised surface, not a wind color.

### Filled button

Role: the one primary action. `לראות את השעות`.

`--radius-button`, background `--color-action` (`#1c1917`), text `--color-action-ink` (`#f6f1e8`), `--text-body` / 600, padding `11px 22px`, min-height `44px`, no border, no glow. It is not shown while a beach or a level is still missing. That state is a 14px ash helper, not a dimmed button. The filled button appears when it can open the hours: `לראות את השעות`, `לראות את הימים`, or `נסו שוב`.

### Outlined button

Role: every other button. Refresh, guide, accessibility, close, an unselected tab.

`--radius-button`, transparent or `--color-elevated` fill, `1px solid var(--color-line-strong)`, text `--color-ink`, `--text-body-sm` / 600, min-height `44px`. Hover raises the fill to `--color-raised`. It does not become the filled action, and it does not turn red.

A selected beach, level, or day uses the filled treatment, because selection is the same job as the action fill: "this one."

The level choice is one segmented control: pill radius, three equal labels, centered. Unselected segments are transparent on the elevated fill. The selected segment uses the filled treatment. The longer definition stays in `מה מגדיר את הרמה?`.

### Feedback link

Role: a quiet way to say what is missing. Not a primary action, and not on the first screen.

Two places: the end of the weekly summary, and the footer. White fill `--color-elevated`, border `1px solid var(--color-line-strong)`, radius `--radius-card` because the control is two lines, flat, no shadow, no pulse. Label `נשמח לדעתך` at 16px / 600. Subtext `מה חסר לך באתר?` at 13px / 400 in ash. The address is `FEEDBACK_FORM_URL` at the top of the page script. An empty constant opens `mailto:aviku.vaad@gmail.com` with subject `פידבק על רק בגלל הרוח`.

### Hour table cell

Role: one hour, tappable, colored by the wind.

No radius on the cell. Row labels stay at the start; numbers stay centered in the column and use the system stack. The hour control has a pointer, a dotted underline, and `▾` / `▴`. In-band / caution / out-of-band use the cell tokens above, not a tint of the action ink. A selected hour gets an inset `2px` ring in `--color-ash`. Hover, on a fine pointer only, is a neutral wash `rgba(28, 25, 23, 0.06)`.

### Conditions label

Role: on a window that already passed the 2-of-3 rule, say the conditions are good. Not a button, and not a model-agreement grade.

`--radius-button`, `--text-caption` / 600, padding `3px 10px`. One style: background `--color-wind-green-bg`, text `--color-wind-green-ink` (`#0f5c34`), label `תנאי גלישה טובים`. For מחדד the same slot uses `רוח חלשה, טוב לתרגול` in practice ink. No spread number, no `המודלים קרובים` / `פער בינוני` / `המודלים חלוקים`. Each week-list row uses this label. The headline does not repeat it, except the optional practice line under a מחדד window. `הטוב ביותר` stays a separate ink marker on the best row. Green ink `#0f5c34` on the light green wash clears WCAG 2.1 AA.

### Model agreement

Role: say how close the models are, on the hour table and in the model-detail panel. Not a button. Not a color. Not used as a grade on the headline or the week list.

Ash text at caption size. No dot.

- Spread ≤ 3 kt and three models: `שלוש התחזיות קרובות`. Two models: `התחזיות קרובות`.
- Spread ≤ 6 kt: `התחזיות לא זהות`.
- Otherwise, or fewer than two models: `התחזיות חלוקות`.

Gusts that disagree by ≥ 8 kt: the same ash text, `המשבים חלוקים`.

### Model-detail panel

Role: the three models for the hour that was opened.

Sits under the hour table. White cards, `--radius-card`, hairline. A model inside the wind band gets a solid green border; gusts over the cap or onshore get a solid amber border; outside the band or offshore, a solid gray border. The name is ash at caption size. The longer note sits in a closed drawer, `איך נספר חלון`. Agreement under the hour is ash text, not a colored pill.

## Accessibility

WCAG 2.1 AA. These are requirements, not aspirations.

- **Body text ≥ 4.5:1.** Anything under 18px regular, including 13–16px captions, kickers, pills, and table numbers. Info text is at least 13px. Body copy is at least 14px. Ink `#1c1917` on white is about 16:1, and on sand about 15:1. Ash `#44403c` on white is about 9:1. Mist `#57534e` on sand is about 7:1. Green cell ink `#0c4f2e` on `#e5f4ec`, amber ink `#5c3d0e` on `#f6edd9`, and gray ink `#2c2926` on `#eceae6` all clear 4.5:1. Do not put cream `#f3f1ec` on a white card.
- **Large text and UI ≥ 3:1.** Headlines and the window figure clear this easily. The focus ring is 2px `#1c1917`. The outlined button edge, `--color-line-strong`, clears 3:1 on white. A status border is the solid wind hue.
- **Focus visible.** Every button and every tappable hour control shows that ring on `:focus-visible`, offset 3px. Do not remove it, and do not paint it in wind green, yellow, or red. Programmatic focus on `main#mainContent` after the intro does not paint that ring. The shell is not a keyboard control.
- **Targets ≥ 44px.** The primary button, the outlined header buttons, beach tabs, the hour control, and the wind number are at least 44px in both axes that the finger hits. Do not shrink them under a phone media query.

The hairline `--color-line` (12% ink) is a decorative divider between figures. It is about 1.4:1. It is not the boundary that identifies a control. Do not use it as the only outline of a button.

## Do

- Use `#1c1917` only as the filled action and the selected control. One fill, one job.
- Pair that filled button with outlined secondary actions. Do not stack two filled buttons.
- Let type size carry hierarchy: the next window is the largest type. The beach and the level are the next largest controls.
- Put explanations in a closed `<details class="copy-drawer">`. That includes `למה?`, level definitions, the legend, the table how-to, disclaimers, and the model-count note. The main screen stays short.
- The weekly summary is one large row per day for the selected beach and level. Each row names the day and date, the status (`מתאים`, `זהירות`, `רוח חלשה, טוב לתרגול`, or `לא מתאים`), the best hours, and the wind range with a plain compass word. The row is closed. Open, it shows that day's hour table.
- Keep the intro video: it still opens until `intro_seen_v2`, on a dark overlay. Do not restyle that overlay into the summer page.
- Use `980px` on single-line buttons and agreement pills, and `8px` on cards. Those are the only two radii, plus the two dots.
- Keep Hebrew at tracking `0`, weight at most `700`. The hero is centered. The rest of the page aligns to the start.
- Show the basis next to every estimate, and name the real loading step. The long basis lives in a drawer.

## Don't

- Never introduce purple, violet, indigo, or periwinkle. A faint sky wash on the page background is allowed. Do not paint a control with it.
- Never paint a button, a tab, or a link with wind green, amber, or red. Those colors are the wind.
- Never use bright yellow. Caution is muted amber `#8a5a12` / `#f6edd9`.
- Never pulse, blink, or flash a control. The refresh icon may spin while a fetch is in progress.
- Never use gradient text or glass. The page background may be a soft sky-to-sand wash.
- Center the hero (kicker, window, beach, level). Hour-table numbers center in the column. The footer and the drawers align to the start.
- Never use a third radius, a pill on a multi-line card, or `50%` on anything except the agreement dot and the freshness dot.
- Never use emoji as icons, bullets, row markers, or card headers. Functional marks only: `▾` `▴` `↑` `✕` `↻` `↔`.
- Never add marketing filler: "רחף", "תובנות", "רוצה לראות", trophy language, or "פרופיל" as a name for the level.
- Never re-ask a saved level or spot.

## Agent prompt guide

Quick reference:

- text: `#1c1917`
- background: `#f6f1e8`, wash `#e7f3f8` to `#f4efe6`
- elevated card: `#ffffff`, shadow `0 10px 28px rgba(60, 48, 30, 0.08)`
- border: `rgba(28, 25, 23, 0.12)`
- primary action: `#1c1917` fill, `#f6f1e8` text, radius `980px`
- outlined action: `1px solid rgba(28, 25, 23, 0.42)`, transparent fill, radius `980px`
- meaning: `#157a45`, `#8a5a12`, `#6b6560`. Wind only.

1. Headline card. White, 8px radius, generous padding, soft shadow. Kicker `חלון הגלישה הבא`, then title `שדות ים · היום 15:00–18:00` at clamp(34px, 5.6vw, 56px) / 700 in `#1c1917`, centered, with `▾` on the same control. The clock span is `bdi dir="ltr"`. Under it, large buttons `חוף: שדות ים` and `רמה: מחדד`, then one sea line `המים 27° · חולצת לייקרה`. Then the wind and `לראות את השעות`. The closed drawer `לבוש לפי המים` is at the bottom of the card. Explanations stay in closed drawers.

2. Primary button. Pill, 980px radius, fill `#1c1917`, text `#f6f1e8`, 16px / 600, padding 11px 22px, no border, no glow. Label `לראות את השעות`.

3. Secondary button. Pill, 980px radius, transparent fill, 1px `rgba(28, 25, 23, 0.42)` border, text `#1c1917`, 14px / 600, min-height 44px. Label `רענון`. Hover fills `#eef3f8`. Do not use green, amber, or red.

4. Hour table cell. No radius. Number centered in the column. In-band cell `#e5f4ec` / `#0c4f2e`. Caution cell `#f6edd9` / `#5c3d0e`. The hour control is a button with a dotted underline and `▾`. Selected state is an inset 2px ring in ash, not a new color.

5. Conditions label on the week list. Pill, 980px radius, 13px / 600, padding 3px 10px. Green wash and text `#0f5c34`, label `תנאי גלישה טובים`. For מחדד, `רוח חלשה, טוב לתרגול`. Hour-table agreement is ash text. It is not clickable.

6. Model-detail panel. White cards, hairline, radius 8px. In-band border `#157a45`. The long note is a closed drawer: `איך נספר חלון`.

7. Weekly day row. White card, 8px radius, soft shadow, one row per day. Day and date at 22px (26px from 768px), status as a pill, hours at 28px (34px from 768px), wind and compass word under that. `▾` when closed, `▴` when open. The open panel is the hour table for that day.

8. Video of the week. A small card under the weekly summary, title `סרטון השבוע`. Data comes only from `video-of-week.json`: `youtubeId`, `title`, `channel`, `week`. The thumbnail loads first. The iframe (`youtube-nocookie`) loads on click. An empty or missing `youtubeId` hides the card.

## CSS custom properties

Put new values in `:root` and consume `var(--…)`. Do not paste a raw hex into a component when a token exists. Accessibility modes override the legacy names (`--bg-primary`, `--text-primary`, `--green-ideal`, and the rest); the named colors point at those names, so a mode repaints the page.

```css
:root {
  --bg-primary: #f6f1e8;
  --bg-secondary: #ffffff;
  --bg-card-hover: #eef3f8;
  --bg-table-row-alt: #f7f4ee;
  --text-primary: #1c1917;
  --text-secondary: #44403c;
  --text-muted: #57534e;
  --green-ideal: #157a45;
  --yellow-caution: #8a5a12;
  --red-danger: #b42318;

  --color-canvas: var(--bg-primary);
  --color-elevated: var(--bg-secondary);
  --color-raised: var(--bg-card-hover);
  --color-ink: var(--text-primary);
  --color-ash: var(--text-secondary);
  --color-mist: var(--text-muted);
  --color-action: var(--color-ink);
  --color-action-ink: var(--color-canvas);
  --color-line: rgba(28, 25, 23, 0.12);
  --color-line-strong: rgba(28, 25, 23, 0.42);
  --color-wind-green: var(--green-ideal);
  --color-wind-green-ink: #0f5c34;
  --color-wind-yellow: var(--yellow-caution);
  --color-wind-yellow-ink: #6b4510;
  --color-wind-red: var(--red-danger);
  --color-wind-red-ink: #8f1d14;
  --color-cell-green-bg: #e5f4ec;
  --color-cell-green-ink: #0c4f2e;
  --color-cell-yellow-bg: #f6edd9;
  --color-cell-yellow-ink: #5c3d0e;
  --color-cell-gray-bg: #eceae6;
  --color-cell-gray-ink: #2c2926;

  --font-he: -apple-system, BlinkMacSystemFont, 'SF Pro Text', 'SF Pro', 'Heebo', sans-serif;
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
  --card-padding: 28px;
  --element-gap: 12px;

  --radius-button: 980px;
  --radius-card: 8px;
  --radius-dot: 50%;
  --shadow-none: none;
}
```

## Purpose and primary user

Israeli wing-foilers planning the week at a beach they already know. The first screen answers whether today works at their beach, and names the next window when it does not.

The primary user is a **מחדד**. Wind bands and the unsaved fallback (`activeLevel`, and `getWindBand` when a level is missing) use `mehded`: 7–12 קשר, gusts up to 16. A first visit with no saved prefs opens on מחדד at שדות ים.

Levels, stored as English keys:

| Key | Name | Wind | Gusts | Definition |
| --- | --- | --- | --- | --- |
| `mehded` | מחדד | 7–12 קשר | up to 16 | שולט בגלשן, מחדד מול הרוח וחוזר לנקודת ההתחלה |
| `merachef` | מרחף | 11–18 קשר | up to 22 | עולה לריחוף על הפויל ושומר עליו |
| `mahapchim` | מהפכים | 14 קשר ומעלה | allowed | מבצע פניות ומהפכים על הפויל |

`mahapchim` keeps a storm cap at 50 קשר so an extreme hour can still leave the window. The copy says `14 קשר ומעלה. מבצע פניות ומהפכים על הפויל, גם במשבים חזקים`. `gustOverCap` is false when `gustsAllowed` is set. Offshore still excludes an hour at every level. Onshore stays a caution, not an exclusion. Gusts over the cap stay in the window and are marked caution, except for מהפכים.

Saved values migrate and are written back: `beginner` and מתחיל to `mehded`, `intermediate` and בינוני to `merachef`, `advanced` and מתקדם to `mahapchim`. The Hebrew names מחדד, מרחף, and מהפכים map to the same keys. Unknown values fall back to `mehded`.

The light-wind practice tag belongs only to מחדד. `PRACTICE_WIND_MIN` is 7, `PRACTICE_MIN_HOURS` is 2, and `PRACTICE_LEVELS` is `{ mehded: true }`. Because the מחדד band already starts at 7, those 7–12 hours are the real windows and they carry `רוח חלשה, טוב לתרגול` when the hour is not a caution. מרחף and מהפכים do not get a below-band practice tier. Offshore is never a window. The elsewhere strip stays limited to flying windows, which for מחדד are the 7–12 windows.

The choice is `{ level, beach }` in `localStorage` key `wind_prefs_v1`. Priority is a valid `?beach=` or `?level=` query, then the saved value, then the default (`mehded`, שדות ים). An id that is not in the beach or level list is ignored. `localStorage` reads and writes are wrapped in try/catch. The head script migrates before first paint, and `loadPrefs` migrates again.

## Core flow

**Returning visit.** Zero taps to know when and where.

- Headline opens on today and names the selected beach. If today has a usable window: `{beach} · היום {HH}:00–{HH}:00`. Before sunset, if today has no flying window but a practice window is still ahead: `{beach} · היום רוח חלשה: טוב לתרגול שיוט {HH}:00–{HH}:00`, with `למה?` opening `רוח של 7–12 קשר טובה לתרגול: שולט בגלשן, מחדד מול הרוח וחוזר לנקודת ההתחלה.` The next-window button still points at the next flying window when one exists. A sooner practice window that is not already the headline is one line: `תרגול: מחר {HH}:00–{HH}:00`. Before sunset, if today has no window, or today's window has already ended while daylight remains, and a later day has a window: the headline stays `{beach} · אין תנאים לגלישה היום` or `{beach} · החלון של היום נגמר`. Under it, one full-width button: `לחלון הבא: מחר ({weekday}) {HH}:00–{HH}:00` when that day is tomorrow, otherwise `לחלון הבא: {weekday} {HH}:00–{HH}:00`. The button selects that day and scrolls to its hours. There is no grey `לא היום` caption under that headline. Before sunset, if the forecast has no window left: headline `{beach} · אין תנאים לגלישה היום` when today truly has no wind, plus plain text `אין חלון גלישה בימים הקרובים`, and no button. After sunset, once today's daylight hours are over: if a later window exists, the headline is `{beach} · ערב טוב. החלון הבא: מחר {HH}:00–{HH}:00` when that day is tomorrow, otherwise `{beach} · ערב טוב. החלון הבא: יום {weekday} {HH}:00–{HH}:00`, and the same full-width button stays under it. If the forecast has no flying window left after sunset but a practice window does: `{beach} · ערב טוב` and the practice line. If nothing is left: `{beach} · ערב טוב. אין תנאים בימים הקרובים.` and no button. Day cards and the week list use the tag `רוח חלשה, טוב לתרגול` with the time range. The elsewhere strip stays limited to flying windows.
- Above the beach and level selectors, a separate strip names every other beach that has a window today for the selected level. Good windows come first as green chips, then caution windows (`אפשר לגלוש, בזהירות`) as the existing muted amber chips. Each group is ranked longest window, then strongest suitable wind. An amber chip's title and accessible name say `אפשר לגלוש, בזהירות`; the visible label stays the beach name. When the selected beach itself has a window today the lead is `היום יש תנאים גם ב:`. Otherwise it is `היום יש תנאים ב:`. If neither exists, the strip is hidden. Chips wrap onto extra lines with a small gap on a narrow phone, instead of scrolling sideways. Tapping a name switches to that beach, scrolls to the card, and toasts `עברנו ל…`. A verified live camera is a separate 44px button on that chip and opens in a new tab. Beaches without a verified camera have no button. The strip reads forecasts already in `forecastCache`. It is not inside the selected-beach card.
- The beach and the level are the two large buttons under the headline. Under a today-window: the wind range, and gusts when they sit above the wind. The label `תנאי גלישה טובים` or `אפשר לגלוש, בזהירות` is on the week-list row, not under the headline. A caution label can add a short reason: `רוח מהים אל החוף`, `רוח חלשה`, or `משבים חזקים`. The model-count and median lines are not on this card. The update time stays in the header. At the footer of the card, a beach with a verified Windguru page has the text link `לבדיקה ב־Windguru`. The same link sits in that beach's row in `מדריך חופים`. It opens in a new tab with `rel="noopener"`.

- One filled button: `לראות את השעות`. It opens the hour table. Time ranges and other numeric ranges (wind, gusts, knots, degrees) are isolated left-to-right (`bdi dir="ltr"`), including the week list, the hour table, and the model comparison.
- The hour table is collapsed behind `פירוט שעה־שעה`. A week-list row opens it and jumps to that hour.

**First visit** opens straight on today's window for מחדד at שדות ים. The selected beach and level are already on the two large buttons. The beach chips and the level segments stay collapsed until that button is tapped. A change is saved immediately.

The hero and the summary card stop at `--content-max-width` (960px). The disclaimer stops at 70ch. Footer source links have a 44px hit area.

Forecast data may prefetch (`sdot-yam`). Do not present that prefetch as the visitor's choice.

Changing level or spot rewrites the one headline to today's window for that choice. If today has more than one window, the headline uses the longest. If today has none during daylight, the headline stays `{beach} · אין תנאים לגלישה היום`. After sunset it uses the evening line from the returning-visit bullet. While a new spot loads: `{beach} · מחפש זמן טוב לגלישה…`. Load failure: `{beach} · לא הצלחנו לטעון את התחזית.`

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
| The sport | **Wingfoil** | ווינג, ווינגפויל, wing foil |
| Getting up | **ריחוף על הפויל** | ריחוף alone as the level name |
| Levels | **מחדד**, **מרחף**, **מהפכים** | מתחיל, בינוני, מתקדם |
| Journey line | **למחדד** / **למרחף** / **למהפכים** | למתחילים, פרופיל |
| Wind direction | plain compass words with spaces: צפון מזרח | a degree in the visible label, or a Hebrew hyphen inside the compass word |
| A pause in a sentence | a middle dot `·` | an em dash or a double dash |
| Mediterranean spots | שדות ים, בת גלים, תל ברוך | תל ברוך / ת״א |
| Kinneret spots | גינוסר, ג'ינו / כפר נחום, דיימונד (צאלון), מעגן | a second marketing name |
| Kinneret tabs | `כנרת:` plus the short name | the short name alone |
| Models in the UI | **ICON**, **ECMWF**, **GFS** | DWD, NOAA, Open-Meteo in the header |
| Legal names | Footer only: ICON of DWD, ECMWF, GFS of NOAA, via Open-Meteo, CC BY 4.0 | in the header or a card title |
| Units | `{n} קשר`. Range `{a}–{b} קשר` | ק׳ |
| Time | `{HH}:00–{HH}:00` | `13:00 - 17:00` |

Helpers: `formatKnots`, `formatKnotRange`, `formatHour`, `formatHourSpan`, `spotName`, `modelShortName`, `formatBandPlain`. `formatKnots` returns `·` for a non-number.

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
