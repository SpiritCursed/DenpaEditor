# DenpaEditor

Comprehensive Editor for the 3DS Title "The Denpa Men: They Came by Wave"

**Important:** You need your own **legally obtained copy of The Denpa Men: They Came by Wave (USA)**, with an **already decrypted application** in a `.3ds`/`.cci` ROM or standalone `.cxi`/`.app` file. No ROM is included. `.cia` files are not supported.

A Windows ROM editor for items, characters, enemies, dungeons and more. Create custom variants and share your changes as **BPS patches**.

<img width="1910" height="1030" alt="DenpaEditor dungeon view with textures, objects and encounter markers" src="https://github.com/user-attachments/assets/78e3c005-4c42-4559-bcbd-b716fc9413b7" />

## Getting started

1. Keep an untouched, decrypted ROM as your **clean source**.
2. Make a separate copy to edit.
3. Run **DenpaEditor.exe** on 64-bit Windows and choose **Files → Open ROM**.
4. Open your working copy, then select **Database**, **Dungeons** or **Island**.
5. Save your edits. Database and island pages have Save/Reset controls; supported dungeon placement and painting operations save automatically.
6. To share your changes, choose **Export BPS**, select the clean source ROM first, then choose where to write the patch.

Saving changes the opened working ROM directly. There is no separate project file. Reopen that ROM to continue editing.

The EXE runs without a separate .NET installation.

<details>
<summary>Feature index</summary>

- [Database](#database)
- [Dungeons](#dungeons)
- [Island and overworld](#island-and-overworld)
- [Saving and BPS patches](#saving-and-bps-patches)
- [Controls](#controls)
- [Catalogs and capacity limits](#catalogs-and-capacity-limits)
- [Current limitations](#supported-inputs-and-current-limitations)

</details>

## Feature overview

| Tab | Features |
| --- | --- |
| **Files** | Open ROMs, inspect the ROM summary and export BPS patches. |
| **Database** | Original and custom items, Denpa Men and antennas, Shop Data, Enemies and Meta starting settings. |
| **Dungeons** | Floor names, terrain, objects, roaming encounters, events, battles, teleports, effects and music. |
| **Island** | Home island and ship-map previews, editable destinations and progression-rule inspection. |

Database pages use a selectable list on the left and details on the right. Search, category filters and original previews are available where mapped.

## Files and ROM handling

- Open NCSD `.3ds`/`.cci`, standalone NCCH `.cxi`/`.app`, and supported decrypted IVFC or level-3 RomFS images.
- View the filename, title ID, container format and access status.
- Detect readable plaintext even when old encryption flags still mark it as encrypted.
- Require readable application ExeFS/RomFS and a valid plaintext extended header. The editor has no key input or ROM decryption support.
- Preserve secondary NCSD partition contents unchanged, including partitions that remain encrypted.
- Decode the game's archives and compressed resources for the editor.
- Preserve unrelated resources and unknown record bytes when supported fields are saved.
- Export a BPS patch containing both data edits and required engine changes.

## Database

### Items, consumables and key items

- Browse the **298 original item slots**, including reserved Dummy entries and any custom items saved into eligible slots.
- Filter by **Consumables**, **Key items**, **Equipment**, **Accessories** or **Clothes**.
- Search by item name or ID.
- Edit supported names, descriptions, buy prices and sell prices.
- Preserve native text formatting and protect text shared by multiple records.
- Set consumable **Battle use** and **Field use** permissions.
- Assign any of the **27 active consumable effect presets**.
- Edit the supported effect's targets, amount range and full-restoration options.
- Configure HP/AP recovery, revival, status cures and effects, debuff removal, escape effects and permanent stat increases where supported.
- Explicitly enable shared-effect editing when changing parameters used by other items.

Key items expose their supported text and prices. Their compiled progression scripts are not a general editable effect system.

Items without verified individual artwork use category symbols. Clothing uses its original ROM appearance.

### Equipment and clothing

Equipment has **General**, **Element resistance**, **Status protection**, **Attack elements** and **Effects** pages.

- Edit HP, AP, Attack, Defense, Speed and evasion bonuses within their native storage ranges.
- Edit resistance to Fire, Water, Ice, Earth, Wind and Darkness.
- Configure protection against Poison, Fatal, Burn, Sleep, Paralysis, Frozen and Blind.
- Give accessories Fire, Water, Ice, Earth, Wind or Light attack elements.
- Set EXP and money multiplier levels.
- Configure attacks against ghosts, ignored evasion and guard piercing.
- Configure battle/walking HP recovery, ambush prevention, improved escape and trap-floor protection.
- Set accessory-only critical bonuses, antenna reduction and fixed damage.
- Convert supported equipment between **Clothes** and **Accessory** slots while preserving its linked stats and effects.
- Choose an existing garment appearance separately from its equipment values.
- Preview the original clothing on a rotatable Denpa Man model, with matching list thumbnails.

Changing a slot or appearance does not migrate equipment already worn in an existing player save; re-equip affected items in-game.

### Custom items and clothing textures

In **Database → Items**, select a consumable, accessory or outfit and choose **New custom** to use it as a template.

- Create an item with its own name, description and prices.
- Give custom accessories and clothes independent equipment stats and effects.
- Configure custom consumables using existing native effect presets and field/battle permissions.
- Use saved custom items in Shop Data, starting inventory, enemy drops, dungeon chests and NPC gifts.
- Export an original or custom clothing texture with **Export PNG**.
- Replace a custom outfit's texture with **Import PNG** and preview it on the original model.
- Save item and texture changes together, or Reset unsaved changes.

Custom items use eligible unused slots within the original 298-slot inventory. They do not expand or renumber inventory IDs. Accessories and clothes also share spare equipment capacity; creation becomes unavailable when compatible slots run out. Key-item creation and new independent consumable effect scripts are not supported. Editing a shared consumable effect still changes other items using that preset.

Clothing PNGs are texture atlases, so keep the exported UV layout. Imports preserve the whole canvas, resize it to the template's dimensions and rebuild its mipmaps. The original texture format is retained; an opaque outfit does not gain transparency. PNGs are limited to **8 MB** and **2048 × 2048 pixels**. Importing a texture does not create a new clothing mesh.

### Denpa Men

Denpa Men has **Antenna**, **Color**, **Face**, **Name**, **Presets** and **Level Curve** pages.

#### Antennas

- Browse **115 antenna definitions** with original models, atlas icons and character samples.
- Change attack elements, buff/status effects and cure conditions through dropdowns.
- Edit supported descriptions, AP costs, targets and power.
- View native growth stages at 70%, 100% and 150% size.
- Configure evolution levels from 1–99 while keeping stages in ascending order.
- Use the native **All AP** setting where supported.
- Edit **Chain**, **Predecessor** and **Successor** links, with up to **four forms** in a supported evolution chain.

#### Custom antennas and artwork

- Choose original 3D shapes, 2D symbols, Ring and Small/Normal/Large artwork sizes.
- Use **Upload PNG** for a private antenna symbol without replacing the shared original atlas.
- Choose an original antenna animation or an adapted general enemy attack presentation.
- Create up to **104 custom antenna definitions** with **New Custom**.
- Give each custom antenna its own name, description and battle label.
- Change its underlying ability with **Template**, while retaining its identity and artwork.
- Link custom antennas into evolution chains and select them in Denpa Men presets.
- Delete unused custom definitions after removing their evolution links.
- Save definitions, text, private artwork and required runtime changes together.

Uploaded antenna PNGs are limited to **8 MB** and **2048 × 2048 pixels**. Transparent margins are cropped, and the visible artwork is fitted proportionally into the native atlas cell. Upload selects Normal size; other size choices remain available afterward. The Animation selector changes presentation while retaining the antenna's gameplay settings. It does not import new 3D models or animation files, and the editor preview does not simulate spell particles.

Selecting a custom antenna for a preset creates an independent family available from level 1. Evolution-link edits can change abilities for existing members of the affected family; preset choices apply when new characters are created.

#### Colors and custom colors

- Browse **22 original solid and striped colors**.
- Create up to **10 custom color slots**.
- Give each custom color a name.
- Use RGB color pickers for a solid color or two striped colors.
- Preview changes on the original character assembly and in preset choices.
- Edit an element dictionary covering Fire, Water, Ice, Earth, Wind, Dark and Light.
- Add or remove entries and set signed amounts from **−99 to 99**: positive resistance, negative weakness, zero neutral.
- Save the palette, generated private texture, name and required battle/menu changes together.
- Delete custom colors while preserving their slot identities.
- Assign custom colors through Presets and fixed starting-party choices.

Color amounts are native signed values, not percentages. Profiles display the first two nonzero elements; combat and equipment comparisons use the full dictionary.

Custom colors do not expand random recruitment's color pool. Deleting a color resets affected editable presets to White; already recruited users of that slot display White until the slot is reused.

#### Faces, names and presets

- Browse **169 face choices** across head, eyes, brows, nose, mouth, cheeks, glasses, skin and hair groups.
- View original character samples for supported choices.
- Browse and edit **1,034 existing names**.
- Edit all **32 stored presets**.
- Set a preset's name, color, antenna and level curve.
- Set Head, Eyes, Brows, Nose, Mouth, Cheeks and Glasses.
- View live thumbnails and rotatable composite previews.

Preset changes apply when characters are created. They do not rewrite the appearance of characters already recruited into a save. Body shape, skin and hair are not editable preset fields.

#### Level curves

- Edit **seven original growth curves**, each covering levels **1–99**.
- Set base HP, AP, Attack, Defense, Speed and cumulative EXP.
- Use **Automatic** for the original antenna-group curve.
- Assign an independent existing curve to each preset through the supported runtime extension.

These are base growth values. Body, head and equipment modifiers still contribute to final in-game stats.

### Shop Data

- Browse **12 original shop stock states** in native order.
- Inspect their dungeon-completion triggers and progress conditions.
- Search item choices by name, ID or category.
- View **Inventory**, **Added**, **Removed** and **Limited** comparisons.
- Add, delete or replace stock entries.
- Restore original stock entries.
- Mark supported stock as Limited.
- Save or reset shop drafts independently of other database pages.

Prices come from the committed item database. The **New** marker follows native stock comparisons. Creating new stock states or rewriting their progression conditions is not currently supported.

### Enemies

Enemies has **General**, **Elemental Attributes**, **Attacks** and **Item drops** pages.

#### Existing enemy definitions

- Browse **110 active battle definitions**, covering **91 named enemy types** and separate boss variants.
- Search and distinguish records by name and battle ID.
- Edit names, with explicit shared-name editing for linked variants.
- Set level, EXP and gold.
- Edit native Min/Max ranges for HP, Attack, Defense and Speed, plus evasion.
- Set Ghost type, Double action and HP recovery traits.
- Edit Fire, Water, Ice, Earth, Wind and Light weakness, resistance and immunity levels, plus Dark when its required runtime extension is available.
- View the original body, texture, skeleton and linked model parts.
- Configure field **Roaming behavior** as **Chase** or **Run away**.
- Keep roaming behavior separate from battle attacks.
- Repair missing field profiles in older custom-enemy ROMs by saving Enemies.

Molar, Golden Fang and Incisor use Run away in the original data. Original battle variants sharing an appearance also share its roaming profile. Custom enemies have independent profiles.

#### Attacks and motion previews

- Configure **six attack slots** per enemy using existing moves or None.
- Use green/yellow/red compatibility dots to distinguish usable moves, missing motions and restricted actions.
- Edit supported physical, ranged, status and healing effect modules.
- Choose native ally/opponent and single/all target settings.
- Set an attack's element, including Dark and Light, or None.
- Edit physical power and critical settings, ranged/healing Min/Max values and supported status parameters.
- Configure status chance tiers, strength and timed duration.
- Create private attack variants so other enemies keep their original move.
- Explicitly enable shared-attack editing to update all references.
- Inspect verified follow-up, charging and transformation dependencies.
- Preview the enemy's mapped normal and charged motions with Play, Stop, Loop and frame scrubbing.

Special actions retain their native handlers. Transformations and ally calls remain available to their verified original users; general moves can be assigned even when the selected model lacks their motion. Arbitrary copies of native scripts are not authored.

Motion previews show the original enemy assembly; they do not simulate a complete battle, target effects, sounds or cameras.

#### Item drops

- Edit both independent drop slots for each enemy battle definition.
- Select an original or saved custom item, or **None** to clear a slot.
- Choose from the opened ROM's native chance settings.
- Save or Reset drops with the enemy's other settings.
- Edit a custom enemy's inherited drops independently of its template.

Each slot rolls independently, so both items can drop. Original chance settings include 100%, 25%, 12.5%, 6.25%, 3.125%, 1.5625%, 0.3906% and 0.0061%; these are native tiers, not arbitrary percentages. Grand King's separate compiled reward is displayed as a fixed drop and is outside the two editable slots.

#### Custom enemies and recoloring

Select an enemy and choose **New custom** to use it as a template.

- Create an independent name, battle definition, appearance and private texture.
- Clone an original enemy or another custom enemy.
- Choose an existing original **Model**, including its skeleton, animations and attachments.
- Recolor the primary texture with **Hue**, **Saturation** and **Brightness**.
- View recoloring immediately in the model preview.
- Preserve the original enemy and its texture.
- Edit the same stats, elements, traits and attacks available for original enemies.
- Set Chase or Run away independently.
- Inherit usable movement speeds and detection settings from the template/model.
- Change the model while keeping the custom name, battle stats, attacks, recoloring and selected roaming behavior.
- Use a normal roaming fallback when choosing a boss model without an original field profile.
- Save custom enemies into the ROM and select them in dungeon encounters and formations.
- Reset unsaved creations without changing original IDs.

Recoloring affects the primary model texture; separately linked attachment textures keep their original appearance. Custom enemies reuse existing models and animations rather than importing new meshes or motion files.

The stock US appearance table has room for **164 additional custom appearances**. Private attack variants share a separate **23-slot** extension space across the ROM.

### Meta: starting settings

Configure a fresh game's initial state:

- Start with **1–8 party members**.
- Choose random members or existing preset definitions.
- Set each member's level from **1–99**.
- Set starting gold from **0–999,999**.
- Add starting inventory with quantities from **0–99**.
- Configure supported starting facilities: House, Docks, Shop, Museum, Digitoll Cave, PC and Spirit Shrine.
- Set **Antenna Tower** availability.
- Enable **Skip intro** for the opening recruitment sequence.
- Choose no ship, Raft, Small Boat or Cruiser.
- Choose a supported house stage.
- Set party capacity within the native **4–8** range.
- Set supported initial story progress.
- Save required runtime changes inside the ROM without a sidecar mod.

Party capacity stays large enough for the configured party. Disabling the Antenna Tower keeps House available and starts its facility cursor there. It does not disable separate PC/QR or scripted recruitment.

Initial party, inventory and progression settings apply to a new game; this is not a player-save editor. The Tower override also affects existing saves. Skip intro leaves the boot logos and title screen intact.

Crystal's native recruitment remains linked to the guarded Cruiser/ending completion paths. Starting directly with a Cruiser does not itself execute that recruitment event.

## Dungeons

Browse original and custom dungeons in a textured OpenGL scene. The editing panel has **Build**, **Objects**, **Enemies**, **Events**, **Teleports**, **Effects** and **Music** tabs.

### Viewing floors and floor names

- Browse **17 original dungeon entries** and **149 selectable floor visits**, including native aliases and sample entries.
- Preview fixed modular floors and original authored maps with mapped resources.
- Display the actual bottom-screen floor name immediately to the **left of the floor dropdown**, in the same header line.
- Edit that name, independently of the editor's floor number.
- Save name changes with Enter or focus loss; use Escape to reset the edit.
- View textures, collision, objects, enemies, teleports and events through layer controls.
- Toggle **X/Z** coordinates and **Rooms** outlines on supported layouts.
- Select a spatial record from its list or by clicking its scene marker.
- Keep the active category visible and synchronize scene/list selection.
- Resize the scene and editing panels.
- Inspect unpositioned pools and events in lists without fabricated coordinates.

For example, Dark Ruins editor **Floor 8** is **Dark Ruins B 6F** in-game. Landing-only transition records are retained as links without rendering nonexistent stairs: Dark Ruins Floor 7 has no central staircase at the blue warp leading to Floor 5.

### Building terrain

- Browse original **Ground**, **Walls**, **Paths** and **All** pieces.
- Paint with the original tile models and textures.
- Apply cosmetic **Decor** variants to compatible existing shapes.
- Preview a translucent brush with its selected rotation.
- Paint multiple cells in one drag stroke.
- Erase or pick existing tiles with keyboard/mouse shortcuts.
- Expand supported modular layouts up to **19 × 19 cells**.
- Choose among **Cave, Ocean, Tower, Forest, Volcano, Oasis, Ruins and Ice** tilesets.
- Save strokes through a background queue while continuing to paint.
- Undo or redo individual strokes.
- Preserve mapped collision and companion object data, with guards around occupied cells and required floor bounds.

**Painting terrain does not randomly generate or reshuffle barrels, rocks or crates on edited layouts.** Place those through Objects when you want them. Cosmetic tile variants remain separate from collision scenery.

Build edits fixed modular layouts. Original authored map geometry remains available for preview and supported placement editing, rather than tile painting.

### Objects, NPCs and chest rewards

- Create brown/red chests, healing points, NPCs, torches, crates, barrels and rocks on eligible floor cells.
- Preview the original object before placement.
- Delete supported stored placements, including original scenery.
- Move selected placements using scene handles.
- Snap cell-based objects to the native **500-unit grid**.
- Move supported absolute actors with X/Z and Y handles.
- Set a chest's item through the item selector.
- Edit supported gold rewards as a fixed amount or inclusive Min/Max range.
- Edit mapped NPC dialogue and supported item gifts.
- Undo/redo supported creation, deletion, movement and content changes.

Chest item changes save automatically. Other controls use their displayed Save or Apply action. Generated scenery and unsupported scripted actors do not become editable stored records.

### Roaming encounters and spawn areas

The Enemies panel separates **Roaming**, **Spawns**, **Companion** and **Static** entries.

- Inspect a floor's native roaming pool and enabled state.
- Enable a supported dormant pool.
- Assign existing or saved custom enemy types.
- Set leader and companion selection weights.
- Configure supported Min/Max encounter counts.
- Edit additional leader draws and battle-group probabilities.
- Use original-model enemy thumbnails.
- Add supported stored-cell spawn overrides.
- Configure generated-room spawn overrides and suppression.
- Select a CSV room and highlight its boundaries before assigning a room spawn.
- Delete supported pools or overrides.
- Keep private floor changes from altering another floor's shared pool.
- Retain enemy database level and stats separately from encounter settings.

Native pools support up to five leader choices and five companion choices, with a battle total of at most eight enemies. Floor override capacity is **16**, including suppression entries.

Generated roaming positions depend on the game's live placement/RNG. The editor shows known stored information rather than simulating every enemy's final position. Floors without eligible enemy placement data cannot receive arbitrary roaming spawns.

### Events, dialogue and battles

- Inspect verified entry events, conditions, triggers, completion flags and actions.
- View before-battle, battle and after-battle phases without duplicate entries.
- Edit mapped event dialogue and supported item gifts.
- Edit supported fixed formations using up to five enemy/count slots.
- Insert, delete or reorder **Stage intro** commands at all **11 main dungeon entrances**.
- Preserve required native entrance sequences and camera flow.
- Preview the supported stage-intro HUD within the Events command editor.
- Edit Guardian Tower's final **Rook**, **Queen** and **King** formations separately.
- Add fixed enemy-proximity battles through Events or Enemies → Static.
- Select their formation and supported placement, then move or delete them.
- Play the native defeat animation, effects and sounds before clearing a placed enemy after victory.
- Clear its body, shadow and collision while preserving completion on re-entry.
- Retry added battles after loss or escape.

Supported floors can have **two new proximity battles**. These events use private scenario/formation records and share existing completion capacity with custom NPCs. They do not create arbitrary chapter milestones or new boss camera scripts.

**Dark Ruins support** includes the orb gate and dwarf guides, required orb conditions, Grand King's first encounter/rematch/victory events on Floor 8, the original boss actor, and the mapped ending dialogue. The ending links cover Crystal's rescue, the credits, automatic island return, Cruiser construction, guarded Crystal recruitment and the post-credits thank-you scene. The native conditional awards are shown as **Evil Emblem ×1**, **Cruiser Parts ×1** and **Room Parts ×1**.

These are mapped native events and awards. Regular enemy drops are edited separately in **Database → Enemies → Item drops**. The event editor exposes the mapped records and dialogue; it does not play the cutscenes or credits.

### Gates, stairs, holes and warps

- Place original gates, stairs up/down, holes, orange teleports and blue return warps on supported modular floors.
- Preview the selected transition model.
- Choose destination dungeon, floor and X/Z cell.
- Pick a destination in its map preview.
- Create one-way or round-trip links where supported.
- Keep holes one-way.
- Redirect existing links with **Destination → Apply**.
- Set a custom overworld entrance gate's facing with **Direction → Apply**.
- Move/delete supported transitions and undo/redo those operations.
- Use native depth rules and distinguish visible transitions from invisible arrivals.

Blue warps retain entrance/re-entry behavior, including supported custom-dungeon bookmarks. New floors start unconnected; links are placed explicitly.

### Effects and music

- Change effects for the selected **Floor** or **Dungeon**.
- Choose None, Cave glow, Ocean glow, Tower sparkles, Forest leaves, Volcano sparks, Oasis glow, Ruins dust or Snow.
- View an approximate animated ambient-effect preview.
- Change music using the original dungeon sound entries.
- Apply a floor override or a dungeon-wide setting.
- Preserve other floor styles and unaffected overrides.
- Preview mapped native damage-patch models and their generated room coverage.

Damage patches are generated previews, not individually editable stored scenery. Ambient previews approximate mapped emitters. Music selection does not provide audio playback.

### Custom dungeons and floors

- Create up to **three custom dungeon identities** without replacing original entries.
- Start with a clean **5 × 5 entrance room** and original exit gate.
- Choose a **North**, **East**, **South** or **West** entrance when creating a dungeon.
- Name the custom dungeon.
- Keep its linked default bottom-screen and entrance title text consistent.
- Add clean **5 × 5 floors** to original or custom dungeons.
- Choose an original tileset for each supported floor.
- Paint terrain and place supported objects, encounters, battles and transitions.
- Link custom dungeons to overworld destinations.
- Use blue return-warps with the supported native re-entry extension.

Each floor bank supports at most **256 records**. Additional floors do not automatically connect or create story progression. Floor deletion, duplication and reordering are not currently provided.

Some original entries share a floor bank, notably Guardian Tower D11/D12. Shared layout edits affect both; floor-name overrides can remain independent.

## Island and overworld

### Overworld previews and destination editing

- Preview the home island with its original terrain, facilities and ship models.
- View the original top-screen and touch-screen island/Docks layouts.
- Edit facility titles and descriptions with Save/Reset controls.
- Click Docks or Ship to browse travel destinations.
- Select destinations through the list or map icons.
- Preview no ship, Raft, Small Boat or Cruiser without changing the player's save.
- Inspect native ship/unlock requirements and destination information.
- Open a destination's dungeon directly.
- Edit original or custom destination titles and multiline descriptions.
- Change the destination dungeon and required ship level.
- Choose from seven mapped original icons and world models.
- Set separate map-icon positions for each supported ship layout.
- In the Ship preview, drag destination icons within their native screen bounds; cancel a drag with Escape.
- Edit top-screen world-model position.
- Add up to **three destinations**, for a maximum of **13 slots**.
- Delete original/custom destinations and reuse deleted slots without shifting the remaining identities.

Different islands can lead to the same dungeon while retaining their own title and description. Deleting a destination leaves its dungeon available in the editor. Save or Reset commits/discards the destination draft.

These are fitted editor composites. They do not reproduce the entire live island camera, sky, ocean, facility animations or a loaded save's visibility state.

### Progression Flags

- Browse decoded facility availability and upgrades.
- Inspect ship, house and party-capacity stages.
- View destination visibility requirements.
- Inspect story and dungeon progress rules.
- Browse mapped scenario-completion flags, including supported custom additions.
- Search/filter names, flag IDs, triggers, required values and effects.

This page is a **read-only view of ROM progression rules**, not current values from a player's save. Supported new-game initialization is edited in Database → Meta.

## Saving and BPS patches

### Direct ROM saving

- Save directly to the opened ROM, without a workspace/project sidecar.
- Keep independent database drafts while saving another section.
- Reset a section to its last committed state.
- Rebuild changed archives while preserving unrelated compressed resources.
- Support resource growth and shrinkage.
- Rebuild RomFS/ExeFS as required.
- Update integrity hashes, file lengths and container offsets.
- Preserve other NCSD partitions.
- Check that the source ROM has not changed externally.
- Validate a temporary sibling image before replacing the working ROM.
- Apply supported runtime updates during the relevant save.

Supported dungeon operations save automatically and have undo/redo history. That history is not retained after reopening the ROM; operations that change external references can clear it.

When **Update available** appears in **Database → Meta**, use **Save** to apply supported runtime updates while retaining the ROM's party, inventory and progression settings.

Unrecognized executable modifications or incompatible concurrent edits are rejected rather than overwritten blindly.

### BPS export and application

**BPS is the editor's only mod-distribution format.**

1. Save your edits and let pending dungeon saves finish.
2. Choose **Files → Export BPS**.
3. Select the separate clean, decrypted source ROM.
4. Choose the output `.bps` file.
5. Share that patch. Recipients apply it to the matching clean ROM using a BPS-compatible patcher.

Export covers the **complete edited image**, including RomFS data, executable changes, extended-header/loading changes, hashes and offsets. Required engine changes are included in the patch.

The exporter checks source compatibility, verifies BPS checksums and reconstructs the target to confirm a byte-exact result before publishing the patch. It does not modify either input ROM. Unsaved drafts, unsupported source combinations, no-change exports and input-overwrite destinations are rejected.

Both source and target are limited to **512 MiB**. Recipients need the exact source bytes used to create the patch. Compatibility checks do not independently prove that a selected ROM is pristine.

There is no **Export 3DS Mod** or LayeredFS mod-package export.

## Controls

| Context | Control | Action |
| --- | --- | --- |
| Dungeon scene | Right-drag | Rotate |
| Dungeon scene | Middle-drag | Pan |
| Dungeon scene | Mouse wheel | Zoom toward the pointer |
| Dungeon scene | Home | Fit the scene |
| Build | Left-click/drag | Paint |
| Build | Shift + right-click/drag | Erase |
| Build | Shift + middle-click | Pick a tile |
| Build | Shift + left-click/drag | Alternate erase gesture |
| Placement mode | Scene click | Place on an eligible cell |
| Placement mode | Escape | Cancel |
| Selected placement | Drag scene handles | Move |
| Supported dungeon edits | Ctrl+Z | Undo |
| Supported dungeon edits | Ctrl+Y or Ctrl+Shift+Z | Redo |
| Floor name | Enter / focus loss / Escape | Save / Save / Reset |
| Model preview | Drag / wheel / Home | Rotate / Zoom / Reset |
| Island map icon | Drag / Escape | Move / Cancel drag |

## Catalogs and capacity limits

Counts below describe the documented **stock US ROM**. Edited ROMs can differ.

| Original catalog | Count |
| --- | ---: |
| Item records | 298 |
| Consumables / Key items | 27 / 25 |
| Accessories / Clothes | 83 / 101 |
| Reserved Dummy item records | 62 |
| Antenna definitions | 115 |
| Colors | 22 |
| Face choices | 169 |
| Names | 1,034 |
| Stored Denpa Men presets | 32 |
| Level curves | 7 × 99 levels |
| Shop stock states | 12 |
| Active enemy battle definitions | 110 |
| Named enemy types | 91 |
| Dungeon entries / selectable floor visits | 17 / 149 |

| Supported extension or editing limit | Capacity |
| --- | --- |
| Custom colors | 10 additional slots |
| Custom antennas | 104 additional definitions |
| Antenna evolution chain | Up to 4 forms |
| Custom items | Eligible unused slots within the original 298-item inventory; equipment also needs spare equipment records |
| Clothing and antenna PNG input | 8 MB; up to 2048 × 2048 pixels |
| Custom enemy appearances | 164 additional slots in a stock ROM |
| Additional private attack definitions | 23 simultaneous definitions, shared across the ROM |
| Attack slots per enemy | 6 |
| Custom dungeon identities | 3 |
| Added overworld destinations | 3; 13 total slots |
| Floor records per bank | 256 |
| Modular floor footprint | 19 × 19 cells |
| Added proximity battles per floor | 2 |
| Event formation rows | Up to 5 enemy/count slots |
| Roaming leader / companion choices | Up to 5 each |
| Enemies in a roaming battle | Up to 8 |
| Floor spawn/suppression overrides | 16 |
| Scenario completion flags | 300 total; 95 unused in stock data, shared by custom NPCs/battles |
| Starting party / party capacity | 1–8 members / 4–8 capacity |
| Starting item quantity | 0–99 |
| BPS source and target size | 512 MiB each |

Custom transition/arrival capacity depends on installed runtime features because they share reserved executable space. It ranges from **16 to 282 records** for supported configurations; source/arrival records both count. The editor checks the active limit before saving.

## Supported inputs and current limitations

### Game version and containers

- Verified application: **The Denpa Men: They Came by Wave (USA)**.
- Title ID: **00040000000A3100**.
- Product code: **CTR-N-JD8E**.
- Container reading supports NCSD, standalone NCCH and supported RomFS images.
- Direct full-image editing requires a readable **decrypted application**, including its executable and extended header.
- The editor does not decrypt ROMs or accept encryption keys. Secondary NCSD partition contents can remain encrypted and are preserved unchanged.
- Standalone RomFS inputs lack executable/header data needed for engine extensions.
- Other regions or revisions are not automatically supported by the verified US mappings.
- **CIA import/export is not implemented.**

Saving rebuilds supported decrypted images; it cannot regenerate Nintendo's retail RSA signatures. Use a runtime that accepts the resulting edited/decrypted image.

### Editing and preview boundaries

- This is a ROM editor, not a player-save editor.
- Unknown fields and unsupported scripts remain preserved.
- Procedural dungeon generation is not an authoring tool in the editor.
- Authored map geometry cannot be replaced with imported meshes or newly authored tilesets.
- General model and animation imports are not implemented. PNG texture changes are limited to custom clothes and supported antenna artwork.
- Arbitrary cutscene compilation, camera scripting and new chapter-clear logic are not implemented.
- Custom item creation is limited to eligible native inventory/equipment slots and existing effect types. New key items and independent consumable effect scripts are not implemented.
- Runtime-generated encounter positions and full battle/field AI are not simulated in previews.
- Database motion and dungeon/island previews cover verified mappings rather than every renderer feature.

## Credits

**Created by Funghi.**

[YouTube](https://www.youtube.com/@SpiritCursed) · [Twitter / X](https://x.com/SpiritCursedDev) · [Website](https://spiritcursed.github.io/)

This is an unofficial project, unaffiliated with the game's developers, publishers or Nintendo. Game names and ROM-derived content belong to their respective rights holders.
