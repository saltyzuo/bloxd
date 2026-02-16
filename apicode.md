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
- // message     or     /* message */

## Boards  

- You can begin a board with `press to code` to run javascript when you right click it.  
- Normally you can't edit a code board after placing it, but you can currently work around this by putting a space before `press to code`.  
- Boards only allow for a small amount of text, we recommend you use Code Blocks instead, or you can work around this by using multiple boards

## player's status  

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
```

api.getHealth(entityId);
// example:
api.getHealth(myId)

```
This function also common,it can get the current health of an entity.
for example,If you want to know how much health a player has, use this function.  
Simply fill in his or her id as the first parameter, and you will be able to obtain the information.  




