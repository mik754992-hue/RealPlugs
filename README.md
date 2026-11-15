# Real Plugs for Create: Power Grid (NeoForge 1.21.1)

Wall outlets and power strips that are **real Create: Power Grid electrical blocks**, plus plugs,
cables and adapters you plug into them, and plugs you can stick onto CC: Tweaked computers.

Needs: Minecraft 1.21.1, NeoForge 21.1.x, Create 6.0.9+, Create: Power Grid 0.6.x (+ Architectury). CC: Tweaked optional.

## Requirements
| | Version |
|---|---|
| Minecraft | 1.21.1 |
| NeoForge | 21.1.x |
| Create | 6.0.9 and up (6.0.x) |
| Create: Power Grid | 0.6.x |
| Architectury | 13.0.8 or newer (needed by Power Grid) |
| CC: Tweaked | optional (1.121.0 tested by users; 1.113.1 crashes with newer Create, see Troubleshooting) |

## Install
Drop the jar into `mods/` next to Create, Power Grid and Architectury.

## Build on GitHub
1. Push the **contents** of this folder to the root of a repo. Keep the hidden `.github/` folder and `libs/`
   (the Power Grid jar the build compiles against).
2. The `build` workflow runs on every push. Download `realplugs-jar` from the run's Artifacts.
3. To publish a release, push a tag such as `v1.0.0`: the `release` workflow attaches the jar to a GitHub release.

## Build locally
Needs JDK 21 and Gradle 8.10+.
```
gradle build        # jar ends up in build/libs/
gradle runClient    # test in a dev client
python3 scripts/validate_assets.py   # check models, lang, loot tables and recipes agree
```
Version numbers and dependency ranges live in `gradle.properties`; `neoforge.mods.toml` is filled from them.

## Outlets, strips and what fits where
Every slot has a **connector standard**. A plug only goes into a slot of the same standard; anything else is refused
with a message on screen ("That doesn't fit - this needs: ...").

| Block | Slots |
|---|---|
| Wall Outlet (US) | 2 x US plug |
| Wall Outlet (EU) | 2 x EU plug |
| Wall Outlet (UK) | 2 x UK plug |
| DC Power Jack Panel | 2 x barrel jack |
| USB Charging Hub | 2 x USB-A, 2 x USB-C |
| Power Strip (US) | 4 x US plug |
| Power Strip (EU) | 4 x EU plug |
| Universal Power Strip | US, EU, UK, USB-A |
| Wall Outlet (AU) | 2 x AU plug |
| Power Strip (UK) | 4 x UK plug |
| Power Strip (AU) | 4 x AU plug |
| Network & AV Wall Plate | 2 x Ethernet, 2 x HDMI |

**Adapters** take one standard on the front and plug into another with the back. Plugging into an adapter works the same
way: the plug must match what the adapter accepts. Hover over any plug or adapter to see what it plugs into / accepts.

| Adapter | Accepts (front) | Plugs into (back) |
|---|---|---|
| US to EU | US plug | EU socket |
| EU to US | EU plug | US socket |
| US to UK | US plug | UK socket |
| UK to US | UK plug | US socket |
| USB-A Wall Adapter | USB-A | US socket |
| USB-C Wall Adapter | USB-C | US socket |
| HDMI to USB-C | HDMI | USB-C port |
| USB-A to USB-C | USB-A | USB-C port |
| Multi-Tap (US) | 3 x US plug | US socket |
| Multi-Tap (EU) | 3 x EU plug | EU socket |
| US to AU | US plug | AU socket |
| AU to US | AU plug | US socket |
| EU to UK | EU plug | UK socket |
| UK to EU | UK plug | EU socket |
| Micro-USB Wall Adapter | Micro-USB | US socket |
| DisplayPort to HDMI | DisplayPort | HDMI port |

Plugs: US, EU, UK, AU, USB-A, USB-C, Micro-USB, Lightning, HDMI, DisplayPort, Ethernet, DC barrel.

## Crafting
All recipes are shapeless.

**Blocks**
| Result | Ingredients |
|---|---|
| Wall Outlet (US) | iron ingot, copper ingot, redstone |
| Wall Outlet (EU) | US outlet + green dye |
| Wall Outlet (UK) | US outlet + blue dye |
| DC Power Jack Panel | US outlet + black dye |
| USB Charging Hub | US outlet + quartz + lapis lazuli |
| Power Strip (US) | 2 US outlets + iron ingot |
| Power Strip (EU) | 2 EU outlets + iron ingot |
| Universal Power Strip | US outlet + EU outlet + UK outlet + USB hub |
| Wall Outlet (AU) | US outlet + yellow dye |
| Power Strip (UK) | 2 UK outlets + iron ingot |
| Power Strip (AU) | 2 AU outlets + iron ingot |
| Network & AV Wall Plate | US outlet + glass pane + string |

**Plugs** (copper ingot + iron nugget + one extra, gives 2)
| Plug | Extra ingredient |
|---|---|
| US | redstone |
| EU | lapis lazuli |
| UK | gold nugget |
| USB-A | quartz |
| USB-C | amethyst shard |
| HDMI | glass pane |
| Ethernet | string |
| DC barrel | coal |
| AU | flint |
| Micro-USB | prismarine shard |
| DisplayPort | glowstone dust |
| Lightning | bone meal |

**Adapters** (all also need an iron ingot)
| Adapter | Ingredients |
|---|---|
| US to EU | US outlet + EU plug |
| EU to US | EU outlet + US plug |
| US to UK | US outlet + UK plug |
| UK to US | UK outlet + US plug |
| Multi-Tap (US) | US outlet + US plug |
| Multi-Tap (EU) | EU outlet + EU plug |
| USB-A Wall Adapter | USB-A plug + US plug |
| USB-C Wall Adapter | USB-C plug + US plug |
| HDMI to USB-C | HDMI plug + USB-C plug |
| USB-A to USB-C | USB-A plug + USB-C plug |
| US to AU | US outlet + AU plug |
| AU to US | AU outlet + US plug |
| EU to UK | EU outlet + UK plug |
| UK to EU | UK outlet + EU plug |
| Micro-USB Wall Adapter | Micro-USB plug + US plug |
| DisplayPort to HDMI | DisplayPort plug + HDMI plug |

## Ports: sockets for CC: Tweaked blocks
A **Port** is a socket item you stick onto any CC: Tweaked block (computer, monitor, disk drive, printer, speaker, modem...) at an
exact spot. There is one per connector: USB-A, USB-C, Micro-USB, Lightning, HDMI, DisplayPort, Ethernet, DC barrel jack, and US, EU, UK and AU power.
Each port is a chunky box in its own colour with the connector's hole in the front, so you can tell them apart.

- **Place:** sneak + right-click a CC: Tweaked block with a port. It lands exactly where you clicked, snapped to the 1/16 grid, on the face you clicked.
- **Plug in:** right-click the port with a **plain plug** of the same standard (adapters don't go in a port). A wrong standard gives a message.
- **Take out:** right-click the port with an empty hand to get the plug back. Sneak + empty hand removes the port (and returns the plug).
- Punching it (or breaking the block it sits on) drops the port and its plug.
- Crafting (shapeless, gives 2): iron ingot + copper ingot + the same extra ingredient as that connector's plug.

**Cords into ports.** Plug cords (and Power Grid's copper cord) can end on a port too:
- Hold the cord and right-click the port. While a cord is in your hand the port steps aside and you aim at the spot where the port sits.
- The port's connector has to be one of the cord's connectors, and the other end follows the usual rule (a US to USB-A cord needs a US slot and a USB-A port).
- The cord is drawn ending exactly at the port, and the port shows its plug seated, like a plugged-in plug. A port holding a plug won't take a cord and the other way round.
- Behind the scenes a computer has no electrical side, so Real Plugs puts a small **invisible anchor block** in the empty block in front of the port for the cord to attach to. It has no collision, drops nothing and cannot be broken; it disappears with its port.
- That needs the block in front of the port to be empty air when you place the port. If it isn't you get a message and the port only takes plugs. Only one port per face of a block can take a cord.
- The anchor has a selection box only while you hold a cord, so it never gets in the way of normal clicks.

Ports are a build feature: they look right and enforce matching connectors, but they do not connect to the computer's peripherals.
Plugs can still be stuck straight onto computers (sneak + right-click) as before.

## Pocket computers with ports
Every port also works as a **CC: Tweaked pocket upgrade** (written against the CC: Tweaked 1.113.1 API and checked against 1.121.0, where everything it uses is unchanged). It becomes the pocket computer's one upgrade slot, so it replaces a modem or speaker.

- **Craft it on:** pocket computer + the port item, the same way you add a modem.
- **Or equip it from the computer:** keep the port item in your inventory and run `pocket.equipBack()` in the pocket computer. `pocket.unequipBack()` takes it off again.
- **Plug in:** hold a plain plug of the same standard in either hand and right-click the pocket computer. A wrong standard gives a message.
- **Unplug:** sneak + right-click with empty hands to get the plug back.
- **From Lua:** the port is the peripheral on `"back"`, type `realplugs_port`: `getStandard()` (e.g. `"usb_c"`), `isPlugged()`, and `getPlug()` (`{name, standard}` or nil).

```lua
local port = peripheral.wrap("back")
print(port.getStandard(), port.isPlugged())
```

A pocket computer has one upgrade slot, so it carries one port. The datapack entries are `data/realplugs/computercraft/pocket_upgrade/port_*.json`.

## CC: Tweaked peripheral
Every outlet, strip and panel is a read-only peripheral (type `realplugs_socket`) when CC: Tweaked is installed.
Attach a computer directly or through a wired modem. Slots are numbered from 1, counting from the viewer's left.

| Method | Returns |
|---|---|
| `getSocketId()` | block id, e.g. `"power_strip"` |
| `getSlotCount()` | number of slots |
| `getSlotStandard(slot)` | connector standard of the slot, e.g. `"us_power"` (nil if no such slot) |
| `isPlugged(slot)` | true if something sits in the slot |
| `getPluggedCount()` | how many slots are in use |
| `getPlug(slot)` | `{name, standard, adapter, accepts?, inner?}` or nil if empty |
| `getSlots()` | one table per slot: `{slot, standard, plugged, plug?}` |

```lua
local strip = peripheral.find("realplugs_socket")
for _, s in ipairs(strip.getSlots()) do
  print(s.slot, s.standard, s.plugged and s.plug.name or "empty")
end
```

## Plug cords (extension leads)
A **Plug Cord** is a real Power Grid cord with a plug on each end. Power Grid draws the hanging cord, limits its length (16 blocks)
and carries the current; Real Plugs decides where the ends fit. There are two kinds:

- **Same plug on both ends**, one per connector standard: US, EU, UK, AU, USB-A, USB-C, Micro-USB, Lightning, HDMI, DisplayPort, Ethernet, DC barrel.
- **Multi-standard cords** with a different connector on each end, like a phone charger lead (US plug on one end, USB-A on the other).

1. Hold a plug cord and right-click a **slot** on an outlet, strip or panel. The slot must take one of the cord's connectors
   and must be empty, otherwise you get a message and nothing is attached.
2. Right-click the other end onto a second slot or onto any other Power Grid block that accepts cords. If the first end is already
   in one of our slots, the second end has to be the cord's other connector (a US to USB-A cord needs one US slot and one USB-A slot).
3. The cord costs one plug cord item. Break the cord to get it back.

Cord ends in our slots are drawn with the **Real Plugs plug model** of that slot's connector (Power Grid's own plug is switched off on our blocks).
The cord end is **slot-specific**: it sits on that slot's tap and the neutral bus, and while it is plugged in it closes that slot's
contact exactly like a plug would, so only that slot supplies the cord. A slot holding a cord won't take a plug, and the other way round.
At a Power Grid device the far end has no connector standard, since Power Grid's own blocks don't have them.

Crafting (shapeless):
- same-plug cord: the plug + copper ingot + string
- multi-standard cord: one plug of each standard + string

| Multi-standard cords |
|---|
| US to USB-A, US to USB-C, US to Micro-USB |
| EU to USB-A, EU to USB-C |
| UK to USB-A, UK to USB-C |
| AU to USB-A, AU to USB-C |
| US to DC Barrel, EU to DC Barrel |
| HDMI to DisplayPort, HDMI to USB-C |
| USB-A to USB-C, USB-A to Micro-USB |
| US to Lightning, USB-A to Lightning, USB-C to Lightning |

Every slot has **its own cord box** (not one big box over the whole plate), so you aim at the slot you want and the cord end sits on that
slot's tap. Power Grid's own **copper cord** works the same way on any slot, without the connector check (clicking a single terminal wires one conductor).

## How the outlets work electrically
Each outlet / power strip has these Power Grid terminals (use Power Grid wires or copper cords on them):
- **Red bar on top = hot bus.** Wire your supply's hot side here.
- **Blue bar at the bottom = neutral bus.** Supply neutral AND every device's return go here.
- **One small copper stud per slot = that slot's hot tap.** Wire the device's hot side here.

A slot's tap is connected to the hot bus **only while a plug (or adapter) is plugged into that slot**.
Unplug it and the tap is cut off.

## How to play
- **Plugging in**: right-click a slot with a plug or adapter. Empty hand removes it (the last plug in an adapter comes out first).
- **Adapters**: put an adapter in a socket, then right-click it with plugs that match its front. Multi-taps hold three.
- **On a computer**: hold a plug/adapter, **sneak + right-click** a CC computer where you want it. Only device-side
  connectors (USB-A, USB-C, HDMI, Ethernet, barrel) fit a computer, mains plugs are refused. These are visual only.
  Use the same right-click with a matching plug on a stuck-on adapter, and an empty hand removes things.
- Everything is in the **Real Plugs** creative tab. Place the outlets against a wall (the back sits on the clicked face).

## Models
Everything is a real 3D cuboid model, not a flat sprite. All colours come from one shared palette,
`assets/realplugs/textures/block/palette.png` (4x4 cells, each element samples one cell), so you can
re-colour every model by editing that one PNG.

Plug and adapter models share one orientation: the **cable / body side faces NORTH (-z, toward the viewer)** and the
**prongs / plug side point SOUTH (+z, into the socket)**. Keep that and your own model will sit correctly in a socket,
on a computer and inside an adapter.

## Add your own plug / cable / adapter / outlet
Plugs, adapters and outlets are all listed in `PlugTypes.java` / `SocketDefs.java`. To add one, edit those and add the matching files by hand:
1. **Plug or adapter**: append an entry to `PLUGS` or `ADAPTERS` in `PlugTypes.java` (the array position is its
   custom_model_data number), choose its `Standard`, then add `models/item/plug_<name>.json` (or `adapter_<name>.json`),
   one line in the `overrides` list of `models/item/plug.json` (or `adapter.json`), the name in `lang/en_us.json`
   (`item.realplugs.plug.<name>` / `item.realplugs.adapter.<name>`) and a recipe `data/realplugs/recipe/plug_<name>.json`. Adapter `sockets` are the front socket centres in model units.
2. **Outlet**: add a `SocketDef` to `SocketDefs.java`, plus `blockstates/<id>.json`, `models/block/<id>.json`,
   `models/item/<id>.json`, a loot table, a recipe, the pickaxe tag entry and a lang name. Copy an existing outlet's files, then run `python3 scripts/validate_assets.py` to catch anything you forgot.
3. **New connector standard**: add a value to the `Standard` enum and a `standard.realplugs.<key>` lang entry.
4. Model orientation: **cable/body faces NORTH (-z), prongs point SOUTH (+z)**. Build in Blockbench and keep the `display` block.

Give one by command: `/give @s realplugs:plug[custom_model_data=3]`

## Known gaps
- Plugs and adapters are visual markers: a plugged item only closes the slot contact, it does not carry its own load.
- Plugs, ports and pocket ports do nothing electrically. They are visual and checked for matching connectors.
- Whether a slot holds a cord is read from Power Grid's connection list (`ElectricBehaviour.getConnections`); a copper cord clicked onto a single slot terminal also counts. `SocketBehaviour` hooks attach/remove to update the slot contact.
- Plug cords register a Power Grid wire type (`data/realplugs/powergrid/wire_types/plug_cord.json`) and hook Power Grid's cord handler list. If Power Grid changes either in a later version, that is the first place to look.
- The CC integrations (outlet peripheral, pocket ports) compile against small stubs of CC's API in `src/main/java/dan200`, written from CC: Tweaked 1.113.1 (the signatures Real Plugs uses are identical in 1.121.0). They are left out of the released jar. If you add CC: Tweaked itself to the dev runtime, delete those stubs first.
- Recipes and the build setup have not been run in-game or on CI yet: if a dependency version in `gradle.properties` (Create, Flywheel, Registrate) or `build.gradle` (Ponder) doesn't resolve, adjust it there.

## Ponder
In-game Ponder scenes (hold W over the item, or look at it in the creative tab / JEI and press W) explain the mod. They use the two showcase schematics:
- **Charging island** (strips, hubs, panels): the airport schematic.
- **Wall outlets** and **Plugs and adapters**: the house schematic.
- **Plug cords**: the airport schematic again.

The schematics are in `src/main/resources/assets/realplugs/ponder/`. The airport one had some Power Grid wire entities saved into it; they were removed
because the scene does not need them. The scenes are written in `ponder/RealPlugsScenes.java`.

## Troubleshooting
- **`NoClassDefFoundError: ...create/content/contraptions/BlockMovementChecks...` with CC: Tweaked installed.** That is CC: Tweaked 1.113.x's own Create
  integration looking for a class Create has since moved, not Real Plugs. Update CC: Tweaked (1.121.0 fixes it).

## License
Real Plugs is MIT licensed (see `LICENSE`). `libs/powergrid-*.jar` is Create: Power Grid (Apache-2.0), see `libs/README.md`.
