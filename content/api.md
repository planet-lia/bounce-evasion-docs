---
title: "API"
date: 2018-08-09T17:29:46+02:00
---

This is the collection of all the data that your bot has access to during the generation of a mach as well as all the methods that it can
use in order to control game entities.

On this page you can find references for:

* [InitialData](#initialdata) - Gives you match state and all the constants when the match starts
* [MatchState](#matchstate) - Gives you access to match state during the match generation
* [Response object](#response-object) - With it you can control your game units, make them move, spawn new ones, etc.

---

## InitialData

Bot receives InitialData object only once at the beginning of the match. It holds the following data:

- **`mapWidth`**`: int` - *In world units*
- **`mapHeight`**`: int` - *In world units*
- **`map`**`: boolean[][]` - *Two dimensional list of booleans. If at `map[y][x]` the value is `true` it means that at `(y,x)` there is a tile on which the unit can be placed. If the value is `false` it means that there is a hole in the map through which the unit can fall and die. `map[0][0]` represents the bottom left corner of the map.*
- **`sawSpawnDelay`**`: int` - *After how many match updates a new pair of saws spawn*
- **`yourUnit`**`: Unit` - *Data about your unit*
    - **`x`**`: int` - *x location of the unit*
    - **`y`**`: int` - *y location of the unit*
    - **`points`**`: int` - *Number of points the unit has gathered*
    - **`lives`**`: int` - *Number of lives the unit has left*
- **`opponentUnit`**`: Unit` - *Data about the opponent unit, the same type as `yourUnit`*
- **`coins`**`: list of Coin objects` - *List of all the coins on the map, each holding the data below:*
    - **`x`**`: int` - *x location of the coin*
    - **`y`**`: int` - *y location of the coin*
- **`saws`**`: list of Saw objects` - *List of all the saws on the map, each holding the data below:*
    - **`x`**`: int` - *x location of the saw*
    - **`y`**`: int` - *y location of the saw*
   - **`direction`**`: SawDirection` - *The direction towards which the saw is traveling, can be `UP_LEFT`, `UP_RIGHT`, `DOWN_LEFT` and `DOWN_RIGHT`.*
- **`__matchDetails`**`: MatchDetails` - *A few details about the match and participating bots*
    - **`yourBotIndex`**`: int` - *Index of the bot in botsDetails to which this instance of MatchDetails was sent to*
    - **`botsDetails`**`: list` - *List of all bots that participate in this match with their details*
        - **`botName`**`: string` 
        - **`teamIndex`**`: int`

---

## MatchState

Bot receives MatchState every update call which equals to every half a match second. 
It holds the data about what is going on with match entities at a current time during the match.

- **```time```**```: float``` - *Current match time in seconds*
- **`yourUnit`**`: Unit` - *Data about your unit*
    - **`x`**`: int` - *x location of the unit*
    - **`y`**`: int` - *y location of the unit*
    - **`points`**`: int` - *Number of points the unit has gathered*
    - **`lives`**`: int` - *Number of lives the unit has left*
- **`opponentUnit`**`: Unit` - *Data about the opponent unit, the same type as `yourUnit`*
- **`coins`**`: list of Coin objects` - *List of all the coins on the map, each holding the data below:*
    - **`x`**`: int` - *x location of the coin*
    - **`y`**`: int` - *y location of the coin*
- **`saws`**`: list of Saw objects` - *List of all the saws on the map, each holding the data below:*
    - **`x`**`: int` - *x location of the saw*
    - **`y`**`: int` - *y location of the saw*
   - **`direction`**`: SawDirection` - *The direction towards which the saw is traveling, can be `UP_LEFT`, `UP_RIGHT`, `DOWN_LEFT` and `DOWN_RIGHT`.*

---

## Response object

Using Response object you can communicate with the match generator and tell it what you want your unit to do. You can use the following method:

* **```moveUnit(Direction direction)```**
    * *Tells match generator to move the unit towards a certain direction. Possible directions are `LEFT`, `RIGHT`, `UP` and `DOWN`.*

---
---