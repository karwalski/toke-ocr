# toke-ocr

Optical character recognition written in toke, for clean machine-printed
documents.

**Status: not started.** This repository holds the plan; there is no
recogniser yet. Work is tracked in the toke project's single tracker,
[`docs/progress.md`](https://github.com/karwalski/toke/blob/main/docs/progress.md),
under Epic 139.

## Scope

In scope: clean, machine-printed, high-contrast **Latin-script** documents —
statements, invoices, payslips, government letters.

Out of scope, deliberately: handwriting, low-resolution photographs, dense
multi-column layouts, and non-Latin scripts. Saying so is what keeps this
finishable.

## What to expect

This will start out **less accurate than Tesseract**, and may stay so for a
long time. It is worth doing for:

- portability — no C++ dependency;
- confidence designed in rather than bolted on: every glyph and every field
  carries a confidence, so a consumer can flag low-confidence fields instead of
  trusting them;
- being written in toke.

It is **not** worth adopting in order to beat Tesseract on accuracy. Do not
adopt it under that assumption.

## Why a separate repository

OCR is a recognition system with an accuracy distribution, model artefacts, a
training pipeline and per-font behaviour. The toke standard library holds
bounded, deterministic, fixture-testable parsers; it should not ship model
weights or acquire an accuracy metric. So this lives here, with its own release
cadence, consumed as a dependency.

toke already provides the preprocessing primitives — `std.image` decodes four
formats and offers greyscale, crop, resize and pixelate, and `std.math`,
`std.vec` and `std.ml` cover the numeric work. The missing piece is recognition.

## Benchmarks

Any published benchmark reports its full distribution and its negative
results. No aggregate accuracy figure is quoted without the distribution
behind it.

## Planned work

Binarisation, deskew, line and word segmentation, glyph segmentation, glyph
classification, a training pipeline, per-glyph and per-field confidence,
layout reconstruction, lexicon post-correction, and a published benchmark.
Each is a story in Epic 139 of the toke tracker.

## Licence

MIT — see [LICENSE](LICENSE).
