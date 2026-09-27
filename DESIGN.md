# Design brief — רק בגלל הרוח

This file is the design source of truth for the site. Future changes, including AI edits, follow it. If the interface and this brief disagree, change the interface. If a product decision here is revised on purpose, update this file in the same change.

The product is one static Hebrew page: `index.html`, `dir="rtl"`, `lang="he"`.

## Purpose and primary user

Israeli wing-foilers planning the week at a beach they already know. The job of the first screen is to answer when and where the next usable window is, for their level.

The primary user is a **מתחיל**. Wind bands, copy, and the unsaved fallback level (`activeLevel`, and `getWindBand` when a level is missing) use beginner: 11–18 קשר, gusts up to 22. A first visit with no saved prefs is still asked for a spot and then a level. It is not shown a beginner forecast as theirs until both answers exist.

Returning visitors have both saved in `localStorage` key `wind_prefs_v1` as `{ level, beach }`. Do not re-ask.

## Core flow

**Returning visit.** Zero taps to know when and where. The first screen is one sentence and one action:

- Headline: `החלון הבא שלך: {day} {HH}:00–{HH}:00, {spot}`
- At most three figures under it: the window (dominant), the wind, the model agreement
- One primary button: `לראות את השעות`
- The hour table starts below that screen (`.opening` fills the first viewport)

**First visit** (`html[data-visit]` is `spot`, then `level`, then `done`). Ask the easy question first, say briefly why, then adapt the next question.

1. `איפה גולשים?` with `נמצא את החלון הבא בחוף שתבחרו.` The button stays disabled: `קודם בחרו חוף`. No tab is pre-selected. No window is shown as theirs.
2. After a spot: `בחרת {spot}. מה הרמה שלך?` with `החלון יכלול רק שעות שהרוח בטווח של הרמה.` Button: `קודם בחרו רמה`.
3. After a level, save prefs, set visit to `done`, and show the next window plus `לראות את השעות`.

Forecast data may prefetch in the background (default beach id `sdot-yam`). Do not present that prefetch as the visitor's choice.

Changing level or spot rewrites the headline to their next window and a week line, for example `למתחיל בשדות ים: 2 חלונות השבוע · הטוב ביותר שני`. One window: `חלון אחד השבוע · {day}` without `הטוב ביותר`. None: `אין חלון השבוע`. While a new spot loads: `ל{level} {at}: מחפש את החלונות…`. Load failure: `…: לא הצלחנו לטעון`. `הטוב ביותר` is the longest window (hours, then ideal-rank, then earlier date).

## Color

Neutral base. One meaning is allowed to use color: wind quality, and the agreement that describes it.

| Role | Token | Value |
| --- | --- | --- |
| Page | `--bg-primary` | `#14161c` |
| Card / header surface | `--bg-secondary`, `--bg-card` | `#1c1f27` |
| Ink | `--text-primary` | `#f3f1ec` |
| Secondary ink | `--text-secondary` | `#a39e94` |
| Muted | `--text-muted` | `#6f6b64` |
| In band / models close | `--green-ideal` | `#3faf7a` |
| Caution, onshore, gusts over the cap, medium spread | `--yellow-caution` | `#f59e0b` |
| Out of band, offshore, models split | `--red-danger` | `#ef4444` |

Agreement pills use those three only:

- Green, spread ≤ 3 kt: `המודלים קרובים`
- Yellow, spread ≤ 6 kt: `פער בינוני`
- Red, otherwise or fewer than 2 models: `המודלים חלוקים`

Selected tabs, the primary button, and the accessibility button are ink on page or page on ink (`#f3f1ec` / `#14161c`). They are not a second brand color. Sea and lake labels use the same muted ink.

No purple, violet, indigo, periwinkle, or sky-blue decorative accents. No teal hover. No cyan glow. Buttons do not turn red on hover; red is for wind that is out of band or offshore.

User-chosen accessibility modes may override this (high contrast, invert, grayscale). The default theme does not.

## Typography

- Hebrew: Heebo (`--font-he`). Page is RTL.
- Latin and table numbers: Inter (`--font-en`).
- Logo: 32px / 800, solid ink, no shadow.
- Hero title: `clamp(24px, 4vw, 34px)` / 800. At 768px and below: 22px.
- Window figure: 28px (22px on a phone). Wind and agreement: 16px (14px on a phone).
- Week line (`.choice-value`): 15px / 750.
- Kicker: 13px / 700, muted.
- Basis line: 12px.
- Lead card value (the window, or the outlook lead): 32px. Other KPI values: 18px.
- Body copy about 14–16px, line-height 1.6.

No gradient text. No uppercase tracking on labels (`letter-spacing: 0`, `text-transform: none`). The readable-font accessibility mode may add tracking.

## Hierarchy

The first screen shows at most three key figures: window, wind, agreement. The window is the dominant one (larger type, and in the hour summary the window card spans the row). Secondary metrics are smaller and quieter. Onshore caution is a caption under the wind. Gust split and spread are a caption under agreement.

Do not give five equal KPI cards the same weight. A comparison of peer models may stay equal weight: the three model cards are a comparison, aligned to the start.

The hour table is the detail view, reached by the one primary action. It is not the first screen.

## Iconography

Data is labeled in Hebrew words: `רוח`, `משבים`, `כיוון רוח`, `גלים`, `מחזור`, `כניסה למים`, `טמפ'`, level names, spot short names. The legend is a color swatch plus words.

Functional marks, and only these, may stand in for a control affordance:

- `▾` / `▴` — hour cell open or closed
- `↑` — wind arrow, rotated to the direction
- `✕` — close, always with the word `סגור`
- `↻` — refresh, with the word `רענון`
- `↔` — the hour table scrolls sideways

No emoji as icons, bullets, row markers, card headers, legends, or status badges. Color carries ideal / caution / out of band. Do not put pictographs back into tabs, levels, or KPI headers.

## Tone and terminology

Singular `שלך`, matching `החלון הבא שלך`. `בחרת` and `שלך` stay masculine, as the rest of the site. Say `חוף`, not ספוט. One Hebrew term per idea. Do not introduce a synonym in a new string.

| Idea | Say | Do not say |
| --- | --- | --- |
| A continuous stretch of usable hours | **חלון** / **חלונות** | חלון גלישה, חלון מוגדר, חלון פעילות, חלון שמיש |
| One clock hour | **שעה** | a window |
| Count of hours that qualify | **שעות שמישות** | חלונות, when you mean hours |
| The displayed sustained wind (model median) | **רוח** | רוח ממוצעת |
| How the models are combined | **חציון** | as a synonym for wind |
| Gusts | **משבים**; one model's gust is **משב N** | mixing the singular into a row label |
| Levels | **מתחיל**, **בינוני**, **מתקדם** | למתחילים on a status line |
| Journey line for a level | **למתחיל** / **לבינוני** / **למתקדם** | למתחילים, פרופיל |
| Place | **חוף**, and the short name | ספוט |
| Mediterranean spots | שדות ים, בת גלים, תל ברוך | תל ברוך / ת״א |
| Kinneret spots | גינוסר, ג'ינו / כפר נחום, דיימונד (צאלון), מעגן | a second marketing name |
| Kinneret tabs | `כנרת:` plus the short name | the short name alone, where the group needs a prefix |
| Place-in-a-sentence | `spotAt()`: if the short name starts with ב, do not add another ב; otherwise prefix ב | בשדות ים written by hand in one place and בת גלים in another |
| Models in the running UI | **ICON**, **ECMWF**, **GFS** | DWD, NOAA, Open-Meteo in the header |
| Legal model names | Footer only: ICON of DWD, ECMWF, GFS of NOAA, via Open-Meteo, CC BY 4.0 | in the header, the basis line, or a card title |
| Units | `{n} קשר` with a space. Range `{a}–{b} קשר` with an en dash and no spaces around the dash | ק׳, a hyphen with spaces |
| Time | `{HH}:00–{HH}:00`, en dash, no spaces | `13:00 - 17:00` |
| Agreement | **המודלים קרובים** / **פער בינוני** / **המודלים חלוקים** | a fourth label |
| Gusts disagree by ≥ 8 kt | **המשבים חלוקים** | a new phrase per screen |

Table cells stay bare numbers. The row label carries the unit: `רוח (קשר)`, `משבים (קשר)`.

Helpers already exist: `formatKnots`, `formatKnotRange`, `formatHour`, `formatHourSpan`, `spotName`, `modelShortName`. Use them. `formatKnots` returns `—` for a non-number, so do not pass a range string through it.

## Trust

Every estimate shows its basis. The pattern is `חציון N מודלים · {support} · עודכן HH:MM` (or `נשמר HH:MM` from cache). The header line is `עודכן HH:MM · ICON · ECMWF · GFS`. A missing model is named (`חסר …`), not hidden. Tapping an hour shows the three models. A model gust over the cap is marked on that model. The window uses the median gust, and an hour joins a window only when at least 2 of 3 models are in the wind band and the direction is not offshore.

Loading names the real step, tied to the fetch or the compare. No fake delay. Sequence:

- Fresh cache: `קורא תחזית שמורה…`
- Network: `מושך ICON, ECMWF ו-GFS…`, then each model as its series is read
- Before the consensus is built: `משווה מודלים…`
- After: `השוויתי N מודלים · N ימים · N שעות שמישות` (hours 6–20 classified ideal or usable)

The first-screen loading state is a skeleton of that card: three quiet blocks, `מחפש את החלון הבא…`, and the work line. It leaves as soon as the selected spot has rendered. No full-page spinner. No blank page.

Empty week: `אין חלון מתאים השבוע ב{spot}.` and one action, `לראות את הימים`. Failed load: one sentence and `נסו שוב`. A filtered hour table with nothing left: `אין חלון ל{level} בתקופה זו. נסו לכבות את הסינון.` aligned to the start.

The footer disclaimer stays: a planning aid, not a go/no-go for the water.

## Interaction

If it can be tapped, it looks tappable. Hour cells use a pointer, a dotted underline, and `▾` / `▴`. Buttons look like buttons (fill, border, label). An icon-only control gets a word.

Every action has visible feedback:

- Level or spot: the headline and the week line update. No "נשמר" toast for those.
- Refresh: `מרענן…`, then `עודכן HH:MM`.

Hover opens hour detail only when `(hover: hover)` and `(pointer: fine)`. A click pins it.

Never re-ask a saved level or spot. The head script sets `documentElement.dataset.visit` from prefs before paint. The inline prefs script applies the saved tab and level before the main script runs.

## Banned defaults

Do not add any of these, including in a new component:

- Purple, violet, indigo, or periwinkle, in any gradient or as a flat accent
- Gradient text, or a gradient wash on the wordmark or the summary card
- Glassmorphism and `backdrop-filter`
- A photo or gradient overlay on the page background
- Everything centered. Page composition, the hero, KPIs, the footer, empty states, and summaries align to the start
- Everything maximally rounded. Corner radius is **4px** (`--radius-sm` through `--radius-xl`)
- Emoji bullets, emoji row icons, emoji card headers, emoji legends
- A grid of identical equal-weight cards for facts that are not equal
- Marketing filler: "רחף על חוף", "רוצה לראות", "תובנות", trophy language, "פרופיל" as a name for the level

Allowed exceptions:

- Numeric columns in the hour table are centered. Row labels stay right-aligned.
- `border-radius: 50%` is only the agreement dot and the freshness dot in the header.
- The filter switch thumb is a small 2px-radius block inside a 4px track, not a pill.
- Legend swatches are 2px-radius squares, not circles.
- Model cards stay equal weight because they compare peers.
- Accessibility modes may invert hue, go grayscale, or use a yellow focus ring. That is the visitor's choice, not the default theme.
