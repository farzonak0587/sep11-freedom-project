# Entry 3
##### 2/8/26

## Content

### What I've learned Since Winter Break: 

#### **1. `on(event: string, tag: Tag, action: (obj: GameObj, args: ...) => void) => EventController`**
**What it does:**  
This function lets you listen for a specific event on certain objects that share a common tag. When that event happens (like an object touching the ground), the action you provide is triggered. It’s useful for triggering things like explosions, effects, or behaviors when certain conditions happen to specific objects.  

**Example:**  
```javascript
on("ground", "bomb", (bomb) => {
    destroy(bomb); // Blow up the bomb when it hits the ground
    addKaboom(bomb.pos); // Boom! Explosion at the bomb's spot
});
```
**Explanation:**
This code listens for the "ground" event, but only on objects that have the "bomb" tag. When a bomb hits the ground, the bomb is destroyed, and an explosion is created at that position. The addKaboom function adds a visual effect for the explosion at the bomb's position.

### 2. on(event: string, action: (message, posX, posY) => void) => EventController

**What it does:**
This function allows you to show a message on the screen at a specific position. You provide the message and the coordinates (X and Y), and it will display it there. This is really useful for showing dialogue, instructions, or notifications in your game.

**Example:**
``` js 
on("talk", (message, posX, posY) => {
    add([text(message), pos(posX, posY - 100)]); // Display the message above the NPC
});
```
**Explanation:**
When the "talk" event is triggered, it will show the message at the specified coordinates, which are posX and posY. The pos(posX, posY - 100) means the message will appear 100 pixels above the given position, typically above the NPC's head.

### 3. onUpdate(tag: Tag, action: (obj: GameObj) => void) => EventController

**What it does:**
This function runs every single frame (around 60 times per second) for all objects that have a specific tag. It's great for behaviors that need to be constantly updated, like movement or checking conditions (e.g., if something goes off-screen).

**Example:**
``` js 
onUpdate("tree", (tree) => {
    tree.move(-120, 0); // Move the tree left at 120 pixels per second
    if (tree.pos.x < 0) {
        destroy(tree); // If the tree moves off the screen (x < 0), destroy it
    }
});
```
**Explanation:**
This code moves all trees (objects with the "tree" tag) to the left at 120 pixels per second. If any tree goes off the left side of the screen (when tree.pos.x < 0), it gets destroyed. This is useful for things like moving platforms or objects that need to be cleaned up once they’re off screen.

### 4. onUpdate(action: () => void) => EventController

**What it does:**
This runs a function every frame, but it’s not tied to any specific game object. It’s useful for things like logging, managing global states, or updating UI elements that don’t belong to a single object.

**Example:**
``` js
onUpdate(() => {
    debug.log("Game is running!"); // Print this message every frame
});
```
**Explanation:**
This code logs the message "Game is running!" to the console every frame. It’s useful for debugging or tracking the game’s performance over time.

### 5. onDraw(tag: Tag, action: (obj: GameObj) => void) => EventController

**What it does:**
This runs a function that draws something to the screen after all the updates have been processed. This is the perfect place to add visual effects, render sprites, or show status bars.

**Example:**
``` js
onDraw("player", (player) => {
    drawRect(player.pos, player.width, player.height, rgb(0, 255, 0)); // Draw a green rectangle around the player
});
```
**Explanation:**
After the game updates the player's position and state, it draws a green rectangle around the player. This could be used for highlighting the player, drawing health bars, or adding special effects around certain objects.

### 6. onDraw(action: () => void) => EventController

**What it does:**
This runs a drawing function every frame, but it’s not tied to any specific object. This is useful for things like drawing background effects, HUD elements, or global visuals like particle effects.

**Example:**
``` js 
onDraw(() => {
    drawLine({
        p1: vec2(0, 0),
        p2: mousePos(), // Draw a line from the top-left corner to the mouse position
        color: rgb(0, 0, 255), // Line color is blue
    });
});
```
**Explanation:**
Every frame, this draws a blue line from the top-left corner (0, 0) to the current mouse position. This is useful for things like showing trails or adding interactive visuals.

### 7. onAdd(tag: Tag, action: (obj: GameObj) => void) => EventController

**What it does:**
This function triggers when a new object with a specific tag gets added to the scene. You can use it to initialize objects or set properties as soon as they appear in the game.

**Example:**
``` js 
onAdd("enemy", (enemy) => {
    enemy.health = 100; // Give every new enemy 100 health
});
```
**Explanation:**
Every time an enemy object is added to the scene, it automatically gets 100 health points. This is useful for setting default properties on newly spawned objects.

### 8. onAdd(action: (obj: GameObj) => void) => EventController

**What it does:**
This runs whenever any object is added to the scene, regardless of its tag. You can use it for things like logging, tracking, or performing global actions when new objects appear.

Example:
``` js
onAdd((obj) => {
    debug.log(`${obj} has been added to the scene!`); // Log every object added
});
```
**Explanation:**
This logs a message every time something new is added to the game. It’s useful for debugging or tracking how many objects are being added to the game.

### 9. onDestroy(tag: Tag, action: (obj: GameObj) => void) => EventController

**What it does:**
This triggers when an object with a specific tag is destroyed. You can use it to clean up, update scores, or play sound effects when objects are removed.

**Example:**
```js 
onDestroy("enemy", (enemy) => {
    score += 100; // Add 100 points to the score when an enemy is destroyed
});
```
**Explanation:**
Whenever an enemy is destroyed (e.g., when it’s killed by the player), the player's score is increased by 100.

### 10. onDestroy(action: (obj: GameObj) => void) => EventController

**What it does:**
This runs when any object in the scene is destroyed. It’s useful for handling global cleanup or actions that should occur whenever any object is removed.

**Example:**
``` js 
onDestroy((obj) => {
    debug.log(`${obj} has been destroyed!`); // Log when any object is destroyed
});
```

**Explanation:**
Every time any object is destroyed, this logs the object that was destroyed. This could be used for general cleanup or tracking what’s being removed from the game.

### 11. `onLoad(action: () => void)`

**What it does:**
This runs once after all game assets (like sprites, sounds, etc.) are loaded. It ensures that the game won’t try to use assets before they are ready, which prevents errors.

**Example:**
``` js 
onLoad(() => {
    const bean = add([sprite("bean")]); // Add a sprite after everything loads
    debug.log(bean.width); // Log the width of the sprite after it's loaded
});
```
**Explanation:**
After the game finishes loading all assets, it adds a "bean" sprite and logs its width to the console. This ensures that everything is fully loaded before the game starts using the assets.

### How I learned all this: 
I learned everything from the [Kaboom.js website](https://kaboomjs.com/), which is honestly packed with so many useful functions and tools for making games. The site has a ton of different tutorials, examples, and documentation, which made it easier for me to get the hang of it.I’ve been working through each part of the website, learning all the different functions, events, and techniques that Kaboom offers. There’s so much I can use in my projects, from simple things like movement and collisions, to more advanced stuff like events.

### Plans for learning my tool:
I know I can’t learn everything about Kaboom, but I want to learn as much as I can so I can use the cool features for my freedom project. At first, my goal before winter break was to make a mini game using everything I had learned, but I kept finding new stuff on the Kaboom website that I wanted to try out, so that didn't happen. There’s just so much to explore, and I kept getting distracted by all the new functions and tools!

Now, I realize I won’t have time to learn everything, so my main goal is to definitely make a mini game. I still want to make the same game I had in mind for winter break, which is an Avoidance Game. In this game, the player moves left and right to dodge falling enemies or obstacles. If the player hits an enemy, the game ends. It’s a simple concept, but it’s perfect because it’ll help me work on important stuff like player movement, making enemies fall, collision detection, and game-over logic. I think it’s a great starting point to put everything I’ve learned into practice.

## Engineering Design Process: 
Right now, we haven’t really started anything with the actual Freedom Project. We’re still in the early stages, mainly focusing on learning the tools we’re going to use for the project. We’re not jumping into building the project yet, we’re taking the time to get comfortable with everything like out tools first. For me, that means spending time learning Kaboom.js, which is what I plan to use for my game. To keep track of my progress, I’ve been logging everything in my [learning log](https://github.com/farzonak0587/sep11-freedom-project/blob/main/tool/learning-log.md). That way, I can see what I’ve already learned and what I might need to go back to if something’s not clicking.

## Skills

**Organization:**
- Keeping a learning log has really helped me stay organized. I’m able to track what I’ve learned, what I still need to figure out, and what I need to revisit. Organizing my learning this way has helped me stay focused and not get overwhelmed by the amount of stuff I need to learn.

**Patience and Persistence:**
- There have definitely been times when I wanted to rush through learning new concepts, or when I felt like I wasn’t getting something right. But I’ve realized that being patient and persistent is key. It takes time to fully understand each new idea and apply it correctly to my game. Rushing through things doesn’t help in the long run, and sometimes it takes several attempts to get something to work. I’ve learned to push through when I get stuck and take my time to absorb everything properly. Even when things get tough, I’ve learned that persistence is what helps me move forward and eventually succeed.
 

[Previous](entry02.md) | [Next](entry04.md)

[Home](../README.md)
