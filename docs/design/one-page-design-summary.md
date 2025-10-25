# Travails of AEternum — One‑Page Design Summary (Binding Atrium Vertical Slice)

## Core concept (one sentence)
A retro SNES‑style JRPG where a demon‑born champion recruits and liberates other created beings, using a pact‑exchange combat system that lets you steal, swap, and combine your makers' powers to turn the unholy pantheon against itself while choosing between destruction, redemption, or ascension.

## Design pillars
- Pact‑Exchange Combat (mechanical hook) — Battles center on Swap / Steal / Fuse actions that reassign and remix god‑granted abilities.
- Liberation as Gameplay (mechanic + narrative) — Freeing a created being changes its abilities and story, tying mechanics to theme.
- Bittersweet, Consequence‑Driven Story (tone) — Moral ambiguity: choices gain power but carry cost; victories are earned and ambiguous.
- Retro Presentation, Modern Usability (tech & scope) — 16‑bit pixel art + chiptune, tight UI, deterministic fusion rules, Clean Architecture in MonoGame (.NET 9).

## Theme
Reclaiming agency — made beings choosing their own purpose and accepting the burden of power and responsibility.

## Core gameplay loop (compact)
- Explore hub/overworld/tiled rooms and read codices.
- Encounter enemies, inspect their pacts.
- In turn‑based combat choose: Attack / Use Pact / Swap / Steal / Fuse / Item / Guard.
- Resolve turns: enemy reactions (Recall/Rebind), status updates.
- Post‑battle: loot, XP, pact acquisitions, recruitment checks.
- Return to Library hub to reassign pacts, craft simple fusions, read lore and choose next objective.

## Vertical slice (this sprint) — scope (in)
- Binding Atrium dungeon (Tiled) with 3–4 fights + Memory‑Warden boss.
- Library Reading Room hub: party screen, save, simple inventory.
- Combat: full turn loop, pact data model, Swap, temporary Steal, 1 deterministic Fuse rule.
- 4 sample pacts (incl. 1 fused result).
- 1 recruitable ally: Scribe‑11 with a short liberation scene and 2 dialogue choices that alter one ability.
- Placeholder 16‑bit art, one chiptune loop, basic SFX.
- Tutorial prompts + playtest with 3–5 players.

Out of scope (now)
- Multiplayer, full fusion matrix, large overworld, many recruitables, full endings, polished final art.

## Acceptance criteria / success metrics
- Players can complete Binding Atrium, defeat Memory‑Warden, and recruit Scribe‑11 in a 30–45 minute session.
- ≥80% of playtesters can execute Swap and Fuse after the tutorial.
- ≥80% of playtesters name pact‑exchange as the primary hook when asked.
- ≥70% notice and rate Scribe‑11’s liberation scene as meaningful (3+/5).
- No critical blocking bugs on the main path; stable demo build.

## Tech & architecture notes
- Engine: MonoGame (C#/.NET 9); Clean Architecture (Domain / Application / Infrastructure / Presentation).
- Maps: Tiled TMX (16×16 tiles, ~40×28 viewport).
- Pact model: data‑driven Pact objects (Id, Tags, Cost, BoundState, Execute delegate); Fusion function deterministic.
- Repo artifacts: core‑concept.md, vertical‑slice/README.md, vertical‑slice/scope.md, protos/battle/PactModel.cs.

## Playtest plan (quick)
- Run 3–5 structured sessions; log: time to first Swap/Fuse, completion, subjective ratings (comprehension, fun, emotional impact).
- Instrument simple runtime events (firstSwap, firstFuse, bossDefeat, recruitLiberated).

## Sprint estimate & owner
- Solo prototype: ~9–11 days (~80–90 hours).
- Owner: brianmchambers — branch: feature/vertical-slice-binding-atrium — tag: v0.1-binding-atrium upon acceptance.

## Quick checklist (pre‑sprint)
- [ ] Finalize pact list & fusion rule
- [ ] Create Trello cards & Toggl estimates
- [ ] Create sprint branch and commit scope.md
- [ ] Implement combat core + pact model
- [ ] Build Binding Atrium map & encounters
- [ ] Implement Scribe‑11 liberation scene
- [ ] Add placeholder art/audio, run playtests, collect results

Notes
Keep fusion deterministic and limited for the slice. Prioritize teachability: tutorial + clear tooltips are more important than extra content. After acceptance, expand fusion rules and recruit roster in RICE‑scored sprints.
