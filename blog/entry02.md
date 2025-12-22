
# Entry 2
##### 12/21/25

## Content

### How have I been leraning Kaboom.js

Right now, I’m focusing on learning from the [Kaboom.js website](https://kaboomjs.com/) because it’s got everything I need to understand the basics of game development with Kaboom. The site covers key concepts like setting up the game, handling input, creating sprites, and working with the game loop. It also provides code examples for each concept, so I can see exactly how the code works in action. My goal is to work through every section on the website, practice the examples, and then apply what I’ve learned to create a simple game. If I run into something I don’t get, I’ll search for more resources or examples online to make sure I fully understand the idea before moving on. 

## What Have I learned so far
#### 1. `make()`
- **What it does**: Prepares an object (like text or sprites) but doesn't show it immediately. This is useful when you want to create something ahead of time but only show it later.
- **Example**:
  ```js
  const label = make([text("Game Over", { size: 32 })]);  // Prepares the "Game Over" text 

#### 2. `readd()`
- What it does: Re-adds an object to the scene and changes its stacking order (z-order) without causing it to trigger any "add" or "destroy" actions. This is helpful when you need to change what appears on top of other objects.
- Example:
``` js 
readd(purpleBean);  // Moves purpleBean to the top of the stack
```

#### 3. `destroyAll(tag)`
- What it does: Removes all objects with a specific tag from the scene. Great for cleaning up a group of objects, like enemies or projectiles, at once.
- Example:
```js 
destroyAll("bomb");  // Removes all bombs from the scene
```

#### 4. Player & Enemy Setup
- What it does: Creates a player and sets up enemies that spawn at intervals. This is how you can make your game generate enemies or objects over time.
- Example:
```js 
loop(2, spawnEnemy);  // Spawns a new enemy every 2 seconds
```

 #### 5. `uvquad(w, h)`
- What it does: Adds a full-screen visual effect (like shaders) to your game. It’s used for things like background effects or transitions.
- Example:
``` js 
add([uvquad(width(), height()), shader("spiral")]);  // Applies a spiral effect to the whole screen
```

#### 6. `area()`
- What it does: Adds collision detection to an object. This is how you can check if two objects are touching or overlapping.
- Example:
``` js 
add([sprite("bean"), area()]);  // Adds collision detection to the bean sprite
```

#### 7. `anchor(o)`
- What it does: Sets the point where an object will rotate or scale from (its "anchor"). By default, objects rotate around their top-left corner, but you can change that.
- Example:
``` js 
add([rect(40, 10), rotate(45), anchor("center")]);  // Rotates the rectangle from its center
```

#### 8. `z(n)`
- What it does: Controls the layering of objects. Objects with a higher number are drawn on top of those with lower numbers. It’s like stacking cards, the higher the number, the closer to the top.
- Example:
```js 
add([sprite("cloud"), z(100)]);  // Makes the cloud appear above other objects
```

#### 9. `outline(width?, color?)`
- What it does: Adds a border around an object to make it stand out. You can change the width and color of the outline.
- Example:
```js 
add([text("hello"), outline(4, rgb(0, 0, 0))]);  // Adds a black outline around the "hello" text
```

#### 10. `body(options?)`
- What it does: Adds physics to an object, allowing it to be affected by gravity, jump, and collide with other objects.
- Example:
```js 
add([sprite("bean"), body()]);  // Adds gravity and physics to the bean object
```
#### 11. `doubleJump(numJumps?)`
- What it does: Lets an object (like the player) jump more than once in mid-air. You can specify how many jumps it can do before touching the ground.
- Example:

``` js 
add([sprite("bean"), doubleJump(2)]);  // Allows the bean to jump twice in the air
```

#### 12. `move(direction, speed)`
- What it does: Makes an object move in a given direction at a set speed. This is useful for making objects like bullets or enemies move automatically.
- Example:
``` js 
add([sprite("bullet"), move(player.pos.angle(enemy.pos), 1200)]);  // Moves the bullet toward the enemy
```

#### 13. `offscreen(options?)`
- What it does: Defines what happens when an object goes off the screen. You can automatically destroy it, reset it, or keep it in the background.
- Example:
```js 
add([sprite("bullet"), offscreen({ destroy: true })]);  // Destroys the bullet when it leaves the screen
```

#### 14. `follow(obj, offset?)`
- What it does: Makes one object (like a camera) follow another object (like the player). You can also set an offset to make the follower stay at a fixed distance.
- Example:
``` js 
camera.follow(player, { x: 0, y: -50 });  // Makes the camera follow the player, 50 units above
```

#### 15. `timer()`
- What it does: Allows you to perform actions after a certain amount of time (delays) or repeatedly at set intervals (like repeating actions every few seconds).
- Example:
``` js 
obj.wait(2, () => console.log("2 seconds passed!"));  // Waits 2 seconds before printing
```

#### 16. `stay(scenesToStay?)`
- What it does: Keeps an object in the game even when changing scenes. Useful for keeping things like background effects or UI elements.
- Example:
``` js 
add([sprite("explosion"), stay()]);  // Explosion stays in the scene even when switching scenes
```

#### 17. `health(hp, maxHP?)`
-  What it does: Adds health to an object, like the player, and lets you decrease or increase it. When health reaches 0, the object can "die" or trigger an event.
- Example:
``` js 
const player = add([health(3)]);  // Player starts with 3 health points
```

#### 18. `lifespan(time, options?)`
- What it does: Makes an object disappear after a certain amount of time. You can also apply effects like fading out before it disappears.
- Example:
```js 
add([sprite("explosion"), lifespan(1, { fade: 0.5 })]);  // Explosion fades out in 0.5 seconds
```

#### 19. `state()`
- What it does: Lets you define different behaviors (states) for an object, such as "idle", "attack", or "move". It helps objects change between these behaviors.
- Example:
``` js 
state("idle", ["idle", "attack", "move"], { "idle": "attack", "attack": "move", "move": "idle" });  // Cycles between states
```

#### 20. `fadeIn(time)`
- What it does: Makes an object slowly appear on the screen over a set amount of time, like fading in from invisible.
- Example:
``` js 
add([sprite("object"), fadeIn(2)]);  // Object fades in over 2 seconds
```
#### 21. `mask(maskType?)`
- What it does: Applies a mask to an object, making it visible only inside a specific shape (like a circle or rectangle).
- Example:
``` js 
add([sprite("object"), mask()]);  // Applies a rectangular mask
```

#### 22. `tile(opt)`
- What it does: Adds a tile (like a piece of grass or a rock) to a grid-based game map. Great for creating levels.
- Example:
```js 
tile({ sprite: "grass", pos: vec2(0, 0), width: 32, height: 32 });  // Adds a grass tile at (0, 0)
```

#### 23. `agent(opt?)`
- What it does: Creates an AI character that can move around and avoid obstacles. It’s useful for enemies or NPCs.
-  Example:
``` js 
add([agent({ speed: 100, pathfinding: true })]);  // Adds an agent that moves and avoids obstacles
```

## Goal for Winter Break

My goal for my Freedom Project over the break is to create a simple game using everything I've learned so far. I’m still figuring out which game to make, but I have two ideas. 

The first is an Avoidance Game where the player moves left and right to dodge falling enemies or obstacles. If the player hits an enemy, the game ends. It’s a pretty straightforward concept and would give me a chance to work on player movement, falling enemies, collision detection, and game over logic. 

The second idea is a Platformer, where the player jumps between platforms, avoids spikes, and collects coins. The challenge here would be adding player movement, jumping, platform collisions, enemies, and collectibles, all while making sure the game over screen triggers if the player falls into a pit.

### Engineering Design Process: 
Right now, I feel like we’re still in the early phase of the Engineering Design Process for our Freedom Project. We haven’t actually started building the game yet. Instead, we’re focusing on getting a good understanding of the tools we’ll be using, so we’re ready when we start the actual project later in the year. Personally, I’ve been learning everything I can from the Kaboom.js website, like how to set up the game, work with sprites, handle player input, and manage the game loop. I’m tracking all of this in my [learning log](https://github.com/farzonak0587/sep11-freedom-project/blob/main/tool/learning-log.md)
, so I can see my progress and any things I might need to revisit.

On top of that, I’ve been brainstorming ideas for what the game will actually look like and how it will work. I think this is important because once I start coding, I want to have a clear idea of what I’m building so I can avoid getting stuck later.

### Skills

 **Time Management**
-  Time management has been super important throughout this project. Since we had weekly learning logs due, I had to be really careful about how I spent my time. It wasn’t just about learning new stuff each week—it was about making sure I kept up with the logs, too. I realized that if I didn’t plan ahead, I’d be scrambling to get everything done last minute.

- Example: Every week, I’d learn new things about Kaboom.js, but I also had to make sure I had time to write down what I learned for the log. I started setting aside specific time to do the logs. That way, I didn’t feel rushed at the end of the week. I learned to pace myself and keep track of my progress, which made it way less stressful.

**Problem-Solving**

- Throughout this project, I definitely worked on my problem-solving skills. Whether it was debugging an issue with my code or figuring out how to make something work in the game, I had to think critically and come up with solutions. A lot of times, I didn’t know exactly how to fix something, so I had to break down the problem step by step and try different approaches until I found a solution.

- Example: There was a time when I couldn’t get my game’s collision detection to work right. I was stuck for a while, but I kept testing different things and looking up resources. Eventually, I figured out that I needed to add a specific function to handle the object interactions.

-
[Next](entry02.md)

[Home](../README.md)
