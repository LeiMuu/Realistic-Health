# Realistic Health

**This module focuses on managing the health states of both players and AI characters. It consists of seven functional submodules, originally designed to meet the advanced needs of a private server community. The goal is to provide high customizability and adaptability across various gameplay modes and scenarios, enabling community or private server administrators to fine-tune parameters as needed.**

* * *

### **🎯 Mod Information:**

*   Mutator name: **RealisticHealth**
*   Requirement : Server and Client
*   Compatible with all game modes, including armory or class-modified mutators.
*   Not compatible with mods with bleed and health vocabulary, including offline mode too.
*   And includes multiple sets of settings such as **RealisticHealth2**, **RealisticHealth3**.

### **🧩 What you can get:**

*   **HealthOverride** : Customize the maximum health of players and various AI classes.
*   **HealthRegen** : Adjust health regeneration for players and AI characters.
*   **Bleeding** : Simulate bleeding effects and sustained consequences after injury.
*   **CurlyBody** : Provide physical reaction feedback based on bleeding conditions.
*   **Shock** : Simulate action restrictions caused by hypovolemic shock.
*   **Fatigue** : Modify stamina drain and recovery when injured.
*   **Dying** : Create an immersive near-death experience.

### **🛠 How to set up:**

1. Make sure you are familiar with the use of the module, you can refer to the [official guide](https://mod.io/g/insurgencysandstorm/r/server-admin-guide).
2. Add mod ID **946949** in your server's ModList.
3. Add the Mutator name to the server startup parameters, or [set it dynamically based on the map](https://mod.io/g/insurgencysandstorm/m/mapvotelabels).
4. Add Mutator configuration in your server's Game.ini .
5. Restart the server.

### **🔥 Mutator configuration:**

*   Default (Ready to use)

```ini
[/RealisticHealth/Mutators/BP_Mutator_RealisticHealth.BP_Mutator_RealisticHealth_C]
;HealthOverride Module
UseHealthOverride=True
PlayerMaxHealth=200.0
NormalAIMaxHealth=200.0

;AdvancedAIClass=SubstringClassName1
;...and more, but no more than three are recommended.
AdvancedAIMaxHealth=250.0
;EilteAIClass=SubstringClassName1
;...and more, but no more than three are recommended.
EliteAIMaxHealth=300.0
;BossAIClass=SubstringClassName1
;...and more, but no more than three are recommended.
BossAIMaxHealth=350.0

;HealthRegen Module(Player)
UseHealthRegen=False
PlayerHealthRegenEveryFewSec=5.0
PlayerHealthRegenAmountPerTime=10.0
PlayerHealthRegenUpperLimit=200.0

;HealthRegen Module(AI)
IsHealthRegenAI=False
;If not specified, the default will apply to all AI soldiers (both friendly and enemy).
;AIClassForHealthRegen=SubstringClassName1
;...and more, but no more than three are recommended.
AIHealthRegenEveryFewSec=10.0
AIHealthRegenRatioPerTime=0.05
AIHealthRegenUpperLimitRatio=0.5

;Bleeding Module
UseBleeding=True
IsBleedingAI=True
DamageThresholdToBleed=30.0
CauseBleedingChance=0.45
LargeBleedingChance=0.25
DamageRatioToBleedpoolLarge=0.6
DamageRatioToBleedpoolSmall=0.25
BleedpoolRatioToPerBleedLarge=0.16
BleedpoolRatioToPerBleedSmall=0.1
AnimThresholdToPerBleedDamage=2.5
PerSecToBleed=1.0
MaxBleedPlayerCount=16
BleedingResponseType=1

;CurlyBody Module
UseCurlyBody=True
IsCurlyBodyAI=False
CurlyBodyDegree=5.0
CurlyBodyAdditiveFac=1.0

;Shock Module
UseShock=True
ShockChance=0.05
ShockDuration=5.0
DeafnessDuration=5.0

;Fatigue Module
UseFatigue=True
HealthThresholdToFatigue=150.0
InterruptSprintSec=5.0
DrainStaminaSprinted=20.0
SwayScaleFatigue=5.0

;Dying Module
UseDying=True
TinnitusDuringDying=False
HealthThresholdToDying=10.0
DyingShakeScale=0.5
SwayScaleDying=50.0

[/RealisticHealth/Mutators/BP_Mutator_RealisticHealth2.BP_Mutator_RealisticHealth2_C]
;RealisticHealth2 has the same variables as RealisticHealth, and is suitable for those who need multiple settings to cope with different game modes or scenarios.
[/RealisticHealth/Mutators/BP_Mutator_RealisticHealth3.BP_Mutator_RealisticHealth3_C]
;RealisticHealth3 has the same variables as RealisticHealth, and is suitable for those who need multiple settings to cope with different game modes or scenarios.
```

*   Customization (Combination with [EnemyBoatSpotted](https://mod.io/g/insurgencysandstorm/m/ebs-custom-theatre), [MadBots](https://mod.io/g/insurgencysandstorm/m/madbots), [Medicon](https://mod.io/g/insurgencysandstorm/m/medicon) Use Cases)

```ini
[/RealisticHealth/Mutators/BP_Mutator_RealisticHealth.BP_Mutator_RealisticHealth_C]
UseHealthOverride=True
PlayerMaxHealth=275.0
NormalAIMaxHealth=275.0
AdvancedAIClass=Elite
AdvancedAIClass=Outpost
AdvancedAIMaxHealth=350.0
EilteAIClass=JuggernautLMG
EilteAIClass=JuggernautHeavy
EliteAIMaxHealth=1600.0
BossAIClass=Bruiser
BossAIMaxHealth=2000.0
UseHealthRegen=True
PlayerHealthRegenEveryFewSec=5.0
PlayerHealthRegenAmountPerTime=5.0
PlayerHealthRegenUpperLimit=50.0
IsHealthRegenAI=False
AIHealthRegenEveryFewSec=10.0
AIHealthRegenRatioPerTime=0.05
AIHealthRegenUpperLimitRatio=0.5
UseBleeding=True
IsBleedingAI=True
DamageThresholdToBleed=45.0
CauseBleedingChance=0.90
LargeBleedingChance=0.20
DamageRatioToBleedpoolLarge=8.0
DamageRatioToBleedpoolSmall=4.0
BleedpoolRatioToPerBleedLarge=0.10
BleedpoolRatioToPerBleedSmall=0.05
AnimThresholdToPerBleedDamage=10.0
PerSecToBleed=1.0
MaxBleedPlayerCount=16
BleedingResponseType=4
UseCurlyBody=True
IsCurlyBodyAI=True
CurlyBodyDegree=8.0
CurlyBodyAdditiveFac=1.2
UseShock=True
ShockChance=0.08
ShockDuration=1.0
DeafnessDuration=5.0
UseFatigue=True
HealthThresholdToFatigue=100.0
InterruptSprintSec=3.0
DrainStaminaSprinted=30.0
SwayScaleFatigue=10.0
UseDying=True
TinnitusDuringDying=True
HealthThresholdToDying=30.0
DyingShakeScale=0.5
SwayScaleDying=50.0

[/RealisticHealth/Mutators/BP_Mutator_RealisticHealth2.BP_Mutator_RealisticHealth2_C]
;RealisticHealth2 has the same variables as RealisticHealth, and is suitable for those who need multiple settings to cope with different game modes or scenarios.
[/RealisticHealth/Mutators/BP_Mutator_RealisticHealth3.BP_Mutator_RealisticHealth3_C]
;RealisticHealth3 has the same variables as RealisticHealth, and is suitable for those who need multiple settings to cope with different game modes or scenarios.
```

* * *

### **✏️ Customization tips:**

*   Through RealisticHealth, RealisticHealth2 and RealisticHealth3 mutators, submodule functions are grouped and managed to facilitate the combination and reuse of settings in different scenarios.
*   Make good use of the modules provided by other authors to combine and match according to your needs, ensure single responsibility and make good use of modularity, such as [Headshot Modifiers](https://mod.io/g/insurgencysandstorm/m/headshot) or [HealthBarPlus](https://mod.io/g/insurgencysandstorm/m/healthbarplus).

* * *

### **⚠️ Known Issues:**

*   😓 When friendly damage occurs, the friendly damage modifier is not set to 1, which may cause the bleed status to not be triggered when the damage is higher than the max HP. (Most of the cases happen in headshots, but teammates don't die).

* * *

🔖 This module aims to offer a comprehensive and extensible health system framework, helping administrators build a more realistic and challenging gameplay environment.