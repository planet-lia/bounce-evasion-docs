---
date: 2018-08-05T04:32:25+02:00
title: Game Rules
---

## Gameplay

Your goal is to write a bot that moves a single unit around the map in order to collect as many resources as possible.
If the unit falls of the map it dies. 
Each time it gets hit by a flying saw it looses one of its 3 lives. 
If 100 seconds elapses without the unit picking up a single coin, it automatically dies.
Once it looses all of its lives it also dies.
Every 11 seconds a new pair of saws spawn which levels up the difficulty.

See if you can collect more resources than your opponent before the saws overflow the field!

**Idea**: Consider solving the game by implementing a path finding algorithm that takes the movement of saws into a consideration.
Pretend that the saws are a part of the map.
This way you can try to adapt your path finding algorithm to be used on a map that dynamically changes through time.


<br/><div style="text-align:center"><img src="/static/docs/images/game-example.png" alt="Game example" width="80%"/></div>

## Map 
Map is always the same size with symmetrically generated gaps on it.

* Width: 20 map units
* Height: 11 map units
* Number of gaps: between 20 and 30

## Coins
There are two coins on the map at all times.
When the match is started, the coins are placed symmetrically.
After a coin is picked a new coin is randomly spawned somewhere else on the map.
If both units arrive at the same coin at the same time, they both collect a point. 

## Saws
Saws are the flying objects on the map that take a life of a unit if they both arrive on the same tile at the same time.
Saws spawn in pairs symmetrically.
The first saw starts at the map position `x = 5`, `y = 0` and has a direction set to `UP_RIGHT`. 
The second saw starts at the map position `x = 14`, `y = 10` and has a direction set to `DOWN_LEFT`. 
Each update they travel one tile over the diagonal, while the units travel one tile in horizontal or vertical direction.
Every `11 seconds` another pair of saws spawn at the same position as mentioned above.
When saws hit the wall they bounce in a predictable way.

## Winner 

The winner is the unit that has the most points at the end of the match. 
If one unit dies while both units have the same number of points, the unit that is still alive automatically wins.

## Bot restrictions

The following are the limitations on your bot while the match is generating. 
Note that when running your bot locally in debug mode with `-d` flag, no restrictions are set.
Head [here](/examples/debugging-your-code/) to see how to run your bot in debug mode.

* When the first update is called it has **2 seconds to respond**
* For all other updates it has **0.2 seconds to respond**
* If the bot **fails to respond in time for 8 or more times** in one match it is disqualified and the match continues without it
* If the bot does **not connect within 10 seconds** since the match-generator has started it is disqualified
* If the sum of the time that bot took to respond to all requests combined is **greater than 15 seconds** it is disqualified

### Related:

* [Getting started](/getting-started/) - Get started with the game
* [API reference](/api/) - Check out how bot can play the game