# Forge of Foes 5e Monster Stats
Here is an expansion on the FoF Monster Stats Generator. This generator now allows for you to choose a Type, Role, and Theme in addition to the CR based on the Forge of Foes monster builder. It will assign your monster stats absed on the CR and Type and add a random power based on the Type, Role or Theme. 
Stat calculations by CR were created by me with information from the 5e SRD.
Monster Type calculations and base stats were created by me based on information from the 5e SRD.
Monster Role calculations were created by me based on information about the Roles from the Lazy GM's 5e Monster Builder Resource Document. There are more detailed calculations in Forge of Foes, see below on how to add those.
Powers are the common powers listed in the document which are adapted from the 5e SRD. Currently they are tagged with a role which I chose based on the Lazy GM's 5e Monster Builder Resource Document. There are even more powers in Forge of Foes, see below on how to add those.

## Editing this document
Fear not if you own Forge of Foes or simply want to add your own powers, themes, roles to this tool. Here is a basic guide. 
I recommend opening the html file with some kind of code editor like [Notepad++](https://notepad-plus-plus.org/downloads/) or [VsCode](https://code.visualstudio.com/Download), both are free. If not regular Notepad will work. Ctrl+f will allow you to search within a document in any of these.

JSON - the objects you'll be editing are in [JSON format](https://www.w3schools.com/whatis/whatis_json.asp) since I've alread given examples you should just need to copy paste.
Comments - lines with '//' before them are comments, meaning they dont get run as actual code. The examples I have in the code are commented, when you copy paste to a new line remove the // (Notepad++ or VS code should make this way easier as it will be a different color)

### Powers
You will most likely want to add more powers, either your own or ones from Forge of Foes. 
- Open the html file in a code editor
- Search the file for "Monster Powers"
- You will see an object like this:
```javascript
    /**
     * Monster Powers
     * 
     * name - Name of Power to display
     * description - Description of Power to display
     * tags - Type, Role, or Theme to tag the power with. 
     * You may add as many tags as you want from the lists above to any power,
     * Consider adding the additional powers listed in Forge of Foes
     */
    const powers = [
      // { tags: ['Tag', 'Another tag'], name: 'Name.', description: "Description", }, // I'm a power! You can copy paste me at the end to add your own just remove the '//' from the start to uncomment
      // Common powers that I have added tags to based on the role descriptions
      { tags: ['Common', "Artillery"], name: 'Damaging Blast.', description: 'This creature has one or more single-target ranged attacks using the attack bonus and damage calculated above, and which deal damage of an appropriate type.', },
      { tags: ['Common'], name: 'Damage Reflection.', description: "Whenever a creature within 5 feet of this creature hits them with a melee attack, the attacker takes damage in return of a type appropriate to the creature. The damage dealt is equal to half the damage of one of this creature's attacks. If you give a creature this feature, give them one less attack than normal.", },
      { tags: ['Common', "Skirmisher"], name: 'Misty Step.', description: "As a bonus action, this creature can teleport up to 30 feet to an unoccupied space they can see.", },
      { tags: ['Common'], name: 'Knockdown.', description: "When this creature hits a target with a melee attack, the target must succeed on a Strength saving throw or be knocked prone.", },
      { tags: ['Common', "Controller"], name: 'Restraining Grab.', description: "When this creature hits a target with a melee attack, the target is grappled (escape DC based on this creature's Strength or Dexterity modifier). While grappled, the target is restrained.", },
      { tags: ['Common'], name: 'Damaging Burst.', description: "As an action, this creature can create a burst of energy, magic, spines, or some other effect in a 10-foot-radius sphere, either around themself or at a point within 120 feet. Each creature in that area must make a Dexterity, Constitution, or Wisdom saving throw (your choice, based on the type of burst). On a failure, a target takes damage of an appropriate type equal to half this creature's total damage per round. On a success, a target takes half as much damage.", },
      { tags: ['Common', "Ambusher"], name: 'Cunning Action.', description: "On each of their turns, this creature can use a bonus action to take the Dash, Disengage, or Hide action.", },
      { tags: ['Common'], name: 'Damaging Aura.', description: "Each creature who starts their turn within 10 feet of this creature takes damage of a type appropriate to the creature. The damage dealt is equal to half the damage of one of this creature's attacks. If you give a creature this feature, give them one less attack than normal.", },
      { tags: ['Common', "Bruiser"], name: 'Energy Weapons', description: "The creature's weapon attacks deal extra damage of an appropriate type. You can add this damage on top of the creature's regular damage output to give them a combat boost, or you can replace some of the creature's normal weapon damage with this energy damage.", },
      { tags: ['Common'], name: 'Damage Transference.', description: "When this creature takes damage, they can transfer half or all of that damage (your choice) to a willing creature within 30 or 60 feet of them. This feature is particularly good for boss monsters.", },
      // Below are from the 5e SRD
      { tags: ['Common', "Leader"], name: 'Leadership.', description: "As a reaction the creature can utter a special command or warning whenever a nonhostile creature that it can see within 30 feet of it makes an attack roll or a saving throw. The creature can add a d4 to its roll.", },
      { tags: ['Common', "Defender"], name: 'Protection.', description: "When an ally within 5 feet of the creature is the target of an attack, the creature can use it's reaction to impose disadvantage on the attack roll.", },
    ];
```
- Powers are formatted like so. Use tags to label the powers with a Role, Theme, Type or anything you want from the options. You can add any amount of tags, I recommend 1 - 3. 
```javascript
{ tags: ['Tag', 'Another tag'], name: 'Name.', description: "Description", },
```
- If you add a new power to the bottom it will look like this. Make sure the description stays on one line, if you copy paste from a pdf it often does not, just backspace to its on a single line.
```javascript
    /**
     * Monster Powers
     * 
     * name - Name of Power to display
     * description - Description of Power to display
     * tags - Type, Role, or Theme to tag the power with. 
     * You may add as many tags as you want from the lists above to any power,
     * Consider adding the additional powers listed in Forge of Foes
     */
    const powers = [
      // { tags: ['Tag', 'Another tag'], name: 'Name.', description: "Description", }, // I'm a power! You can copy paste me at the end to add your own just remove the '//' from the start to uncomment
      // Common powers that I have added tags to based on the role descriptions
      { tags: ['Common', "Artillery"], name: 'Damaging Blast.', description: 'This creature has one or more single-target ranged attacks using the attack bonus and damage calculated above, and which deal damage of an appropriate type.', },
      { tags: ['Common'], name: 'Damage Reflection.', description: "Whenever a creature within 5 feet of this creature hits them with a melee attack, the attacker takes damage in return of a type appropriate to the creature. The damage dealt is equal to half the damage of one of this creature's attacks. If you give a creature this feature, give them one less attack than normal.", },
      { tags: ['Common', "Skirmisher"], name: 'Misty Step.', description: "As a bonus action, this creature can teleport up to 30 feet to an unoccupied space they can see.", },
      { tags: ['Common'], name: 'Knockdown.', description: "When this creature hits a target with a melee attack, the target must succeed on a Strength saving throw or be knocked prone.", },
      { tags: ['Common', "Controller"], name: 'Restraining Grab.', description: "When this creature hits a target with a melee attack, the target is grappled (escape DC based on this creature's Strength or Dexterity modifier). While grappled, the target is restrained.", },
      { tags: ['Common'], name: 'Damaging Burst.', description: "As an action, this creature can create a burst of energy, magic, spines, or some other effect in a 10-foot-radius sphere, either around themself or at a point within 120 feet. Each creature in that area must make a Dexterity, Constitution, or Wisdom saving throw (your choice, based on the type of burst). On a failure, a target takes damage of an appropriate type equal to half this creature's total damage per round. On a success, a target takes half as much damage.", },
      { tags: ['Common', "Ambusher"], name: 'Cunning Action.', description: "On each of their turns, this creature can use a bonus action to take the Dash, Disengage, or Hide action.", },
      { tags: ['Common'], name: 'Damaging Aura.', description: "Each creature who starts their turn within 10 feet of this creature takes damage of a type appropriate to the creature. The damage dealt is equal to half the damage of one of this creature's attacks. If you give a creature this feature, give them one less attack than normal.", },
      { tags: ['Common', "Bruiser"], name: 'Energy Weapons', description: "The creature's weapon attacks deal extra damage of an appropriate type. You can add this damage on top of the creature's regular damage output to give them a combat boost, or you can replace some of the creature's normal weapon damage with this energy damage.", },
      { tags: ['Common'], name: 'Damage Transference.', description: "When this creature takes damage, they can transfer half or all of that damage (your choice) to a willing creature within 30 or 60 feet of them. This feature is particularly good for boss monsters.", },
      // Below are from the 5e SRD
      { tags: ['Common', "Leader"], name: 'Leadership.', description: "As a reaction the creature can utter a special command or warning whenever a nonhostile creature that it can see within 30 feet of it makes an attack roll or a saving throw. The creature can add a d4 to its roll.", },
      { tags: ['Common', "Defender"], name: 'Protection.', description: "When an ally within 5 feet of the creature is the target of an attack, the creature can use it's reaction to impose disadvantage on the attack roll.", },
      { tags: ['Tag', 'Another tag'], name: 'New Power.', description: "Replace me with a new Description", },
    ];
```
  
### Type Stats
If you own Forge of Foes there are recommended stats to add for each monster type. Here is how to edit those if you would like.

- Open the html file in a code editor
- Search the file for "Monster Type Stats"
- You will see a function like this:
```javascript
    /**
     * Monster Type Stats
     * (if you add a new role here make sure to add it to the monTypeList above)
     * Baseline stats and abilties for various monster types based on my own calculations from the 5e SRD
     * These OVERRIDE any stats in the baseline statBlock
     * If the stat doesnt exist it will ADD that stat
     * Consider adding the common resistances/immunities or senses listed in Forge of Foes for each monster type
     */
    function getmonTypeStats() {
      return {
        // 'Example': {
        //   stats: { str: 10, dex: 10, con: 12, int: 10, wis: 10, cha: 10 }, // these are the baseline things will get added/subtracted after
        //   skills: 'Athletics',
        //   speed: 40, // must stay a number if you want the Role modification to work
        //   languages: 'Common, Giant',
        //   resistances: 'fire',
        //   immunities: 'fire, Prone, Restrained',
        //   // etc. you can really add whatever you want recommended it be a number or string
        //   // randomizer works like this: getRandomDifferent(['Option 1', 'Option 2'])
        // },
        'Aberration': {
          stats: { str: 10, dex: 10, con: 12, int: 10, wis: 10, cha: 10 },
        },
        'Beast': {
          skills: 'Athletics',
          speed: 40,
          stats: { str: 10, dex: 12, con: 12, int: 7, wis: 10, cha: 8 },
        },
        'Celestial': {
          stats: { str: 10, dex: 10, con: 10, int: 10, wis: 12, cha: 12 },
        },
        'Construct': {
          stats: { str: 10, dex: 10, con: 15, int: 10, wis: 10, cha: 10 },
        },
        'Dragon': {
          speed: 40,
          stats: { str: 10, dex: 10, con: 10, int: 10, wis: 10, cha: 12 },
        },
        'Elemental': {
        },
        'Fey': {
          stats: { str: 10, dex: 10, con: 10, int: 10, wis: 10, cha: 14 },
        },
        'Fiend': {
          resistances: 'fire',
          languages: getRandomDifferent(['Abyssal', 'Infernal']),
          stats: { str: 10, dex: 10, con: 10, int: 10, wis: 10, cha: 12 },
        },
        'Giant': {
          languages: 'Common, Giant',
          stats: { str: 14, dex: 10, con: 12, int: 10, wis: 10, cha: 10 },
        },
        'Humanoid': {
          skills: getRandomDifferent(skillsList), // random skill
          stats: { str: 11, dex: 11, con: 11, int: 11, wis: 11, cha: 11 },
        },
        'Monstrosity': {
          skills: 'Perception, Stealth',
          stats: { str: 10, dex: 10, con: 12, int: 10, wis: 10, cha: 8 },
        },
        'Ooze': {
          senses: 'blindsight 60 ft. (blind beyond this radius)',
          speed: 20,
          stats: { str: 10, dex: 10, con: 10, int: 1, wis: 6, cha: 2 },
        },
        'Plant': {
          stats: { str: 10, dex: 10, con: 10, int: 1, wis: 7, cha: 1 },
        },
        'Undead': {
          stats: { str: 10, dex: 10, con: 12, int: 10, wis: 10, cha: 10 },
        }
      };
    }
```
- Here is an example with every option available, for each type you may copy paste a line from this and edit what is in the quotes
```javascript
 'Example': {
   stats: { str: 10, dex: 10, con: 12, int: 10, wis: 10, cha: 10 }, // these are the baseline stats will get added/subtracted after
   skills: 'Athletics, Stealth, etc.',
   speed: 40, // must stay a number if you want the Role modification to work do not surround with quotes like: '40',
   languages: 'Common, Giant',
   resistances: 'fire',
   immunities: 'fire, Prone, Restrained',
   vulnerability: 'radiant',
 },
```
Here you can see I added a vulnerability of fire and force to the Plant type
```javascript
 'Plant': {
    stats: { str: 10, dex: 10, con: 10, int: 1, wis: 7, cha: 1 },
    vulnerability: 'fire, force',
},
```
Anything you add will appear in the stat block so you can add a custom one if you want in this format- name: 'Whatever you want',
```javascript
 'Plant': {
    stats: { str: 10, dex: 10, con: 10, int: 1, wis: 7, cha: 1 },
    vulnerability: 'fire, force',
    other: "Disadvantage on Dexterity checks",
    noSpacesHere: "Anything can go here, but include a comma after the quotes",
},
```

### Roles
 I have added some calculations for monster roles listed in the Lazy GM's 5e Monster Builder Resource Document, but the calculations in Forge of Foes are much more detailed. For example the Artillery role says they "typically have a high attack bonus and deal good damage at range, but have lower hit points or AC than other foes", but in Forge of Foes actual numerical options are given. The calculations in this app are not the same and are my own based only on whats in the resource document. But you can change them to match.
- Search for "Role Modifications"
- You will see this object
 ```javascript
    /** 
     * Role Modifications (if you add a new role here make sure to add it to the monRoleList above)
     * https://slyflourish.com/lazy_5e_monster_building_resource_document.html#monsterroles
     * These are my own calculations based on the 5e_monster_building_resource_document, Consider using the more detailed guidance from Forge of Foes to update the calculations
     * Options:
     * main - Main stat for attack purposes: str, dex, con, int, wis, or cha 
     *        You can have multiple options here comma separated like this main: ['dex', 'cha'] it will choose randomly
     * HP - HP multiplier allows for reducing or increasing HP by a percent i.e .8 reduces by 20%, 1.2 will increase by 20%
     * Atk - Attack bonus, additive i.e -2 will reduce the attack bonus by 2, 2 will increase by 2
     * AC - AC bonus, additive i.e -2 will reduce the AC by 2, 2 will increase by 2
     * dmg - Damage bonus, additive i.e -2 will reduce the AC by 2, "CR" will add the CR to attack damage
     * speed - Speed bonus, additive i.e 20 will increase speed by 20
     * skills - Additional skill proficiencies
     */
    const monRoleMods = {
      // The example lowers HP by 10%, lowers AC by 2, increases attack bonus by 2, adds "+ Bonus" to damage string, adds stealth to skills, and adds 20 to the base speed
      // 'Example': { main: ['dex'], HP: .9, AC: -2, Atk: 2, dmg: 'Bonus', skills: 'Stealth', speed: 20 },
      'Ambusher': { main: ['dex'], HP: .9, skills: 'Stealth' }, // can hide, typically have lower health
      'Artillery': { main: ['dex'], AC: -1, Atk: 3 }, // lower AC, high attack bonus
      'Bruiser': { main: ['str'], AC: -1, dmg: 'Prof Bonus' }, // higher than average damage, lower AC
      'Controller': { main: ['str'] }, // some can grapple or swallow opponents
      'Defender': { main: ['str'], AC: 2, Atk: -1, save: 1 }, // less accurate with attacks, higher AC
      'Leader': { main: ['cha'], HP: .9 }, // lower than average HP
      'Skirmisher': { main: ['dex'], HP: .9, speed: 10 }, // high mobility, lower HP
    };
```

- Edit or add calculations for each role by adding a modifier separated with a comma
Modifier: , HP: .9,

Lets say I wanted to add the Athletics and Acrobatics skill to the Controller
```javascript
 'Controller': { main: ['str'], skills: 'Athletics, Acrobatics', }, // some can grapple or swallow opponents
```
Lets say I wanted to update the HP modifier for the Skirmisher to reduce the HP by 30% instead of the current 10%, I change that value to .7
```javascript
'Skirmisher': { main: ['dex'], HP: .7, speed: 10 }, // high mobility, lower HP
```

## Attribution
Adapted from original code from the [LGMRD repository](https://github.com/crit-tech/LGMRD/blob/main/5e_Monster_Builder.html)

This work includes material taken from the Lazy GM's 5e Monster Builder Resource Document written by Teos Abadía of Alphastream.org, Scott Fitzgerald Gray of Insaneangel.com, and Michael E. Shea of SlyFlourish.com, available under a Creative Commons Attribution 4.0 International License.

This work includes material taken from the A5E System Reference Document (A5ESRD) by EN Publishing and available at A5ESRD.com, based on Level Up: Advanced 5th Edition, available at www.levelup5e.com. The A5ESRD is licensed under the Creative Commons Attribution 4.0 International License available at https://creativecommons.org/licenses/by/4.0/legalcode.

This work includes material taken from the System Reference Document 5.1 ("SRD 5.1") by Wizards of the Coast LLC and available at https://dnd.wizards.com/resources/systems-reference-document. The SRD 5.1 is licensed under the Creative Commons Attribution 4.0 International License available at https://creativecommons.org/licenses/by/4.0/legalcode.