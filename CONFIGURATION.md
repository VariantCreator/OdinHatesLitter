# Settings

File: `BepInEx/config/Dova.OdinHatesLitter.cfg`

**Multiplayer:** server settings apply automatically. Only admins can change them; hosts control their own worlds. Install this build on the server and every client, with BepInEx, Jotunn, and Epic Loot 0.14.10 or newer.

With Configuration Manager, open **F1 > Odin Hates Litter > Admin and server** to check sync, preview rewards, clear your own wrath, or use **Reset all timers**. These controls are for admins and hosts.

The menu groups settings into 13 categories. Existing config-file sections and saved values remain unchanged; the full file reference below uses those original section names.

| Menu category | Includes |
| --- | --- |
| General and display | Messages, wrath meter, event counter and screen position |
| Admin and server | Sync, admin overrides and public bin approval |
| Wrath and encounters | Dropped items, warnings, timers, fury and forgiveness |
| Enemies | Counts, scaling, spawn distances and loot chance per biome |
| Enemy waves | Wave mode, total waves, timing, mini-bosses and single-boss events |
| Biome creatures | Enemy, mini-boss and single-boss lists for every biome |
| Atmosphere | Music, storms and event outline |
| Cleanup | Litter, placement, hints and replacement piles |
| Litter Bin | Crafting, offerings, trials and individual bin settings |
| Ocean | Sea enemies, sailing area and crew rewards |
| Rewards | Participation, return limits, Wacky MMO XP, items and stamina blessing |
| Biome rewards | Ordinary and Epic Loot materials |
| Equipment rewards | Gear chances, equipment lists and rarities |

The event display starts lower to leave room for status effects. Adjust **General and display > Distance from top of screen (pixels)** to move it. Larger values move it down.

Old defaults upgrade automatically. Custom settings stay in place.

Default wrath is 100. Peaceful cleanup grants the base rewards; combat doubles coins and materials. The bin and HUD count litter carried by other connected players when showing your remaining target. Music and weather are together under Atmosphere; detailed logs are under Server.

## New in 1.5.1

- **Rewards > Participation:** Three returns after death by default. A fourth death locks that player outside the event until it ends. Ordinary respawns and Resurrection share the allowance. Reconnecting does not reset it. Graves can be recovered after the event.
- **Enemy waves:** Turn on **Spawn a single boss instead of waves** for one biome champion with no adds or later waves. Adjust its health here and choose creatures under **Biome creatures**. Land cleanup still applies.
- **Enemies:** Each biome has an enemy loot percentage. **Allow normal enemy drops** must also be on. This is one chance per enemy for its normal drop bundle, including Epic Loot, and does not change completion rewards.
- **Rewards:** **Wacky MMO experience from event enemies (%)** defaults to one third. It applies once to kill XP and group shares; other XP is unchanged.
- **Bin settings:** Opening a placed bin shows its own panel to admins and the host. Set event radius and litter distances, preview its boundary, or approve public base access. Each bin keeps its own settings across restarts. Changing or resetting one bin leaves the others alone. The server saves and syncs changes; the nearby-bin controls in F1 still work.
- **Admin and server:** Admin bins are protected from damage and accidental removal, including debug mode. Empty the bin and finish its event, then use **Remove this bin > Confirm removal** in its settings. Materials are not returned.
- Events resume from the last world save after a restart, with the timer paused while offline. Keep the server's `BepInEx/config/Dova.OdinHatesLitter.events` folder with its world backups.
- Enemies spread around the full circle within their configured spawn distances. Fixed-wave events show the total and waves left.

## Event dome

An invisible wall follows the event circle and has a closed roof. Players inside get a 10-second warning before it seals. Leave during that warning or stay until the event ends. Late helpers can enter by default; entering commits them too. Event enemies stay inside, and a brief golden ripple shows where players or their boat touch the wall.

Three returns allow the starting life plus three revives or normal respawns. After the fourth death, entry and Resurrection inside that event are blocked until it ends. Death still allows normal respawning. If an exhausted player's bed is inside, the mod chooses an outside spawn before the player appears. Portals cannot bypass the dome. Return counts and participation persist through reconnects and server restarts.

Ocean domes wait until combat starts, allowing the warning to follow the boat. The crew's boat follows the boundary too. The dome disappears with the event; it does not add time to the ten-minute event limit.

Find the **Dome** settings under **Atmosphere**. Adjust the seal warning, late entry, player and enemy confinement, height and messages. **Admins can cross the dome** is off by default and provides a maintenance bypass without restoring returns or rewards. Turning off **Enable event dome** releases all domes immediately. All of these settings are controlled and synced by the server.

## Start here

| You want to change | Section and setting |
| --- | --- |
| Time to retrieve an item | Wrath → Pickup grace period (seconds) |
| How often Odin visits | Wrath → Wrath required for a visit; Encounters → Encounter cooldown (seconds) |
| Solo and group difficulty | Enemies → Solo enemy count, Enemies added per extra player, Enemy limit including fury |
| Repeating waves, growth and limits | Enemy waves |
| Creatures and chances in each biome | Biome enemies |
| One boss or champion per wave | Wave bosses; Biome wave bosses |
| Admin events near bases or wards | Admin tools |
| A particular bin's event and search radius | Open the bin's admin panel, or Litter Bin → Individual bin settings |
| Litter radius, spacing, rock tops and layout | Cleanup placement |
| Help finding missing piles | Cleanup → Show hints for missing litter |
| Visible event outline | Atmosphere → Show event boundary |
| Event wall, late entry and seal warning | Event dome (under Atmosphere in F1) |
| CLLC difficulty and creature loot | Enemies → Use CLLC enemy levels, Allow normal enemy drops |
| Reward size | Rewards → Main reward amount per player, Extra coins per biome tier; Combat rewards → Combat item reward multiplier |
| Reward cooldowns | Rewards → Cleanup reward cooldown (seconds); Combat rewards → Combat reward cooldown (seconds) |
| Stamina strength and duration | Stamina blessing |
| Equipment drop chance | Epic Loot equipment → Equipment chance per player (%) |
| Bin building materials and who can build it | Litter Bin → Building materials, Only admins can build bins |
| Pile count and returning litter | Cleanup; Litter Bin > Litter piles to clean |
| Litter placement on hills and near plants | Cleanup placement → Allow uneven ground, Avoid trees and bushes, Plant clearance |
| Replacement litter when pickups stop | Cleanup → Time without finding litter (seconds), Time between replacement piles (seconds) |
| Cleanup trial cost and timing | Litter Bin |
| Trial shortcut | Litter Bin > Trial shortcut modifier |
| Event countdown | Display > Show event timer |
| Odin warning text | Messages > Litter warning lines, Land arrival lines, Ocean arrival lines, Fury lines |
| Better trial equipment chance | Litter Bin rewards |
| Serpents and sailing room | Ocean |
| Who qualifies for rewards | Participation |
| Fewer popups | Messages |
| Ignore items such as stone | Drop protection → Ignored item prefabs |

## How rewards work

Each eligible player earns their own coins, materials, and 15% stamina regeneration for 3 minutes. The base coin reward is 60, with larger material bundles. Combat doubles ordinary item rewards. Separate cleanup and trial item multipliers can adjust those amounts. Cleanup and combat reward cooldowns are separate and default to zero, allowing rewards for every completed event. At sea, rewards go into your inventory; overflow floats.

Wrath resets when a judgment starts and when the encounter ends, including a timeout. Death or leaving does not cancel an active event; other players can finish it. Event summons disappear at the end. The cleanup countdown stays visible while Odin waits; the wrath meter clears afterward. Old litter does not start another encounter.

Creature Level and Loot Control is optional. Its level roll follows the installed CLLC settings, while repeat-offender stars act as a minimum. Other CLLC effects and infusions apply, but splitting and spawn multipliers cannot add enemies to the wave. Turn on Allow normal enemy drops to use the ordinary loot rules, including CLLC's loot settings. Separate per-player rewards still apply.

Shared biome materials apply to both outcomes. Extra cleanup items and Extra combat items are separate tables. Each outcome also has its own item-bundle chance. For entirely custom outcome tables, set the main reward amount to zero and turn off biome and Epic Loot material rewards.

Item table format: `IronScrap 6-10, Chain 1-2 @ 50%`. Amounts are per player, not shared. Use the item's prefab name. Empty tables add nothing; unavailable prefabs are skipped. Bundles are limited to 24 item types and 64 dropped stacks per player.

Epic Loot is required on the server and clients. Equipment has a 15% chance after combat or 40% after a Litter Bin trial. Pools include weapons, shields and armor, including compatible loaded gear. Equipment follows player and world progress by default. Mythic and Ancient are available in later biomes. The server rolls each player's item and effects.

Build a Litter Bin with 10 wood and 5 stone in an open area away from bases and wards. Put 20 accepted materials inside, close it, then use the challenge action shown on the bin (Alt + E by default; change Trial shortcut modifier to use Ctrl or Shift). Pick up the six mission piles, press E at the bin to deposit them, and defeat the wave within 10 minutes. Placed-bin trials start their wave immediately; the two-minute warning applies only to automatic wrath encounters. Piles spread around the bin; the configurable maximum is 100. Litter is an inventory item with a base stack size of 50; stack-size mods can increase it. Keep it in your main inventory when returning it. Death sends it through the normal tombstone system, and another player can return recovered or traded litter. Piles use open ground all around the bin and avoid low plants and bushes. High tree canopies no longer block the whole clearing. Allow uneven ground skips slope and height checks; Avoid trees and bushes and Plant clearance control foliage checks. Solid trunks, structures and water remain blocked. The bin cannot be damaged or removed during its event. Protection ends with the event, after completion or its ten-minute limit. Placed bins remain afterward; Odin's temporary bins disappear. Changing the event time limit also changes the protection duration. The bin has a 15-minute trial cooldown; reward cooldowns still apply. Failed starts return the offering, but abandoning a started trial does not.

Regular land judgments summon their own temporary return bin and mission piles; the original dropped items are not the mission objective.

Ocean judgments can begin while standing, seated, or steering a boat in the Ocean biome. Odin appears above the water beside the bow and follows the boat during his warning. His apparition does not require a deep-water spawn point; serpents still need suitable water. These events are combat only, without mission litter or a temporary bin. They start with one serpent for a solo player, add one per nearby helper, and cap at three. The area extends 140 metres to give you room to sail.

To qualify on land by default, deal 20 damage to judgment enemies or return one mission litter pile. At sea, living nearby crew also qualify, including the person steering. Reward nearby crew and Crew participation time control this option. Stay alive and nearby until the encounter finishes. The progress display shows contribution eligibility; reward cooldowns still apply.

Wrath begins to fade after 10 minutes without more litter, then loses one point each minute. It pauses during warnings and combat. Repeated visits can strengthen one enemy: the first two visits have no extra star, the third can have one. An hour between visits clears this count.

Shuffle encounter music uses the editable Music playlist for any biome. Readable boss names and Event 1 through Event 4 work, as do exact loaded track names. The default is one looping track per event; set Time between music tracks above zero to enable mid-event changes. All nearby players follow the same order. Normal cinematic and real boss priorities still apply.

Shuffle storms chooses independently from Storm playlist. Match event duration keeps the music and weather tied to the event countdown. Turning it off uses Atmosphere duration instead. Both stop when the event finishes. Each new event gets a fresh selection.

Default timing:

| Timer | Default |
| --- | --- |
| Dropped-item pickup grace | 30 seconds |
| Automatic wrath cleanup warning | 120 seconds |
| Full wrath encounter, including warning | 10 minutes |
| Placed-bin trial, with immediate enemies | 10 minutes |
| Minimum time between judgments, measured from the start | 5 minutes |
| Stamina blessing | 3 minutes |
| Ordinary wrath meter visibility | 8 seconds after a change |
| Litter rescue | First replacement after 1 minute without a pickup; one per minute afterward |

Encounter cooldown controls Next judgment and applies to existing waits when an admin changes it. An active event must finish before another begins. Next judgment and active-event countdowns stay visible even when the ordinary wrath meter fades.

Move hard-to-reach litter replaces an uncollected ground pile closer to the bin after nobody finds litter for a while. Time without finding litter defaults to 60 seconds. Every successful pickup by any player restarts this shared wait. Afterward, another pile is replaced each minute until pickups resume. It preserves the required total, skips carried and returned litter, and does not run at sea. Both timers are configurable.

The admin-only Reset all timers button clears judgment, reward and bin cooldowns for everyone, including players who join later. It keeps current events, their countdowns and wrath intact. The reset is saved per world in the server config folder.

## Enemy waves and placement

Single wave preserves the original difficulty. Fixed waves requires the configured number; Until cleanup keeps spawning while litter remains, then requires the surviving enemies to be defeated. Ocean has no litter, so Until cleanup uses the fixed wave count there. Survive timer keeps the event running until its timer ends; mission litter must still be returned to win. All modes share the same event timer, music and weather. Waves do not extend the event.

Time between waves and Rest after a cleared wave both apply. Turn off Clear enemies before next wave to allow overlap. Maximum enemies alive prevents overcrowding, and Total enemy limit caps the whole encounter. Individual waves still respect the existing land or Ocean enemy limit. The configurable caps are 100 living enemies and 1,000 enemies in total; defaults remain much lower. If a fixed wave count cannot fit before the event deadline, lower the count or increase the event time.

Biome enemies accepts `Greydwarf 70 8, Greydwarf_Elite 20 2, Greydwarf_Shaman 10 1`: name, relative weight, maximum per wave. A name alone has weight 1. Empty uses the automatic biome pool. Missing or unsuitable mod creatures are skipped; if none of a custom list remain available, automatic biome enemies are used. Bosses use their own biome lists. Enable wave bosses and choose the first wave, frequency, chance and health multiplier. A boss replaces one normal wave slot and counts toward the limits. Event boss copies do not unlock vanilla boss progression. Choose swimming creatures for Ocean lists.

Admin and server has separate personal base and ward overrides. These are off by default. Public base trials are enabled by default for new admin-placed bins, including normal Infinity Hammer placement. The server verifies the admin and saves approval for that exact bin and world, so anyone can use it while the admin is offline. Normal players cannot approve bins or place their own bins inside bases. Ward protection and physical clearance still apply.

For an older bin, stand within 8 metres and open Litter Bin > Individual bin settings. Use Approve public base trials or Revoke public base trials. The same panel sets its event radius and litter search distances. Zero uses global defaults. Resetting the radius keeps its approval. A copied or rebuilt bin has a different identity and needs its own approval. Finish the active event before changing that bin.

Biome creatures comes filled with local enemy and mini-boss examples. Empty old defaults upgrade; custom lists stay intact. Meadows and Ocean use local creature champions, with strength adjustable through Boss health multiplier. Optional mini-bosses remain off until Enable wave bosses is turned on under Enemy waves.

Cleanup placement controls the inner and outer litter radius, spacing, even circles, random scatter or clusters. Rock tops are optional and must be wide enough, low enough and within the slope limit. Group litter scaling fixes the objective when the event starts. Optional golden hints appear after a shared period without successful pickups. Replacement piles use the same placement rules. Mission litter clears from loaded inventories when its event ends; saved containers and tombstones are cleaned when loaded.

The Solo, Group and Survival preset buttons change only the settings listed beside them. They never apply automatically. Preview this biome's enemy choices lists configured creatures without spawning anything.

## Modded rewards and updates

Include Epic Loot registered gear reads the currently loaded biome pools, including compatible Therzie and other equipment. Custom equipment entries accept relative weights, such as `SwordBronze 2, SwordFlint_TW 1`. Registered equipment weight controls the additional pool. Excluded equipment supports names and `*` wildcards; Epic Loot's denied-item list is also respected. Equipment type balancing and progression limits still apply.

Missing items are skipped. If Epic Loot's optional equipment API changes, the equipment bonus is skipped with a single warning and ordinary rewards continue. If CLLC's API changes, event creatures fall back to normal level handling. These fallbacks reduce disruption from mod updates; a breaking Valheim or dependency update can still require a new build. Keep the same Odin Hates Litter build and content mods on the server and clients.

## Full reference

Defaults below apply to new configs. Existing custom values stay in place.

### Admin tools

| Setting | Default | What it does |
| --- | --- | --- |
| Admins can start events inside bases | false | Allow admins and the host to start judgments and bin trials near workbenches and other base objects. Other players keep the normal protection checks. |
| Admins can start events inside wards | false | Separate admin override for event placement inside wards. Does not grant access to another player's chest. |
| Admin-placed bins allow public trials inside bases | true | New bins placed by an admin or host are approved by the server so anyone can start their trials near bases. Approval stays with that bin across restarts. Existing bins can be approved or revoked under Individual bin settings. Ordinary players cannot approve bins or place their own inside bases. Ward access is unchanged. |
| Protect admin-placed bins | true | Protect admin-placed and admin-approved Litter Bins from damage and accidental removal, even in debug mode. Admins can still use Remove this bin in its settings after emptying it and finishing its event. Normal player bins keep the usual rules. |


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


### Cleanup

| Setting | Default | What it does |
| --- | --- | --- |
| Scale litter with nearby players | false | Add litter for nearby living players when an event begins. The objective stays fixed after the event starts. |
| Litter per extra player | 2 | Additional piles for each nearby player when litter scaling is enabled. |
| Group litter limit | 100 | Maximum piles after group scaling. Applies to both bin trials and regular wrath cleanup. |
| Move replacement piles closer | true | Prefer the inner part of the configured litter area when replacing hard-to-find piles. Off uses the entire search area. |
| Show hints for missing litter | false | After no successful pickup for a while, show a small pulsing golden marker above uncollected piles. Carried litter is never marked. |
| Time before litter hints (seconds) | 60 | Every successful pickup by any participant restarts this shared hint timer. |
| Litter hint visibility (metres) | 35 | How close a player must be to see a missing-pile hint. |
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
| Maximum distance from bin (metres) | 14 | Outer edge of the litter search area. Always kept at least 5 metres inside the event boundary. |
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
| Item amount multiplier | 1 | Scale coins and materials after peaceful cleanup. 1 is normal, 2 is double, and 0 disables these items. Does not change the stamina blessing or equipment chance. |
| Item reward chance (%) | 100 | Chance for each eligible player to receive the cleanup item bundle. The stamina blessing is separate. |
| Extra cleanup items | Empty | Extra items in addition to the biome bundle. Example: Honey 2-4 @ 50%. Empty adds nothing. |
| Give rewards for peaceful cleanup | true | Reward each qualifying helper when all litter is returned before enemies arrive. Uses cleanup items, chance, multiplier and cooldown, plus the stamina blessing. |


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
| Encounter cooldown (seconds) | 300 | Controls the Next judgment countdown. Minimum time between Odin visits, starting when an event begins. Stored across relogs. Zero removes this wait; active events must still finish first. |
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


### Epic Loot equipment

| Setting | Default | What it does |
| --- | --- | --- |
| Registered equipment weight | 1 | Relative weight of gear added by Epic Loot, including Therzie and other compatible mods. Custom choices use weight 1 unless a weight follows the prefab name. Zero disables the registered pool. |
| Excluded equipment | Empty | Equipment prefab names to leave out of rewards, separated by commas. Supports * wildcards. Epic Loot's own denied-item list is also respected. |
| Include earlier biome equipment | false | Also include registered gear from earlier biome tiers. Off keeps the current tier's equipment. Progression limits still apply. |
| Enable equipment bonus | true | Chance to award one enchanted weapon or armor piece to each eligible contributor. Requires Epic Loot on the server and clients. |
| Allow equipment for cleanup | false | Also roll the equipment bonus after peaceful cleanup. Off means combat victories only. |
| Equipment chance per player (%) | 15 | Separate equipment roll for each player who earns an item bundle. At most one equipment item per reward. |
| Maximum equipment rarity | Ancient | Highest allowed equipment rarity. Unavailable tiers in an older Epic Loot version are skipped. |
| Balance equipment types | true | Choose a weapon type or armor slot first, then an item. This keeps large armor lists from crowding out other gear. |
| Avoid recent equipment repeats | true | Avoid the last three equipment rewards for each player while the server is running, when another choice is available. |
| Include Epic Loot registered gear | true | Add loaded equipment from Epic Loot's biome item lists, including compatible modded gear. Your custom equipment choices are still included. |
| Match equipment to player progress | true | Cap equipment by bosses the recipient has defeated, and by the world's progress. Ocean equipment uses this progression tier. |


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
| Meadows | Club, AxeStone, AxeFlint, SpearFlint, KnifeFlint, Bow, ShieldWood, ShieldWoodTower, HelmetLeather, ArmorLeatherChest, ArmorLeatherLegs, CapeDeerHide | Equipment prefab names, separated by commas. Loaded Epic Loot gear can also join the pool. Empty Ocean uses player progress. |
| Black Forest | SwordBronze, AxeBronze, MaceBronze, SpearBronze, AtgeirBronze, KnifeCopper, BowFineWood, ShieldBronzeBuckler, HelmetBronze, ArmorBronzeChest, ArmorBronzeLegs, HelmetTrollLeather, ArmorTrollLeatherChest, ArmorTrollLeatherLegs, CapeTrollHide | Equipment prefab names, separated by commas. Loaded Epic Loot gear can also join the pool. Empty Ocean uses player progress. |
| Swamp | SwordIron, AxeIron, MaceIron, SpearElderbark, AtgeirIron, SledgeIron, Battleaxe, BowHuntsman, ShieldIronBuckler, ShieldBanded, ShieldIronTower, HelmetIron, ArmorIronChest, ArmorIronLegs, HelmetRoot, ArmorRootChest, ArmorRootLegs | Equipment prefab names, separated by commas. Loaded Epic Loot gear can also join the pool. Empty Ocean uses player progress. |
| Mountains | SwordSilver, MaceSilver, SpearWolfFang, KnifeSilver, BattleaxeCrystal, BowDraugrFang, ShieldSilver, HelmetDrake, ArmorWolfChest, ArmorWolfLegs, CapeWolf, HelmetFenring, ArmorFenringChest, ArmorFenringLegs, FistFenringClaw | Equipment prefab names, separated by commas. Loaded Epic Loot gear can also join the pool. Empty Ocean uses player progress. |
| Plains | SwordBlackmetal, AxeBlackMetal, KnifeBlackMetal, AtgeirBlackmetal, MaceNeedle, BowDraugrFang, ShieldBlackmetal, ShieldBlackmetalTower, HelmetPadded, ArmorPaddedCuirass, ArmorPaddedGreaves, CapeLox, CapeLinen | Equipment prefab names, separated by commas. Loaded Epic Loot gear can also join the pool. Empty Ocean uses player progress. |
| Mistlands | SwordMistwalker, THSwordKrom, SpearCarapace, AtgeirHimminAfl, SledgeDemolisher, KnifeSkollAndHati, BowSpineSnap, CrossbowArbalest, StaffFireball, StaffIceShards, StaffShield, StaffSkeleton, ShieldCarapace, ShieldCarapaceBuckler, HelmetCarapace, ArmorCarapaceChest, ArmorCarapaceLegs, HelmetMage, ArmorMageChest, ArmorMageLegs, CapeFeather | Equipment prefab names, separated by commas. Loaded Epic Loot gear can also join the pool. Empty Ocean uses player progress. |
| Ashlands | SwordNiedhogg, THSwordSlayer, SpearSplitner, MaceEldner, AxeBerzerkr, BowAshlands, CrossbowRipper, StaffClusterbomb, StaffLightning, StaffGreenRoots, StaffRedTroll, ShieldFlametal, ShieldFlametalTower, HelmetFlametal, ArmorFlametalChest, ArmorFlametalLegs, HelmetAshlandsMediumHood, ArmorAshlandsMediumChest, ArmorAshlandsMediumLegs, HelmetMage_Ashlands, ArmorMageChest_Ashlands, ArmorMageLegs_Ashlands, CapeAsh, CapeAsksvin | Equipment prefab names, separated by commas. Loaded Epic Loot gear can also join the pool. Empty Ocean uses player progress. |
| Deep North | SwordGold, THSwordGold, SwordGold_FrostFire, THSwordGold_FrostFire, SwordGold_BloodLightning, THSwordGold_BloodLightning, ArmorDeepNorthMageChest, ArmorDeepNorthMagelegs | Equipment prefab names, separated by commas. Loaded Epic Loot gear can also join the pool. Empty Ocean uses player progress. |
| Ocean | Empty | Equipment prefab names, separated by commas. Loaded Epic Loot gear can also join the pool. Empty Ocean uses player progress. |


### Equipment rarities

| Setting | Default | What it does |
| --- | --- | --- |
| Meadows | Magic 95, Rare 5 | Rarity names with weights, such as Legendary 70, Mythic 29, Ancient 1. Names alone have equal odds. Empty Ocean uses player progress. |
| Black Forest | Magic 70, Rare 30 | Rarity names with weights, such as Legendary 70, Mythic 29, Ancient 1. Names alone have equal odds. Empty Ocean uses player progress. |
| Swamp | Rare 80, Epic 20 | Rarity names with weights, such as Legendary 70, Mythic 29, Ancient 1. Names alone have equal odds. Empty Ocean uses player progress. |
| Mountains | Rare 50, Epic 45, Legendary 5 | Rarity names with weights, such as Legendary 70, Mythic 29, Ancient 1. Names alone have equal odds. Empty Ocean uses player progress. |
| Plains | Epic 80, Legendary 20 | Rarity names with weights, such as Legendary 70, Mythic 29, Ancient 1. Names alone have equal odds. Empty Ocean uses player progress. |
| Mistlands | Epic 50, Legendary 45, Mythic 5 | Rarity names with weights, such as Legendary 70, Mythic 29, Ancient 1. Names alone have equal odds. Empty Ocean uses player progress. |
| Ashlands | Legendary 70, Mythic 29, Ancient 1 | Rarity names with weights, such as Legendary 70, Mythic 29, Ancient 1. Names alone have equal odds. Empty Ocean uses player progress. |
| Deep North | Legendary 30, Mythic 65, Ancient 5 | Rarity names with weights, such as Legendary 70, Mythic 29, Ancient 1. Names alone have equal odds. Empty Ocean uses player progress. |
| Ocean | Empty | Rarity names with weights, such as Legendary 70, Mythic 29, Ancient 1. Names alone have equal odds. Empty Ocean uses player progress. |


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
| Trial cooldown (seconds) | 900 | Wait between trials for the bin and the player. Both cooldowns survive server restarts and pause while offline. Normal reward cooldowns also apply. |
| Trial time limit (seconds) | 600 | Time to return every litter pile and defeat the wave. Music, weather and the visible countdown follow this timer. The trial continues if its starter dies or leaves. |
| Individual bin settings | Empty | Admins can open a placed bin for its own settings panel, or use these nearby-bin controls. Set event radius, litter distances and public base access, preview the boundary, or confirm removal of an empty bin. Zero uses server defaults. Finish its event before editing or removing it. |


### Litter Bin rewards

| Setting | Default | What it does |
| --- | --- | --- |
| Item amount multiplier | 1 | Extra multiplier for coins and materials after a paid bin trial, applied after the combat multiplier. 1 is normal and 2 is double. Does not change the stamina blessing or equipment chance. |
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
| Show received item rewards | true | Show the items you actually receive and the stamina blessing. Reward cooldown messages also use this setting. |
| Time between pickup reminders (seconds) | 10 | Minimum time between drop reminders. Zero allows a reminder for every drop. |
| Time between ordinary comments (seconds) | 30 | Minimum time between ordinary litter comments. Final warnings and fury dialogue are not delayed. |
| Show notices in the center | true | Show Odin's dialogue in the center as well as above his apparition. |
| Chance of an Odin comment (%) | 25 | Chance of an ordinary roast when a drop's grace period expires. |
| Show wrath notices | true | Show a notice whenever abandoned drops increase wrath. Separate from the random comment chance and the meter. |
| Show drop reminders | true | Show the pickup window or explain why an item, base or ward is exempt. Use Time between pickup reminders to control how often these appear. |


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
| Keep sea rewards safe | true | At sea, put rewards in the player's inventory when there is room. Overflow floats on the water. Litter dropped from a boat also floats so it can be recovered. |


### Participation

| Setting | Default | What it does |
| --- | --- | --- |
| Limit returns after death | true | Limit each player's returns during an event. Counts ordinary deaths and Resurrection. Once no returns remain, the next death locks that player out until the event ends. Graves stay in place and can be recovered afterward. |
| Returns allowed per event | 3 | Three allows the starting life and three returns. The fourth death ends participation. Zero locks a player out on their first death. Leaving or reconnecting does not restore returns. Each new event starts fresh. |
| Damage needed for rewards | 20 | Total damage to judgment enemies needed to qualify. Alternatively, return the required number of mission litter piles. |
| Litter stacks needed for rewards | 1 | Cleaned piles needed to qualify instead of dealing damage. When Return litter to the bin is on, a pile counts only after depositing it. Each pile counts once. |


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
| Give biome materials | true | Give each contributor biome materials in addition to the main item reward and stamina blessing. |
| Give Epic Loot materials | true | Add biome-based Epic Loot enchanting materials to each eligible player's rewards. Epic Loot is required; this setting controls its material rewards. |
| Extra coins per biome tier | 20 | Extra Coins for each biome tier after Meadows. Tiers run Meadows, Black Forest, Swamp, Mountains, Plains, Mistlands, Ashlands, Deep North. Only applies when the main reward is Coins and its base amount is above zero. |
| Wacky MMO experience from event enemies (%) | 33.333333 | Share of normal Wacky MMO kill experience, including group shares. The default is one third. Zero disables this experience; 100 keeps the normal rate. Wild enemies, crafting and other experience are unchanged. Wacky MMO is optional. |
| Cleanup reward cooldown (seconds) | 0 | Extra wait between cleanup rewards. Zero gives rewards for each completed cleanup. Event cooldowns still apply. Combat has its own reward cooldown. |
| Reward players who help | true | Reward players who successfully pick up encounter litter or damage judgment enemies when the encounter is resolved. |
| Give rewards after combat | true | Reward contributors after all judgment enemies are defeated. |
| Enable item rewards | true | Give configured item rewards alongside the optional stamina blessing. Items appear at the recipient's feet. |
| Main reward item (prefab name) | Coins | Guaranteed item for each contributor, in addition to biome materials. Use a prefab name, such as Coins. The biome coin bonus applies only when this is Coins. |
| Main reward amount per player | 60 | Base main-item amount for each contributor. Biome coins and the combat multiplier can increase it. Zero disables the main item and its biome coin bonus; materials and blessing can still be earned. |


### Server

| Setting | Default | What it does |
| --- | --- | --- |
| Write detailed logs | false | Log tracked world drops and encounter decisions. |


### Single boss events

| Setting | Default | What it does |
| --- | --- | --- |
| Spawn a single boss instead of waves | false | Replace enemy waves with exactly one creature from this biome's single-boss list. Ignores group enemy counts, repeating waves and wave mini-boss chances. Land events still have their cleanup objective. Applies to new events. |
| Single boss health multiplier | 3 | Health multiplier for the single boss, after its level is applied. Separate from the wave mini-boss multiplier. Summoned bosses do not unlock world progression. |


### Stamina blessing

| Setting | Default | What it does |
| --- | --- | --- |
| Enable stamina blessing | true | Give each eligible contributor extra stamina regeneration after cleanup or victory. The reward cooldown also applies to this blessing. |
| Extra stamina regeneration (%) | 15 | Extra stamina regeneration percentage from Odin's reward. |
| Blessing duration (seconds) | 180 | Duration of the stamina reward in seconds. |


### Wave bosses

| Setting | Default | What it does |
| --- | --- | --- |
| Enable wave bosses | false | Optionally replace one enemy in a wave with a chosen boss or champion. Each biome has its own choices. Empty lists do not add a boss. |
| Boss chance per wave (%) | 100 | Chance to add one boss on an eligible wave. The boss counts toward the wave and alive limits. |
| First boss wave | 1 | First wave that may include a boss. |
| Waves between bosses | 1 | One means every wave; three means every third wave after First boss wave. |
| Boss health multiplier | 1 | Additional health multiplier for wave bosses. One preserves their normal strength and CLLC level. Event bosses do not unlock world progression or start a separate boss event. |


### Wrath

| Setting | Default | What it does |
| --- | --- | --- |
| Pickup grace period (seconds) | 30 | Time to retrieve a successful world drop before it counts as litter. |
| Track wrath | true | Enable wrath tracking and encounters. |
| Wrath required for a visit | 100 | Odin can visit when wrath reaches this amount. Each abandoned stack adds the configured wrath per dropped stack. |
| Wrath per dropped stack | 1 | Wrath per abandoned world stack, regardless of stack size. Retrieval reverses that stack's contribution. |

