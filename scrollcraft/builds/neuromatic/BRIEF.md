# Neuromatic: BRIEF

Interviewed in part (answers below are verbatim where the user gave them). The
remaining topics are authored decisions, labeled as such, derived from the
existing site, `CLAUDE.md`, and the brand rules.

## The interview

1. **Vibe.** User: "premium design. Showcasing the business's professionality.
   While keeping a buttery smooth and premium look."
   Authored references: the stillness of a control room at night shift change;
   Michael Mann's *Collateral* (city at night, practical light); a printed
   operations logbook.
2. **Journey, section by section.** Authored from the current page (the user's
   existing order): hero → the problem (missed calls, calculator) → what we build
   (Answer / Automate / Grow) → how it works → proof (call the demo line, founder
   note) → who it's for → the free audit → FAQ → final call to action.
3. **Energy curve.** Authored: calm open at dawn, rising unease in the problem,
   the loudest motion in the peak mid-afternoon, then a deliberate wind-down to a
   quiet night close.
4. **Feeling and the one moment.** User picked: **"The business runs itself."**
5. **One thing no other site does.** Authored: the page is one working day, and
   the scroll is the clock. A log in the margin writes down everything the system
   handled while the owner was busy.
6. **Range.** User: "We'll go premium minimal but also make sure to review the
   current website because we steered away from the local service business niche
   and made it more broad to service businesses and industrial companies."
7. **One world or scenes.** User: **Distinct scenes.**
8. **Assets.** User: "Do a mix of generated photographics and type + motion."
   Existing: Sora (self-hosted), wordmark + favicon SVG, black / white / lime.
   Hard brand rules: Sora only, lime only on booking buttons and one key word or
   callout per section, no gradients, glows or em dashes, no hype words, no
   unbacked numbers.

## Audience and belief

- For: owners and operators of service businesses and industrial companies
  (HVAC, plumbing, roofing, restoration, cleaning, med spa, manufacturing,
  distribution), US and abroad.
- Must believe by the end: **the calls, leads and admin can be handled without
  me, and this team can build it.**
- One action, one label: **Book a free audit** (`data-book`, all buttons).

## Grammar (new, defined here): Working day

The page is one example working day, in strict chronological order. Each scene
is a time of day, not a numbered section.

- **Navigation:** a day clock. Desktop: a fixed rail on the left edge with the
  day's times, clickable, the current time highlighted; the sticky brand header
  stays (brand rule). Phone: the current time sits in the header.
- **Sequence:** chronological only. No section numbers or eyebrow kickers; the
  timestamp is the only label a scene gets.
- **Ending:** the day closes at night; the last log entry is tomorrow's audit,
  and that entry is the booking button.
- **Bans:** `01 / 06` numbering, kickers above every heading, any scene out of
  time order, more than two `scrub` clips, magnet CTAs, spotlight.

## Signature move: the day log

A thin log that lives in the margin for the whole page. As the visitor scrolls,
the clock advances and entries stamp in ("6:12 AM · Call answered · Booked for
8:30"). At the peak the log leaves the margin and takes the centre of the screen:
the afternoon runs at speed, entries arrive faster than anyone could handle,
each one turning from *incoming* to *handled* on its own, while the owner in the
photo keeps working. Then it folds back into the margin. Every entry is
illustrative and the log is labeled "Example day".

## Feeling curve

| Time | Feeling | What causes it |
|---|---|---|
| 6:12 AM | Calm recognition | Dawn on a commercial rooftop, a technician with a phone; the headline sits between the sky and the person |
| 9:47 AM | Unease | Hands busy on pipework, the phone lit and ignored; the calculator turns it into the visitor's own money |
| 12:30 PM | Clarity | Answer / Automate / Grow travel past sideways at huge scale |
| 1:58 PM | Held breath (authored silence) | One short line on black: "Same afternoon. Different system." |
| 2:30 PM | **Awe, then relief (PEAK)** | The log takes over the screen while the shop-floor shot pushes in; the owner never touches the phone |
| 4:00 PM | Confidence | Three plain steps, live in 2 weeks |
| 5:15 PM | Trust | A real number you can call right now, the founder in their own words |
| 6:30 PM | Belonging | Industry names travel across the screen; the fit list |
| 7:45 PM | Ease | The audit and the questions, compact |
| 9:40 PM | Resolve | Night, the phone lit on an empty desk, the last log entry is tomorrow's audit |

## The peak

Visitor's sentence: **"you scroll through the owner's afternoon and the whole
log fills up with calls and bookings, and nobody ever picks up the phone."**
Lives at 2:30 PM. Largest span on the page (3.6 viewport-heights; the offer rail
is 4.0 but is travel, not a hold), the quiet 1:58 PM beat directly before it.
Planned as the page's only video clip; shipped without one (see Status).

## Tell-someone sentence

"It's the site where you scroll through a business owner's whole day and
everything that comes in gets handled without them touching the phone."

## Authored silence

The 1:58 PM beat is deliberately near-empty: one line on black. Not dead scroll.

## Status (first build)

- Five Higgsfield stills are live as webp in `assets/scenes/` (hero-sky,
  hero-sky-p, hands, shop, night) and their photo planes are on. The rooftop
  technician still is generated but unused until the hero cutout plane is built.
- Not built yet: hero cutout plane (technician), the peak's scrub clip.
