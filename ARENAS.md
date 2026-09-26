# Odin's shrines

Each shrine has a Litter Bin altar, carved stones, banners and braziers. Add the offering shown on the bin, close it, then press **Alt + E** to request its event, then press it again within 20 seconds to confirm. Land shrines start cleanup trials. Ocean shrines start sea battles, without litter piles.

Shrines have two layouts per biome. By default, a new world can place up to six in each biome. Flat ground and available space affect how many appear. Runes and braziers light up during events; discovered shrines get a bin icon on the map.

## Add them to an existing world

1. Install Odin Hates Litter **1.5.7** on the server and every client.
2. Install **Upgrade World** on the server and the admin client. Keep a world backup before adding locations.
3. Set the counts under **Litter Altars > World generation**, then run `odin_arenas` in the game console as an admin.
4. Review Upgrade World's queued operation. Run `start` to apply it.

The helper queues `locations_add` for the enabled shrine layouts. It keeps Upgrade World's normal base protection and does not add `force`. It does not reset other locations. Changing a location count alone does not rebuild an existing world.

## Settings

**Litter Altars** holds shared settings for generation, event area, enemies, waves, rewards, litter, music and weather. Changes apply to existing and new altars. A bin's own settings or preset take priority. Land events use a **40 m** radius; Ocean altars use **160 m** of sailing space. Radius is measured out from the bin.

Only admins and hosts can edit settings. Open a shrine's bin to change its radius, timer, enemies, waves, boss, rewards and messages. Each shrine keeps its own settings and cooldown across restarts. Players can use it without the admin being online. Normal ward access still applies.

Land shrines start with **12 litter piles plus 10 per participant**, including the starter: 22 for one player, 32 for two. Litter is twice its normal size with no glow ring. It spreads across the event area, leaving two metres inside the boundary. The group cap is 100. Turn off **Litter fills the event area** to use fixed distances, or set distances on an individual bin.

Shrines wait **45 minutes after the event ends** before they can be used again. A ten-minute event followed by the full cooldown means 55 minutes between starts. Every event type starts its cooldown at the end. Cooldowns pause while the server is offline.

Under **Enemy strength**, set enemy and boss sizes independently. Use prefab overrides such as `Greydwarf 80, Troll 150` for specific creatures. Values are percentages; 100 keeps normal size. CLLC's usual size scaling still applies.

The bin's shrine name, event type and radius are filled in automatically. Altars and their bins cannot be damaged or removed with a hammer, including debug mode. Use the bin's admin menu for deliberate removal.

## Place an altar yourself

Admins can spawn the scenery prefab or place it with Infinity Hammer. For example:

```text
spawn Dova_ArenaShrine_Meadows_1
```

Stay nearby for a few seconds while the server creates and sets up its bin. Replace `Meadows` with a biome from the table below, or use `_2` for the other layout. Place Ocean altars at sea. Manually placed scenery does not add a world-location map marker or terrain protection.

Missing bins at generated world locations are restored automatically. For older altars placed with the spawn command, visit as the host or placing admin to complete their setup.

Land platforms and decorations fit to the terrain when the shrine loads. An active event finishes before an older shrine is adjusted.

## Ocean and removal

Ocean altars use the shared **Litter Altars** settings, with sea controls in its **Ocean** categories. Land litter settings do not apply at sea. Ordinary sea judgments and crafted Sea Offerings keep their separate Ocean settings.

Turning generation off keeps existing shrines. To remove one, finish its event, empty the bin and confirm removal in its admin menu. This removes that shrine's bin, scenery, map marker and ground protection. Other shrines stay.

Venture Location Reset skips these shrines by default so their bins and settings stay intact. Explicit allow-list entries and forced resets can override that protection.

## Location IDs

Replace the ending `_1` with `_2` for the second layout.

| Biome | Shrine | Location ID |
| --- | --- | --- |
| Meadows | The Oathkeeper's Ring | `Dova_LitterArena_Meadows_1` |
| Black Forest | The Rootbound Court | `Dova_LitterArena_BlackForest_1` |
| Swamp | The Sunken Tribunal | `Dova_LitterArena_Swamp_1` |
| Mountains | The Frostwatch Circle | `Dova_LitterArena_Mountain_1` |
| Plains | The Bonebound Ring | `Dova_LitterArena_Plains_1` |
| Mistlands | The Silent Court | `Dova_LitterArena_Mistlands_1` |
| Ashlands | The Ember Tribunal | `Dova_LitterArena_AshLands_1` |
| Deep North | The Winter Oath | `Dova_LitterArena_DeepNorth_1` |
| Ocean | The Tidekeeper's Shrine | `Dova_LitterArena_Ocean_1` |

To queue just one layout:

```text
locations_add Dova_LitterArena_Meadows_1
start
```
