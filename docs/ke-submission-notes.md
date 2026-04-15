# Submitting HyperJIS to the Karabiner-Elements community repo

How to submit HyperJIS rules to [KE-complex_modifications](https://github.com/pqrs-org/KE-complex_modifications) for listing on [ke-complex-modifications.pqrs.org](https://ke-complex-modifications.pqrs.org/).

## Strategy: three separate PRs

Split into three PRs so each has a clear audience:

### PR 1: HyperJIS Core (JIS remapper + Vim + Hyper)
- **File**: `public/json/hyperjis_core.json`
- **Category**: "International" or propose a new "JIS Keyboard" group
- **Audience**: anyone using a JIS Apple keyboard who wants US-like modifiers and Vim navigation

### PR 2: Romance accent base
- **File**: `public/json/hyperjis_accents_romance.json`
- **Category**: "International Keyboard Layouts"
- **Audience**: anyone typing Italian, Spanish, French, or Portuguese on a US or JIS keyboard

### PR 3: Language extensions (French, Spanish, German)
- **Files**: `public/json/hyperjis_accents_french.json`, `hyperjis_accents_spanish.json`, `hyperjis_accents_german.json`
- **Category**: "International Keyboard Layouts"
- **Audience**: speakers of these specific languages

You could bundle these into one PR or split them. Splitting gives the maintainer smaller reviews.

## Steps

1. Fork `pqrs-org/KE-complex_modifications`
2. Add JSON files to `public/json/`
3. Update `public/groups.json` (add entries in the right group)
4. Remove any `"comment"` fields from manipulator objects (Karabiner ignores them, but the repo maintainers may flag non-standard keys)
5. Run `make`
6. Test locally with `make server`, open `http://localhost:8000`
7. Commit (do NOT commit `public/build/dist.json`), push, open PR

## PR description: Core layout

```
## HyperJIS Core: JIS Apple Keyboard → US Layout + Vim + Hyper

Remaps an Apple JIS keyboard into a US-like power-user layout:

- Caps Lock → Fn
- Space (hold) → Control
- Left Control: tap → Escape, hold → Control
- Left Option → Hyper key (⌃⌥⇧⌘)
- Vim navigation via Ctrl+HJKL
- Eisuu → Command, Kana → Command, ¥ → `/~
- Arrow keys freed for window tiling (optional)

Each rule is independent. Designed for Apple Magic Keyboard (JIS) and JIS MacBooks.
https://github.com/smnrg/HyperJIS
```

## PR description: Romance accents

```
## Romance language accents via Fn key (grave/acute toggle)

Type accented vowels using Fn as the trigger:

- Fn + vowel → grave (è, à, ì, ò, ù)
- Double-tap → acute (é, á, í, ó, ú)
- Fn + Shift + vowel → uppercase
- Fn + 4 → €, Fn + comma/period → «/», Fn + brackets → "/"

No input source switching. Works for Italian, Spanish, French, Portuguese.
https://github.com/smnrg/HyperJIS
```

## PR description: Language extensions

```
## French, Spanish, and German accent extensions

Small files that add language-specific characters on top of the Romance base:

French: Fn + Option + vowel → circumflex (â, ê, î, ô, û), Fn + c → ç, Fn + q → œ
Spanish: Fn + n → ñ, Fn + 1 → ¡, Fn + / → ¿
German: Fn + Option + a/o/u → umlauts (ä, ö, ü), Fn + s → ß

Each file is standalone. Enable alongside the Romance base for full coverage.
https://github.com/smnrg/HyperJIS
```
