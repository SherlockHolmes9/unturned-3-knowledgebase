# Item Data

!!! info inline end
    This page may be outdated, you can help by submitting a pull request

**Items** in _Unturned_ encompass anything that can be carried in a player's in-game inventory. All items share some properties, while many item types have their own unique data. All of the data applicable to each possible item type can be found below. Items that are sub versions of another Item inherit their applicable properties, for instance, anything in Attachments is also applicable to a Grip.

## Formatting

  **Property_name**: <*datatype*>

  Some properties may have a specific default value which is applied if you do not specify one in your .dat. It's also possible to have a mathematical operation based on the values of other keys.

  **Property_with_default** <*datatype*: `value`>

  Some properties have different defaults depending on a prior Enum value. In this case, the enum value will appear in parentheses next to the default value.

  **Property_with_default_and_enum** <*datatype*: `value`(key_1), `value`(key_2)>

  Some properties may be specified in multiple key value pairs. They are denoted by a pair curly brackets (`{}`) with a series of strings in them which should be substituted for the brackets when used. Generally you can specify any number of these key/value pairs. In the case of the example, you would input this to your .dat file as 4 separate keys `Nightvision_Color_R 255`, `Nightvision_Color_G 255`, etc...

  **Nightvision\_Color\_{R,G,B,A}** <*uint8*: `102, 102, 102, 0`>

### Value Data Types

#### Numerical

| Data Type | Min                        | Max                        | Description                                    |
| --------- | -------------------------- | -------------------------- | ---------------------------------------------- |
| `uint8`   | 0                          | 255                        | unsigned 8 bit integer                         |
| `uint16`  | 0                          | 65,535                     | unsigned 16 bit integer                        |
| `uint32`  | 0                          | 65,535                     | unsigned 32 bit integer                        |
| `uint64`  | 0                          | 18,446,744,073,709,551,615 | unsigned 64 bit integer                        |
| `int8`    | -127                       | 127                        | signed 8 bit integer                           |
| `int16`   | -32,768                    | 32,767                     | signed 16 bit integer                          |
| `int32`   | -2,147,483,648             | 2,147,483,647              | signed 32 bit integer                          |
| `int64`   | -9,223,372,036,854,775,808 | 9,223,372,036,854,775,807  | signed 64 bit integer                          |
| `float`   | ±1.5 x 10−45               | ±3.4 x 1038                | 32 bit floating point number. Supports decimal values |

#### Enum

  Enums are data types with specific values, they appears on this list as "<*Enum_Name*> `key_1`, `key_2`". You can use any one of these as the value, and in a .dat file it would appear as `Enum_name key_1`.

#### Flag

  Flags are simple keys without a value, if you include the property in your .dat file, it's active.

- [Item Data](#item-data)
  - [Formatting](#formatting)
    - [Value Data Types](#value-data-types)
      - [Numerical](#numerical)
      - [Enum](#enum)
      - [Flag](#flag)
  - [Non-specific Data](#non-specific-data)
    - [Capacity](#capacity)
    - [Quality](#quality)
    - [Damage](#damage)
    - [Blueprints](#blueprints)
    - [Actions](#actions)
  - [Asset Bundles and Error Handling](#asset-bundles-and-error-handling)
  - [Barricades](#barricades)
    - [Beacons](#beacons)
    - [Experience Storages](#experience-storages)
    - [Generators](#generators)
    - [Item Storages](#item-storages)
    - [Liquid Storages](#liquid-storages)
    - [Oil Pumps](#oil-pumps)
    - [Plants](#plants)
    - [Remote Explosives](#remote-explosives)
    - [Robotic Turrets](#robotic-turrets)
    - [Traps](#traps)
  - [Box](#box)
  - [Attachments](#attachments)
    - [Barrels](#barrels)
    - [Grips](#grips)
    - [Magazines](#magazines)
    - [Sights](#sights)
    - [Tacticals](#tacticals)
  - [Clothing](#clothing)
    - [Bag](#bag)
      - [Backpack](#backpack)
      - [Pants](#pants)
      - [Shirt](#shirt)
      - [Vests](#vests)
    - [Gear](#gear)
      - [Glasses](#glasses)
      - [Hat](#hat)
      - [Mask](#mask)
    - [Body Mesh Replacements](#body-mesh-replacements)
  - [Consumables](#consumables)
  - [Crafting Supplies](#crafting-supplies)
  - [Fishing Poles](#fishing-poles)
  - [Fuel Canisters](#fuel-canisters)
  - [Growth Supplements](#growth-supplements)
  - [Mapping Equipment](#mapping-equipment)
  - [Melee Weapons](#melee-weapons)
  - [Optics](#optics)
  - [Parachutes](#parachutes)
  - [Projectiles](#projectiles)
  - [Radiation Filters](#radiation-filters)
  - [Ranged Weapons](#ranged-weapons)
  - [Remote Triggers](#remote-triggers)
  - [Restraining Devices](#restraining-devices)
    - [Catchers](#catchers)
    - [Releasers](#releasers)
  - [Structures](#structures)
  - [Tools](#tools)
    - [Car Jacks](#car-jacks)
    - [Car Lock Picks](#car-lock-picks)
    - [Tire Replacements](#tire-replacements)
    - [Vehicle Batteries](#vehicle-batteries)
    - [Walkie-talkies](#walkie-talkies)
  - [Water Canisters](#water-canisters)

## Non-specific Data

This first set of data is universal, and is applicable to any item type. Some of this data is required in order for the item to function.

**GUID**: The GUID is automatically generated for the item when the game is launched. If it is not automatically generated, then it is assumable that the content was not set up properly.

**Type**: Each category of item has its own type. The type to use can be found for each specific item category below, and is used for the item's context type as viewed in the context menu.

**Rarity**: `Common`, `Uncommon`, `Rare`, `Epic`, `Legendary`, `Mythical`. Defaults to common.

**Useable**: Defines which class to use for the item when equipped. If unspecified it will default to None, meaning that the item cannot be equipped. Which value to use for equippable items can be found below for each item category.

**Slot**: `Primary`, `Secondary`, `Any`

**ID**: The item ID is used to spawn the item into the game, and is represented as an unsigned 16 bit integer (a range of 0–65535). It is recommended not to use a value less than 2,000 as those are reserved for official content. It is also recommended to avoid any ID range being used by curated content, as those are often used by modded servers and custom Workshop maps.

**Size_X**: The width of the item in the inventory.

**Size_Y**: The height of the item in the inventory.

**Size_Z**: The size of the camera for item icons.

**Size2_Z**:

**Can_Use_Underwater**: `false`, `true`. Applicable to equipable items, and defaults to false for primary weapons.

**Should_Drop_On_Death**: `false`, `true`. Defaults to true.

**Should_Delete_At_Zero_Quality**: `false`, `true`. Applicable to usable items, and defaults to false.

**Allow_Manual_Drop**: `false`, `true`. Defaults to true.

**Backward**: Specified if this item should be visually held in the opposite hand.

### Capacity

**Amount**: Maximum capacity of a container.

**Count_Min**: The minimum amount to generate in the container.

**Count_Max**: The maximum amount to generate in the container.

### Quality

**Quality_Min**: The minimum quality to generate. Set to 10 by default.

**Quality_Max**: The maximum quality to generate. Set to 90 by default.

**Override_Show_Quality**:

**Durability**: Either a decimal probability chance of quality loss upon action, or guaranteed loss and durability value is instead representative of the amount lost.

- _Canteens_: Guaranteed quality loss occurs upon drinking. Durability value represents the amount of quality loss.
- _Melee Weapons_: Decimal probability chance of quality loss occurs upon hitting.
- _Ranged Weapons_: Decimal probability chance of quality loss occurs upon shooting.

**Wear**: Increment to degrade quality by. Only applicable to items where durability represents a decimal probability chance of quality loss.

### Damage

Damage data can be utilized by explosive consumables, explosive throwables, traps, remote explosives, melee weapons, and ranged weapons.

**Player_Damage**: Base damage dealt to player entities, prior to calculating limb modifiers, and used independently from limb modifiers for explosive and trap damage.

**Player_Leg_Multiplier**: The multiplier of player_damage against player legs.

**Player_Arm_Multiplier**: The multiplier of player_damage against player arms.

**Player_Spine_Multiplier**: The multiplier of player_damage against player torso.

**Player_Skull_Multiplier**: The multiplier of player_damage against player head.

**Instakill_Headshots**: `false`, `true`. Defaults to false. If true, headshots bypass hat armor on servers with Allow_Instakill_Headshots enabled.

**Player_Damage_Bleeding**: `Always`, `Default`, `Heal`, `Never`

**Player_Damage_Bones**: `Always`, `Heal`, `None`

**Player_Damage_Food**: Damage dealt to a player's food.

**Player_Damage_Water**: Damage dealt to a player's water.

**Player_Damage_Virus**: Damage dealt to a player's immunity.

**Player_Damage_Hallucination**: Length of hallucinations inflicted upon a player.

**Zombie_Damage**: Base damage dealt to zombie entities, prior to calculating limb modifiers, and used independently from limb modifiers for explosive and trap damage.

**Zombie_Leg_Multiplier**: The multiplier of zombie_damage against zombie legs.

**Zombie_Arm_Multiplier**: The multiplier of zombie_damage against zombie arms.

**Zombie_Spine_Multiplier**: The multiplier of zombie_damage against zombie torso.

**Zombie_Skull_Multiplier**: The multiplier of zombie_damage against zombie head.

**Animal_Damage**: Base damage dealt to animal entities, prior to calculating limb modifiers, and used independently from limb modifiers for explosive and trap damage.

**Animal_Leg_Multiplier**: The multiplier of animal_damage against animal limbs.

**Animal_Spine_Multiplier**: The multiplier of animal_damage against animal torso.

**Animal_Skull_Multiplier**: The multiplier of animal_damage against animal head.

**Barricade_Damage**: Damage dealt to barricades.

**Structure_Damage**: Damage dealt to structures. Multiplied by 3 in single-player.

**Vehicle_Damage**: Damage dealt to vehicles.

**Resource_Damage**: Damage dealt to resources.

**Object_Damage**: Damage dealt to objects.

**Invulnerable**: Specified if damage ignores structures, barricades, and vehicles that are considered invulnerable to low-power weaponry. Not applicable to explosive damage, which always ignores invulnerability.

**Range**: For ranged and melee weapons – max distance in meters before damage is no longer possible. For explosive weapons (including magazine attachments that generate explosive projectiles) – the radius of the explosion in meters.

**Explosive**: Specified if the explosive component is used.

**Explosion**: The visual effect ID to play as the explosion.

**Spawn_Explosion_On_Dedicated_Server**:

### Blueprints

**Blueprints**: The number of blueprints available.

**Blueprint\_#\_Type**: `Ammo`, `Apparel`, `Barricade`, `Furniture`, `Gear`, `Repair`, `Structure`, `Supply`, `Tool`, `Utilities`

**Blueprint\_#\_Supplies**: The number of unique supplies required for the blueprint.

**Blueprint\_#\_Supply\_#\_ID**: The ID of the unique supply required.

**Blueprint\_#\_Supply\_#\_Amount**: The amount of the unique supply required.

**Blueprint\_#\_Supply\_#\_Critical**: Specified if the unique supply is a prerequisite to showing the blueprint.

**Blueprint\_#\_Tool**: The ID of the unique non-consumed tool required.

**Blueprint\_#\_Tool_Critical**: Specified if the unique non-consumed tool is a prerequisite to showing the blueprint.

**Blueprint\_#\_Level**: The skill level needed.

**Blueprint\_#\_Skill**: `Cook`, `Craft`, `None`, `Repair`. The skill required to craft – defaults to None.

**Blueprint\_#\_Product**: The ID of the product created.

**Blueprint\_#\_Products**: The amount of the product created.

**Blueprint\_#\_Outputs**: The number of unique products created from fulfilling the blueprint.

**Blueprint\_#\_Output\_#\_ID**: The ID of the unique product created.

**Blueprint\_#\_Output\_#\_Amount**: The amount of the unique product created.

**Blueprint\_#\_Build**: The auditory effect ID to play.

**Blueprint\_#\_Map**: Name of the map the condition applies to.

**Blueprint\_#\_Conditions**: The number of required conditions.

**Blueprint\_#\_Condition\_#\_Type**: `Holiday`

**Blueprint\_#\_Condition\_#\_Value**: `Christmas`, `Halloween`

### Actions

**Actions**: The number of actions available.

**Action\_#\_Type**: `Blueprint`

**Action\_#\_Source**: ID of the item with the blueprint this action should perform.

**Action\_#\_Blueprints**: The amount of the unique blueprint actions.

**Action\_#\_Blueprint\_#\_Index**: ID of the specific blueprint this action should perform.

**Action\_#\_Key**: `Craft_Bandage`, `Craft_Dressing`, `Craft_Rag`, `Craft_Seed`

## Asset Bundles and Error Handling

See [AssetBundles.md](../AssetBundles.md) for full documentation regarding asset bundles.

**Ignore_TexRW**: Specified if read/writeable texture errors for the item should be hidden from the error logs.

## Barricades

**Type**: `Barricade`

**Useable**: `Barricade`

**Build**: `Barrel_Rain`, `Barricade`, `Bed`, `Cage`, `Campfire`, `Claim`, `Clock`, `Door`, `Fortification`, `Freeform`, `Gate`, `Glass`, `Hatch`, `Ladder`, `Mannequin`, `Note`, `Oven`, `Oxygenator`, `Safezone`, `Shutter`, `Sign`, `Sign_Wall`, `Spot`, `Stereo`, `Torch`, `Vehicle`

**Health**: Amount of health.

**Range**: Distance away the barricade can be placed from the player.

**Radius**:

**Offset**: Inherent distance above the point to place.

**Locked**: Usability/interactivity access restricted to owner.

**Explosion**: Destruction effect ID.

**Salvage_Duration_Multiplier**: Multiplier on salvage duration.

**Unpickupable**: Cannot be salvaged.

**Unrepairable**: Cannot be repaired.

**Unsalvageable**: If damaged, salvaging yields no partial ingredients.

**Unsaveable**: Cannot be saved by the game.

**Vulnerable**: Specified if the barricade can be destroyed by low-power weaponry.

**Proof_Explosion**: Specified in immune to explosion damage.

**Armor_Tier**: `High`. Doubles health value.

**Use_Water_Height_Transparent_Sort**:

**Should_Close_When_Outside_Range**: `true`. Defaults to false. Only applicable to interactive barricades that generate a UI element, such as item storages and signs.

**Allow_Collision_While_Animating**: Allows animated interactables (e.g., doors) to perform collision movement upon players.

**Allow_Placement_On_Vehicle**: `false`, `true`. Defaults to false for beds and robotic turrets.

### Beacons

**Type**: `Beacon`

**Useable**: `Barricade`

**Build**: `Beacon`

**Wave**: Number of zombies that must be killed.

**Rewards**: Number of rewards spawned.

**Reward_ID**: Spawn table ID for rewards.

### Experience Storages

**Type**: `Library`

**Useable**: `Barricade`

**Build**: `Library`

**Capacity**: Numerical maximum capacity of experience able to be stored.

**Tax**: Percent tax on deposits.

### Generators

**Type**: `Generator`

**Useable**: `Barricade`

**Build**: `Generator`

**Capacity**: Numerical maximum capacity of fuel units able to be stored.

**Wirerange**: Radius range in meters (representative of a sphere) for how large of an area is considered powered.

**Burn**: Number of seconds before one fuel unit is burned.

### Item Storages

**Type**: `Storage`

**Useable**: `Barricade`

**Build**: `Storage`, `Storage_Wall`

**Storage_X**: Horizontal storage space.

**Storage_Y**: Vertical storage space.

**Display**: Stored item is visible.

### Liquid Storages

**Type**: `Tank`

**Useable**: `Barricade`

**Build**: `Tank`

**Source**: `Fuel`, `Water`

**Resource**: Numerical maximum capacity of liquid units that can be stored. Water units are measured in potential drinking uses.

### Oil Pumps

**Type**: `Oil_Pump`

**Useable**: `Barricade`

**Build**: `Oil`

**Fuel_Capacity**: Numerical maximum capacity of fuel units able to be stored.

### Plants

**Type**: `Farm`

**Useable**: `Barricade`

**Build**: `Farm`

**Growth**: Number of seconds required to fully grow.

**Grow**: ID of the item generated when harvesting a fully grown plant.

### Remote Explosives

**Type**: `Charge`

**Useable**: `Barricade`

**Build**: `Charge`

**Range2**: Meter radius of range for explosive damage.

**Explosion2**: Explosion effect ID for the damaging explosion.

Limb-independent entity damage is also applicable.

### Robotic Turrets

**Type**: `Sentry`, `Sentry_Freeform`

**Useable**: `Barricade`

**Build**: `Sentry`

**Storage_X**: Horizontal storage space.

**Storage_Y**: Vertical storage space.

**Display**: Stored item is visible.

**Mode**: `Friendly`, `Hostile`, `Neutral`

**Infinite_Ammo**: Weapon ammunition never depletes.

**Infinite_Quality**: Weapon quality never depletes.

### Traps

**Type**: `Trap`

**Useable**: `Barricade`

**Build**: `Spike`, `Wire`

**Damage\_Tires**: Specified if tires can be popped when ran over by a vehicle.

**Player\_Damage**: a

**Zombie\_Damage**:

**Animal\_Damage**:

**Object\_Damage** <*Float*>:

**Range2**: Meter radius of range for explosive damage.

**Explosion2**: Explosion effect ID for the damaging explosion.

Limb-independent entity damage is also applicable.

## Box

*Item Box Asset*

**Type**: `Box`

**Generate** <*int32*>:

**Destroy** <*int32*>:

**Drops** <*int32*>: Specify the number of drops you will provide.

**Drop_#** <*int32*>:

**Item_Origin** <*BoxItemOrigin*>: `Unbox`, `Unwrap`

**Probability_Model** <*BoxProbabilityModel*>: `Original`, `Equalized`

**Contains_Bonus_Items** <*Boolean*>:
## Attachments

*Item Caliber Asset*

**Calibers** <*uint8*>: The number of calibers applicable.

**Caliber\_#** <*uint16*>: ID of an applicable caliber.

**Recoil\_X** <*float*>: Decimal amount to multiply horizontal look recoil by.

**Recoil\_Y** <*float*>: Decimal amount to multiply vertical look recoil by.

**Spread** <*float*>: Decimal amount to multiply spread by.

**Sway** <*float*>:

**Shake** <*float*>: Decimal amount to multiply physical recoil by.

**Damage** <*float*>: Decimal amount to multiply damage by.

**Firerate** <*uint8*>: Amount to decrease minimum fire rate delay by.

**Ballistic\_Damage\_Multiplier** <*float*>:

**Paintable** <*flag*>: Specified if skins can retexture the attachment.

**Bipod** <*flag*>: Specified if effects only take place when prone.

### Barrels

**Type**: `Barrel`

**Braked** <*flag*>: Specified if a muzzle flash is hidden.

**Silenced** <*flag*>: Specified if alerts are not generated.

**Volume** <*float*>: Amount to multiply gunfire sound volume.

**Durability** <*uint8*: 1>:

**Ballistic_Drop** <*float*>:

**Gunshot_Rolloff_Distance_Multiplier** <*float* : `1.0`(Silenced),`0.5`(default)>

### Grips

**Type**: `Grip`

No specific configuration, see [Attachments](#attachments)

### Magazines

**Type**: `Magazine`

**Pellets** <*uint8*>: Number of bullet rays shot.

**Stuck** <*uint8*>: Amount of quality to lose when hit. Fired projectiles can be picked back up until quality reaches 0.

**Projectile_Damage_Multiplier** <*float*>: Multiplier on the damage dealt by projectile weapons.

**Projectile_Blast_Radius_Multiplier** <*float*: 1>: Multiplier on the blast radius of projectiles fired from projectile weapons.

**Projectile_Launch_Force_Multiplier** <*float*: 1>: Multiplier on the launch force applied to projectiles fired from projectile weapons.

**Range** <*float*>:

**Player_Damage** <*float*>:

**Zombie_Damage** <*float*>:

**Animal_Damage** <*float*>:

**Barricade_Damage** <*float*>:

**Structure_Damage** <*float*>:

**Vehicle_Damage** <*`float`*>:

**Resource_Damage** <*`float`*>:

**Explosion_Launch_Speed** <*float*: `Player_Damage * 0.1`>:

**Explosion**: <*uint16*>

**Tracer**: Tracer effect ID.

**Impact**: Impact effect ID.

**Speed**: Multiplier on reload speed.

**Explosive** <*flag*>:

**Spawn_Explosion_On_Dedicated_Server** <*flag*>:

**Delete_Empty**: Specified if the magazine should be deleted when depleted.

**Should_Fill_After_Detach**: Specified if ammunition is fully refilled when reloaded, effectively allowing for infinite ammunition only limited by reload time.

Limb-independent damage is also applicable.

### Sights

**Type**: `Sight`

**Vision** <*LightingVision*>: `civilian`, `military`

**Nightvision\_Color\_{R,G,B,A}** <*uint8*: `102, 102, 102, 0`(civilian), `20, 120, 80, 0.0`(military)>: Specify the color of the nightvision scope, all 4 key/value pairs do not need to be present. If they aren't present, the default value for the given type will be used.

**Nightvision\_Fog\_Intensity** <*float*: `0.5`(civilian), `0.25`(military)>:

**Zoom** <*float*>: Multiplicative amount of zoom. Must be at least 1.

**Holographic** <*flag*>: Use the holographic sight effects .

### Tacticals

**Type**: `Tactical`

**Laser** <*flag*>: Specified if a laser can be toggled.

**Light** <*flag*>: Specified if a light can be toggled. If 

  **SpotLight_Range** <*float*: `64`>:

  **SpotLight_Angle** <*float*: `90`>:

  **SpotLight_Intensity** <*float*: `1.3`>:

  **SpotLight_Color\_{R,G,B,A}** <*uint8*: `245, 223, 147, 255`>:

**Rangefinder** <*flag*>: Specified if a rangefinder can be toggled.

**Melee** <*flag*>: Specified if a melee attack can be performed.

## Clothing

**Type**: `Backpack`, `Glasses`, `Hat`, `Mask`, `Pants`, `Shirt`, `Vest`

**Useable**: `Backpack`, `Glasses`, `Hat`, `Mask`, `Pants`, `Shirt`, `Vest`

**Pro**: Specified if the item should be unable to spawn. Intended for cosmetics. Will disable the ability to change **Armor** through **Movement_Speed_Multiplier** properties.

**Armor** <*float*: `1`>: Incoming damage is multiplied by this value. i.e. .50 would half incoming damage.

**Armor_Explosion** <*float*: *`Armor`*>: 

**Proof_Water** <*flag*>:

**Proof_Fire** <*flag*>:

**Proof_Radiation** <*flag*>:

**Movement_Speed_Multiplier** <*float*: `1`>:

**Visible_On_Ragdoll** <*Boolean*: `true`>:

**Hair_Visible** <*Boolean*: `true`>:

**Beard_Visible** <*Boolean*: `true`>:

**Mirror_Left_Handed_Model**  <*Boolean*: `true`>:

### Bag

This is solely a subclass and cannot be used on it's own.

**Width** <*uint8*>: The amount of horizontal storage space.

**Height** <*uint8*>: The amount of vertical storage space.

#### Backpack

See [Bag](#bag)

#### Pants

See [Bag](#bag)

#### Shirt

**Has_1P_Character_Mesh_Override** <*Boolean*: `false`>:

**Character_Mesh_3P_Override_LODs** <*uint16*>:

**Has_Character_Material_Override** <*Boolean*: `false`>:

**Ignore_Hand** <*flag*>:

#### Vests

See [Bag](#bag)

### Gear

**Hair** <*flag*>: Specified if hair shows up when wearing.

**Beard** <*flag*>: Specified if beard shows up when wearing.

**Hair_Override** <*String*>: Specified if hair material should be used. Only applicable to hats, masks, and glasses.
#### Glasses

**Blindfold**: Specified if the player should be blinded when the glasses are worn.

**Vision** <*LightingVision*>: `none`, `civilian`, `military`, `headlamp`. If this isn't present, you won't be able to use spotlight or nightvision properties

**SpotLight_Range** <*float*: `64`>: Requires `headlamp` **Vision** type.

**SpotLight_Angle** <*float*: `90`>: Requires `headlamp` **Vision** type.

**SpotLight_Intensity** <*float*: `1.3`>: Requires `headlamp` **Vision** type.

**SpotLight_Color\_{R,G,B,A}** <*uint8*: `245, 223, 147, 255`>: Requires `headlamp` **Vision** type.

**Nightvision\_Color\_{R,G,B,A}** <*uint8*: `102, 102, 102, 0`(civilian), `20, 120, 80, 0.0`(military)>: Requires `civilian` or `military` **Vision** type. Specify the color of the nightvision, all 4 key/value pairs do not need to be present. If they aren't present, the default value for the given type will be used. The `G` and `B` values will be set to whatever the `R` value is by the game when the civilian night vision type is used, if you want to change these independently, you'll have to use the military vision type instead.

**Nightvision\_Fog\_Intensity** <*float*: `0.5`(civilian), `0.25`(military)>: Requires `civilian` or `military` **Vision** type.

**Blindfold** <*flag*>: Will blindfold the player when worn

#### Hat

See [Gear](#gear)

#### Mask

**Earpiece** <*flag*>:

### Body Mesh Replacements

Body mesh replacements are only applicable to shirts. See [CharacterMeshReplacement.md](../CharacterMeshReplacement.md) for full documentation.

**Has_1P_Character_Mesh_Override**: `false`, `true`

**Character_Mesh_3P_Override_LODs**: Number of LODs.

**Has_Character_Material_Override**: `false`, `true`

**Hair_Visible**: `false`, `true`. Defaults to true.

**Beard_Visible**: `false`, `true`. Defaults to true.

## Consumables

Consumables in _Unturned_ encompass anything that is irreversibly consumed by the player on use, and directly affect a player's stats such as food or health.

**Type**: `Food`, `Medical`, `Water`

**Useable**: `Consumeable`

**Aid**: Specified if the item can be used on other players via right-click.

**Bleeding**: Specified if bleeding is healed. Deprecated in favor of Bleeding_Modifier.

**Bleeding_Modifier**: `Cut`, `Heal`, `None`

**Broken**: Specified if broken legs are healed. Deprecated in favor of Bones_Modifier.

**Bones_Modifier**: `Break`, `Heal`, `None`

**Health**: The number of health to restore.

**Food**: The number of food to restore.

**Water**: The number of water to restore.

**Food_Constrains_Water**: Specified if max potential water gain should be capped by actual food gain. Applies to items where max potential water gain is less than max potential food gain.

**Disinfectant**: The number of immunity to restore.

**Virus**: The number of immunity to deplete.

**Energy**: The number of energy to restore.

**Vision**: The length of hallucinations. The length does not stack with each time eaten, but the timer is reset for equal or longer Vision values relative to the remaining hallucination time.

**Oxygen**: The number of oxygen to restore or deplete.

**Should_Delete_After_Use**: `false`, `true`. Defaults to true.

**Item_Reward_Spawn_ID**: ID of an item generated upon usage of the consumable.

**Min_Item_Rewards**: Minimum possible amount of items rewarded.

**Max_Item_Rewards**: Maximum possible amount of item rewarded.

## Crafting Supplies

**Type**: `Supply`

## Fishing Poles

**Type**: `Fisher`

**Useable**: `Fisher`

**Reward_ID**: ID of the spawn table to pull catchable items from.

## Fuel Canisters

**Type**: `Fuel`

**Useable**: `Fuel`

**Fuel**: Amount of fuel units added to target.

## Growth Supplements

**Type**: `Grower`

**Useable**: `Grower`

## Mapping Equipment

**Type**: `Map`, `Compass`

**Enables_Map**: Specified if this item provides a satellite map display.

**Enables_Chart**: Specified if this item provides a chart map display.

**Enables_Compass**: Specified if this item provides a compass display.

## Melee Weapons

## Optics

**Type**: `Optic`

**Useable**: `Optic`

**Zoom**: Multiplicative amount of zoom.

## Parachutes

**Type**: `Cloud`

**Useable**: `Cloud`

**Gravity**: Decimal multiplier on the influence of gravity.

## Projectiles

**Type**: `Throwable`

**Useable**: `Throwable`

**Explode_On_Impact**: Specified if the projectile immediately explodes upon impact.

**Sticky**: Specified if the projectile sticks to objects upon impact.

**Fuse_Length**: Timer in seconds for fuse length. Defaults to 2 seconds.

Limb-independent damage is also applicable.

## Radiation Filters

**Type**: `Filter`

**Useable**: `Filter`

## Ranged Weapons

**Type**: `Gun`

**Useable**: `Gun`

**Barrel**: The barrel item ID to spawn attached.

**Grip**: The grip item ID to spawn attached.

**Sight**: The sight item ID to spawn attached.

**Tactical**: The tactical item ID to spawn attached.

**Hook_Barrel**: Specified if a barrel can be manually attached.

**Hook_Grip**: Specified if a grip can be manually attached.

**Hook_Sight**: Specified if a sight can be manually attached.

**Hook_Tactical**: Specified if a tactical can be manually attached.

**Magazine**: The magazine item ID to spawn attached.

**Magazine_Replacements**: Number of unique conditions with alternative default magazine attachments.

**Magazine_Replacement\_#\_Map**: Name of the map the condition applies to.

**Magazine_Replacement\_#\_ID**: ID of the alternative magazine attachment.

**Ammo_Min**: The minimum amount of ammo to generate.

**Ammo_Max**: The maximum amount of ammo to generate.

**Safety**: Specified if the safety firing mode can be swapped to.

**Semi**: Specified if semi-automatic firing mode can be swapped to.

**Bursts**: Number of shots fired in a burst. Specified if burst firing mode can be swapped to.

**Auto**: Specified if automatic firing mode can be swapped to.

**Caliber**: The caliber ID to check for attachment compatibility.

**Attachment_Calibers**: Number of unique attachment calibers.

**Attachment_Caliber_#**: ID of applicable caliber for hook attachments.

**Magazine_Calibers**: Number of unique magazine calibers.

**Magazine_Caliber_#**: ID of applicable caliber for magazine attachments.

**Firerate**: The minimum number of ticks between the firing of each bullet.

**Replace**: Multiplier of the reload animation length before the magazine is respawned.

**Unplace**: Multiplier of the reload animation length before the magazine is despawned.

**Reload_Time**: Multiplier on reload animation length.

**Action**: `Bolt`, `Break`, `Minigun`, `Pump`, `Rail`, `Rocket`, `String`, `Trigger`. Rocket action has inherently explosive projectiles, uses ballistic force instead of alternative advanced ballistics options, and has infinite firing range.

**Delete_Empty_Magazines**: Specified if the attached magazine should be deleted when depleted. Deprecated in favor of Should_Delete_Empty_Magazines.

**Should_Delete_Empty_Magazines**: `false`, `true`. No applicable default flag. If set to true, it will override how empty magazines are handled by the action item mode.

**Spread_Aim**: The spread multiplier when aiming down sights. This is multiplied by the spread_hip value.

**Spread_Hip**: The spread multiplier when not aiming down sights.

**Ballistic_Force**: Measured in Newtons. Primarily applicable to the rocket action, and usage ignores all other advanced ballistic options.

**Ballistic_Steps**: Defaults to (range / 10).

**Ballistic_Travel**: Defaults to 10.

**Ballistic_Drop**: Defaults to 0.002.

**Recoil_Aim**: Multiplier on all recoil parameters when aiming down sights. Defaults to 1.

**Recoil_Min_X**: The minimum horizontal look recoil in degrees.

**Recoil_Min_Y**: The minimum vertical look recoil in degrees.

**Recoil_Max_X**: The maximum horizontal look recoil in degrees.

**Recoil_Max_Y**: The maximum vertical look recoil in degrees.

**Recover_X**: Multiplier on degrees to be counter-animated horizontally over the next 250 milliseconds.

**Recovery_Y**: Multiplier on degrees to be counter-animated vertically over the next 250 milliseconds.

**Shake_Min_X**: The minimum X axis physical recoil.

**Shake_Max_X**: The maximum X axis physical recoil.

**Shake_Min_Y**: The minimum Y axis physical recoil.

**Shake_Max_Y**: The maximum Y axis physical recoil.

**Shake_Min_Z**: The minimum Z axis physical recoil.

**Shake_Max_Z**: The maximum Z axis physical recoil.

**Muzzle**: The muzzle effect ID to play when shooting.

**Shell**: The shell effect ID to play after shooting.

**Turret**: Specified if the weapon should be treated as a vehicular turret.

**Can_Ever_Jam**: Specified if the weapon can jam.

**Jam_Quality_Threshold**: Decimal representative of the quality percentage threshold for jamming can begin to occur.

**Jam_Max_Chance**: Decimal-to-percent chance for jamming to occur.

**Unjam_Chamber_Anim**: Name of the animation clip to play for unjamming. Defaults to UnjamChamber.

**Can_Aim_During_Sprint**: Specified if the player can sprint while aiming down sights.

**Ammo_Per_Shot**: Numeric option for ammunition consumed per shot.

**Fire_Delay_Seconds**: Numeric option for the delay between initiating attempting to fire, and the actual firing of the weapon.

**Allow_Magazine_Change**: `false`, `true`. Defaults to true. If false, the magazine in the weapon cannot be reloaded, unloaded, or replaced.

Damage data (explosive, limb-dependent, and limb-independent setups), durability, and wear are also applicable.

## Remote Triggers

**Type**: `Detonator`

**Useable**: `Detonator`

## Restraining Devices

### Catchers

**Type**: `Arrest_Start`

**Useable**: `Arrest_Start`

**Strength**: Amount of effort required to break free.

### Releasers

**Type**: `Arrest_End`

**Useable**: `Arrest_End`

**Recover**: ID of the restraining device that can be unlocked with this item.

## Structures

**Type**: `Structure`

**Useable**: `Structure`

**Construct**: `Floor`, `Floor_Poly`, `Pillar`, `Post`, `Rampart`, `Roof`, `Roof_Poly`, `Wall`

**Health**: Amount of health.

**Range**: Distance away the barricade can be placed from the player.

**Explosion**: Destruction effect ID.

**Foliage_Cut_Radius**: Numerical value in meters for the radius in which foliage is removed from around the structure. Only applicable to floor structure types.

## Tools

### Car Jacks

Car jacks launch vehicles into the air as a method of reorienting them if they were flipped over.

**Type**: `Tool`

**Useable**: `Carjack`

### Car Lock Picks

Car lock picks allow players to unlock any locked vehicle, but are single-use.

**Type**: `Tool`

**Useable**: `Carlockpick`

### Tire Replacements

Tire replacements allow for adding or removing tires from four-wheeled vehicles.

**Type**: `Tire`

**Useable**: `Tire`

**Mode**: `Add`, `Remove`

### Vehicle Batteries

Vehicle batteries can be placed into vehicles, allowing them to perform activities that consume electrical energy rather than fuel. They are affected by quality.

**Type**: `Vehicle_Repair_Tool`

**Useable**: `Battery_Vehicle`

### Walkie-talkies

When initiating voice chat with a walkie-talkie held, voice is transmitted through a two-way radio. An audible cue plays when initiating voice chat.

**Type**: `Tool`

**Useable**: `Walkie_Talkie`

## Water Canisters

**Type**: `Refill`

**Useable**: `Refill`

**Water**: The number of water to restore.
