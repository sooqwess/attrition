# Changelog

All notable changes to Attrition. Dates are in ISO format.
The datapack and the resource pack share one version number — keep them in step.

---

## 3.1.0 — Triage — 2026-08-14

Everything since 3.0.0, gathered by theme rather than by patch. Saves from 3.0.x
carry over and no configuration changes are needed.

### At a glance

| | 3.0.0 | 3.1.0 |
|---|---|---|
| Functions | 414 | 439 |
| Advancement files | 211 | 214 (198 in-game + 16 internal triggers) |
| Custom items | 20 | 27 |
| Custom recipes | 22 | 25, all unlocked in the recipe book |
| Localisation strings | 376 | 518 |
| Locales | 69 machine-translated | 69 hand-translated |
| Config keys | 78 | 79 |
| Item textures | 25 | 27 |

### The pack tells you what is killing you

The headline change. In 3.0.0 you died without learning why.

- Action bar names the cure: *Bleeding — craft a Bandage*, and with one in hand,
  *Hold still and SNEAK to bind the wound*. Same for fractures.
- **Body temperature is on the HUD**, in all three variants. It used to live three
  menu clicks away while freezing damage began at 5 — deaths looked arbitrary.
- **A nine-page Field Manual** is handed to you on first join: threat, Gloom,
  temperature, thirst, wounds, the cost of dying and of the totem, menu and presets.
- **The Gloom ritual is discoverable.** Glowstone dust in hand, standing on a block
  of gold, sneak. It clears the Gloom floor — the one thing rest cannot undo. The
  ritual shipped in 3.0 and nothing in the game ever mentioned it. The pack now says
  when the floor is holding you down, and it is in the tips and the manual.
- Contract rewards are itemised line by line instead of applied silently.

### Survival rebalanced

| | 3.0.0 | 3.1.0 |
|---|---|---|
| Thirst, base drain | −1 every 5s | −1 every 15s |
| Thirst, extra drain | — | sprinting, heat, the Nether, heavy load |
| Thirst damage | 2 at 35% | 1 at 25% |
| Stamina, sprint | −8 / −4 | −5 / −2 |
| Stamina, jumps | every jump | only a run of five |
| Stamina at zero | damage | immobilises, does not kill |
| Bleeding | −1/s, 25% damage | −2/s, 15% damage |
| Bleeding, posture | no effect | standing still clots faster, sprinting slower |

Resources now drain from effort rather than from the passage of time. Heavy
bleeding also applies weakness and mining fatigue, so an injury feels like one
instead of quietly ticking down your health.

### Medicine

- **Bandages and splints are real items.** Their recipes produced ordinary paper
  and ordinary sticks: no components, no advancement, no craft function. Worse, the
  item tags matched the raw material, so *any* paper in hand healed bleeding and a
  crafted bandage was indistinguishable from a stack of paper. Predicates now match
  on the item model, so only a real bandage heals.
- **All 25 custom recipes unlock in the recipe book** on first join. Previously not
  one of them was granted — they could only be found by guessing the grid.
- **Drinking works.** Water bottles and purified water were consumed without
  quenching anything: the check ran on a 15-second scan and required you to be
  sneaking at that exact moment. Both now fire on the drink itself — +45 for a
  bottle, +100 and a 35% cure chance for purified water. Sneak in water to drink
  from a lake or river.
- **Consumables cost more and yield less** — one craft, one item, rations aside:

  | Recipe | Was | Now |
  |---|---|---|
  | Bandage | string + 2 paper, ×2 | 2 string + 3 paper, ×1 |
  | Splint | 2 sticks + string, ×2 | 3 sticks + 2 string + leather, ×1 |
  | Ashen Bandage | 3 paper + 2 string + gunpowder | + blaze powder |
  | Field Surgery Kit | 2 iron + bone + 2 paper | + diamond, 2 bone, 3 paper |
  | Gloom Tonic | 2 amethyst + glowstone + honey | + 2 ender pearls |
  | Hard Splint | 2 sticks + nugget + leather | 2 iron ingots + 2 leather |
  | Tinder Bundle | 4 sticks + coal, ×2 | + 2 string, ×1 |

- Boiling water is slower and grants no experience: furnace 300 ticks, campfire 900,
  smoker 200. The smoker stays the fast route deliberately.

### Gloom

- **No more chat spam.** At maximum Gloom the hunt rolled every second and announced
  itself in chat — roughly once every 7 seconds on the default preset. The roll now
  waits for its cooldown, cannot start twice, and speaks on the action bar.
- Added an upper clamp so the meter cannot drift past its own maximum and stick there.

### Stability

- **Server stalls on respawn.** The scatter radius grew without a ceiling
  (1200 + 1400 per progress step) and by mid-game threw players into terrain that had
  never been generated; the server froze on generation, with drops of up to 12
  seconds in the log. Capped at 8000 blocks, with the arrival area force-loaded for
  30 seconds.
- **`Couldn't set damage of loot item 0 minecraft:air`**, 17 times in a single log:
  `item modify` was firing on empty equipment slots in three places.
- **Blank values in the status screen.** A scoreboard nobody has written to renders
  as an empty string, so Gloom Shards, Contracts and Grudge showed nothing. A new
  per-player init seeds 30+ counters and the body baselines once, on first join.
- **Contracts and kills work.** No function ever issued a contract, and there was no
  kill hook at all, so kills, shards and packs stayed at zero — which also froze
  several advancement chains.
- **13 of 15 delta meters** never seeded a baseline, so the first cycle after
  installing measured your entire lifetime total and set off noise, backlash, terror
  and the price of trade at once.
- **Hunger** was read through a scoreboard criterion that reports 0 until it first
  changes, briefly starving freshly joined players.
- 18 load-time errors from the server log, and argument spacing in 222 command lines.

### Localisation

- **All 69 locales are hand-translated.** In 3.0.0 only `en_us` and `ru_ru` were
  complete; the other 67 were machine output covering the core.
- Coverage extends past the UI to **mob names, item names, lore and death messages** —
  518 strings per locale.
- Confidence is graded honestly: tier A (10 locales), tier B (4 regional variants),
  tier C (55 hand-translated but not proofread by a native speaker). See
  [`LANGUAGES.md`](LANGUAGES.md).
- Terminology in tier C is cross-checked against Mojang's own translations, so an
  Ender Pearl in a crafting hint is called what the player's inventory calls it.
- Survival hints no longer spell out an exact recipe. "2 paper + 1 string" forced
  every language to agree with a numeral and broke grammar in a dozen of them; the
  hint names the cure and the recipe book carries the ingredients.

### Housekeeping

- Removed **24 dead objectives** declared for features that never arrived. Two more,
  `atr.storm` and `atr.since_death`, were finished instead of dropped: a long storm
  now chills and soaks you further, and a recent death leaves your hands shaking.
- Removed a subsystem that copied player health to a scoreboard **every second, for
  every player**, where nothing ever read it.
- Added `/function attrition:core/selftest` — eight self-diagnostics, also reachable
  from the menu.
- Validators on this build: lint2 0/0, simparse 0, validate 0/0, checklang 69/0,
  audit 0 notes.

### Resource pack

- Two new 16×16 textures: **bandage** and **splint** (27 total). Until now a crafted
  bandage looked exactly like the sheet of paper it came from.
- **The resource pack is no longer optional in practice.** Without it your medicine
  is indistinguishable from your building materials.

---

## 3.0.3 — Field Repairs III — 2026-08-12

Fixes found by reading a real server log rather than a validator.

- `item modify` on empty slots (`player/rust_bite`, `combat/parry_late`,
  `item/use_surgery_kit`)
- Blank counters in the status readout — added a one-shot per-player init
- Temperature added to all three HUD variants
- Respawn scatter capped and force-loaded, ending the multi-second freezes
- Contract payment printed line by line; shards and XP actually granted
- Field Manual book handed out on first join

## 3.0.2 — Field Repairs II — 2026-08-11

- Contracts are issued, tracked from the moment you accept, and counted on delivery
- Added kill hooks: kills, elite kills, packs broken and Gloom Shards now move
- Hunger read directly from the player instead of a stale scoreboard criterion
- Gloom and Grudge clamped at both ends
- 13 delta meters seed their baseline before the first comparison
- Sprint noise used a foreign baseline and a one-metre threshold

## 3.0.1 — Field Repairs — 2026-08-10

- 18 load-time errors gone; the pack loads clean with no red lines
- Argument spacing fixed in 222 command lines
- Four JSON files with invalid predicate syntax
- Attribute commands targeting the wrong entity after an `execute as` wrapper
- Mob names, item names and lore translated, not just the UI
- Death, effect and subtitle strings moved to the namespace the game actually reads
- Added `/function attrition:core/selftest` and shipped `LICENSE` inside both archives

## 3.0.0 — Everything It Takes — 2026-08-08

+272 mechanics (288 → 560), +171 advancements (36 → 207), 20 craftable items.

- New systems: thirst, stamina, noise, wetness, insomnia
- Curses (8) and boons (6); diseases (3), each with its own cure
- Parry and riposte, rage and focus
- Cairns — buildable safe ground
- Grudges, contracts, the tally, titles, the Price, the Waste Trader
- Graves, blights, echoes, the Nemesis
- Mob adaptation and species elders
- Altitude, Nether heat, End pressure, lava fear, cave-ins, frostbite, starvation
- The Reckoning and the Hollow King (400 HP, three phases)
- 34 recipes; menu extended with systems II, survival tips and credits
- Five-second tick pass split into three rotating phases: 560 mechanics cost less
  server time than 288 did in 2.0

## 2.0.0 — The Long Dark

Body layer (bleeding, infection, fractures, temperature, load, sanity, adrenaline),
rebuilt bosses, scars, boss marks, pacts, world events, night watch, depth pressure,
pack tactics, 8 custom textures, English as the base language.

## 1.1.0

Enchantment rebalance, totem penalty, gear wear, the rite of mending, 36 advancements,
resource pack with 69 locales.

## 1.0.0

Initial release.
