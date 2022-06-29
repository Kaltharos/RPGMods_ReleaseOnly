# RPGMods
### [Original Repository](https://github.com/NopeyBoi/ChatCommands)
### Server Only Mod
This Mod is originaly made by NopeyBoi and is now modified, and has a lot of extra additions in.\
Read the changelog for extra details.

## Experience System
Disable the VRising Gear Level system and replace it with a traditional RPG EXP system.

## HunterHunted System
A new system where every NPC you killed contribute to a heat system,\
if you kill too many NPC from that faction, eventually your heat level will raise higher and higher.

The higher your heat level is, a more difficult squad of ambushers will be sent by that faction to kill you.\
Heat level will eventually cooldown the longer you went without killing NPCs from that faction,\
space your kills so you don't get hunter by an extremely elite group of assassins.

Otherwise, if you are dead for any reason at all, your heat/wanted level will reset back to anonymous.\
`-- Note` Ambush may only occur when the player is in combat.

## Kill Announcer & PvP Statistics
Every PvP kill will be announced server wide to all users.\
Kill/Death will also be recorded, and a ladder board for the Top 5 K/D in the server.

## Config
### Basic
- `Prefix` [default `.`]\
The prefix use for chat commands.
- `DisabledCommands` [default `dim,debug,bufflist,speed,sunimmunity,sun,bloodsight,bs`]\
Enter command names to disable them. Seperated by commas.
- `WayPoint Limits` [default `3`]\
Set a waypoint limit per user.
- `DBSave Ticks` [default `600`]\
Save the player data from the mods to a json file every specified seconds.
- `Enable SunImmunity Fix` [default `true`]\
Enable the SunImmunity Fix to fix the persistance immunity issue.
- `Enable BloodHUD Fix` [default `true`]\
Enable the BloodHUD Fix to fix the persistance HUD issue.
### PvP
- `Announce PvP Kills` [default `true`]\
Do I really need to explain this...?
- `Enable the PvP Ladder` [default `true`]\
Hmm... well it enables the ladder board in .pvp command
### Hunter Hunted
- `Enable` [default `true`]\
Enable/disable the HunterHunted system.
- `Heat Cooldown Value` [default `35`]\
Set the reduction value for player heat for every cooldown interval.
- `Bandit Heat Cooldown Value` [default `35`]\
Set the reduction value for player heat from the bandits faction for every cooldown interval.
- `Cooldown Interval` [default `60`]\
Set every how many seconds should the cooldown interval trigger.
- `Ambush Interval` [default `300`]\
Set how many seconds player can be ambushed again since last ambush.
- `Ambush Chance` [default `50`]\
Set the percentage that an ambush may occur for every cooldown interval.
### Experience
- `Enable` [default `true`]\
Enable/disable the Experience system.
- `Max Level` [default `80`]\
Configure the experience system max level..
- `Multiplier` [default `1`]\
Multiply the experience gained by the player.
- `VBlood Multiplier` [default `15`]\
Multiply the experience gained from VBlood kills.
- `EXP Lost / Death` [default `0.10`]\
Percentage of experience the player lost for every death by NPC, no EXP is lost for PvP.
- `Constant` [default `0.2`]\
Increase the constant component in the EXP Formula.\
[EXP Table & Formula](https://bit.ly/3npqdJw)

## Permissions
You can only decide whether a command is admin only or not at this time.\
The permissions are saved in `BepInEx/config/RPGMods/permissions.json` and look like this:
```json
{
  "dim": true,
  "debug": true,
  "bufflist": true,
  "bl": true,
  "help": false,
  "speed": true,
  "kit": true,
  "heat": false,
  "ping": false,
  "pvp": false,
  "waypoint": false,
  "wp": false,
  "health": true,
  "hp": true,
  "give": true,
  "g": true,
  "bloodsight": true,
  "bs": true,
  "bloodpotion": true,
  "bp": true,
  "sunimmunity": true,
  "sun": true,
  "spawnnpc": true,
  "snp": true,
  "nocooldown": true,
  "nocd": true,
  "resetcooldown": true,
  "cd": true,
  "teleport": false,
  "tp": false,
  "godmode": true,
  "god": true,
  "autorespawn": true,
  "experience": false,
  "xp": false
}
```
Removing a command from the list will automatically set it's value to `false`.

## Chat Commands
`help [<Command>]`: Shows a list of all commands.\
`kit <Name>`: Gives you a previously specified set of items.
<details>
<summary>How does kit work?</summary>

&ensp;&ensp;You will get a new config file located in `BepInEx/config/RPGMods/kits.json`
```json
[
  {
    "Name": "Example1",
    "PrefabGUIDs": {
      "820932258": 50, <-- 50 Gem Dust
      "2106123809": 20 <-- 20 Ghost Yarn
    }
  },
  {
    "Name": "Example2",
    "PrefabGUIDs": {
      "x1": y1,
      "x2": y2
    }
  }
]
```
&ensp;&ensp;A list of all PrefabGUIDs can be found [here](https://github.com/NopeyBoi/ChatCommands/blob/main/PrefabGUIDs%20-%209th%20June%202022.txt)!

</details>

`bloodsight`: Enable blood hunger hud without using the necessary ability.\

`bloodpotion <BloodType> [<Quality>]`: Creates a Potion with specified Blood Type, Quality and Value.\
&ensp;&ensp;**Example:** `bloodpotion Scholar 100`

`waypoint <Name|Set|Remove|List> [<Name>] [global]`: Teleports you to previously created waypoints.\
&ensp;&ensp;**Example:** `waypoint set home` <-- Creates a local waypoint just for you.\
&ensp;&ensp;**Example:** `waypoint set arena global` <-- Creates a global waypoint for everyone (Admin-Only).\
&ensp;&ensp;**Example:** `waypoint home` <-- Teleports you to your local waypoint.\
&ensp;&ensp;**Example:** `waypoint remove home` <-- Removes your local waypoint.\
&ensp;&ensp;**Example:** `waypoint list` <-- Shows a list of all to you accessible waypoints.

`give <Item Name> [<Amount>]`: Adds the specified Item to your Inventory.\
&ensp;&ensp;**Example:** `give Stone Brick 17`

`spawnnpc <Prefab Name> [<Amount>] [<Waypoint>]`: Spawns a NPC. Optional: To a previously created waypoint.\
&ensp;&ensp;**Example:** `spawnnpc CHAR_Cursed_MountainBeast_VBlood 1 arena`

`health <Amount>`: Sets your health to the specified amount.\
`speed <Amount|Reset>`: Increase your movement speed by the specified amount.\
`sunimmunity`: Toggles sun immunity.\
`nocooldown`: Toggles all skills & abilities to have no cooldown.\
`resetcooldown [<PlayerName>]`: Reset all skills & abilities cooldown for you or the specified player.\
`teleport <PlayerName>`: Teleport to another online player within your clan.\
`godmode`: Toggles god mode for you.\
`autorespawn [<All>|<PlayerName>]`: Toggles auto respawn on same position on death.\
&ensp;&ensp;**Admin Only Params -> `[<All>|<PlayerName>]`** `Toggle the auto respawn for specified player or server wide.

`heat`: Checks your heat/wanted level by the factions.\
&ensp;&ensp;**Admin Only Params -> `[<debug>|<value>] [<value>]`** `Display current configuration or set your heat value`\
&ensp;&ensp;**Example:** `heat 500 500`
`ping`: Show you your latency to the server.\
`pvp`: Display your PvP statistics & the current leaders in the ladder.\
`experience`: Diplays your current exp and progression to the next level.\
&ensp;&ensp;**Admin Only Params -> `[<set>] [<value>] [<PlayerName>]`** `Set your or the specified player experience value`\
&ensp;&ensp;**Example:** `experience set 1000`\
&ensp;&ensp;**Example:** `experience set 2000 LegendaryVampire`

## More Information
<details>
<summary>Changelog</summary>

`1.3.9`
- Added Max Level configuration for experience system
- Improved EXP gain algorithm
- Minor bug fix

`1.3.8`
- Added BloodHUD command
- Added Experience System
- Added some more configs
- Added AutoSave for PvP & Experience System

`1.3.7`
- Improved ambush squad variety
- Added PvP stats for kills & death
- Added configuration for HunterHunted system
- Added configuration for PvP Kill announcement system
- Added !pvp command
- I/O violation error on first installation fixed.

`1.3.6`
- Added Hunter & Hunted system
- Added a player kill announcement
- Added heat command
- Added ping command

`1.3.5`
- Added godmode command
- Added autorespawn command
- Optimization & small fixes

`1.3.4`
- Added teleport command

`1.3.3`
- Added nocooldown command
- Added resetcooldown command

`1.3.2`
- Implemented a hacky fix for sunimmunity being persistent on respawn/relogin

`1.3.1`
- Fixed NPC Spawn
- Added ammount to spawn multiple NPC
- Temporary fix for sun immunity
- Hide commands from user without sufficient priviledge
- Disabled "waypoint" command for user in combat
- Admin ignore waypoint limits

`1.3.0`
- Added new command: spawnnpc
- Added rather whacky "permissions"
- Added a Waypoint Limit per User
- Added waypoint list option
- Added a reset function to speed
- Fixed health command
- Having no set parameters on ?health restores max health

`1.2.0`
- Added new command: waypoint
- Added new command: kit
- Added new config: DisabledCommands
- Fixed console spam when using give

`1.1.1`
- Tiny fix

`1.1.0`
- Added new command: bloodpotion
- Reworked give command (Send items directly into the inventory now)

`1.0.0`
- Initial release

</details>

<details>
<summary>Known Issues</summary>

- If BloodHUD command is enabled and the fix isn't enabled the user will be left with persistent BloodHUD.
- If SunImmunity command is enabled and the fix isn't enabled the user will be left with persistent SunImmunity.
- A save wipe is required to fix those issue, so don't enable those 2 command on your primary server if possible.

</details>

<details>
<summary>Planned Features</summary>

- Chat Permission Roles
- Kits Option: Limited Uses
- More optimization! It never hurts to optimize!
- Need a better fix for sunimmunity persistence issue
- Need a better system for bloodhud
- Add ban command
- Add heal command for healing other player

</details>
