# Settings

File: `BepInEx/config/Dova.OdinHatesLitter.cfg`

Install the same build on the server and every client. Server settings sync automatically; only admins and hosts can change them. Configuration Manager is opened with **F1**.

## Event modes

| Mode | What it does |
| --- | --- |
| Wrath | Dropping items builds wrath. Odin gives players time to clean up before enemies arrive. |
| Cleanup Trial | A bin offering starts a litter collection event with enemies. |
| Endless Raid | Combat waves continue until the timer ends, unless you choose another wave rule. |
| Ocean Battle | Sea combat with its own enemies, sailing radius, waves and rewards. No litter collection. |
| Ocean Endless Raid | A crafted Sea Offering starts a separate sea raid. Survival waves by default. |
| Boss Raid | A chosen boss, with optional phases and reinforcements. |

In shudnal's Configuration Manager split view, expand a mode folder to see its categories: enemy spawning, enemy strength, drops, waves, mini-bosses, rewards, music, weather and more. Ocean has two folders: **Judgment** and **Endless Raid**. Searching shows matching settings inside closed folders. Other managers and list view keep labeled categories. Only relevant settings appear; existing keys and values are kept.

Both Ocean modes have independent enemies, waves, sailing radius, drops, rewards, XP, atmosphere and messages. Neither has litter piles, cleanup rewards or terrain-placement controls. Altar bins use **Litter Altars** instead, with separate sea controls in its Ocean categories. F1 shows settings wherever you stand. Sea encounters apply in Ocean water or on a Leviathan, even if its seabed reports another biome. A land bin's selected enemy biome cannot turn it into an Ocean encounter.

Old Ocean settings that used land waves are copied into independent sea wave settings during the upgrade. Later land changes do not change sea battles.

### Sea Offering

Craft a **Sea Offering** at a level-one workbench. The default recipe is **Coins 20, Resin 10, Chitin 5**. Use it in the Ocean, then use it again within 20 seconds to confirm the raid. Starting consumes one offering. Rejected starts return it, with overflow kept afloat.

Open **Ocean > Endless Raid > Sea Offering** for crafting materials, permissions, event duration, arrival warning and player cooldown. Defaults are ten minutes total, a 30-second arrival warning and a 15-minute cooldown after the event ends. The warning counts toward the event timer. Music, weather and boundary follow that same timer. **Waves** controls survival, fixed waves or a single wave. Ordinary Ocean judgments keep their own cooldown.

Crafting accepts up to eight `PrefabName amount` entries, separated by commas. Missing materials disable the recipe until they become available or the recipe is corrected. Recipe changes sync automatically. Server admins can restrict using offerings to admins while still letting other players help.

Existing settings are copied into the new modes on the first load. Later changes to one mode do not change the others. Endless Raid starts with **Survive timer** when the old wave setting was **Single wave**.

Config-file keys inside each mode use `Original section / Setting name`. For example, `[Boss Raid]` contains `Event creatures / Enemy damage multiplier`. The full reference below lists the original sections and defaults to help find each setting. Hidden legacy entries remain for migration; use the mode entries for new changes.

## Presets

Open **Presets** inside an event folder or **Litter Altars**. Choose **Relaxed**, **Balanced**, **Veteran** or **Brutal**, then apply it to the whole event or one category. Applying a preset replaces those settings. Existing settings stay as they are until an admin applies one. Finish active events of that type first.

**Litter Altars > Presets** applies to land altars. **Litter Altars > Ocean - Presets** applies to Ocean altars, with shark and serpent choices. Each keeps its own settings; applying one does not change the other.

| Preset | Fight | Stamina / health / Eitr regeneration | Equipment chance |
| --- | --- | --- | --- |
| Relaxed | Fewer enemies and gentler damage | 10% / 5% / 10% | 10% |
| Balanced | Moderate waves and enemy strength | 15% / 8% / 15% | 15% |
| Veteran | More waves and tougher enemies | 18% / 10% / 18% | 20% |
| Brutal | Harder fights with capped spawns | 20% / 12% / 20% | 25% |

Blessings last three minutes. Equipment is a chance for **one item per player when the event ends**, separate from enemy drops. Boss Raid completion chances are 20%, 30%, 40% and 50%. Peaceful cleanup gives a smaller material reward without equipment. High-tier enchanting materials and equipment follow each player's progression. Ancient equipment remains rare.

Whole-event presets cover timing, cooldowns, solo and group counts, waves, mini-bosses, health, damage, sizes, enemy drops, completion loot, equipment, modded supplies, XP, blessings, participation, lives, litter, placement, atmosphere and notices. Each mode keeps only the settings it uses. Appearance and messages return to standard defaults. Server permissions, world generation, individual bin overrides and custom raid phases stay in place.

Wrath and Cleanup Trial presets last up to ten minutes. Endless raids range from eight to fifteen minutes; Boss Raids range from fifteen to thirty. Waves, music, weather and the boundary follow the event timer. Event cooldowns start afterward. Land altars retain 12 litter piles plus 10 per player, double-size litter without a ring, and a 45-minute cooldown.

Ocean presets offer **Serpents**, **Sharks** or **Sharks and serpents** at every difficulty. Sharks require Monstrum; unavailable sharks fall back to serpents. Both sea modes have their own counts, waves, loot, XP and sailing radius, with no litter collection. Ocean supplies use private progression when available, with world progress as the fallback.

Admin bins can choose a built-in preset in **Settings preset**. For Boss Raid bins, choose a **Phase preset** and press **Use these boss phases**, then save. Relaxed has one phase. The others warn before a rage phase at half health and add limited reinforcements. Custom bin values still take priority over the selected preset.

Enemy drops are reduced separately from completion rewards. Wacky MMO XP stays below the normal rate in all four presets. CLLC levels, custom creatures and other server modifiers still affect difficulty; individual settings remain editable after applying a preset.

## Reward previews

Open **Admin and server > Reward previews**. Choose an event, current settings or a preset, a land biome, and a progression tier. Ocean modes always use Ocean rewards. You can check any biome without travelling there.

The buttons roll a sample for one eligible player, including the correct bin multipliers and blessings. Cleanup previews appear only for modes with cleanup rewards. Item and equipment chances are shown separately. Press again for another roll. Nothing is granted or applied.

**Current settings** uses synced mode or altar defaults, without individual bin overrides. **Configured progression (you)** uses your reward rules; starter and group rules use your progress for this single-player sample. You can instead select world progress or a specific tier. Enemy drops, contribution requirements and reward cooldowns remain separate.

## Blessings

Each event mode has a **Blessings** section for **Odin's Forgiveness**. Set **Extra stamina regeneration (%)**, **Extra health regeneration (%)** and **Extra Eitr regeneration (%)** independently from 0 to 200. Zero disables that type. Without a preset, the default is 15% stamina regeneration for 180 seconds; health and Eitr start at zero. The four difficulty presets enable all three.

All enabled types use **Blessing duration (seconds)** and the same reward cooldown. Health improves normal regeneration rather than providing an instant heal. Eitr regeneration does not create an Eitr pool. The tooltip lists the enabled bonuses. Changes sync automatically; only admins and hosts can edit them. Each mode and admin bin can have different values. Existing stamina settings, presets and bin overrides are retained under the new name.

## Litter Altars

Biome shrines have a central Litter Bin and two layouts per biome. New worlds can generate up to six shrines per biome by default. For existing worlds, install Upgrade World, run `odin_arenas`, review the queue, then run `start`. See [Arena locations](ARENAS.md) for the location IDs and details.

**Litter Altars** contains shared controls for generation, event area, enemies, waves, rewards, litter, atmosphere and messages. Land and Ocean altars keep separate event settings. Existing values carry over on the first load. Changes apply to existing and new altars; individual bin settings and presets take priority. All settings sync from the server. Ocean altars use sea combat without litter collection, with a radius of 160 metres. Land altars use 40 metres. Changing the event radius does not move the decorations.

Land altar defaults are 200% litter size, no glow ring, and 12 piles plus 10 per player, including the starter. That means 22 solo or 32 with two players, up to the group cap of 100. Altars wait 45 minutes after an event ends.

**Litter fills the event area** spreads piles across the event radius, leaving two metres inside the boundary. Turn it off to use the shared minimum and maximum distances, or set a distance on an individual bin. Old factory distances switch to this shared default; custom distances remain.

**General and display** controls the icons above event enemies' names, levels and health bars. Bosses and mini-bosses show Valheim's boss icon beside the Litter Bin. Adjust their size, opacity and spacing. Turn off boss icons separately, or hide all event enemy icons. They follow the enemy's normal nameplate visibility.

## Each admin bin

Open the bin's inventory to see its admin menu. Regular players cannot see or use these controls.

- **Area:** event radius, inner and outer litter distances, and a boundary preview.
- **Event:** cleanup, endless raid or boss raid; an independent event length up to 120 minutes.
- **Creatures:** a land biome, boss prefab and boss health multiplier. Ocean remains separate.
- **Access:** public use near bases, approval and deliberate removal of an empty bin.
- **Name, preset and raid phases:** name the event, choose a saved preset, edit phases, copy settings, set messages and override individual settings.

Save Area or Event/Creatures changes using that page's Save button. Save detailed overrides with **Save this bin**. Editing is locked during an active event. Admin bins are protected from accidental damage or debug removal; use the confirmed removal button after emptying the bin and finishing its event.

Settings resolve in this order: **this bin's overrides, its named preset, shared altar settings for altars, its event mode**. A star beside a detailed setting means this bin overrides it. **Use inherited values for this category** clears that category's overrides. Other bins are unaffected.

Every event starts its cooldown after it ends, whether completed or timed out. Active events do not spend any of that wait. Cooldowns pause while the server is offline. A failed bin setup returns the offering without charging a cooldown.

Admin bins have their own event cooldowns. A finished event does not block another ready bin. Ordinary bins also use the player's trial cooldown. Completion reward cooldowns are separate.

## Creature sizes and floating loot

Each mode and admin bin has **Enemy size (%)** and **Boss size (%)** under **Enemy strength**. 100 keeps the normal size; 200 doubles it. Specific overrides use prefab names and percentages, for example `Greydwarf 80, Troll 150`. These replace the general value for that creature. CLLC scaling is included; health and damage have separate settings.

Sea rewards and event creature drops keep their floating marker after the event ends, after stacking and after a reload. With **Venture Floating Items**, they reuse its floating component. Event-marked loot floats even if its item type normally sinks; Venture's rules still control ordinary drops.

## Event announcements

**Admin and server > Event announcement destination** selects Automatic, ServerGuard, Discord Connector, Both or Off. Automatic uses the full server version of Discord Connector when available, otherwise ServerGuard. Configure the chosen mod's webhook and event messages first. Both sends through both mods, so use it only if you want both feeds.

Variant Announcements has its own in-game notice settings. Enable its Odin event notices to show starts and victories there. No extra announcement mod is required to play.

Regular players' bins always use their local biome. An admin may change an approved bin's enemy and completion-reward biome. Progression still limits rewards, not the selected enemies.

## Monstrum

Monstrum is optional. Install it and its dependencies on the server and every client if you want to use its content.

Under **Modded supplies**, **Include Monstrum supplies** adds materials from its loaded creature drops to automatic completion rewards. It uses the existing supply count and amounts. **Include Monstrum trophies** is off by default and adds regular creature trophies when enabled. Boss trophies and unique boss weapons stay in their normal drop tables. Custom supply lists replace the automatic selection.

Ocean rewards include sea drops, such as shark fins, alongside supplies for each player's progression. Missing creatures or items are skipped. Servers without Monstrum keep their vanilla fallback rewards.

Under **Enemy drops**, **Monstrum Epic Loot fallback** lets event creatures use a similar vanilla creature's loot table when no Monstrum table exists. A pack's existing tables take priority. Normal drop permissions, biome chances, boss settings and CLLC still apply. Wild creatures are unchanged.

Enemy lists are kept on upgrade. Add creatures by prefab name to include them in a mode or bin. These are examples, not automatic replacements:

| Biome | Example enemy list | Example boss |
| --- | --- | --- |
| Meadows | `Greyling 80, Fox_TW 20` | `BossAsmodeus_TW` |
| Black Forest | `Greydwarf 80, Razorback_TW 20` | `BossSvalt_TW` |
| Swamp | `Draugr 70, Crawler_TW 20, RottingElk_TW 10` | `BossVrykolathas_TW` |
| Mountains | `Wolf 70, GrizzlyBear_TW 20, ObsidianGolem_TW 10` | `ObsidianGolem_TW` |
| Plains | `Goblin 80, Prowler_TW 20` | `Prowler_TW` |
| Ocean | `Serpent 70, Shark_TW 30` | `Shark_TW` |

Weights are relative chances. Empty enemy lists use automatic biome selection; Ocean can then choose loaded sharks as well as serpents. Svalt spawned for an Odin event leaves dungeon doors alone. These settings sync automatically and only admins or hosts can change them.

## Boss phases and adds

Choose **Boss raid**, save a boss prefab, then enable **Use this bin's raid phases** in the detailed editor. Use the arrows to edit up to six phases. The first phase sets starting attributes. Later phases trigger once when the boss reaches the configured health percentage **or** the current phase reaches its time trigger. Zero disables a trigger.

Each phase has a warning, stars, health and damage multipliers, minimum health refill, CLLC choices and reinforcements. For a rage phase at half health, use a 50% health trigger, 100% refill and the extra stars you want. Refills do not repeat after a restart. Health multipliers replace the previous phase's multiplier; they do not compound each phase.

**Invulnerability after transition (seconds)** defaults to **5** for each later phase. The boss is also protected throughout that phase's warning, including from poison and burning already applied. Set it to zero to disable transition protection. Remaining protection pauses with the event during a restart.

Adds support **1-20 creatures per call**, an alive limit, a weighted enemy list and either a repeating interval or explicit times such as `20,60,120` seconds after the phase begins. Explicit times replace the interval. The event's overall enemy cap and time limit still apply. Old adds may be cleared on transition. The event ends when its main boss is defeated and its other objectives are complete.

CLLC choices come from the installed version. Creature effects apply to creature champions; true bosses use boss affixes. Effects that create untracked copies are excluded. CLLC is optional; stars and ordinary attributes work without it.

## Rewards, drops and XP

Completion rewards are separate from enemy drops. Gear chance is one roll per eligible player at completion, not per kill. **100%** guarantees that roll; it does not mean 100 items.

Enemy and boss drop settings control their own loot chances and ordinary drop quantities. Epic Loot follows the creature's drop permission and chance, but equipment is not duplicated by the ordinary quantity multiplier. Keep **Use separate boss loot settings** enabled to tune bosses independently.

For land modes, completion rewards follow **each player's own progress** by default, including World Advancement Progression private keys. Starter, highest participating player and world progression are alternatives. These choices do not change a bin's enemies.

For Ocean, **Use private progression when available** is on by default. Each recipient gets the tier allowed by their WAP private boss keys. If WAP is absent or private progression is disabled, actual global world boss keys set the tier. An empty private list remains at the starting tier. Turn this option off to always use global progression. Materials, extra supplies, coins and equipment use this tier; serpent death drops remain separate and follow the enemy drop controls and Epic Loot's own rules.

Ocean's **Progression** reward categories include land-biome material and equipment tables. These are reward tiers: defeating Eikthyr unlocks Black Forest pools, for example. Sea materials remain in the Ocean bundle. Land enemy lists and litter settings do not appear in either Ocean mode.

**Mod rewards** discovers supplies from recipes for Epic Loot's loaded biome equipment, including compatible Therzie gear. **Mod material choices** uses `Auto` by default, or accepts custom item tables. Ocean adds progression supplies. Missing items are skipped; an unavailable supply table uses vanilla items. Excluded equipment and Epic Loot's deny list still apply.

Wacky MMO enemy and boss XP have separate **0-500%** settings in each mode and bin override. `1` is 1%, `100` is normal XP, and `500` is five times normal. The default is about one third. Group shares use the same event rate once.

## Cleanup and participation

Wrath gives two minutes to clean up by default. Trial timing is separate. Adjust litter count, size, glow, inner/outer radius, spacing, terrain and plant checks. Mission litter stacks to 50 before stack-size mods.

Late helpers add litter only while required piles remain unfound. Each player increases the target at most once; rejoining does not add more. The total remains capped at 100. Replacement piles help when pickups stop, using the configured delay and placement rules. The counter includes litter carried by other participants.

Three returns mean the starting life plus three revives or respawns. A fourth death locks the player out until the event ends. Resurrection uses the same allowance. Reconnecting does not reset it. Graves can be recovered after the event.

The dome gives a warning before sealing. Late helpers can enter by default, then must stay. Boat and player participation at sea use horizontal distance, so waves do not push the crew outside the event. Music, weather, object protection and the dome follow the event timer.

**Event rules** controls overlap, outside hostiles, group scaling and what happens when the area is empty: continue, pause or end. Player tames are left alone. Wild enemies return to normal behavior when the event ends. Events save their objectives, waves, phases, return counts and remaining time. Time pauses while the server is offline. Back up `BepInEx/config/Dova.OdinHatesLitter.events` with the world.

## Messages and display

**Event popup** controls the banner or minimal style, position, size, width, duration, colors, opacity and animation. **Display** controls the persistent timer, litter and wave tracker separately.

An admin bin can override **Event messages** for entering, leaving, starting and completing its event. Use `{event}` for the bin's name and `{player}` for the entering/leaving player or event starter. Empty text keeps the usual notices. These messages use the event popup settings and are saved separately for each bin.

## Admin tools

Refresh the live event list to see remaining time and participants. Choose a connected player, mode and timer to reset just that cooldown. **Next judgment** applies to Wrath and Ocean Battle. Resetting a cooldown keeps active events and return counts. A bin's own cooldown reset is in its admin panel.

Cancellation requires confirmation and can return the offering when it is still available. Save named presets, copy modes, reset one category, or check configured enemies and loot. Recent event and reward actions appear in history. Detailed logs are in the Server section.

Optional integrations use the installed mod data and fall back when an API is unavailable. Breaking game or dependency updates can still require a new build. Keep the same content mods on the server and clients.

## Full reference

Defaults apply to new configs. Existing custom values are kept. Event settings below are available under their relevant mode categories.

### Admin tools

| Setting | Default | What it does |
| --- | --- | --- |
| Admins can start events inside bases | false | Allow admins and the host to start judgments and bin trials near workbenches and other base objects. Other players keep the normal protection checks. |
| Admins can start events inside wards | false | Separate admin override for event placement inside wards. Does not grant access to another player's chest. |
| Admin-placed bins allow public trials inside bases | true | New bins placed by an admin or host are approved by the server so anyone can start their trials near bases. Approval stays with that bin across restarts. Existing bins can be approved or revoked under Individual bin settings. Ordinary players cannot approve bins or place their own inside bases. Ward access is unchanged. |
| Protect admin-placed bins | true | Protect admin-placed and admin-approved Litter Bins from damage and accidental removal, even in debug mode. Admins can still use Remove this bin in its settings after emptying it and finishing its event. Normal player bins keep the usual rules. |
| Allow admins to overlap events | false | Allows an admin starting an event to bypass the overlap check. Ordinary players still follow it. |


### Atmosphere

| Setting | Default | What it does |
| --- | --- | --- |
| Show event boundary | true | Draw a subtle ring along the ground or water around the active event. Players can pass through it freely. |
| Boundary colour | #FFC04D | Colour of the event ring, written as a hex colour such as #FFC04D. |
| Boundary brightness | .45 | Opacity of the event outline. Lower values make it subtler. |
| Boundary width (metres) | .12 | Thickness of the event outline. |
| Storm during encounters | true | Let nearby players experience the storm together. It clears after the encounter or its configured duration. Normal weather effects still apply. |
| Encounter radius (metres) | 60 | Size of the shared encounter area. Players can enter or leave freely. Death or departure does not end the event. |
| Music during encounters | true | Play boss music for players in the encounter area. Uses each player's music volume. |
| Shuffle encounter music | true | Choose music from the playlist for any encounter, regardless of biome. Nearby players follow the same order. Off uses Music track or automatic boss music. |
| Music playlist | Eikthyr, The Elder, Bonemass, Moder, Yagluth, The Queen, Fader, Frozen King, Event 1, Event 2, Event 3, Event 4, Jotun Invasion | Music to shuffle, separated by commas. Use the default boss/event names or exact loaded track names. Any track can play with any encounter. *boss* and *event* also work. Missing tracks are skipped. Empty uses all loaded boss/event tracks. |
| Time between music tracks (seconds) | 0 | Zero keeps one looping track for the whole encounter. A positive value changes shuffled tracks at this interval while the event is active. |
| Play raven warnings | true | Play a loaded native raven idle effect when wrath rises through warning tiers. |
| Atmosphere duration (seconds) | 600 | Used only when Match event duration is off. Limits weather and music from the start of the event; event completion always stops them. |
| Match event duration | true | Keep weather and music for the entire event, including the cleanup warning. Follows the regular or bin-trial timer automatically and stops when the event ends. |
| Music track | Empty | Used only when Shuffle encounter music is off. Leave empty for automatic boss music, or enter one loaded track name. Use Music playlist when shuffle is on. |
| Storm weather | Eikthyr | Weather used when Shuffle storms is off. Enter a loaded weather name, such as Eikthyr. With shuffle on, use Storm playlist instead. |
| Shuffle storms | true | Choose weather independently from the music for each encounter. Nearby players use the same selection. Off uses Storm weather. |
| Storm playlist | Eikthyr, GoblinKing, *storm* | Weather names to shuffle, separated by commas. *storm* includes loaded storm weather. Missing names are skipped. Empty uses Eikthyr and loaded storms. Weather keeps its normal wet and cold effects. |
| Time between storms (seconds) | 0 | Zero keeps one shuffled storm for the event. A positive value cycles the storm list independently of music. |


### Biome enemies

| Setting | Default | What it does |
| --- | --- | --- |
| Meadows | Greyling 60, Neck 25, Boar 15 | Prefab, relative weight, optional maximum per wave. Example: Greyling 60, Neck 25, Boar 15. Empty uses automatic biome enemies. Loaded mod creatures are supported. |
| Black Forest | Greydwarf 70, Greydwarf_Elite 20 2, Greydwarf_Shaman 10 1 | Prefab, relative weight, optional maximum per wave. Example: Greydwarf 70, Greydwarf_Elite 20 2, Greydwarf_Shaman 10 1. Empty uses automatic biome enemies. Loaded mod creatures are supported. |
| Swamp | Draugr 55, Skeleton 25, Blob 15 2, Draugr_Elite 5 1 | Prefab, relative weight, optional maximum per wave. Example: Draugr 55, Skeleton 25, Blob 15 2, Draugr_Elite 5 1. Empty uses automatic biome enemies. Loaded mod creatures are supported. |
| Mountains | Wolf 80, Fenring 20 2 | Prefab, relative weight, optional maximum per wave. Example: Wolf 80, Fenring 20 2. Empty uses automatic biome enemies. Loaded mod creatures are supported. |
| Plains | Goblin 85, GoblinShaman 15 1 | Prefab, relative weight, optional maximum per wave. Example: Goblin 85, GoblinShaman 15 1. Empty uses automatic biome enemies. Loaded mod creatures are supported. |
| Mistlands | Seeker 60, SeekerBrood 25, Tick 15 3 | Prefab, relative weight, optional maximum per wave. Example: Seeker 60, SeekerBrood 25, Tick 15 3. Empty uses automatic biome enemies. Loaded mod creatures are supported. |
| Ashlands | Charred_Melee 40, Charred_Archer 25, Charred_Twitcher 25, Asksvin 10 2 | Prefab, relative weight, optional maximum per wave. Example: Charred_Melee 40, Charred_Archer 25, Charred_Twitcher 25, Asksvin 10 2. Empty uses automatic biome enemies. Loaded mod creatures are supported. |
| Deep North | Frysling 65, Skeleton_DeepNorth 35 | Prefab, relative weight, optional maximum per wave. Example: Frysling 65, Skeleton_DeepNorth 35. Empty uses automatic biome enemies. Loaded mod creatures are supported. |
| Ocean | Serpent 100 | Prefab, relative weight, optional maximum per wave. Example: Serpent 100. Empty uses automatic biome enemies. Loaded mod creatures are supported. |


### Biome enemy loot

| Setting | Default | What it does |
| --- | --- | --- |
| Meadows enemy loot chance (%) | 100 | One chance per event creature for all its normal drops, including Epic Loot and Lucky Loot. Requires Allow normal enemy drops. Completion rewards are separate. |
| Black Forest enemy loot chance (%) | 100 | One chance per event creature for all its normal drops, including Epic Loot and Lucky Loot. Requires Allow normal enemy drops. Completion rewards are separate. |
| Swamp enemy loot chance (%) | 100 | One chance per event creature for all its normal drops, including Epic Loot and Lucky Loot. Requires Allow normal enemy drops. Completion rewards are separate. |
| Mountains enemy loot chance (%) | 100 | One chance per event creature for all its normal drops, including Epic Loot and Lucky Loot. Requires Allow normal enemy drops. Completion rewards are separate. |
| Plains enemy loot chance (%) | 100 | One chance per event creature for all its normal drops, including Epic Loot and Lucky Loot. Requires Allow normal enemy drops. Completion rewards are separate. |
| Mistlands enemy loot chance (%) | 100 | One chance per event creature for all its normal drops, including Epic Loot and Lucky Loot. Requires Allow normal enemy drops. Completion rewards are separate. |
| Ashlands enemy loot chance (%) | 100 | One chance per event creature for all its normal drops, including Epic Loot and Lucky Loot. Requires Allow normal enemy drops. Completion rewards are separate. |
| Deep North enemy loot chance (%) | 100 | One chance per event creature for all its normal drops, including Epic Loot and Lucky Loot. Requires Allow normal enemy drops. Completion rewards are separate. |
| Ocean enemy loot chance (%) | 100 | One chance per event creature for all its normal drops, including Epic Loot and Lucky Loot. Requires Allow normal enemy drops. Completion rewards are separate. |


### Biome materials

| Setting | Default | What it does |
| --- | --- | --- |
| Meadows | LeatherScraps 10-14, Resin 12-18 | Items per player. Use ItemName 1-3, optionally followed by @ 50%. Empty disables this table. |
| Black Forest | SurtlingCore 2-4, CopperOre 5-7 | Items per player. Use ItemName 1-3, optionally followed by @ 50%. Empty disables this table. |
| Swamp | IronScrap 7-12, Chain 1-2 @ 60% | Items per player. Use ItemName 1-3, optionally followed by @ 50%. Empty disables this table. |
| Mountains | SilverOre 5-7, WolfPelt 6-10 | Items per player. Use ItemName 1-3, optionally followed by @ 50%. Empty disables this table. |
| Plains | BlackMetalScrap 10-14, Needle 6-10 | Items per player. Use ItemName 1-3, optionally followed by @ 50%. Empty disables this table. |
| Mistlands | Softtissue 7-12, Sap 12-18 | Items per player. Use ItemName 1-3, optionally followed by @ 50%. Empty disables this table. |
| Ashlands | FlametalNew 5-7, Blackwood 12-24 | Items per player. Use ItemName 1-3, optionally followed by @ 50%. Empty disables this table. |
| Deep North | Crystal 10-14, FreezeGland 10-14 | Items per player. Use ItemName 1-3, optionally followed by @ 50%. Empty disables this table. |
| Ocean | SerpentMeat 5-7, SerpentScale 4-6, Chitin 7-12 | Items per player. Use ItemName 1-3, optionally followed by @ 50%. Empty disables this table. |


### Biome single bosses

| Setting | Default | What it does |
| --- | --- | --- |
| Meadows | Boar 70, Neck 30 | Exactly one boss or champion from this weighted list when single-boss events are on. Example: Boar 70, Neck 30. Land cleanup still applies; normal waves are not substituted when the list is unavailable. |
| Black Forest | Troll 100 | Exactly one boss or champion from this weighted list when single-boss events are on. Example: Troll 100. Land cleanup still applies; normal waves are not substituted when the list is unavailable. |
| Swamp | Abomination 100 | Exactly one boss or champion from this weighted list when single-boss events are on. Example: Abomination 100. Land cleanup still applies; normal waves are not substituted when the list is unavailable. |
| Mountains | StoneGolem 80, Fenring_Cultist 20 | Exactly one boss or champion from this weighted list when single-boss events are on. Example: StoneGolem 80, Fenring_Cultist 20. Land cleanup still applies; normal waves are not substituted when the list is unavailable. |
| Plains | GoblinBrute 75, Lox 25 | Exactly one boss or champion from this weighted list when single-boss events are on. Example: GoblinBrute 75, Lox 25. Land cleanup still applies; normal waves are not substituted when the list is unavailable. |
| Mistlands | SeekerBrute 80, Gjall 20 | Exactly one boss or champion from this weighted list when single-boss events are on. Example: SeekerBrute 80, Gjall 20. Land cleanup still applies; normal waves are not substituted when the list is unavailable. |
| Ashlands | Morgen 100 | Exactly one boss or champion from this weighted list when single-boss events are on. Example: Morgen 100. Land cleanup still applies; normal waves are not substituted when the list is unavailable. |
| Deep North | ElakingMole 50, Bjorn 30, Unbjorn 20 | Exactly one boss or champion from this weighted list when single-boss events are on. Example: ElakingMole 50, Bjorn 30, Unbjorn 20. Land cleanup still applies; normal waves are not substituted when the list is unavailable. |
| Ocean | Serpent 100 | Exactly one boss or champion from this weighted list when single-boss events are on. Example: Serpent 100. Land cleanup still applies; normal waves are not substituted when the list is unavailable. |


### Biome wave bosses

| Setting | Default | What it does |
| --- | --- | --- |
| Meadows | Boar 70, Neck 30 | One optional mini-boss or champion, selected by relative weight. Example: Boar 70, Neck 30. Empty disables bosses in this biome. Enable wave bosses must be on. Meadows and Ocean use local creature champions; Boss health multiplier adjusts their strength. |
| Black Forest | Troll 100 | One optional mini-boss or champion, selected by relative weight. Example: Troll 100. Empty disables bosses in this biome. Enable wave bosses must be on. Meadows and Ocean use local creature champions; Boss health multiplier adjusts their strength. |
| Swamp | Abomination 100 | One optional mini-boss or champion, selected by relative weight. Example: Abomination 100. Empty disables bosses in this biome. Enable wave bosses must be on. Meadows and Ocean use local creature champions; Boss health multiplier adjusts their strength. |
| Mountains | StoneGolem 80, Fenring_Cultist 20 | One optional mini-boss or champion, selected by relative weight. Example: StoneGolem 80, Fenring_Cultist 20. Empty disables bosses in this biome. Enable wave bosses must be on. Meadows and Ocean use local creature champions; Boss health multiplier adjusts their strength. |
| Plains | GoblinBrute 75, Lox 25 | One optional mini-boss or champion, selected by relative weight. Example: GoblinBrute 75, Lox 25. Empty disables bosses in this biome. Enable wave bosses must be on. Meadows and Ocean use local creature champions; Boss health multiplier adjusts their strength. |
| Mistlands | SeekerBrute 80, Gjall 20 | One optional mini-boss or champion, selected by relative weight. Example: SeekerBrute 80, Gjall 20. Empty disables bosses in this biome. Enable wave bosses must be on. Meadows and Ocean use local creature champions; Boss health multiplier adjusts their strength. |
| Ashlands | Morgen 100 | One optional mini-boss or champion, selected by relative weight. Example: Morgen 100. Empty disables bosses in this biome. Enable wave bosses must be on. Meadows and Ocean use local creature champions; Boss health multiplier adjusts their strength. |
| Deep North | ElakingMole 50, Bjorn 30, Unbjorn 20 | One optional mini-boss or champion, selected by relative weight. Example: ElakingMole 50, Bjorn 30, Unbjorn 20. Empty disables bosses in this biome. Enable wave bosses must be on. Meadows and Ocean use local creature champions; Boss health multiplier adjusts their strength. |
| Ocean | Serpent 100 | One optional mini-boss or champion, selected by relative weight. Example: Serpent 100. Empty disables bosses in this biome. Enable wave bosses must be on. Meadows and Ocean use local creature champions; Boss health multiplier adjusts their strength. |


### Blessings

| Setting | Default | What it does |
| --- | --- | --- |
| Enable blessing | true | Give eligible contributors Odin's Forgiveness after cleanup or victory. The blessing boosts the regeneration types configured below. Reward cooldowns also apply. |
| Extra stamina regeneration (%) | 15 | Extra stamina regeneration percentage from Odin's reward. |
| Extra health regeneration (%) | 0 | Extra health regeneration from Odin's Forgiveness. Zero disables this bonus. Increases normal health regeneration; does not instantly heal or add maximum health. |
| Extra Eitr regeneration (%) | 0 | Extra Eitr regeneration from Odin's Forgiveness. Zero disables this bonus. Does not grant an Eitr pool to a player without one. |
| Blessing duration (seconds) | 180 | Duration of Odin's Forgiveness in seconds. All enabled regeneration bonuses last this long. |


### Cleanup

| Setting | Default | What it does |
| --- | --- | --- |
| Scale litter with nearby players | false | Add litter for nearby living players when an event begins. Late joiners use the separate Add litter for late helpers setting. |
| Include starter in litter scaling | false | Count every player, including the starter, for Litter per extra player. With 12 base piles and 10 per player, one player gets 22 piles and two get 32. Off keeps the base count for a solo player. |
| Add litter for late helpers | true | Add litter when a new player joins while required piles remain unfound. Each player counts once per event. Stops once every pile has been found, even if it still needs returning. Uses Litter per extra player and Group litter limit. |
| Litter per extra player | 2 | Additional piles for each nearby player when litter scaling is enabled. |
| Group litter limit | 100 | Maximum piles after group scaling. Applies to both bin trials and regular wrath cleanup. |
| Move replacement piles closer | true | Prefer the inner part of the configured litter area when replacing hard-to-find piles. Off uses the entire search area. |
| Show hints for missing litter | false | After no successful pickup for a while, show a small pulsing golden marker above uncollected piles. Carried litter is never marked. |
| Time before litter hints (seconds) | 60 | Every successful pickup by any participant restarts this shared hint timer. |
| Litter hint visibility (metres) | 35 | How close a player must be to see a missing-pile hint. |
| Litter glow opacity (%) | 50 | Opacity of the soft gold ring around litter. Zero hides it. Applies to existing litter for everyone. |
| Litter size (%) | 100 | Size of litter in the world. 100 is normal, 200 is double. Its pickup hitbox scales with it. Applies to existing litter for everyone. |
| Move hard-to-reach litter | true | When nobody has picked up litter for a while, replace one uncollected ground pile at a time with a new pile near the bin. The required total stays the same. Carried and returned litter is never replaced. |
| Time without finding litter (seconds) | 60 | Start replacements after this long without a successful litter pickup anywhere in the event. Every player's pickup restarts the wait. Default: one minute. Zero disables replacements. |
| Time between replacement piles (seconds) | 60 | After the first replacement, add another at this interval while nobody finds litter. Default: one per minute. Each replaces an uncollected pile; the goal does not grow. No replacements at sea. |
| Spawn litter during wrath | true | Odin summons mission litter and a temporary return bin during regular wrath events on land. Original dropped items stay where you left them. Off uses the original dropped items as the cleanup objective. |
| Wrath litter piles | 6 | Number of mission piles scattered around Odin's temporary bin. Bin trials have their own pile count under Litter Bin. |
| Return litter to the bin | true | Pick up litter into your inventory, then press Use at its bin to return it. Keep it in your main inventory when depositing. Off counts each pile as cleaned on pickup. Applies to new encounters. |


### Cleanup placement

| Setting | Default | What it does |
| --- | --- | --- |
| Minimum distance from bin (metres) | 6 | Inner edge of the litter search area. Existing bins can have individual admin overrides. |
| Maximum distance from bin (metres) | 14 | Outer edge of the litter search area. Kept inside the boundary by five metres, or two at altars. Altars use the full event area unless Litter fills the event area is off or the bin has its own distance. |
| Minimum space between piles (metres) | 2 | Space between litter piles, including replacement piles. Larger spacing needs a larger search area. |
| Spread pattern | Even circle | Even circle covers every side of the bin. Random scatters freely. Clusters creates small groups while keeping minimum spacing. |
| Allow litter on rocks | false | Allow litter on low, open rock tops. Piles rest on the rock surface and are never placed inside it. Temporary bins still use ground. |
| Maximum rock height (metres) | 2 | Highest rock top above the surrounding terrain that may hold litter. |
| Maximum surface slope (degrees) | 37 | Steepest litter surface when Allow uneven ground is off. Rock tops always respect this limit. |
| Distance from buildings (metres) | 1 | Extra clear space around player-built pieces. Zero still prevents litter from intersecting solid objects. |
| Allow uneven ground | false | Skip slope and height-difference checks for litter and temporary bins. Water and solid obstructions are still checked. Piles follow the ground slope. |
| Avoid trees and bushes | true | Keep litter clear of low plants and bushes. Off allows litter among foliage. Solid trunks, walls and buildings remain blocked. Overhead tree canopies no longer exclude a whole clearing. |
| Plant clearance (metres) | .2 | Extra space around ground-level plants when Avoid trees and bushes is on. Lower values allow closer placement. |


### Cleanup rewards

| Setting | Default | What it does |
| --- | --- | --- |
| Item amount multiplier | 1 | Scale coins and materials after peaceful cleanup. 1 is normal, 2 is double, and 0 disables these items. Does not change Odin's Forgiveness or equipment chance. |
| Item reward chance (%) | 100 | Chance for each eligible player to receive the cleanup item bundle. Odin's Forgiveness is separate. |
| Extra cleanup items | Empty | Extra items in addition to the biome bundle. Example: Honey 2-4 @ 50%. Empty adds nothing. |
| Give rewards for peaceful cleanup | true | Reward each qualifying helper when all litter is returned before enemies arrive. Uses cleanup items, chance, multiplier and cooldown, plus Odin's Forgiveness. |


### Combat rewards

| Setting | Default | What it does |
| --- | --- | --- |
| Combat item reward multiplier | 2 | Multiply coins and materials after defeating the wave. The default 2 gives twice the base bundle; peaceful cleanup uses its own multiplier. Does not multiply the blessing or equipment bonus. Zero disables ordinary combat items. |
| Item reward chance (%) | 100 | Chance for each eligible player to receive combat items. Equipment has an additional roll within this chance. |
| Combat reward cooldown (seconds) | 0 | Extra wait between combat rewards. Zero rewards every completed encounter. Each player still receives only one bundle per event, and event cooldowns remain separate. |
| Extra combat items | Empty | Extra items in addition to the biome bundle, before the combat multiplier. Example: Coins 10-20 @ 50%. Empty adds nothing. |


### Display

| Setting | Default | What it does |
| --- | --- | --- |
| Show event enemy icons | true | Show a Litter Bin icon above the name, level and health of enemies spawned by Odin Hates Litter. Ordinary creatures keep their usual display. |
| Show event boss icons | true | Add Valheim's boss icon beside the Litter Bin icon for event bosses and mini-bosses. Requires event enemy icons to be enabled. |
| Event enemy icon size (pixels) | 28 | Icon size in the game's HUD. Follows the HUD scale. |
| Event enemy icon spacing (pixels) | 8 | Space above the enemy's nameplate, including level and health indicators. |
| Event enemy icon opacity (%) | 90 | Visibility of the event enemy icon. Zero hides it. |
| Event boss icon spacing (pixels) | 4 | Space between the Litter Bin and boss icons. Both use the event enemy icon size and opacity. |
| Tracker horizontal position (%) | 50 | Horizontal center of the event timer, litter and wave tracker. Vertical position uses Top offset. |
| Tracker size (%) | 100 | Size of the persistent event tracker and wrath meter. |
| Tracker width | 650 | Maximum width of the event tracker at 1080p. Long text wraps. |
| Tracker background opacity (%) | 15 | Soft background behind the event tracker. Zero hides it. |
| Show encounter progress | true | Show nearby enemies or litter remaining, and whether your contribution qualifies for rewards. You must still finish alive and nearby; reward cooldowns apply. |
| Show event timer | true | Show the time left in the nearby encounter. Events continue if their starter dies or leaves, until completed or timed out. |
| Show wrath meter | true | Show the wrath count and cleanup countdown at the top of the screen. Turn off to hide the meter entirely. |
| Keep the wrath meter visible | false | Keep the ordinary wrath count visible until it is cleared. Off hides it after the display timer. Next judgment and active event countdowns stay visible either way. |
| Hide wrath after (seconds) | 8 | Time to show the ordinary wrath count after it changes when Keep the wrath meter visible is off. Does not hide Next judgment or active event countdowns. |
| Distance from top of screen (pixels) | 155 | Vertical position of the wrath meter and event counters at 1080p. Larger values move the display down. Scales with screen resolution; adjust to leave room for status effects and other HUD mods. |


### Drop protection

| Setting | Default | What it does |
| --- | --- | --- |
| Ignored item prefabs | Empty | Items that never cause wrath. Separate prefab names with commas, for example Stone, Wood, BeechSeeds. Empty means no extra exemptions. |
| Ignore drops inside active wards | true | Ignore drops inside enabled wards, using their actual configured radius. |
| Minimum ward protection radius (metres) | 0 | Optional minimum active-ward radius. Zero uses the ward's own radius. This no longer treats every base object as a ward. |
| Ignore drops inside bases | true | Also ignore drops within vanilla PlayerBase effect areas, such as workbenches. |


### Encounters

| Setting | Default | What it does |
| --- | --- | --- |
| Protect buildings from event enemies | false | Prevent damage to player-built pieces from creatures summoned by this mod. Does not stop ordinary enemies or player damage. |
| Allow Odin encounters | true | Odin appears at the threshold and summons enemies if litter remains after his warning. |
| Final cleanup warning (seconds) | 120 | Time to clean up before enemies arrive. Included in the event time limit: the default ten-minute event gives two minutes to clean up and up to eight minutes to fight. |
| Encounter cooldown (seconds) | 300 | Controls the Next judgment countdown. Wait after an event ends before Odin can return. Saved across restarts and paused while the server is offline. Zero removes this wait; active events must still finish first. |
| Delay before Odin appears (seconds) | 0 | Wait this long after reaching the wrath threshold before Odin can appear. Zero means immediately. Cleaning below the threshold restarts this delay. This is separate from the pickup grace period and final warning. |
| Encounter time limit (seconds) | 600 | Maximum time to finish an encounter and earn rewards, including Odin's warning. |


### Enemies

| Setting | Default | What it does |
| --- | --- | --- |
| Solo enemy count | 2 | Enemies for a solo player before fury. With group scaling off, this is the base count for everyone. No new encounter while your previous summons are alive. |
| Scale enemies with nearby players | true | Add enemies for each extra living player inside the encounter area when the warning ends. Distant, dead, teleporting and indoor players do not count. Joining later does not spawn another wave. |
| Enemies added per extra player | 1 | Extra enemies for each nearby player beyond the judged player. Uses the shared encounter area radius. |
| Enemy limit including fury | 10 | Maximum enemies in one encounter, including group scaling and fury. |
| Use CLLC enemy levels | true | When Creature Level and Loot Control is installed, use its star chances and world difficulty for judgment enemies. Repeat-offender stars provide a minimum rather than stacking on top. CLLC effects and infusions still apply. Splitting is disabled for summons to keep the enemy limit accurate. |
| Allow normal enemy drops | false | Let event enemies drop their usual loot, including Epic Loot equipment, Lucky Loot bonuses and CLLC loot changes. Off blocks these enemy drops while keeping each player's completion rewards. Wild creatures are unaffected. |


### Enemy choices

| Setting | Default | What it does |
| --- | --- | --- |
| Respect world progression | true | Keep registered creature unlock requirements. Custom lists can use loaded mod creatures; missing prefabs are skipped with a warning. |
| Respect day and night restrictions | true | Automatic enemies keep their normal day/night restrictions. Turn off to allow either during an event. |
| Allow flying creatures | false | Allow flying creatures in custom or automatic enemy pools. Ocean encounters still need suitable sea creature choices. |
| Automatic creature variety | 3 | Number of eligible creature types in the automatic pool, starting with the weakest. Zero uses every eligible type. An explicit biome list replaces the automatic pool. |
| Minimum spawn distance (metres) | 18 | Nearest distance from the event centre for enemy spawns. Ocean uses at least 25 metres. |
| Maximum spawn distance (metres) | 26 | Farthest enemy spawn distance. Kept inside the event area. Ocean uses at least 38 metres. |


### Enemy waves

| Setting | Default | What it does |
| --- | --- | --- |
| Wave mode | Single wave | Single wave keeps the original rules. Fixed waves requires the chosen number. Until cleanup keeps sending waves until litter is returned; combat-only events use the fixed count. Survive timer rewards participation only after surviving the full event timer. |
| Number of waves | 3 | Waves required in Fixed waves mode, and in combat-only events using Until cleanup. |
| Time between waves (seconds) | 60 | Minimum time between the starts of enemy waves. Does not extend the event timer. |
| Rest after a cleared wave (seconds) | 15 | Additional breathing room after the last enemy in a wave is defeated. |
| Clear enemies before next wave | true | Wait until all current event enemies are defeated before starting another wave. The maximum alive limit always applies. |
| Extra enemies each wave | 0 | Add this many enemies for each wave after the first, on top of the existing solo, group and fury settings. |
| Maximum enemies alive | 20 | Upper limit on living enemies per event across all waves. Existing biome encounter limits still control each wave. |
| Total enemy limit | 300 | Maximum enemies across an entire event. Once reached, no more waves spawn. |
| Stop new waves with time left (seconds) | 15 | Avoid starting a wave just before the event ends. Single-wave events still get their first wave. |
| Health increase per wave (%) | 0 | Extra health for later waves, capped by Maximum wave multiplier. |
| Damage increase per wave (%) | 0 | Extra damage for later waves, capped by Maximum wave multiplier. |
| Maximum wave multiplier | 3 | Upper limit for gradual wave health and damage increases. Completion rewards are awarded once per event. |


### Epic Loot equipment

| Setting | Default | What it does |
| --- | --- | --- |
| Registered equipment weight | 1 | Relative weight of gear added by Epic Loot, including Therzie and other compatible mods. Custom choices use weight 1 unless a weight follows the prefab name. Zero disables the registered pool. |
| Excluded equipment | Empty | Equipment prefab names to leave out of rewards, separated by commas. Supports * wildcards. Epic Loot's own denied-item list is also respected. |
| Include earlier biome equipment | false | Also include registered gear from earlier biome tiers. Off keeps the current tier's equipment. Progression limits still apply. |
| Enable equipment bonus | true | Chance to award one enchanted weapon or armor piece to each eligible contributor. Requires Epic Loot on the server and clients. |
| Allow equipment for cleanup | false | Also roll the equipment bonus after peaceful cleanup. Off means combat victories only. |
| Equipment chance per player (%) | 15 | Chance for one equipment item per eligible player after a land wrath event. Placed-bin trials and Ocean events have their own chances. Does not change enemy drops. |
| Maximum equipment rarity | Ancient | Highest allowed equipment rarity. Unavailable tiers in an older Epic Loot version are skipped. |
| Balance equipment types | true | Choose a weapon type or armor slot first, then an item. This keeps large armor lists from crowding out other gear. |
| Avoid recent equipment repeats | true | Avoid the last three equipment rewards for each player while the server is running, when another choice is available. |
| Include Epic Loot registered gear | true | Add loaded equipment from Epic Loot's biome item lists, including compatible modded gear. Your custom equipment choices are still included. |
| Match equipment to player progress | true | Cap land equipment to the Progression source in Rewards. Ocean always uses that source to choose its equipment tier. Does not change enemy drops. |


### Epic Loot materials

| Setting | Default | What it does |
| --- | --- | --- |
| Meadows | DustMagic 3-5, EssenceMagic 1-2 | Epic Loot materials per player. The mod must be installed on server and clients. Empty disables this table. |
| Black Forest | DustMagic 5-8, EssenceMagic 2-3 | Epic Loot materials per player. The mod must be installed on server and clients. Empty disables this table. |
| Swamp | DustRare 5-8, EssenceRare 2-3 | Epic Loot materials per player. The mod must be installed on server and clients. Empty disables this table. |
| Mountains | DustRare 8-12, EssenceRare 3-5, DustEpic 1 @ 25% | Epic Loot materials per player. The mod must be installed on server and clients. Empty disables this table. |
| Plains | DustEpic 5-8, EssenceEpic 2-3 | Epic Loot materials per player. The mod must be installed on server and clients. Empty disables this table. |
| Mistlands | DustEpic 8-12, EssenceEpic 3-5, DustLegendary 1 @ 25% | Epic Loot materials per player. The mod must be installed on server and clients. Empty disables this table. |
| Ashlands | DustLegendary 5-8, EssenceLegendary 2-3, DustMythic 2-3 @ 35%, EssenceMythic 1 @ 20% | Epic Loot materials per player. The mod must be installed on server and clients. Empty disables this table. |
| Deep North | DustMythic 5-8, EssenceMythic 2-3, DustAncient 1-2 @ 25%, EssenceAncient 1 @ 10% | Epic Loot materials per player. The mod must be installed on server and clients. Empty disables this table. |
| Ocean | DustRare 5-8, EssenceRare 2-3 | Epic Loot materials per player. The mod must be installed on server and clients. Empty disables this table. |


### Equipment choices

| Setting | Default | What it does |
| --- | --- | --- |
| Meadows | Club, AxeStone, AxeFlint, SpearFlint, KnifeFlint, Bow, ShieldWood, ShieldWoodTower, HelmetLeather, ArmorLeatherChest, ArmorLeatherLegs, CapeDeerHide | Equipment prefab names, separated by commas. Loaded Epic Loot gear can also join the pool. Empty Ocean uses the progression source selected in Rewards. |
| Black Forest | SwordBronze, AxeBronze, MaceBronze, SpearBronze, AtgeirBronze, KnifeCopper, BowFineWood, ShieldBronzeBuckler, HelmetBronze, ArmorBronzeChest, ArmorBronzeLegs, HelmetTrollLeather, ArmorTrollLeatherChest, ArmorTrollLeatherLegs, CapeTrollHide | Equipment prefab names, separated by commas. Loaded Epic Loot gear can also join the pool. Empty Ocean uses the progression source selected in Rewards. |
| Swamp | SwordIron, AxeIron, MaceIron, SpearElderbark, AtgeirIron, SledgeIron, Battleaxe, BowHuntsman, ShieldIronBuckler, ShieldBanded, ShieldIronTower, HelmetIron, ArmorIronChest, ArmorIronLegs, HelmetRoot, ArmorRootChest, ArmorRootLegs | Equipment prefab names, separated by commas. Loaded Epic Loot gear can also join the pool. Empty Ocean uses the progression source selected in Rewards. |
| Mountains | SwordSilver, MaceSilver, SpearWolfFang, KnifeSilver, BattleaxeCrystal, BowDraugrFang, ShieldSilver, HelmetDrake, ArmorWolfChest, ArmorWolfLegs, CapeWolf, HelmetFenring, ArmorFenringChest, ArmorFenringLegs, FistFenringClaw | Equipment prefab names, separated by commas. Loaded Epic Loot gear can also join the pool. Empty Ocean uses the progression source selected in Rewards. |
| Plains | SwordBlackmetal, AxeBlackMetal, KnifeBlackMetal, AtgeirBlackmetal, MaceNeedle, BowDraugrFang, ShieldBlackmetal, ShieldBlackmetalTower, HelmetPadded, ArmorPaddedCuirass, ArmorPaddedGreaves, CapeLox, CapeLinen | Equipment prefab names, separated by commas. Loaded Epic Loot gear can also join the pool. Empty Ocean uses the progression source selected in Rewards. |
| Mistlands | SwordMistwalker, THSwordKrom, SpearCarapace, AtgeirHimminAfl, SledgeDemolisher, KnifeSkollAndHati, BowSpineSnap, CrossbowArbalest, StaffFireball, StaffIceShards, StaffShield, StaffSkeleton, ShieldCarapace, ShieldCarapaceBuckler, HelmetCarapace, ArmorCarapaceChest, ArmorCarapaceLegs, HelmetMage, ArmorMageChest, ArmorMageLegs, CapeFeather | Equipment prefab names, separated by commas. Loaded Epic Loot gear can also join the pool. Empty Ocean uses the progression source selected in Rewards. |
| Ashlands | SwordNiedhogg, THSwordSlayer, SpearSplitner, MaceEldner, AxeBerzerkr, BowAshlands, CrossbowRipper, StaffClusterbomb, StaffLightning, StaffGreenRoots, StaffRedTroll, ShieldFlametal, ShieldFlametalTower, HelmetFlametal, ArmorFlametalChest, ArmorFlametalLegs, HelmetAshlandsMediumHood, ArmorAshlandsMediumChest, ArmorAshlandsMediumLegs, HelmetMage_Ashlands, ArmorMageChest_Ashlands, ArmorMageLegs_Ashlands, CapeAsh, CapeAsksvin | Equipment prefab names, separated by commas. Loaded Epic Loot gear can also join the pool. Empty Ocean uses the progression source selected in Rewards. |
| Deep North | SwordGold, THSwordGold, SwordGold_FrostFire, THSwordGold_FrostFire, SwordGold_BloodLightning, THSwordGold_BloodLightning, ArmorDeepNorthMageChest, ArmorDeepNorthMagelegs | Equipment prefab names, separated by commas. Loaded Epic Loot gear can also join the pool. Empty Ocean uses the progression source selected in Rewards. |
| Ocean | Empty | Equipment prefab names, separated by commas. Loaded Epic Loot gear can also join the pool. Empty Ocean uses the progression source selected in Rewards. |


### Equipment rarities

| Setting | Default | What it does |
| --- | --- | --- |
| Meadows | Magic 95, Rare 5 | Rarity names with weights, such as Legendary 70, Mythic 29, Ancient 1. Names alone have equal odds. Empty Ocean uses the progression source selected in Rewards. |
| Black Forest | Magic 70, Rare 30 | Rarity names with weights, such as Legendary 70, Mythic 29, Ancient 1. Names alone have equal odds. Empty Ocean uses the progression source selected in Rewards. |
| Swamp | Rare 80, Epic 20 | Rarity names with weights, such as Legendary 70, Mythic 29, Ancient 1. Names alone have equal odds. Empty Ocean uses the progression source selected in Rewards. |
| Mountains | Rare 50, Epic 45, Legendary 5 | Rarity names with weights, such as Legendary 70, Mythic 29, Ancient 1. Names alone have equal odds. Empty Ocean uses the progression source selected in Rewards. |
| Plains | Epic 80, Legendary 20 | Rarity names with weights, such as Legendary 70, Mythic 29, Ancient 1. Names alone have equal odds. Empty Ocean uses the progression source selected in Rewards. |
| Mistlands | Epic 50, Legendary 45, Mythic 5 | Rarity names with weights, such as Legendary 70, Mythic 29, Ancient 1. Names alone have equal odds. Empty Ocean uses the progression source selected in Rewards. |
| Ashlands | Legendary 70, Mythic 29, Ancient 1 | Rarity names with weights, such as Legendary 70, Mythic 29, Ancient 1. Names alone have equal odds. Empty Ocean uses the progression source selected in Rewards. |
| Deep North | Legendary 30, Mythic 65, Ancient 5 | Rarity names with weights, such as Legendary 70, Mythic 29, Ancient 1. Names alone have equal odds. Empty Ocean uses the progression source selected in Rewards. |
| Ocean | Empty | Rarity names with weights, such as Legendary 70, Mythic 29, Ancient 1. Names alone have equal odds. Empty Ocean uses the progression source selected in Rewards. |


### Event creature loot

| Setting | Default | What it does |
| --- | --- | --- |
| Meadows boss loot chance (%) | 100 | Chance for each event boss to drop ordinary and Epic Loot items. Requires separate boss loot settings and Allow boss drops. Completion rewards are unchanged. |
| Black Forest boss loot chance (%) | 100 | Chance for each event boss to drop ordinary and Epic Loot items. Requires separate boss loot settings and Allow boss drops. Completion rewards are unchanged. |
| Swamp boss loot chance (%) | 100 | Chance for each event boss to drop ordinary and Epic Loot items. Requires separate boss loot settings and Allow boss drops. Completion rewards are unchanged. |
| Mountains boss loot chance (%) | 100 | Chance for each event boss to drop ordinary and Epic Loot items. Requires separate boss loot settings and Allow boss drops. Completion rewards are unchanged. |
| Plains boss loot chance (%) | 100 | Chance for each event boss to drop ordinary and Epic Loot items. Requires separate boss loot settings and Allow boss drops. Completion rewards are unchanged. |
| Mistlands boss loot chance (%) | 100 | Chance for each event boss to drop ordinary and Epic Loot items. Requires separate boss loot settings and Allow boss drops. Completion rewards are unchanged. |
| Ashlands boss loot chance (%) | 100 | Chance for each event boss to drop ordinary and Epic Loot items. Requires separate boss loot settings and Allow boss drops. Completion rewards are unchanged. |
| Deep North boss loot chance (%) | 100 | Chance for each event boss to drop ordinary and Epic Loot items. Requires separate boss loot settings and Allow boss drops. Completion rewards are unchanged. |
| Ocean boss loot chance (%) | 100 | Chance for each event boss to drop ordinary and Epic Loot items. Requires separate boss loot settings and Allow boss drops. Completion rewards are unchanged. |
| Use separate boss loot settings | false | On lets event bosses use their own loot switch and biome chances. Off keeps the existing enemy loot switch and biome chances for all event creatures. |
| Allow boss drops | true | Allow ordinary and Epic Loot drops from event bosses when separate boss loot settings are on. Completion rewards are separate. |
| Enemy drop amount multiplier | 1 | Multiplies ordinary creature drop quantities for event enemies, after other mods. Fractional amounts use a stable roll. Does not duplicate Epic Loot equipment or change completion rewards; use the biome chances to control Epic Loot drops. |
| Boss drop amount multiplier | 1 | Multiplies ordinary creature drop quantities for event bosses. Independent of normal event enemies. Epic Loot equipment and completion rewards are unchanged. |
| Monstrum Epic Loot fallback | true | If a Monstrum event enemy has no Epic Loot table, use a similar vanilla creature. Existing loot tables and event drop limits still apply. Does not change wild enemies. |


### Event creatures

| Setting | Default | What it does |
| --- | --- | --- |
| Enemy health multiplier | 1 | Health of ordinary event enemies after their level is applied. Wild creatures are unchanged. Boss health uses the existing mini-boss and single-boss settings. Applies to new spawns. |
| Enemy damage multiplier | 1 | Damage dealt by ordinary event enemies. One keeps their usual damage, including other mods. Changes apply during combat. |
| Boss damage multiplier | 1 | Damage dealt by event mini-bosses and single bosses. Does not change ordinary enemies or world bosses. |
| Enemy size (%) | 100 | Size of new event enemies. 100 keeps their normal size, 200 doubles it. Includes their hitbox. Health and damage use their own settings. |
| Boss size (%) | 100 | Size of new event bosses and mini-bosses. Multiplies their usual size, including CLLC scaling. Each event type and admin bin can use different values. |
| Enemy size overrides | Empty | Size for specific enemy prefabs. Example: Greydwarf 80, Troll 150. Values are percentages from 25 to 500. These replace Enemy size for matching creatures; empty uses Enemy size. |
| Boss size overrides | Empty | Size for specific event bosses. Example: Troll 150, StoneGolem 120, Serpent 130. Values are percentages from 25 to 500. These replace Boss size for matching creatures; empty uses Boss size. |


### Event dome

| Setting | Default | What it does |
| --- | --- | --- |
| Enable event dome | true | Place an invisible physical wall at the event circle. It disappears when the event ends. Turning this off releases every dome immediately; return limits still control combat and rewards. |
| Time before the dome seals (seconds) | 10 | Give nearby players time to leave before the dome seals. Once sealed, participants stay until the event ends. Ocean domes wait until the fight starts so the warning can follow the boat. |
| Allow late helpers | true | Players with returns available can enter a running event. Once inside, they must stay until it ends. Off keeps new helpers outside after the dome seals; existing participants may still return after death. |
| Keep participants inside | true | Hold participants inside the dome until the event ends. Ordinary respawning still works, and eligible players can return. Portals cannot be used to leave an active dome. |
| Keep event enemies inside | true | Keep creatures summoned for this event inside its dome, including flying and swimming enemies. Wild creatures are unaffected. |
| Dome height above terrain (metres) | 120 | Room above the highest sampled ground around the event, with a closed roof. The sides follow the event radius on hills and extend below the water for sea creatures. |
| Show the wall when touched | true | Briefly show a golden ripple where a player or their boat touches the invisible wall. |
| Show dome messages | true | Explain when the dome seals, when a helper joins, why a crossing is blocked, and when players are free to leave. Repeated wall messages are limited. |
| Admins can cross the dome | false | Let admins and solo hosts cross the dome for maintenance. Off makes them follow the same boundary rules as players. This does not restore returns or grant rewards. |


### Event messages

| Setting | Default | What it does |
| --- | --- | --- |
| Entering the area | Empty | Custom notice for this mode or admin bin. Use {event} and {player}. Empty keeps the usual notices. Up to 256 characters are shown. |
| Leaving the area | Empty | Custom notice for this mode or admin bin. Use {event} and {player}. Empty keeps the usual notices. Up to 256 characters are shown. |
| Event started | Empty | Custom notice for this mode or admin bin. Use {event} and {player}. Empty keeps the usual notices. Up to 256 characters are shown. |
| Event completed | Empty | Custom notice for this mode or admin bin. Use {event} and {player}. Empty keeps the usual notices. Up to 256 characters are shown. |


### Event popup

| Setting | Default | What it does |
| --- | --- | --- |
| Show styled notices | true | Use a framed, fading notice for Odin's dialogue and event messages. Off uses the game's message style. |
| Style | Banner | Banner has a subtle frame. Minimal shows only the title and text. |
| Title | ODIN'S JUDGMENT | Heading above event notices. Leave empty for no heading. |
| Notice duration (seconds) | 7 | How long each notice stays visible. Includes its short fade in and out. |
| Horizontal position (%) | 50 | Center of the notice: 0 left, 50 center, 100 right. Kept inside the screen. |
| Vertical position (%) | 32 | Center of the notice: 0 top, 50 middle, 100 bottom. Separate from the persistent tracker. |
| Size (%) | 100 | Overall notice size, including text and spacing. Adapts to screen resolution. |
| Width | 620 | Width at 1080p. Longer messages wrap inside the screen. |
| Text size | 20 | Message text size at 1080p, before the size multiplier. |
| Background opacity (%) | 45 | Banner background opacity. Zero leaves only the frame and text. |
| Animate notices | true | Add a short, gentle slide during the fade. |
| Accent color | #FFC961 | Title and frame color, as #RRGGBB or #RRGGBBAA. |
| Text color | #FFF2D1 | Message color, as #RRGGBB or #RRGGBBAA. |
| Background color | #10151A | Banner color, as #RRGGBB or #RRGGBBAA. Opacity has a separate setting. |


### Event rules

| Setting | Default | What it does |
| --- | --- | --- |
| Keep wild enemies outside | true | Stops outside hostile creatures from entering or fighting across the event boundary. Tamed creatures and wildlife are unchanged. Existing hostiles inside may leave. |
| When nobody is in the area | Continue | Continue keeps the clock running. Pause freezes event timers after the empty-area delay. End closes without rewards. Death alone does not end an event. |
| Empty-area delay (seconds) | 60 | Time without a living participant before the empty-area rule applies. |
| Enemy group scaling | Future waves | Players at start fixes group difficulty for the event. Future waves uses nearby players at each new wave; living creatures never change health when someone joins. |


### Forgiveness

| Setting | Default | What it does |
| --- | --- | --- |
| Allow wrath to fade | true | Slowly reduce wrath after you stop littering. Fading wrath never grants rewards and pauses during a warning or fight. |
| Delay before wrath fades (seconds) | 600 | Wait this long after your last counted world drop before wrath starts to fade. A new drop restarts the wait. |
| Time between forgiveness ticks (seconds) | 60 | After the delay, remove wrath at this interval. |
| Wrath removed per tick | 1 | Wrath points forgiven each tick. This does not award cleanup credit. |


### Fury

| Setting | Default | What it does |
| --- | --- | --- |
| Enable fury | true | Once per visit, more litter aging during Odin's warning provokes a shorter countdown and additional enemies. |
| Time removed from warning (seconds) | 5 | Seconds removed from the current warning on escalation; leaves at least 3 seconds. |
| Extra enemies when furious | 2 | Enemies added when more litter ages during the final warning. The enemy limit under Enemies still applies. |


### General

| Setting | Default | What it does |
| --- | --- | --- |
| Enable OdinHatesLitter | true | Enable Odin's litter judgments. |


### Litter Bin

| Setting | Default | What it does |
| --- | --- | --- |
| Enable cleanup trials | true | Build a Litter Bin with the hammer. Store unwanted materials, then use the challenge action to start a cleanup trial. Pick up litter, return it to the bin, and defeat the enemies. |
| Trial shortcut modifier | Alt | Hold this key while pressing Use (E by default) to start a trial. Alt avoids the Shift+E action used by lock mods. Plain Use opens the bin. This setting is controlled by the server. |
| Building materials | Wood 10, Stone 5 | Items needed to build a bin. Use prefab names and amounts, separated by commas, such as Wood 10, Stone 5. Up to 8 materials, 1 to 10000 of each. Invalid or unavailable items use the default recipe until corrected. Changes apply automatically. |
| Only admins can build bins | false | Off lets everyone build bins. On limits placement to server admins and the host. Everyone can still use existing bins, subject to normal ward access. Server settings apply automatically. |
| Show offering counter | true | Show accepted offerings before a trial, then returned litter and your carried pile count during cleanup. The hover text also shows the count. |
| Counter distance (metres) | 8 | How close players must be to see the offering counter above a bin. |
| Accepted offering items | Wood, Stone, Resin, BeechSeeds, FirCone, GreydwarfEye | Comma-separated prefab names that can pay for a trial. Only plain items are consumed. All other items stay in the bin. |
| Items needed for a trial | 20 | Total accepted items consumed from the bin when the server approves a trial. Item types can be mixed. |
| Litter piles to clean | 6 | Piles spread in a full circle around the bin on open ground, from 1 to 100. Pick them up and return the litter. Base stack size is 50; stack-size mods can increase it. Mission litter never adds wrath. |
| Trial cooldown (seconds) | 900 | Wait after an event ends before the same bin can run another event. Admin-placed and admin-approved bins have independent cooldowns: finishing one lets you start another ready bin. Ordinary player bins also apply a personal trial cooldown. Cooldowns survive restarts and pause while offline. Reward cooldowns are separate. |
| Trial time limit (seconds) | 600 | Time to return every litter pile and defeat the wave. Music, weather and the visible countdown follow this timer. The trial continues if its starter dies or leaves. |
| Individual bin settings | Empty | Admins can open a placed bin for its Area, Event, Creatures and Access tabs. Set event radius, litter distances and public base access, preview the boundary, or confirm removal of an empty bin. Zero uses server defaults. Finish its event before editing or removing it. |


### Litter Bin rewards

| Setting | Default | What it does |
| --- | --- | --- |
| Item amount multiplier | 1 | Extra multiplier for coins and materials after a paid bin trial, applied after the combat multiplier. 1 is normal and 2 is double. Does not change Odin's Forgiveness or equipment chance. |
| Equipment chance per player (%) | 40 | Chance for an enchanted equipment reward after a completed cleanup trial. Requires Epic Loot and an eligible item reward. |


### Messages

| Setting | Default | What it does |
| --- | --- | --- |
| Litter warning lines | My ravens brought word of a warrior. All I see is a trail of rubbish. \| You carry a weapon worthy of a saga, yet cannot carry your own scraps? \| Leave another heap, and the wilds will answer. | Random litter warnings. Separate lines with \|. Leave empty to use the default lines. |
| Wrath building lines | The ravens have seen what you left behind. \| Another scrap. Another reason for Odin to watch you. \| Your rubbish remains. So does the Allfather's displeasure. \| The wind carries a warning. Pick up your mess. \| Even the greydwarfs clean up better than this. \| You leave a trail worthy of a pig, warrior. \| Odin counts your deeds. He counts your rubbish too. \| That pile will not vanish because you look away. \| The forest has had enough of your offerings. \| Your saga is beginning to smell. \| A raven lands nearby. It does not look impressed. \| Clean up before the Allfather comes to inspect it himself. | Messages as abandoned drops build wrath. Separate lines with \|. Uses the wrath-notice switch and comment interval. The same line will not play twice in a row. |
| Land arrival lines | I gave you forests, mountains, and a place in the sagas. You repay me with this? \| Enough. Even my ravens refuse to touch what you leave behind. | Odin's arrival lines on land, separated with \|. The cleanup instruction is added automatically. Empty uses the default lines. |
| Ocean arrival lines | You cast your filth into these waters? Then face what rises from them. \| The sea is no dumping ground, warrior. Something below has heard my call. | Odin's warnings at sea, separated with \|. Ocean encounters are combat only. Empty uses the default lines. |
| Fury lines | More rubbish, while I stand before you? Very well. Let the wilds settle this. \| You have spent the last of my patience. Ready your weapon. | Lines when more litter angers Odin during his warning. Separate lines with \|. Empty uses the default lines. |
| Show Odin dialogue | true | Show Odin's arrival, fury, warning and victory lines. Does not hide the countdown or change encounter rules. |
| Show ordinary comments | true | Allow random remarks about litter. Wrath notices and Odin encounter dialogue have their own switches. |
| Show received item rewards | true | Show the items you actually receive and Odin's Forgiveness. Reward cooldown messages also use this setting. |
| Time between pickup reminders (seconds) | 10 | Minimum time between drop reminders. Zero allows a reminder for every drop. |
| Time between ordinary comments (seconds) | 30 | Minimum time between ordinary litter comments. Final warnings and fury dialogue are not delayed. |
| Show notices in the center | true | Show Odin's dialogue in the center as well as above his apparition. |
| Chance of an Odin comment (%) | 25 | Chance of an ordinary roast when a drop's grace period expires. |
| Show wrath notices | true | Show a notice whenever abandoned drops increase wrath. Separate from the random comment chance and the meter. |
| Show drop reminders | true | Show the pickup window or explain why an item, base or ward is exempt. Use Time between pickup reminders to control how often these appear. |


### Mod material choices

| Setting | Default | What it does |
| --- | --- | --- |
| Meadows | Auto | Auto uses loaded biome equipment recipes. Or use ItemName 2-4. An unavailable list falls back to vanilla supplies. Ocean also follows player progression. |
| Black Forest | Auto | Auto uses loaded biome equipment recipes. Or use ItemName 2-4. An unavailable list falls back to vanilla supplies. Ocean also follows player progression. |
| Swamp | Auto | Auto uses loaded biome equipment recipes. Or use ItemName 2-4. An unavailable list falls back to vanilla supplies. Ocean also follows player progression. |
| Mountain | Auto | Auto uses loaded biome equipment recipes. Or use ItemName 2-4. An unavailable list falls back to vanilla supplies. Ocean also follows player progression. |
| Plains | Auto | Auto uses loaded biome equipment recipes. Or use ItemName 2-4. An unavailable list falls back to vanilla supplies. Ocean also follows player progression. |
| Mistlands | Auto | Auto uses loaded biome equipment recipes. Or use ItemName 2-4. An unavailable list falls back to vanilla supplies. Ocean also follows player progression. |
| Ash Lands | Auto | Auto uses loaded biome equipment recipes. Or use ItemName 2-4. An unavailable list falls back to vanilla supplies. Ocean also follows player progression. |
| Deep North | Auto | Auto uses loaded biome equipment recipes. Or use ItemName 2-4. An unavailable list falls back to vanilla supplies. Ocean also follows player progression. |
| Ocean | Auto | Auto uses loaded biome equipment recipes. Or use ItemName 2-4. An unavailable list falls back to vanilla supplies. Ocean also follows player progression. |


### Mod rewards

| Setting | Default | What it does |
| --- | --- | --- |
| Use loaded mod materials | true | Choose supplies from loaded gear recipes and supported creature drops. Missing mods use vanilla supplies. Progression limits still apply. |
| Supply types per reward | 2 | Different materials chosen for each player's completion reward. Supplies are rolled once when the event succeeds. |
| Minimum supply amount | 2 | Minimum amount of each automatically chosen supply, before the normal reward multiplier. |
| Maximum supply amount | 5 | Maximum amount of each automatically chosen supply, before the normal reward multiplier. |
| Include Monstrum supplies | true | Add materials from loaded Monstrum creatures to automatic completion supplies for their biome. Uses the normal supply count and amount. Monstrum is optional. |
| Include Monstrum trophies | false | Also allow regular Monstrum creature trophies in automatic supplies. Boss trophies and unique boss weapons stay in their normal drop tables. |


### Ocean

| Setting | Default | What it does |
| --- | --- | --- |
| Enable ocean encounters | true | Allow Odin to judge littering at sea while the player is aboard a boat. Combat only, with serpents and separate enemy limits. No mission litter or temporary bin at sea. |
| Reward nearby crew | true | Reward living players who stay in the sea battle area, including the person steering. Off requires credited damage. Reward cooldowns still apply. |
| Crew participation time (seconds) | 0 | Time inside an active sea battle needed for crew rewards. Zero rewards nearby crew at victory. Damage can qualify sooner. Dead, disconnected and distant players do not receive rewards. |
| Solo serpent count | 1 | Serpents for a solo player. Creature Level and Loot Control can still affect their strength. |
| Serpents per extra player | 1 | Extra serpents for nearby players when group scaling is enabled. |
| Serpent limit | 3 | Maximum serpents, including group scaling and fury. |
| Encounter radius (metres) | 140 | Room to sail during an Ocean encounter. Leaving stops your local music and weather; the event keeps running until completed or timed out. |
| Keep sea rewards safe | true | At sea, put rewards in the player's inventory when there is room. Overflow and loot from Ocean event enemies float, including serpent scales and Epic Loot drops. Items dropped from a boat also float. |


### Ocean rewards

| Setting | Default | What it does |
| --- | --- | --- |
| Use private progression when available | true | Ocean completion rewards use each recipient's World Advancement Progression private boss keys when enabled. Without private progression, use actual global world boss keys. Off always uses global keys. An empty private key list stays at the starting tier; another player's progress never raises it. |
| Equipment chance per player (%) | 60 | Chance for one Epic Loot equipment reward after completing an Ocean event. Replaces the land equipment chance. Still requires item rewards and equipment rewards to be enabled. Enemy drops are separate. |
| Minimum equipment rarity | Rare | Raise successful Ocean equipment rolls to at least this rarity, within the global maximum and rarities supported by Epic Loot. Does not change enemy drops. |
| Progression supplies (%) | 50 | Extra materials from the progression biome, alongside Ocean materials. 50 gives half that biome's base bundle; 0 disables the bonus. Includes enchanting materials when enabled. Combat and bin reward multipliers still apply. |


### Ocean waves

| Setting | Default | What it does |
| --- | --- | --- |
| Wave mode | Single wave | Sea battles use their own waves: defeat one wave, a fixed number of waves, or survive until the event timer ends. Land wave settings do not apply. |
| Number of waves | 3 | Waves to defeat in Ocean Fixed waves mode. Does not change land events. |
| Time between waves (seconds) | 60 | Minimum time between sea waves. Uses the existing Ocean serpent count and group scaling for each wave. |
| Rest after clearing a wave (seconds) | 15 | Break after the last serpent in a wave dies, before the next wave can arrive. |
| Wait for the current wave to die | true | On prevents overlapping sea waves. Off allows new waves while serpents remain, up to the alive limit. |
| Extra enemies each wave | 0 | Additional sea enemies per later wave. Zero keeps each wave at the normal Ocean group-scaled count. Ocean serpent limits still apply. |
| Maximum living enemies | 6 | Maximum living event enemies in one sea battle. Does not change land limits. |
| Maximum enemies per event | 100 | Total sea enemies across all waves. Survive timer still lasts until the timer ends when this cap is reached. |
| Stop new waves near the end (seconds) | 15 | Do not start another sea wave with less than this much event time remaining. |


### Participation

| Setting | Default | What it does |
| --- | --- | --- |
| Limit returns after death | true | Limit each player's returns during an event. Counts ordinary deaths and Resurrection. Once no returns remain, the next death locks that player out until the event ends. Graves stay in place and can be recovered afterward. |
| Returns allowed per event | 3 | Three allows the starting life and three returns. The fourth death ends participation. Zero locks a player out on their first death. Leaving or reconnecting does not restore returns. Each new event starts fresh. |
| Damage needed for rewards | 20 | Total damage to judgment enemies needed to qualify. Alternatively, return the required number of mission litter piles. |
| Litter stacks needed for rewards | 1 | Cleaned piles needed to qualify instead of dealing damage. When Return litter to the bin is on, a pile counts only after depositing it. Each pile counts once. |


### Raid boss

| Setting | Default | What it does |
| --- | --- | --- |
| Boss stars | -1 | -1 uses normal CLLC/repeat-offender levels. 0 is no stars. Positive values force this many stars before health multipliers. |
| CLLC creature effect | Automatic | For raid bosses made from ordinary creatures. Splitting is excluded to keep event ownership and counts reliable. |
| CLLC infusion | Automatic | Applies a loaded CLLC infusion. Automatic keeps CLLC's roll; None removes it. CLLC must enable infusions. |
| CLLC boss affix | Automatic | For true boss creatures. Clone/summoner affixes are excluded; use the tracked reinforcement settings for adds. CLLC must enable boss affixes. |


### Raid reinforcements

| Setting | Default | What it does |
| --- | --- | --- |
| Boss calls reinforcements | false | Summon helpers while the raid boss is alive. Remaining helpers disappear when the boss is defeated. No extra completion reward per reinforcement wave. |
| Enemy choices | Empty | Weighted enemy names for boss helpers, for example Greydwarf:3:8, Greydwarf_Shaman:1:2. Empty uses this mode's biome enemies. Missing choices fall back to biome enemies. |
| Enemies per reinforcement wave | 2 | Number of helpers the boss calls each time, limited by Maximum living reinforcements and the event total enemy limit. |
| Maximum living reinforcements | 8 | Maximum simultaneous helpers, separate from the raid boss. |
| Time between reinforcements (seconds) | 45 | First helpers arrive this long after the boss. Further waves use the same interval. |


### Repeat offenders

| Setting | Default | What it does |
| --- | --- | --- |
| Enable repeat offender difficulty | true | Repeated visits can add stars to judgment enemies. This affects strength, not the enemy count. |
| Visits for each extra star | 2 | Every this many repeat visits adds a star. With 2, the first two visits have no extra stars and the third can have one. |
| Maximum extra stars | 1 | Limit for added enemy stars. Zero keeps all summons at their normal level. |
| Only strengthen one enemy | true | Apply extra stars to one leader. Turn off to strengthen every summoned enemy. |
| Time to clear repeat offences (seconds) | 3600 | A gap this long between Odin visits clears the repeat-offender count. Remembered across logins. |


### Rewards

| Setting | Default | What it does |
| --- | --- | --- |
| Give biome materials | true | Give each contributor biome materials in addition to the main item reward and Odin's Forgiveness. |
| Give Epic Loot materials | true | Add biome-based Epic Loot enchanting materials to each eligible player's rewards. Epic Loot is required; this setting controls its material rewards. |
| Extra coins per biome tier | 20 | Extra Coins for each biome tier after Meadows. Tiers run Meadows, Black Forest, Swamp, Mountains, Plains, Mistlands, Ashlands, Deep North. Only applies when the main reward is Coins and its base amount is above zero. |
| Wacky MMO experience from event enemies (%) | 33.333333 | Wacky MMO kill XP for ordinary event enemies and reinforcements, including group shares. Default is one third; 0 disables it, 100 is normal and 500 is five times normal. Wild enemies and crafting are unchanged. |
| Wacky MMO experience from event bosses (%) | 33.333333 | Separate kill XP for event mini-bosses and raid bosses. Default is one third; 0 disables it, 100 is normal and 500 is five times normal. Each mode and admin bin can use its own value. |
| Progression source | Each player | Whose boss keys set completion reward tiers. Each player uses their own keys. Group choices use eligible contributors still in the event area when it ends. Event starter keeps their last known tier if offline. Reads World Advancement Progression private keys when enabled; world mode uses actual global keys. Does not change enemies. |
| Limit materials to progression | true | Cap land material and coin rewards to the chosen progression tier. Off uses the event biome directly. Ocean supplies always follow progression. Equipment keeps its separate progression limit. |
| Cleanup reward cooldown (seconds) | 0 | Extra wait between cleanup rewards. Zero gives rewards for each completed cleanup. Event cooldowns still apply. Combat has its own reward cooldown. |
| Reward players who help | true | Reward players who successfully pick up encounter litter or damage judgment enemies when the encounter is resolved. |
| Give rewards after combat | true | Reward contributors after all judgment enemies are defeated. |
| Enable item rewards | true | Give configured item rewards alongside optional Odin's Forgiveness. Items appear at the recipient's feet. |
| Main reward item (prefab name) | Coins | Guaranteed item for each contributor, in addition to biome materials. Use a prefab name, such as Coins. The biome coin bonus applies only when this is Coins. |
| Main reward amount per player | 60 | Base main-item amount for each contributor. Biome coins and the combat multiplier can increase it. Zero disables the main item and its biome coin bonus; materials and blessing can still be earned. |


### Sea Offering

| Setting | Default | What it does |
| --- | --- | --- |
| Enable Sea Offerings | true | Craft and use a Sea Offering to start an Ocean Endless Raid. Does not change ordinary Ocean judgments. |
| Only admins can use offerings | false | On restricts starting Ocean Endless Raids to hosts and server admins. Everyone can still join an active event. |
| Crafting materials | Coins 20, Resin 10, Chitin 5 | Workbench recipe for one Sea Offering. Use exact item prefabs and whole amounts, separated by commas. Up to eight materials. Example: Coins 20, Resin 10. Missing or invalid materials disable crafting until corrected. Syncs automatically. |
| Event duration (seconds) | 600 | Total Ocean Endless Raid time, including the arrival warning. Music, weather and the event boundary follow this timer. Waves use this raid's own Ocean wave settings. |
| Arrival warning (seconds) | 30 | Time to prepare before sea enemies arrive. Limited to half the event duration so the fight has time to begin. |
| Player cooldown (seconds) | 900 | Wait after an Ocean Endless Raid ends before starting another. Separate from wrath and regular Ocean judgments. Admin timer resets can clear it; active events continue. |


### Server

| Setting | Default | What it does |
| --- | --- | --- |
| Maximum simultaneous events | 8 | Server-wide event limit. New events wait until a slot is available. |
| Prevent overlapping event areas | true | Keep event circles apart so their domes and objectives do not conflict. |
| Event announcement destination | Automatic | Send event starts and results through an installed server mod. Automatic uses Discord Connector when installed, otherwise ServerGuard. Both sends through both integrations. Variant Announcements keeps its separate in-game notices. Requires the chosen mod's server webhook and event messages to be enabled. |
| Write detailed logs | false | Log tracked world drops and encounter decisions. |


### Single boss events

| Setting | Default | What it does |
| --- | --- | --- |
| Spawn a single boss instead of waves | false | Replace enemy waves with exactly one creature from this biome's single-boss list. Ignores group enemy counts, repeating waves and wave mini-boss chances. Land events still have their cleanup objective. Applies to new events. |
| Single boss health multiplier | 3 | Health multiplier for the single boss, after its level is applied. Separate from the wave mini-boss multiplier. Summoned bosses do not unlock world progression. |


### Wave bosses

| Setting | Default | What it does |
| --- | --- | --- |
| Enable wave bosses | false | Optionally replace one enemy in a wave with a chosen boss or champion. Each biome has its own choices. Empty lists do not add a boss. |
| Boss chance per wave (%) | 100 | Chance to add one boss on an eligible wave. The boss counts toward the wave and alive limits. |
| First boss wave | 1 | First wave that may include a boss. |
| Waves between bosses | 1 | One means every wave; three means every third wave after First boss wave. |
| Boss health multiplier | 1 | Additional health multiplier for wave bosses. One preserves their normal strength and CLLC level. Event bosses do not unlock world progression or start a separate boss event. |


### World arenas

| Setting | Default | What it does |
| --- | --- | --- |
| Generate arena locations | true | Place biome shrines with a Litter Bin in new worlds. Use Upgrade World to add them to existing worlds. Turning this off keeps existing arenas. |
| Show discovered arenas on the map | true | Reveal each arena's map marker when it is discovered. Does not reveal undiscovered shrines. |
| Protect arena ground | true | Block ordinary building and digging inside land arenas. Does not change terrain. Reload the area after changing this. Admin terrain tools may bypass it. |
| Light the shrine during events | true | Light the rune carvings and braziers in sequence when a shrine event begins. |
| Minimum distance between arenas (metres) | 600 | Minimum spacing between generated arenas. Applies to future location placement. |
| Minimum distance from world centre (metres) | 700 | Keep generated arenas away from the starting area. Applies to future location placement. |
| Maximum ground height difference (metres) | 3 | Prefer reasonably level land across the arena. No flattening is applied. Higher values allow more uneven sites. |
| Starting land event radius (metres) | 40 | Shared radius for land altar events. Applies to existing altars too. A radius set on an individual bin takes priority. Does not move the altar decorations. |
| Starting ocean event radius (metres) | 160 | Shared sailing radius for ocean altars. A radius set on an individual bin takes priority. |
| Litter fills the event area | true | Spread altar litter across the full event radius, leaving two metres inside the boundary. A bin's own maximum litter distance takes priority. Off uses the Litter placement distances. Ocean altars have no litter. |
| Meadows - locations | 6 | Maximum locations in this biome, shared between two layouts. Zero prevents new placements. Existing locations stay. Suitable terrain may limit the actual count. |
| Black Forest - locations | 6 | Maximum locations in this biome, shared between two layouts. Zero prevents new placements. Existing locations stay. Suitable terrain may limit the actual count. |
| Swamp - locations | 6 | Maximum locations in this biome, shared between two layouts. Zero prevents new placements. Existing locations stay. Suitable terrain may limit the actual count. |
| Mountain - locations | 6 | Maximum locations in this biome, shared between two layouts. Zero prevents new placements. Existing locations stay. Suitable terrain may limit the actual count. |
| Plains - locations | 6 | Maximum locations in this biome, shared between two layouts. Zero prevents new placements. Existing locations stay. Suitable terrain may limit the actual count. |
| Mistlands - locations | 6 | Maximum locations in this biome, shared between two layouts. Zero prevents new placements. Existing locations stay. Suitable terrain may limit the actual count. |
| Ash Lands - locations | 6 | Maximum locations in this biome, shared between two layouts. Zero prevents new placements. Existing locations stay. Suitable terrain may limit the actual count. |
| Deep North - locations | 6 | Maximum locations in this biome, shared between two layouts. Zero prevents new placements. Existing locations stay. Suitable terrain may limit the actual count. |
| Ocean - locations | 6 | Maximum locations in this biome, shared between two layouts. Zero prevents new placements. Existing locations stay. Suitable terrain may limit the actual count. |


### Wrath

| Setting | Default | What it does |
| --- | --- | --- |
| Pickup grace period (seconds) | 30 | Time to retrieve a successful world drop before it counts as litter. |
| Track wrath | true | Enable wrath tracking and encounters. |
| Wrath required for a visit | 100 | Odin can visit when wrath reaches this amount. Each abandoned stack adds the configured wrath per dropped stack. |
| Wrath per dropped stack | 1 | Wrath per abandoned world stack, regardless of stack size. Retrieval reverses that stack's contribution. |
