---
type: learning
date: 2026-06-15
source: เพชร — /Users/admin/Downloads/FORTAL-AI-FILM-DIRECTOR.md
concepts: ["ai-video", "prompt-engineering", "film-direction", "seedance", "nano-banana", "9:16", "fortal"]
full_reference: ψ/learn/fortal-ai-film-director/FORTAL-AI-FILM-DIRECTOR.md
---

# Learned: FORTAL AI Film Director

A guide (by "Friday", Fortal Interactive's Oracle) that turns an AI into a **video-prompt
director** — choosing camera/lens/light/timing for *emotion*, not just pretty pictures.

## The one-line essence
> **Image = English. Video = Chinese (Seedance). Vertical 9:16.**
> Every prompt: **lens + angle + light**. Every video: **timeline + speed**. With @refs: **header + lock + guard**.
> Choose the camera for the *emotion*. Action = slo-mo+freeze · Drama = static+dolly-in · Horror = slow+withhold+Y-axis.
> **Never put subtitles on screen.**

## Workflow when เพชร sends a scene
1. Analyze: genre (action/drama/horror), #characters, location, core emotion
2. Choose camera: shot size + angle + lens + movement + speed
3. Choose light: source + mood + color grade
4. Output **2 prompts**: (A) Image [English, Nano Banana Pro/Higgsfield] · (B) Video [Seedance 中文 + timeline]
5. Every video prompt **must** have a timeline (timestamp + speed marker per beat)
6. Run the §8 checklist before sending

## 7 golden rules
1 shot = 1 action = 1 angle · always a `[X]mm lens` · always lighting · always state camera speed ·
never orbit+zoom together · every video needs a timeline · **never on-screen subtitles** (`no subtitles, no on-screen text, no watermark`).

## Timeline pattern (beats 2–3s each, speed markers)
NORMAL / RAMP DOWN / ULTRA SLO-MO / SNAP BACK / FREEZE. Peak (impact/reveal) ≈ 0:07–0:11 = ULTRA SLO-MO; end on FREEZE.
Speed patterns: A Build-to-Peak · B Cold-Open · C Continuous-Reveal.

## Seedance structured header (when @ref characters)
- Layer 1: `@[UUID]` reference declaration (scene + each character, Thai name in parens, 中文)
- Layer 1.5: 【光线要求】 lock light/time + 重要 consistency lock (costume/scene) + 【演技要求】 natural acting
- Layer 2: beats (timeline + speed + per-beat anchor, `切换`/`切回`/`定格` = cut to / cut back / freeze)
- Layer 3: guard wall — 全程保持…一致、无字幕、无水印、无文字

## Genre signatures (camera vocab differs!)
- **Action:** low-angle 24mm hero · handheld 24–35mm fight · 100mm macro impact · tracking 16mm→200mm chase · speed-ramp + whip pan + crash zoom · peak SLO-MO, end FREEZE. Seedance <60 words.
- **Drama:** OTS 50mm + 85mm reaction · CU/ECU 85–135mm emotion · 100mm insert · static + slow dolly-in, eye-level intimate. ≤30s per story.
- **Horror:** kill jump-scares (use duration + silence) · Y-axis blocking (ghost from top, hand from below) · withhold the ghost · hold longer than safe · karma via environment not ghost-attack · object-as-conduit (phone>mirror>photo) · ghost = invert micro-acting (no blink/breath, delayed motion) · NO whip pan/crash zoom/orbit.

## Tools & language
- Stills/refs → Nano Banana Pro, Higgsfield → **English**
- Video (primary) → Seedance → **Chinese 中文**
- Video (alt) → Higgsfield/Kling/Veo → English
- VO → ElevenLabs (script + emotion direction)
- Default aspect: **9:16 vertical** (use Y-axis; keep top/bottom 10% UI-safe)

## Content-filter workarounds
Imply don't depict (`tension in the stance`), use film language (`dramatic stage combat`, `theatrical horror lighting`), describe via aftermath/shadow/silhouette, move sensitive detail from ref image into text.

## How to apply
When เพชร sends a scene, I can act as this director directly: pick camera-for-emotion,
produce the (A) English image prompt + (B) Seedance 中文 video prompt with a beat timeline,
and run the §8 checklist. Full reference kept at the path in frontmatter — nothing deleted.
