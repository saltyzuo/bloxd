# api Instruction 
The API command is one of Bloxd's proprietary commands, enabling greater creativity in game world rules.  
Here's an example:
``` javascript

// myId  is like  playerId ,is store the player ID of who is running the code.
api.setPosition(myId,[2.45,12.00,-472.86]);   // this functon can set player position
// [2.45,12.00,-472.86]  is x,y,z coordinates  

```   
like this,very easy,so let's get started!  
bloxd official explanation website: [bloxd api](https://github.com/Bloxdy/code-api)  

## Code Blocks  

- World owners can find these by searching in the creative menu
- and you can use code get code blocks  
- No need to add `press to code`, this text is only needed for code boards, and will automatically be removed  
- If you want to run code without opening the code editor, you can trigger the code block by right clicking an adjacent `press to code` board instead
- If u use comments,write  // message    or    /* message */

## Boards  

- You can begin a board with `press to code` to run javascript when you right click it.  
- Normally you can't edit a code board after placing it, but you can currently work around this by putting a space before `press to code`.  
- Boards only allow for a small amount of text, we recommend you use Code Blocks instead, or you can work around this by using multiple boards

## player's status codes  

### 1.getPosition()  
``` javascript  

api.getPosition(entityId)  

// One of the usages:
let playerPos = api.getPosition(myId);
api.log(playerPos);    // api.log()   another function,can print mesage to you,if playerPos = 1,1,1 ,there will print:  log:[1,1,1]

```
This is a commonly used function that can obtain the **coordinates of a player**.  
The first parameter is the player's ID **(to be precise, it doesn't necessarily have to be a player, as long as it is an entity)**. The return value(player can't see) is a list that should be filled with the player's x, y, and z coordinates.  
Simply executing the code will obtain the player's coordinates Edit translation paragraph comparison.  

### 2.setPosition()  
``` javascript

api.setPosition(entityId, x, y, z);
// the usage:
api.setPosition(myId, 100, 100, 100);  //set player x,y,z to 100,100,100

```
This is also a commonly used function that can obtain the player's coordinates.   
The first parameter is the player's ID **(to be precise, it doesn't necessarily have to be a player; it can be any entity)**. The second, third, and fourth parameters are the set **x, y, z** coordinates.
After executing the command, the player will be **teleported** to the designated location.  

### 3.getPlayerIds()
``` javascript

api.getPlayerIds()    // some strange


```
This function can obtain the names of all players in the room where the instruction is located.   
This function is quite special. It doesn't take any parameters, and after executing the instruction, it returns a list containing the names of all the players in this room.  

### 4.playerIsInGame()  
```

api.playerIsInGame(playerId)
// usage:
api.playerIsInGame("Hansen325");    //u can write everyones id test he/she is in game.

```
This commonly used function can detect whether a player is online.
The first parameter is the **player's ID**(if you fill in your own ID, you will definitely be online). After executing the command, a boolean value (true or false) will be returned.

### 5.getBlockCoordinatesPlayerStandingOn()  
``` javascript

api.getBlockCoordinatesPlayerStandingOn(playerId)
// usage:
api.getBlockCoordinatesPlayerStandingOn(myId)

```
This function can get the co-ordinates of the blocks the player is standing on as a list.
For example, if the center of the player is at 0,0,0
this function will return [[0, -1, 0], [-1, -1, 0], [0, -1, -1], [-1, -1, -1]]
If the player is just standing on one block, the function would return e.g. [[0, 0, 0]]  
If the player is middair then returns an empty list [].  

### 6.getBlockTypesPlayerStandingOn()
``` javascript

api.getBlockTypesPlayerStandingOn(playerId)
// example:
api.getBlockTypesPlayerStandingOn(myId)

```
this function is like last function,but changed!it can get the types of block the player is standing on.  
for example, if a player is standing on 4 dirt blocks, this will return  ["Dirt", "Dirt", "Dirt", "Dirt"]  

### 7.getHealth()  
```javascript

api.getHealth(entityId);
// example:
api.getHealth(myId)

```
This function also common,it can get the current health of an entity.
for example,If you want to know how much health a player has, use this function.  
Simply fill in his or her id as the first parameter, and you will be able to obtain the information.  

### 8.setHealth()  
```javascript

api.setHealth(entityId, newHealth, whoDidDamage, increaseMaxHealthIfNeeded)
// example:
api.setHealth(myId,100, null, false)  // set player health to 100

```
This function can be used in PvP.  
The first parameter is the ID of the player (or living creature) as usual.  
The second parameter is the modified health (100 represents the maximum health of the player in normal state).   
The third parameter is special, which can be filled with either the ID of the player or creature, or written as follows: {lifeformId: LifeformId; withItem: string} (withItem is the tool used, null represents none).  
The last parameter indicates whether to modify the maximum health as needed (for demonstration purposes, if true is filled and the command adjusts the health above 100, the maximum health will be modified as needed).  

### 9.attemptApplyDamage()  
```javascript

api.attemptApplyDamage({
    eId,
    hitEId,
    attemptedDmgAmt,
    withItem,
    bodyPartHit = undefined,
    attackDir = undefined,
    showCritParticles = false,
    reduceVerticalKbVelocity = true,
    horizontalKbMultiplier = 1,
    verticalKbMultiplier = 1,
    broadcastEntityHurt = true,
    attackCooldownSettings = null,
    hittingSoundOverride = null,
    ignoreOtherEntitySettingCanAttack = false,
    isTrueDamage = false,
    damagerDbId = null,
    })

example:

api.attemptApplyDamage({
    entityId,
    hitEntityId,
    60,  // the damage
    "Diamond Sword", // use this hit another entity
    bodyPartHit = undefined, // that maybe not me to explain
    attackDir = undefined,
    showCritParticles = false,  // commonly ,hit entity have a particle , but there write false
    reduceVerticalKbVelocity = true,
    horizontalKbMultiplier = 1,
    verticalKbMultiplier = 1,
    broadcastEntityHurt = true, // if there's true,it will be have a hurt sound
    attackCooldownSettings = null, // can setting this attack cooldown 
    hittingSoundOverride = null, // attack sound whether will appear in other computer
    ignoreOtherEntitySettingCanAttack = false, // if there's true,will ignore other attack damage
    isTrueDamage = true, // I don't need to explain this
    damagerDbId = null, 
    })

```

this function have a lot of peramers(actually,There are many things that don't need to be write out,Including those without annotations),it can make a damage to player(entity).  

### 10.forceRespawn()
```javascript

api.forceRespawn(playerId, respawnPos) // respawn pos is a list:[x,y,z]

```
this code is commonly....can Force respawn a player to a position.  

### 11.isAlive()  
```javascript

api.isAlive(entityId);

```
Whether a lifeform is alive or dead (or on the respawn screen, in a player's case).  

## particle effect : api.playParticleEffect()
These are the strings you can give to functions that take a particle effect `texture` as input:

`bubble`
`critical_hit`
`drift`
`effect_5`
`generic_2`
`glint`
`heart`
`scary_face`
`soul_0`
`square_particle`
`z-particle`  
here is a example:  
```ts

let [x, y, z] = thisPos  // thisPos u know ? there.
y += 1
api.playParticleEffect({
    dir1: [-1, -1, -1],
    dir2: [1, 1, 1],
    pos1: [x, y, z],
    pos2: [x + 1, y + 1, z + 1],
    texture: "bubble",
    minLifeTime: 0.2,
    maxLifeTime: 0.6,
    minEmitPower: 2,
    maxEmitPower: 2,
    minSize: 0.25,
    maxSize: 0.35,
    manualEmitCount: 20,
    gravity: [0, -10, 0],
    colorGradients: [
        {
            timeFraction: 0,
            minColor: [60, 60, 150, 1],
            maxColor: [200, 200, 255, 1],
        },
    ],
    velocityGradients: [
        {
            timeFraction: 0,
            factor: 1,
            factor2: 1,
        },
    ],
    blendMode: 1,
})

```
You can also use a `presetId` instead to use a pre-defined particle effect, to replicate effects we use in-engine.
Here is the code for an example of using a presetId:

```ts
let [x, y, z] = thisPos
y += 1
api.playParticleEffect({
    presetId: "aura",
    pos1: [x, y, z],
    pos2: [x + 1, y + 1, z + 1],
})
```

Here is a list of the presetIds you can use:

`brainRot`
`stomp`
`fertiliser`
`bonemeal`
`mobTameSuccess`
`mobTameFailure`
`mobCatch`
`spawnCaughtMob`
`mobFeedDefault`
`mobFeedSuperliked`
`mobFeedLike`
`mobFeedNeutral`
`mobFeedDisliked`
`mobDeath`
`mobDeathSoul`
`boardShopSuccess`
`mobSpawnerBlockFail`
`mobSpawnerBlockPassive`
`mobSpawnerBlockNeutral`
`mobSpawnerBlockHostile`
`mobSpawnOrb`
`aura`
`yellowFirecrackerSmall`
`yellowFirecrackerLarge`
`whiteFirecrackerSmall`
`whiteFirecrackerLarge`
`redFirecrackerSmall`
`redFirecrackerLarge`
`purpleFirecrackerSmall`
`purpleFirecrackerLarge`
`pinkFirecrackerSmall`
`pinkFirecrackerLarge`
`orangeFirecrackerSmall`
`orangeFirecrackerLarge`
`magentaFirecrackerSmall`
`magentaFirecrackerLarge`
`limeFirecrackerSmall`
`limeFirecrackerLarge`
`lightGrayFirecrackerSmall`
`lightGrayFirecrackerLarge`
`lightBlueFirecrackerSmall`
`lightBlueFirecrackerLarge`
`greenFirecrackerSmall`
`greenFirecrackerLarge`
`grayFirecrackerSmall`
`grayFirecrackerLarge`
`cyanFirecrackerSmall`
`cyanFirecrackerLarge`
`brownFirecrackerSmall`
`brownFirecrackerLarge`
`blueFirecrackerSmall`
`blueFirecrackerLarge`
`blackFirecrackerSmall`
`blackFirecrackerLarge`
`defaultFirecrackerSmall`
`defaultFirecrackerLarge`
`mango`
`speedInner`
`speedOuter`
`damageReductionInner`
`damageReductionOuter`
`damageInner`
`damageOuter`
`invisibleInner`
`invisibleOuter`
`jumpBoostInner`
`jumpBoostOuter`
`knockbackInner`
`knockbackOuter`
`poisonedInner`
`poisonedOuter`
`slownessInner`
`slownessOuter`
`weaknessInner`
`weaknessOuter`
`cleansedInner`
`cleansedOuter`
`instantDamageInner`
`instantDamageOuter`
`healthRegenInner`
`healthRegenOuter`
`instantHealthInner`
`instantHealthOuter`
`hasteInner`
`hasteOuter`
`shieldInner`
`shieldOuter`
`doubleJumpInner`
`doubleJumpOuter`
`heatResistanceInner`
`heatResistanceOuter`
`thiefInner`
`thiefOuter`
`xRayVisionInner`
`xRayVisionOuter`
`miningYieldInner`
`miningYieldOuter`
`brainRotInner`
`brainRotOuter`
`auraInner`
`auraOuter`
`wallClimbingInner`
`wallClimbingOuter`
`airWalkInner`
`airWalkOuter`
`pickpocketerInner`
`pickpocketerOuter`
`lifestealInner`
`lifestealOuter`
`bouncinessInner`
`bouncinessOuter`
`blindnessInner`
`blindnessOuter`
`poopyInner`
`poopyOuter`



