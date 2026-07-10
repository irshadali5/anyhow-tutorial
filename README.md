# 📦 anyhow — Interactive Rust Error Handling Tutorial

A self-contained, offline-first reference for learning `anyhow`, the crate Rust developers reach for when `Box<dyn Error>` and custom error enums get tedious. Built for learners who want to go from *"what is this crate even for"* to *"I can architect error handling for a real Axum service"* — without leaving a single HTML file.

---

## Why this exists

Rust's error handling is powerful but has a steep on-ramp: `Result<T, E>`, the `?` operator, `From` conversions, trait objects, and eventually crates like `anyhow` and `thiserror` all show up at once. Most tutorials either skim the surface or dump the whole crate's API on you in one page.

This site is built the opposite way — concepts are **layered**, each page assumes only what came before it, and nothing requires an internet connection once the file is downloaded. It's meant to be the *one tab* you keep open while working through `anyhow` for real, instead of bouncing between docs.rs, blog posts, and Stack Overflow.

---

## Who it's for

This guide assumes you already:

- Understand Rust's `Result<T, E>` and `Option<T>`
- Have written a few functions using the `?` operator
- Know what a `struct` and `enum` are

It does **not** assume you've used `anyhow`, `thiserror`, or any error-handling crate before. If you've worked through the official Rust Book up through error handling (Chapter 9) and maybe a small CLI project, you're in the right place.

---

## Layout of the site

The page is a single HTML file with a **fixed sidebar** on the left and a **content panel** on the right — no page reloads, no external requests. Clicking a sidebar item swaps the visible section instantly.

```
┌─────────────────┬──────────────────────────────────────┐
│                  │                                      │
│   📦 anyhow      │   Article Title                      │
│                  │   breadcrumb › trail                 │
│   Getting        │                                      │
│   started        │   Prose, explained simply,            │
│   • Introduction │   followed by an annotated            │
│   • Setup        │   code block.                         │
│   • First error  │                                      │
│                  │   ┌──────────────────────────────┐    │
│   Core concepts  │   │ rust              [copy]      │    │
│   • Result type  │   ├──────────────────────────────┤    │
│   • ? operator   │   │ fn example() -> Result<()> {  │    │
│   • Context      │   │     ...                       │    │
│                  │   │ }                              │    │
│   Intermediate   │   └──────────────────────────────┘    │
│   • Downcasting  │                                      │
│   • Custom types │   💡 Callout boxes highlight tips,    │
│   • Chaining     │      warnings, and gotchas.           │
│                  │                                      │
│   Advanced       │   [ Next: following section → ]      │
│   • + thiserror  │                                      │
│   • Libs vs bins │                                      │
│   • Patterns     │                                      │
│                  │                                      │
│   Reference      │                                      │
│   • API sheet    │                                      │
└─────────────────┴──────────────────────────────────────┘
```

**Sidebar** — organized by difficulty tier (color-coded badges: 🟢 beginner, 🟠 mid, 🔴 advanced), so you always know how deep you're going before you click.

**Content panel** — each page follows the same rhythm: a short explanation in plain English, then a real, runnable code example, then (where relevant) a callout box flagging a common mistake or best practice. A "Next →" button at the bottom keeps you moving linearly if you don't want to think about navigation at all.

**Copy buttons** on every code block — one click copies the snippet to your clipboard for testing in your own `cargo` project.

---

## How the content is structured

| Tier | Pages | What you walk away with |
|---|---|---|
| **Getting started** | Introduction, Setup, Your first error | `anyhow` installed, and the three core macros (`anyhow!`, `bail!`, `ensure!`) |
| **Core concepts** | Result type, `?` operator, Adding context | The mental model: anyhow as a "type-erased box," and `.context()` as the tool that makes errors readable |
| **Intermediate** | Downcasting, Custom error types, Error chaining | How to recover specific error types from a generic `anyhow::Error`, and how chains of causes are built |
| **Advanced** | anyhow + thiserror, Libs vs binaries, Real-world patterns | The production-grade split: `thiserror` for libraries, `anyhow` for applications — plus Axum and CLI examples |
| **Reference** | API cheatsheet | A fast lookup table for macros, methods, and format strings once you've already learned the concepts |

The intent is that you could realistically read this top to bottom in under an hour, or jump straight to **Reference** once the concepts have stuck and you just need a quick reminder of `.with_context()` syntax.

---

## How to use it

1. Open `anyhow_tutorial.html` in any modern browser — no server, build step, or internet connection required.
2. Read linearly using the **Next →** buttons, or jump around using the sidebar.
3. Copy code snippets straight into a scratch Cargo project to test them as you go.
4. Keep it open as a sidebar reference while you work through your own `anyhow`-based code — it's built to be glanced at, not just read once.

---

## Design notes

The dark terminal aesthetic and monospace code blocks are intentional — built to feel like an extension of your editor rather than a marketing site. No images, no external fonts, no analytics, nothing that requires a network round-trip. The whole point is that it survives being copied to a USB stick or read on a flight.

---

## warning

I used AI as a learning assistant to explain concepts I found difficult in the official documentation, then verified examples and behavior against the official anyhow documentation and by running the code myself.

---

## Help

If you find any mistakes or outdated information, please open an issue or submit a pull request.

---

*Part of an ongoing series of self-contained crate tutorials — built to extend the official Rust Book with the practical crates (`clap`, `anyhow`, and beyond) that real projects actually depend on.*
