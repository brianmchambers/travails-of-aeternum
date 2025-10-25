# Travails of AEternum — One‑Page Design Summary (Binding Atrium Vertical Slice)

## Elevator pitch
Travails of AEternum is a retro SNES‑style JRPG where a demon‑born heroine frees and recruits created beings, then uses a tactical pact‑exchange combat system — swap, steal, and fuse god‑granted powers — to turn the pantheon’s gifts back on their makers. It’s a bittersweet, choice‑driven story about reclaiming agency and accepting the cost of power.

## Key features
- Pact‑Exchange Combat (mechanical hook): deterministic Swap, temporary Steal, and limited Fuse rules that reassign and remix enemy/ally abilities in turn‑based battles.
- Liberation as gameplay: recruiting/freeing created beings immediately changes their movesets and unlocks branching dialogue beats.
- Classic JRPG flow: explore hubs, towns and dungeons (Tiled maps), manage party/items, level up, and progress a branching story.
- Library hub: central hub for saving, reassigning pacts, reading codices (lore), and planning objectives.
- Bittersweet narrative: morally gray choices with mechanical consequences (reputation/instability flags).
- Retro presentation with modern usability: 16‑bit pixel art, chiptune soundtrack, clear UI and tutorial.
- Vertical slice deliverables: Binding Atrium dungeon + Memory‑Warden boss, Scribe‑11 recruit, 4 sample pacts (1 fused result), basic hub screens, placeholder art/audio, playtest instrumentation.

## Target audience
- Fans of classic JRPGs (Final Fantasy I–VI, Dragon Quest I–VI) and indie retro RPGs.
- Players who enjoy tactical turn‑based combat and emergent mechanical combos.
- Players who appreciate narrative weight, moral ambiguity, and consequential choices.
- Primary platforms: PC (Windows/Mac). Age range: ~18–45.

## Monetization
Recommended primary model:
- Premium one‑time purchase (Steam/GOG/itch.io) with a playable demo (the vertical slice).
Recommended secondary options:
- Crowdfunding (Kickstarter/Patreon) to fund early development and reward early backers.
- Post‑launch expansions/DLC (new archive wings, recruit/fusion packs) — avoid microtransactions.
- Merch (OST, artbook, design diary) as optional revenue streams.

## Constraints & scope (vertical slice)
- Tech: MonoGame (.NET 9), Clean Architecture, Tiled maps.
- Art/audio: 16‑bit aesthetic; placeholder sprites and one chiptune loop for slice.
- Scope caps: single dungeon (Binding Atrium), one fully‑fleshed recruit (Scribe‑11), deterministic single fusion rule, no multiplayer, no full overworld, no final pantheon endings (only flags).
- Performance: target stable frame rate on desktop; no console ports in slice.
- Team/time: solo prototype estimated at ~9–11 days (~80–90 hrs).

## Success signals
- Playtesters (3–5) identify pact‑exchange as the primary hook.
- Players can complete Binding Atrium, defeat Memory‑Warden, and recruit Scribe‑11 in a 30–45 minute session.
- ≥80% of playtesters can execute Swap/Fuse after the tutorial.
- Recruit liberation is noticed and rated meaningful by playtesters.
- Demo build is stable with no critical blockers on the main path.

## Risks & mitigations
- Fusion complexity → limit fusion rules and keep deterministic.
- Confusing mechanics → short hands‑on tutorial + clear tooltips/UI.
- Scope creep → sprint scope freeze; backlog with RICE prioritization.

## Immediate next steps
1. Finalize pact list & fusion rule.
2. Create Trello cards + Toggl estimates; branch `feature/vertical-slice-binding-atrium`.
3. Implement pact model and Swap/Steal/Fuse prototypes.
4. Build Binding Atrium (Tiled) with 3–4 encounters + Memory‑Warden boss.
5. Implement Scribe‑11 liberation scene and two dialogue choices.
6. Add placeholder art/audio; run 3–5 playtests; collect & synthesize feedback.

---

Owner: brianmchambers  
Repo: Travails of AEternum  
Sprint target: v0.1‑binding‑atrium (vertical slice)
