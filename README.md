# Marooned

A macOS screensaver starring **Gus**, a bearded castaway with a red bandana
and an endless supply of optimism, marooned on a very small island with one
palm tree. 412 original comic vignettes play in shuffled order — raft
disasters, crab negotiations, message-in-a-bottle disappointments, and one
unforgettable encounter with an AI that offers to generate him a new island.
(It looks like crap.) Recent batches push well past the shoreline with
cultural humor: music and concerts, politics, blockbuster parodies,
datacenter IT jokes, streaming culture, sports fandom, gaming, and
tech-industry satire.

An original, loving homage to the story-driven screensavers of the early
90s: limited VGA-style palette, chunky nearest-neighbor pixel art, dry
Sierra-flavored humor. All art, writing, and code are original. Marooned is
not affiliated with any classic screensaver product.

## Quickstart

Install from the Marooned app (**Install**, then **Enable as Screensaver**),
or just watch it live: open the **Preview** window (⌘⌥P or Window menu).
Press **S** to skip to the next vignette; use the list button (top-right
circle) to search all 412 episode titles and play any scene on demand.

## Testing iterations

- **Iteration 1.0** — first 20-vignette build.
- **Iteration 2.0** (current) — full scene library of 412 vignettes in
  shuffled order, every title now a Friends-style episode name
  ("The One With...", "The One Where..."), plus a faint "[s] skip" hint
  that appears every couple of minutes; pressing **S** skips to the next
  vignette (works in the Preview window and the saver). Also new: a
  searchable scene picker in the Preview window that plays any title on
  demand, an always-on date/time readout, and scenes that stage their own
  moon no longer share the sky with the day-cycle moon.

## Features

- ~412 hand-written vignettes + idle interludes, shuffled forever
- Scene picker: a searchable sheet of every Friends-style episode title in
  the Preview window — pick one and it plays immediately
- Skip key: press **S** to jump straight to the next vignette
- Small always-on date/time readout (e.g. TUE AUG 25 5:42PM) in the corner,
  updated each minute
- A day/night cycle with sun, moon, and twinkling stars
- Rendered with SpriteKit at a 480×270 virtual resolution, integer-scaled
  with nearest-neighbor filtering on any display
- All art generated procedurally from pixel grids in code — no assets to load
- In-app Preview window that shows exactly what the screensaver plays

## Requirements

- macOS 14 (Sonoma) or newer — including macOS 27 "Golden Gate"
- Xcode to build

## Building

1. Open `Marooned.xcodeproj`
2. Set your signing Team on both targets (`Marooned`, `MaroonedExtension`)
   under Signing & Capabilities (required for distribution; ad-hoc works
   locally)
3. Build the `Marooned` target (⌘R) — the host app launches

The host app exists to bundle, register, and activate the extension; macOS
will not load `.appex` screensavers that are not embedded in an application.
A build-phase script registers the extension with `pluginkit` automatically.

## Installing the screensaver

For testing and troubleshooting — including why you can't just run
ScreenSaverEngine from a terminal — see [TESTING.md](TESTING.md).

In the Marooned host app:

1. **Install** — registers the embedded `.appex` with `pluginkit`
2. **Enable as Screensaver** — uses
   [PaperSaver](https://github.com/AerialScreensaver/PaperSaver) to set
   Marooned as the active screensaver on every display

You can also preview anytime from the app's **Preview** window (⌘⌥P / Window
menu) without activating anything.

## Project layout

- `Marooned/` — host app (registration UI + preview window)
- `MaroonedExtension/` — the screensaver itself (`.appex` principal class,
  view controller, private ScreenSaver headers)
- `Engine/` — shared rendering: pixel-art factory, sprite library, stage,
  actor, director, and the 412 vignettes
- `scripts/main.swift` — dev tool: renders a contact sheet of every sprite
  for offline review
- `BACKGROUND.md` — technical notes on the appex screensaver architecture
  (from the upstream template)

## Credits

Built on [AppexSaverMinimal](https://github.com/AerialScreensaver/AppexSaverMinimal)
by [Guillaume Louel](https://github.com/glouel) (MIT) — see [NOTICE](NOTICE).
Screensaver activation thanks to
[PaperSaver](https://github.com/AerialScreensaver/PaperSaver).

## License

[MIT](LICENSE) — derived from AppexSaverMinimal © 2026 Guillaume Louel.
