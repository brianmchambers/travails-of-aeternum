# Travails of AEternum — Short Game Design Document

High-level: Travails of AEternum is a retro (SNES/NES-style) top-down JRPG built in MonoGame (.NET 9). Maps designed in Tiled. Code follows Clean Architecture (Core domain, Gameplay, Presentation, Infrastructure). Development tracked in Toggl and Trello; site/blog on GitHub Pages.

---

## Elevator Pitch
A small-town apprentice and an unlikely band of allies must restore a fractured world by chasing down shards of a broken relic—facing moral choices, hidden loyalties, and the consequences of restoring power to a forgotten god.

---

## Core Pillars
- Feel of classic 16-bit JRPGs: tactical, deliberate combat and exploration.
- Tight modular code enabling rapid iteration and content authoring (Tiled maps + scriptable events).
- Player-facing choices that slightly alter story/party composition without branching into many separate endings.

---

## Systems

### Movement & World Exploration
- Top-down, tile-based movement (4-directional).
- Maps authored in Tiled:
  - Collision layers define walkable areas.
  - Event objects (NPC spawn, triggers, chest, cutscene zones).
  - Multiple layers for parallax/decoration.
- Movement features:
  - Walk / Run toggle (Hold B to run).
  - Interact (A) and Cancel/Menu (Start).
  - Smooth pixel movement with sub-tile offsets to preserve retro look while feeling modern.
  - Overworld encounters:
    - Visible monsters on most maps (preferred). Random encounter override on specific zones (caves, fog banks).
    - Stepping into enemy sprite triggers battle; walking near triggers conditional events (ambushes, fleeing).
- Map streaming: Load adjacent Tiled maps seamlessly for larger regions.

Implementation note (architecture):
- Presentation layer reads Tiled JSON and converts to domain map objects via Infrastructure adapter.
- Collision and pathfinding logic live in Gameplay/Core modules.

### Combat
- Turn-based, party-of-up-to-4, side-view battle screen (classic SNES JRPG layout).
- Combat flow:
  - Encounter -> Battle init -> Party & enemy sprites on screen -> Player selects actions -> Actions resolve in phase order.
- Turn sequencing:
  - Hybrid ATB-lite: each combatant has a Speed stat; every turn each character gets one action per "round". Higher Speed gives earlier action order each round and small chance for follow-up.
  - Initiative order computed at round start: Initiative = base + floor(Speed / 4).
- Actions:
  - Attack (weapon), Skill (consumes MP or item cooldown), Item, Defend, Run (chance depends on enemy), Tactical actions (Guard Break, Stagger).
- Positioning:
  - No grid inside battle, but a simple front/back row affects damage received and some skills target specific rows.
- Status effects:
  - Standard (Poison, Sleep, Paralyze, Burn, Freeze, Confused) + Light tactical states (Staggered, Weakened, Enraged).
  - Durations measured in rounds.
- Damage formula (simple, tunable):
  - Damage = max(1, floor((Atk * SkillPower)/(Def * 0.5)) + random(-2..2))
- Enemy design:
  - Encounters tuned for pacing — avoid long grind fights early.
  - Mini-bosses introduce mechanics (force players to use status removal, swap formation, etc.)

### Progression
- Core progression:
  - XP -> Levels. Each level grants stat points and unlocks skill nodes.
  - Equipment: Weapons/Armor with simple stat modifiers and occasional special effects (life-steal, status resist).
- Skill system:
  - Job-lite + node tree per character archetype.
  - Characters have a default class and can unlock 1 secondary specialty mid-game (e.g., Apprentice -> Spellblade or Alchemist).
- Currency & economy:
  - Gold for equipment and consumables.
  - Crafting: basic synthesis system (combine items at shops / camp).
- Side progression:
  - Reputation with factions (affects some NPC behavior and quest availability).
  - Relic shards: collectible progression items that open story beats and unlock late-game systems.
- Save system:
  - Slots + autosave at key points (inns, major events).
  - Quick save limited to out-of-combat.

---

## Major Characters

- Aet (Protagonist)
  - Role: Young apprentice blacksmith, 17.
  - Archetype: Balanced physical attacker, latent affinity for ancient magic bound to the relic.
  - Motivation: Find out why his village was silenced and restore what was lost.
  - Growth: Learns to fuse smithcraft and magic (Spellblade path).

- Mira
  - Role: Traveling scholar and magic-user, mid-20s.
  - Archetype: Ranged mage/support.
  - Motivation: Study the relic's history; cautious and analytical.
  - Hook: Knows fragments of ancient language; key to unlocking relic shards.

- Rowan
  - Role: Exiled knight, late-20s.
  - Archetype: Tank, defensive leader.
  - Motivation: Redemption and to find evidence to clear his name.
  - Hook: Has ties to the antagonist faction.

- Lio
  - Role: Streetwise rogue/merchant, 15.
  - Archetype: Speed/utility.
  - Motivation: Money and thrill; slowly softens toward party.
  - Hook: Access to black-market goods and shortcuts.

- The Warden (Antagonist)
  - Role: Regional enforcer for the Dominion, commander of shard-hunters.
  - Motivation: Restore order by reassembling the relic to cement Dominion rule.
  - Hook: Charismatic, believes ends justify means; morally ambiguous.

- Supporting:
  - Old Master Haru (mentor)
  - Mayor Celene (village leader)
  - Spirit of AEternum (mysterious entity tied to relic; appears in visions)

---

## Story Beats (High-level)

Act I — Spark
- Opening: Village festival interrupted by a shard storm; Aet witnesses relic fragment fall and villagers go missing.
- Inciting Incident: Master Haru is taken; party forms to investigate.
- Midpoint: Party recovers first shard — a vision hints at AEternum’s past. Dominion forces take interest.

Act II — Journey & Discovery
- Travel across several regions (forest, mine, frost plateau).
- Introduce party members (Mira, Rowan, Lio) via localized arcs.
- Sidequests build faction reputation and reveal Warden’s methods.
- Mid-game Twist: The relic's power is alive — reassembling it will awaken an agency that neither side fully controls. A morally gray choice appears: use relic to restore lost lives or seal its power.

Act III — Confrontation & Choice
- Party collects final shards, faces corrupted vestiges and Dominion's elite.
- Final boss duel against The Warden; reveal his motives and a deeper manipulator (a remnant spirit).
- Resolution branches (small variations):
  - Reforge & Release: Restores some, but awakens spirit — world changes in tone.
  - Seal & Lose: World remains imperfect but stable; some losses become poignant.
  - Partial: Compromise ending with unique epilogue scenes for party members.

Epilogue
- Scenes showing aftermath based on choices: rebuilt village, reputation changes, which NPCs survive, a closing journal entry by Aet.

---

## Quests & Pacing
- Main quest focused and linear with open side-content pockets.
- Major dungeons ~ 2–4 per act with puzzle/floor mechanics.
- Sidequests: 20–30 small quests (fetch, escort, puzzles) that reward items, XP, or story tidbits.
- Estimated playtime: 12–18 hours for main; 20–30 hours completionist.

---

## UI / UX Sketches (textual + ASCII)

Notes: Inputs map to gamepad (D‑pad, A = confirm, B = cancel, Start = menu, Select = quick options). Keyboard/Mouse support mirrors these.

1) Overworld HUD
- Minimal: Top-left = HP/MP party snapshot; bottom-right = minimap (small), top-right = time/day indicator.
- Interact prompts appear contextually (speech bubble icon with A).

ASCII mockup:
```
+------------------------------+------------------+
| HP/MP: Aet 45/12  Mira 30/20 |  Day 03  12:30   |
| Rowan 60/05  Lio 28/10       |  [minimap]       |
+------------------------------+------------------+
```

2) Main Menu (Start)
- Vertical choices: Inventory, Equipment, Skills, Quests, Save/Load, Settings.
- Right panel: Context preview (selected item or character stats).

ASCII mockup:
Main Menu
> Items
  Equipment
  Skills
  Quests
  Save
  Settings

[Right panel]
Selected Item: Potion
Effect: Restores 50 HP
Value: 15G

3) Battle Screen
- Left: Party sprites (stacked vertically), Right: Enemies.
- Bottom: Command box with four options or skill list; Top-right: Turn order strip (icons).
- Dialog box for combat text.

ASCII mockup:
```
------------------------------------------------
| Party         |                 Enemies     |
| Aet  [sprite] |  1. Goblin  [sprite]        |
| Mira [sprite] |  2. Wolf    [sprite]        |
| Rowan[sprite] |  3. Brute   [sprite]        |
| Lio  [sprite] |                             |
------------------------------------------------
| Commands: Attack  Skill  Item  Defend         |
| [Skill submenu displays when selected]        |
------------------------------------------------
| Turn Order: [Aet][Goblin][Mira][Wolf][Rowan]  |
------------------------------------------------
```

4) Inventory / Equipment
- Grid for items; equip screen shows current vs selected item stats; quick compare highlight.

5) Dialogue & Choices
- Dialogue box at bottom, name tag top-left of box.
- Choice UI: short list with highlighted selection; consequences preview if applicable (e.g., reputation +2).

---

## Audio & Visual Direction
- Pixel art, 16-bit color palette.
- Animations: limited frame counts for retro feel but crisp input responsiveness.
- Music: chiptune orchestral blends, leitmotifs for characters and regions.

---

## Technical / Dev Notes
- Tiled maps exported to JSON; a map-importer in Infrastructure converts to runtime scenes.
- Encounter & enemy data driven by JSON/Scriptable-like data (no hardcoded monsters).
- Clean Architecture modules:
  - Core (domain models: Character, Item, CombatEngine)
  - Gameplay (systems: BattleSystem, ProgressionSystem, MapSystem)
  - Presentation (MonoGame renderers, UI)
  - Infrastructure (Tiled importer, file I/O, save system)
- Unit-testable CombatEngine with deterministic RNG mode for testing.
- Telemetry: Toggl entries for task timing; Trello for milestone tracking; CI placeholder workflows exist in repo.

---

## Metrics & Success Criteria
- Combat feels responsive and balanced: average battle time 30–90s.
- Players reach mid-game (Act II) within ~4–6 hours.
- Fewer than 10 reported game-breaking bugs prior to release; consistent save reliability.

---

## Next Steps (MVP)
1. Implement core movement, Tiled importer, and map streaming.
2. Build CombatEngine with basic Attack/Skill/Item/Defend.
3. Create first dungeon, two sidequests, and 3 major characters (Aet, Mira, Rowan).
4. Basic UI templates and input mapping.
5. Playtest loop; tune XP curve and encounter design.

---

Authorship / Context
- Document tailored for Travails of AEternum development in MonoGame/.NET 9 with Tiled maps. This is a concise GDD to guide the early production sprint.
