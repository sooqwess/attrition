# Installing Attrition

For Minecraft Java **1.21.11**. Version **3.1.0**.

You need two files:

| File | Goes to | Required? |
|---|---|---|
| `Attrition-3.1.0.zip` | `saves/<world>/datapacks/` | yes |
| `Attrition-RP-3.1.0.zip` | `.minecraft/resourcepacks/` | strongly recommended |

Download both from the
[Modrinth page](https://modrinth.com/datapack/attrition-datapack) or from
[Releases](../../releases).

> **The resource pack is not really optional.** Without it a bandage looks exactly
> like a sheet of paper and a splint like a stick — in an inventory full of paper
> and sticks you cannot tell medicine from building material. The datapack runs
> without it, but it is an uncomfortable way to play.

---

## Single player

1. Create a **new world**. In an existing world your first death will scatter you a
   long way from your base.
2. Put `Attrition-3.1.0.zip` into `saves/<world>/datapacks/`.
   Do not unzip it, and do not zip the folder — `pack.mcmeta` must be at the root
   of the archive.
3. Put `Attrition-RP-3.1.0.zip` into `.minecraft/resourcepacks/`, then enable it in
   **Options → Resource Packs**.
4. Enter the world.
5. **Leave the world and enter it again.** See the note below — this step is not
   optional.
6. Run `/trigger atr.menu`.

## Dedicated server

1. Put `Attrition-3.1.0.zip` into `<server>/world/datapacks/`.
2. Restart the server. Do not use `/reload` for the first install.
3. Each player installs `Attrition-RP-3.1.0.zip` locally, or you serve it with
   `resource-pack=` in `server.properties`.
4. Any player can run `/trigger atr.menu` — no operator rights are required.

---

## The re-entry step

Custom damage types are not registered when a datapack is enabled in a running
world ([MC-260660](https://bugs.mojang.com/browse/MC-260660)). Until you leave and
re-enter, a death from bleeding or infection prints an empty death message.

Enter the world once, quit to title, and load it again. On a server, restart it.
This applies only to the first install.

---

## Checking that it works

Expected result after each step:

| Step | You should see |
|---|---|
| First join | A **Field Manual** book in your inventory and a few lines of chat |
| `/trigger atr.menu` | A clickable menu in chat |
| Press `E` | Attrition recipes present in the recipe book |
| Walk around | A HUD line on the action bar with temperature, thirst and stamina |
| `/function attrition:core/selftest` | Eight checks, all reporting OK |

If the menu prints nothing, the datapack is not loaded — check `/datapack list`.

If items show as paper and sticks, the resource pack is not enabled or is in the
wrong order in **Options → Resource Packs**.

---

## First hour

The pack starts on the **ATTRITION** preset, which is deliberately brutal. If you
want to actually finish the game, open the menu and switch to **Harsh** or
**Tempered** — every mob in the world is recalculated immediately.

Four things kill new players:

1. **Thirst.** Drink from a lake by sneaking in water. Boil it before you trust it.
2. **Bleeding.** Craft a bandage, hold it, stand still and sneak.
3. **Cold.** Watch the temperature on the HUD. A campfire under your feet warms you.
4. **The Gloom.** It rises in the dark. Above 90 it blinds you, and on the harder
   presets it leaves a floor that rest will not remove — for that, hold glowstone
   dust, stand on a block of gold and sneak.

The Field Manual covers all of this. Read it before you go mining.

---

## Load order

Attrition overrides 12 vanilla recipes (planks, sticks and torches). If you run
other datapacks that touch the same recipes, load Attrition last:

```
/datapack enable "file/Attrition-3.1.0.zip" last
```

It does not touch world generation, so Terralith, Incendium, Nullscape, Structory
and similar packs work alongside it.

It does change these gamerules: `players_sleeping_percentage`,
`natural_health_regeneration`, `spawn_phantoms`, and difficulty to Hard. To keep
your own settings:

```
/scoreboard players set RULES atr.cfg 0
```

---

## Uninstalling

```
/function attrition:core/reset
```

This removes the scoreboards, tags and attribute modifiers the pack applied. Then
delete the ZIP from `datapacks/` and restart. Run the reset **before** removing the
file, otherwise the attribute modifiers stay on your player.

---

## Reporting a problem

Open an [issue](../../issues) with:

- your Minecraft version and the pack version
- the output of `/function attrition:core/selftest`
- the relevant part of `logs/latest.log`
