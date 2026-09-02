# WSJT-X Improved JP1LRT Edition

🌐 **Languages:** English | [日本語](https://github.com/jp1lrt/wsjtx-avelag/blob/main/README_ja.md)

[![Status](https://img.shields.io/badge/status-Public%20Release%20Candidate-orange)](https://github.com/jp1lrt/wsjtx-avelag/releases/tag/20260901A-REB522-P6)
[![Current release](https://img.shields.io/badge/release-20260901A--REB522--P6-blue)](https://github.com/jp1lrt/wsjtx-avelag/releases/tag/20260901A-REB522-P6)
![User Guide](https://img.shields.io/badge/User%20Guide-Edition%201.8%20%7C%2016%20languages-brightgreen)

**A JTDX-inspired operating layer for WSJT-X Improved — preserving the original capabilities while adding smarter CQ RUN, Wanted/Hunting, safer QSO transitions, and operator-focused FT8/FT4 workflow.**

> **Current Public Release Candidate:** `20260901A-REB522-P6 / P6-AL`  
> **Base:** WSJT-X Improved `3.1.0 / 260522` (22 May 2026)  
> **This is not a WSJT-X Improved 3.2.0-based release.**

**Latest release:**  
https://github.com/jp1lrt/wsjtx-avelag/releases/tag/20260901A-REB522-P6

---

## Why JP1LRT Edition exists

I am **Yoshi / JP1LRT**, an **authorized JTDX beta tester** and a contributor responsible for **Japanese localization**.

In everyday FT8/FT4 operation, I had become very comfortable with the JTDX operating philosophy — especially its CQ RUN workflow, priority-based caller selection, Wanted-station handling, and the way the operator can keep control while still using automation.

Then WSJT-X 3.0 appeared, followed by WSJT-X Improved 3.1.

I started reading and analyzing the source code, and I became deeply impressed by the newer decoder architecture and the practical decoder improvements that had been added to WSJT-X Improved.

That led to a very simple idea:

> **What if I could use the WSJT-X Improved decoder and platform, but operate it in a way that feels much more like JTDX?**

That idea became **WSJT-X Improved JP1LRT Edition**.

### It actually started with Avg/Lag

The project did not begin as a large-scale attempt to redesign operating logic.

The **first JP1LRT modification was Avg/Lag** — a timing aid that observes received decode `DT` values and presents a robust average and cycle-boundary lag indication in the status area.

That small experiment became the starting point.

From there, the project gradually expanded into internal logical-time Sync support, CQ RUN and AutoSeq ownership logic, Wanted/Hunting, safer manual takeover, Terminal Hold, DF handling, directed-CQ safeguards, expanded callsign data, diagnostics, and the other operating features now found in P6 / P6-AL.

So the current edition grew organically from a simple practical question:

> **Can I make the information and operating flow I want during everyday FT8/FT4 operation available directly inside WSJT-X Improved?**

The goal is **not** to turn WSJT-X Improved into JTDX, and not to remove or replace the capabilities that already exist in WSJT-X / WSJT-X Improved.

Instead, JP1LRT Edition tries to:

- **keep what already works,**
- **preserve the original WSJT-X Improved capabilities,**
- and **add a JTDX-inspired operating layer on top of them.**

The JP1LRT modifications do **not** replace or retune the FT8 decoder core. The main work is in the operating logic around it: CQ RUN selection, Wanted/Hunting, QSO ownership and handoff, terminal-message protection, manual intervention, DF behavior, diagnostics, and related workflow improvements.

### The decoder analysis that inspired this project

I also wrote a long-form source-based article about the WSJT-X Improved 3.1 decoder and why it caught my attention:

**Understanding FT8 Decoder Settings in WSJT-X 3.1 improved**

The decoder-analysis article is now available in **16 languages**:

[🇬🇧 English](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_en.html) | [🇯🇵 日本語](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_ja.html) | [🇫🇷 Français](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_fr.html) | [🇩🇪 Deutsch](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_de.html) | [🇪🇸 Español](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_es.html) | [🇨🇳 简体中文](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_zh-cn.html) | [🇹🇼 繁體中文](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_zh-tw.html) | [🇰🇷 한국어](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_ko.html) | [🇵🇹 Português](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_pt.html) | [🇮🇹 Italiano](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_it.html) | [🇳🇱 Nederlands](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_nl.html) | [🇷🇺 Русский](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_ru.html) | [🇵🇱 Polski](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_pl.html) | [🇹🇷 Türkçe](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_tr.html) | [🇸🇪 Svenska](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_sv.html) | [🇮🇩 Bahasa Indonesia](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_id.html)

The article looks at Decode Start, staged decoding, the STD/MTD relationship, CPU allocation inside the FT8 cycle, and practical decoder tuning.

---

## What makes JP1LRT Edition different?

JP1LRT Edition is designed around **real operating flow**.

The priority is not simply to add more buttons or more automation. The goal is to make automatic operation **predictable**, while protecting the operator's intent and the state of an active QSO.

### Key operating ideas

- **Avg/Lag and optional internal Sync — where the project started**  
  Avg/Lag derives timing information from received decode `DT` values. `Avg=` shows a robust average of usable DT values, while `Lag=` provides a signed cycle-boundary timing indication. It is a status/timing aid and does **not** modify the FT8 decoder core. The later optional internal Sync function grew from this timing work.

- **AutoSeq 2 / AutoSeq 3**  
  Priority-based CQ RUN caller selection inspired by the operating style familiar to JTDX users.

- **Wanted / Hunting**  
  Wait for Wanted callsigns, prefixes, grids, or other configured targets and acquire them when conditions are safe.

- **Wanted-Pounce no-reply return to Hunting (P6)**  
  A Hunting-origin QSO that receives no continuing response after exactly three transmitted reports does not send a fourth report and does not drift into automatic CQ. The program safely returns to Hunting standby while keeping Wanted Pounce armed.

- **Terminal Hold**  
  Keeps QSO ownership through RR73 / 73 handling and the protected terminal phase, helping prevent premature clearing or unsafe target handoff.

- **Safe manual takeover**  
  Manual operator action has priority, but protected transmissions are allowed to finish before the new target is applied.

- **Active-QSO protection**  
  A third-party decode should not overwrite the station that is already in progress.

- **Best S&P language-independent selection**  
  New Call on Band and New DXCC selection uses stable internal category identifiers rather than translated display strings.

- **LoTW tie-break**  
  When otherwise equivalent candidates remain, LoTW status can be used as a tie-break.

- **Directed-CQ safety**  
  Automatic acquisition has explicit safety rules for `CQ DX` and canonical regional CQs.

- **Orange Wanted vs. Blue display-only highlighting**  
  Orange can participate in automatic Wanted / priority behavior. Blue is available for visual highlighting without becoming an automatic Wanted target.

- **Quick Call OFF remains meaningful**  
  Best S&P may prepare the target, DX Call, DX Grid, and transmit message without automatically beginning transmission.

- **JTDX-inspired Band Activity / Activity Window display**  
  The activity display was expanded so useful station attributes can remain visible not only on CQ lines, but also on ordinary QSO traffic such as reports, `RRR`, `RR73` and `73`. This makes the window much closer to the information-dense operating view I was accustomed to in JTDX.

- **Explicit LoTW-user indication**  
  When current LoTW-user data is available, LoTW users are marked explicitly in the activity display. Country/entity, worked/B4 state, Wanted/highlight status and other station attributes can also be shown without depending on the line being a CQ.

- **Improved Wide Graph readability**  
  The Wide Graph / waterfall display was refined for practical everyday use. Contrast uses JTDX-derived median-noise normalization, with **Gain -11 / Zero 7** as practical starting values. I also corrected the Wide Graph layout so the clock text is no longer clipped and remains properly readable.

- **High-precision own-station Grid Locator**  
  Up to 10 characters can be entered for reporting and services that can use higher locator precision.

- **Expanded `ALLCALL7.TXT` support**  
  The original ALLCALL7 handling was expanded to a **250,000-entry-class capacity**.  
  The P6 / P6-AL package currently includes an `ALLCALL7.TXT` dataset containing **218,100 unique callsigns**.  
  This substantially broadens local callsign lookup and the related display/classification functions. It does **not** modify the FT8 decoder or over-the-air messages.

- **Detailed diagnostics**  
  Optional JP1LRT diagnostic information can be recorded in `ALL.TXT` to help reproduce and analyze difficult operating-state problems.

This is deliberately an **additive** design: the intention is to enhance everyday FT8/FT4 operation without taking away the normal WSJT-X Improved operating capabilities.

---

## How the project grew

The release history shows that JP1LRT Edition was **not designed all at once**. It grew very quickly from one practical timing aid into a broader JTDX-inspired operating environment.

### April 2026 — the project takes shape

1. **6 April — Avg/Lag was the starting point (`v20260406`).**  
   The first published JP1LRT build was the **Avg/Lag display patch**.

2. **7 April — Avg/Lag/Sync (`v20260407`).**  
   The timing experiment expanded into Avg/Lag plus internal logical-time Sync.

3. **8 April — the Wide Graph / waterfall became part of the project (`v20260408`).**  
   JTDX's `scale_by_median()` normalization was ported to improve waterfall contrast, the gain calculation was changed toward the JTDX behavior, and numeric Gain/Zero tooltips were added.

4. **9 April — AutoSeq 2/3 and priority-based CQ operation (`v20260409`).**  
   AutoSeq 2 and AutoSeq 3 were added, together with priority-based station selection. Non-CQ message coloring was also extended in a JTDX-like direction.

5. **9 April evening — JTDX-style display and large `ALLCALL7.TXT` support (`v20260409b`).**  
   This was an important early expansion, not a late addition. The release added:
   - attribute-oriented highlighting for non-CQ lines,
   - an explicit **LoTW `●` marker**,
   - improved Fox/Hound / MSHV composite-message presentation,
   - current-DX-Call row emphasis,
   - Wide Graph identification,
   - and **larger `ALLCALL7.TXT` array/read support**.  
   The following `v20260409c` repack restored the full ALLCALL7 dataset when the preceding package was found incomplete.

6. **11 April — standalone packaging and project identification (`v20260411b`).**  
   The Windows package became self-contained and the modified build gained explicit PSK Reporter / title-bar identification.

7. **13 April — CQ RUN became a real operating system (`v20260413`).**  
   Automatic next-station CQ RUN handoff was introduced, together with ADIF snapshot protection and stronger manual/AutoSeq ownership safeguards. The `ALLCALL7.TXT` implementation was further expanded to a **250,000-entry-class capacity**; the release notes record a 210,981-entry dataset at that stage.

8. **17–28 April — terminal-message and target-selection hardening.**  
   RR73/73 duplicate-transmission problems, stale candidates, manual-target ownership and double-click corner cases were investigated and fixed.  
   On **27 April (`v20260427B`)**, Wanted callsign/prefix/grid priority was added to AutoSeq / CQ RUN.

### May 2026 — Wanted/Hunting becomes a major theme

9. **25–27 May — Wanted Pounce / Hunting and color-action separation.**  
   The `v20260525A–G` line developed aggressive Wanted pounce, stale timeout and return-to-Hunting behavior.  
   `v20260527C` then separated the roles clearly:
   - **Orange** = display + Wanted / AutoSeq / pounce action
   - **Blue** = display-only highlighting

10. **29 May — FT4 late-pick and target DF following (`v20260529D`).**  
    AutoSeq 2 late-pick support was extended to FT4, and Rx DF could follow a target's decoded DF while calling without moving Tx DF.

### June 2026 — QSO ownership and terminal safety are hardened

11. **June — Terminal Hold, terminal arbitration and manual-takeover safety.**  
    Development concentrated on protecting the active QSO through RR73/73, preventing stale ownership and unsafe next-target handoff, and defining safe behavior when the operator intervenes manually.

12. **Late June — Rx DF / Terminal Hold interaction.**  
    The RXDF1/RXDF2 line refined when Rx DF may return to Tx DF and explicitly prevented premature Rx-marker restoration while Terminal Hold was still active.

### July 2026 — Standard and AL become parallel builds

13. **July — further active-QSO, stale-target and manual-takeover protection.**  
    The operating logic continued to be hardened from tester feedback.

14. **22 July line — Standard and AL GUI builds.**  
    The project formally distributed the same core logic in:
    - **Standard GUI** — WSJT-X Improved PLUS-style
    - **AL GUI** — AL_PLUS / JTDX-like layout  
    The first multilingual User Guide series was also published in English, Japanese, German and Spanish.

### August–September 2026 — Public RC maturation

15. **August — higher-precision Grid, directed-CQ safety and release-line consolidation.**  
    The GL10/RCQ work added direct higher-precision own-grid support while preserving mode-safe transmitted locator lengths, and automatic acquisition gained explicit `CQ DX` / regional-CQ safety gates.

16. **August — REB522 / P3→P5 Public-RC line.**  
    The accumulated work was rebased and consolidated into the JP1LRT Edition release line. Best S&P language-independent selection and Return-to-Hunting behavior were among the later refinements.

17. **1 September — P6 / P6-AL.**  
    P6 added the current Wanted-Pounce no-reply rule: after exactly three unanswered reports, no fourth report and no automatic CQ are sent; the program safely returns to Hunting. User Guide Edition 1.8 subsequently reached **16 languages**.

What began as a small **Avg/Lag display experiment** therefore grew, step by step, into an attempt to combine the **decoder/platform I liked in WSJT-X Improved** with the **operating flow and information density I was accustomed to in JTDX**.

---

## Display improvements for everyday operation

Not all JP1LRT changes are about automation or QSO state machines.

A major part of the project has also been making the information on screen easier to use during real operating.

### Band Activity / Activity Window

I wanted the activity display to feel closer to JTDX.

In the JP1LRT Edition, useful station attributes are not limited to CQ lines. They can remain visible across ordinary QSO traffic as well — including report exchanges, `RRR`, `RR73` and `73`.

Depending on the available data files and settings, the display can show or emphasize information such as:

- **LoTW-user status**
- country / DXCC entity
- worked / B4 status
- Wanted and highlight status
- current-target emphasis
- other station attributes used by the JP1LRT display/classification logic

This means the operator does not lose useful station context simply because the decoded line is part of an ongoing QSO rather than a CQ.

The explicit **LoTW-user marker** is particularly useful because LoTW status is also used as a tie-break in parts of the JP1LRT candidate-selection logic.

### Wide Graph / waterfall

The Wide Graph was also adjusted for better readability.

The waterfall contrast uses **JTDX-derived median-noise normalization**, and **Gain -11 / Zero 7** are practical starting values for the JP1LRT Edition.

The Wide Graph layout itself was refined as well. In the upstream layout, the clock text could be partially clipped; the JP1LRT layout was adjusted so the clock remains fully visible and easier to read during normal operation.

These are small UI changes compared with AutoSeq or Terminal Hold, but they are part of the same design philosophy:

> **Make the information the operator actually needs easier to see while operating.**

---

## Expanded ALLCALL7.TXT callsign database

JP1LRT Edition also expands support for the local `ALLCALL7.TXT` callsign database.

This is actually one of the **early JP1LRT modifications**. Large-ALLCALL7 support appeared in the **9 April 2026 `v20260409b`** release, where the array sizes and read limits were enlarged to accept substantially larger datasets. The following package update also restored the complete dataset after an incomplete package was detected.

By `v20260413`, the internal callsign arrays and `MAXC` had been expanded to a **250,000-entry class**, with the release then documenting **210,981 entries**.

The current P6 / P6-AL distribution contains **218,100 unique callsigns**.

This larger dataset improves the coverage of local callsign lookup and the display/classification functions that depend on that information.

`ALLCALL7.TXT` is a supporting local data file. Expanding it does **not** change the FT8 decoder itself, transmitted FT8/FT4 messages, AutoSeq QSO-ownership protections, or PSK Reporter behavior.

For the P6 / P6-AL packaged dataset:

`SHA-256: 676f1a402ead5944fccd88656427ae9f016dfdfa58b7fdc3c8e0b7ac88033b18`

Keep `ALLCALL7.TXT` beside `wsjtx.exe`.

---

## Current release: P6 / P6-AL

| Item | Current value |
|---|---|
| Release | `20260901A-REB522-P6 / P6-AL` |
| Status | **Public Release Candidate** |
| Base | WSJT-X Improved `3.1.0 / 260522` |
| Base date | 22 May 2026 |
| User Guide | Edition 1.8 |
| Guide languages | **16** |
| Windows builds | Standard GUI / AL GUI |
| Source | Complete source bundles provided |

### Standard and AL

Both builds contain the same current QSO, AutoSeq, Wanted/Hunting, Terminal Hold, manual-takeover safety, Best S&P, and directed-CQ safety logic.

Their principal difference is the **GUI layout**.

**Do not extract Standard and AL into the same directory.**

---

## P6 highlight — Wanted-Pounce no-reply handling

P6 improves an important edge case in Hunting.

When a QSO was started by Wanted Pounce / Hunting and the partner does not continue after exactly three transmitted reports:

- no fourth report is transmitted,
- CQ is not started automatically,
- Auto Tx stops,
- DX Call is cleared,
- the program returns to Tx6 / CALLING,
- Wanted Pounce remains armed,
- orange Hunting standby is restored,
- accumulated AutoSeq candidates are preserved,
- and the same Wanted station can be acquired again later as a new QSO.

If a valid response such as **RR73** arrives immediately after report #3, normal QSO completion takes priority:

**final 73 → Terminal Hold → normal return to Hunting**

Normal `CQ: First` and normal AutoSeq 2 CQ RUN no-progress behavior remain separate and unchanged by this P6-specific Hunting return path.

---

## Download and SHA-256

### Windows GUI packages

| Build | File | SHA-256 |
|---|---|---|
| Standard GUI | `WSJT-X_20260901A-REB522-P6_win64.zip` | `d69ef54fb7d10feb3a7bc9620497eda8ec40c700f08f4d5302e8e016a02e992b` |
| AL GUI | `WSJT-X_20260901A-REB522-P6-AL_win64.zip` | `658db59666b89ae4884365e5ba55087b234b29aaa0cf7950fee80fcb2ab800e7` |

### Source bundles

| Build | File | SHA-256 |
|---|---|---|
| Standard source | `WSJT-X_20260901A-REB522-P6_source_bundle.zip` | `86e53df77bacaa93fc16bed15aec8e8ae1529231df16873486dacdb619803e2c` |
| AL source | `WSJT-X_20260901A-REB522-P6-AL_source_bundle.zip` | `8ecb9f4d6ec4763a2eb03f7d33a1971466263b7435a7efc491e56b8365a1c1f4` |

Corresponding `.sha256` sidecar files are provided with the release assets.

**Download:**  
https://github.com/jp1lrt/wsjtx-avelag/releases/tag/20260901A-REB522-P6

---

## User Guide Edition 1.8 — 16 languages

The P6 / P6-AL User Guide is available in:

- 🇯🇵 Japanese
- 🇬🇧 English
- 🇫🇷 French
- 🇪🇸 Spanish
- 🇩🇪 German
- 🇨🇳 Chinese — Simplified
- 🇹🇼 Chinese — Traditional
- 🇰🇷 Korean
- 🇵🇹 Portuguese
- 🇮🇹 Italian
- 🇳🇱 Dutch
- 🇷🇺 Russian
- 🇵🇱 Polish
- 🇹🇷 Turkish
- 🇸🇪 Swedish
- 🇮🇩 Indonesian

The English Edition 1.8 is the semantic master for the multilingual guides.

The guides cover installation, Standard / AL differences, AutoSeq 2/3, Wanted/Hunting, Terminal Hold, manual takeover, Best S&P, DF behavior, diagnostics, known limitations, and Public RC precautions.

All current guide files are available from the P6 release page:

https://github.com/jp1lrt/wsjtx-avelag/releases/tag/20260901A-REB522-P6

---

## Public RC precautions

P6 / P6-AL are **Public Release Candidates**, not GA/stable releases.

For initial testing:

1. Keep your known-good installation.
2. Extract JP1LRT Edition into a **new, separate folder**.
3. Do not mix Standard and AL files.
4. Use a separate `--rig-name` profile when testing alongside another build.
5. Back up your settings and logs.
6. Verify callsign, grid, rig, PTT, audio, reporting, and logging settings.
7. Monitor the generated Tx message, selected DX Call, and Auto Tx state.
8. Do not use the Public RC for unattended or unmonitored operation.
9. Stop transmission immediately if anything unexpected occurs.

Automatic selection does not remove the operator's responsibility for transmitted messages or regulatory compliance.

---

## Known limitations / areas still under investigation

P6 does **not** claim to have solved every existing issue.

Current known items include:

- Prefix-form slash calls such as `F/DB6LL` remain an incomplete RR73 area and should be monitored carefully.
- An intermittent `jt9.exe` SIGSEGV remains a separate unresolved investigation item.
- A reported issue involving **“Highlight also messages with 73 or RR73”** remains under investigation.
- With `--language=es`, some newly added untranslated UI strings may appear in Japanese instead of English because of existing translator-stacking behavior. This does not affect QSO logic or transmitted messages.
- Fox/Hound is not the primary modification/test scope.
- Do not assume that every FT8/FT4 protection or score-mode rule applies identically to MSK144 or other modes.

A Public RC validation result does **not** mean that every mode, setting combination, or boundary condition has been exhaustively exercised.

---

## Reporting a problem

If you find unexpected behavior, please include as much of the following as possible:

- Standard or AL build
- complete version identifier from the title bar
- Windows version
- mode and relevant settings
- whether Wanted Pounce / Hunting was armed
- Quick Call ON/OFF
- event time in UTC
- expected behavior
- actual behavior
- relevant `ALL.TXT` excerpt
- screenshot when useful
- `wsjtx_log.adi` excerpt when applicable

For diagnostic reproduction, enable the JP1LRT diagnostic recording option described in the User Guide.

Please review logs before sharing them publicly. They may contain callsigns, locators, frequencies, timestamps, and internal operating state.

---

## Development background and related reading

### Decoder analysis — 16 languages

**Understanding FT8 Decoder Settings in WSJT-X 3.1 improved**

[🇬🇧 English](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_en.html) | [🇯🇵 日本語](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_ja.html) | [🇫🇷 Français](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_fr.html) | [🇩🇪 Deutsch](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_de.html) | [🇪🇸 Español](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_es.html) | [🇨🇳 简体中文](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_zh-cn.html) | [🇹🇼 繁體中文](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_zh-tw.html) | [🇰🇷 한국어](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_ko.html) | [🇵🇹 Português](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_pt.html) | [🇮🇹 Italiano](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_it.html) | [🇳🇱 Nederlands](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_nl.html) | [🇷🇺 Русский](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_ru.html) | [🇵🇱 Polski](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_pl.html) | [🇹🇷 Türkçe](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_tr.html) | [🇸🇪 Svenska](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_sv.html) | [🇮🇩 Bahasa Indonesia](https://www.asahi-net.or.jp/~vj5y-tkur/ft8/wsjtx_31improved_article_id.html)

---

## Upstream projects and acknowledgement

JP1LRT Edition exists because of the work done by the upstream amateur-radio software communities.

- **WSJT-X**  
  https://wsjtx.sourceforge.io/

- **WSJT-X Improved by Uwe Risse / DG2YCB**  
  https://sourceforge.net/projects/wsjt-x-improved/

- **JTDX**  
  https://sourceforge.net/projects/jtdx/

JP1LRT Edition is an **independently modified edition**. It is not an official release of WSJT-X, WSJT-X Improved, or JTDX.

The project is based on the GPL-licensed WSJT-X / WSJT-X Improved code lineage. Complete source bundles are published with the binary releases; consult the source bundle and included license/copyright notices for the applicable terms.

My sincere thanks go to the original WSJT-X authors and contributors, Uwe / DG2YCB and the WSJT-X Improved community, and the JTDX developers and testers whose work and operating ideas made this project possible.

---

## About JP1LRT

**Yoshi / JP1LRT**

- Amateur radio operator since 1983
- Authorized JTDX beta tester
- JTDX Japanese localization contributor
- Developer / maintainer of WSJT-X Improved JP1LRT Edition

My main interest is not automation for its own sake.

It is making FT8/FT4 operation more predictable and practical:

> Protect the active QSO.  
> Protect terminal handling.  
> Respect deliberate manual operator action.  
> Select the next station intelligently.  
> And when the operator chooses to wait for a Wanted station, return to that state correctly.

73,  
**[Yoshi / JP1LRT](https://www.qrz.com/db/JP1LRT)**
