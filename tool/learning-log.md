# Tool Learning Log

## Tool: **Kaboom.js**

## Project: **Reaction Focus Game**

---

### 09/29/25:
**What I learned**

Today I learned that Kaboom.js is a JavaScript library that helps you make simple 2D games in the browser. You don’t need to install anything big or confusing. You just add one script link and call the function `kaboom()`, which sets up your game space. It basically gives you a blank area where your game will happen.

**What I tried**

I wrote my very first line of Kaboom code:
``` js 
kaboom();
```

When I opened the file in my browser, a blank checkerboard screen appeared. That’s the Kaboom canvas, which means everything is running correctly.

Challenges I had and how I solved them
At first, nothing showed up when I ran the file. I realized I forgot to include the Kaboom library in my HTML. I fixed it by adding this line:

```js
<script src="https://unpkg.com/kaboom/dist/kaboom.js"></script>
```

After saving and refreshing, the Kaboom canvas appeared. I also learned that the `kaboom()` function has to go at the very top of the JavaScript code or nothing will work.

What I learned from solving it
I understood how Kaboom initializes and that it needs to be loaded before any other game functions. Once it’s set up, the rest of the code builds on top of it.
  
### 09/30/25:

What I learned:
Today I learned how to add stuff to the screen using add().
Kaboom uses these things called components, which are like pieces of info you attach to an object — for example:

`rect(#(width),#(height)` gives it a shape.

`pos(#(left/right),#(up/down)` sets where it goes.

`color(0, 0, 255)` changes the color to blue.

Each thing you see in the game is built out of these small “lego” components.

What I tried:
I made my first blue square:
```js 
kaboom();

add([
  rect(50, 50),
  pos(100, 100),
  color(0, 0, 255),
]);
```
When I opened it a blue square appeared.


* Then I tried changing numbers:

* Made it bigger with `rect(100, 100)`.

* Moved it to the top left with `pos(0, 0)`.

* Changed color to red with `color(255, 0, 0)`.

It’s fun to mess with the numbers and instantly see what happens.

**What I learned from solving it:**

Playing around with the numbers was the best way to learn. Every change helped me see what the code does.

**What I can do with it:**

Now I know how to put stuff on screen and give it color. Tomorrow, I want to learn how to make it move, because right now everything just sits there.

 ### 10/1/25:
**What I learned**

Today I learned about movement in Kaboom. There’s a function called `onUpdate()` that runs all the time, kind of like a heartbeat that keeps checking stuff every frame. You can make objects move using `.move(x, y),` which moves them a certain number of pixels per second.

**What I tried**

I made my blue square move to the right:
``` js  
kaboom();

const box = add([
  rect(50, 50),
  pos(100, 100),
  color(0, 0, 255),
]);

onUpdate(() => {
  box.move(50, 0); // move right
});
````

It started sliding across the screen slowly! Then I tried different directions and speeds:
`box.move(0, 100)` — it moved down instead.
`box.move(200, 0)` — it went faster.
`box.move(-50, 0)` — it moved left.

**Challenges and How I Solved Them**
At first, my square shot across the screen super fast. I checked the Kaboom docs and found out the number means pixels per second, not per frame. I lowered it from 500 to 50, and it started moving smoothly.

**What I learned from solving it**

The movement speed in Kaboom depends on time, not frames, which makes everything look smoother no matter how fast your computer runs.
  
### 10/2/25:

**What I learned**

Today I learned how to make things move when I press keys on the keyboard. Kaboom has functions like `onKeyDown()` and `onKeyPress()` that can detect when you press or hold down a key. This is how games let you control your character.

**What I tried**

I used `onKeyDown()` to move my square in different directions with the arrow keys.

```js
kaboom();

const box = add([
  rect(50, 50),
  pos(100, 100),
  color(0, 255, 0),
]);

onKeyDown("right", () => box.move(120, 0));
onKeyDown("left", () => box.move(-120, 0));
onKeyDown("up", () => box.move(0, -120));
onKeyDown("down", () => box.move(0, 120));
```

When I ran the game, I could finally move the square around using my keyboard. It felt like the first “real” game.

What other code mean: 
* `() => {}` = a small, quick function.

* The parentheses `()` mean “no inputs.”

* The arrow `=>` means “do this next.”

* The braces `{}` hold the code you want to run.


  
### 10/3/25:

**What I learned**

Today I learned how to change the shape or color of an object when I press a certain key. I already knew how to move my square with the arrow keys, but now I wanted to make it react in other ways too. 

**What I tried**

I made a square that changes color and shape depending on what key I press.

``` js
onKeyPress("space", () => {
  box.color = rgb(255, 0, 0);
});
```
This changed the blue color box to become red once the spacebar is pressed. 


`add()` creates a new game object and puts it on the screen.


``` js
onKeyPress("s", () => {
  destroy(box);
  box = add([
    rect(80, 20),
    pos(100, 100),
    color(0, 255, 0),
  ]);
});
```
When I press “S”, the old square gets removed and a new green rectangle appears.


### 10/27/25:
**What I learned**
Today I learned how to scale and rotate objects in Kaboom using the `scale()` and `rotate()` functions. These let you change the size and orientation of an object.

`scale(factor)` changes the size of the object. For example, scale(2) makes the object twice as big.

`rotate(angle)` rotates the object by a specified number of degrees. For instance, `rotate(45)` turns the object 45 degrees.

Both of these functions let you modify the appearance of your game objects without changing their basic structure.

First, I made a simple square again, but this time I added scale() and rotate():

``` js 
kaboom();

add([
  rect(50, 50),
  pos(100, 100),
  color(255, 0, 0),
  scale(2),
  rotate(45),
]);

```
I created a red square with these components:

`scale(2)` makes it twice as big.

`rotate(45)` rotates it 45 degrees.

When I ran the code, I saw a red square that was bigger and tilted at an angle.

**What I tried next:**

I experimented with different numbers to see how they affected the object:

Changed the scale to `scale(0.5)` to make the square smaller.

Used `rotate(90)` to rotate it by 90 degrees.

Played with `scale(3)` to make it three times as big.

What I learned from solving it:

Scaling: If you increase the scale value, the object gets larger; if you decrease it, the object shrinks.

Rotating: You can make the object face different directions by changing the rotate angle. Positive numbers rotate clockwise, and negative numbers rotate counterclockwise.

### 10/28/25:
🧠 What is `area()`?

The `area()` function defines the collision area of an object. It makes the object interact with other objects in the game world by detecting collisions and overlaps. Without `area()`, the object won't react to anything, even if it touches another object.

**Key Uses:**

- Collision detection: To check if the object touches another.

- Click detection: You can detect mouse clicks on the object.

- Overlap detection: Detects if two objects are overlapping.

Example:

``` js
let box = add([
  rect(40, 40),      // Creates a 40x40px rectangle
  pos(100, 100),     // Position: (100, 100)
  color(0, 0, 255),  // Color: Blue
  area(),            // Adds collision detection (hitbox)
]);
```

Now, this box will respond to things like mouse clicks or collisions with other objects that also have `area()`.

**What is `body()`?**

The `body()` function gives the object physics properties. It applies gravity to the object and allows it to react to forces (like jumping or falling). You need `body()` for the object to behave like a physical entity in the game world.

**Key Uses:**
- Gravity: Makes the object fall naturally.

- Movement: You can apply velocity and forces to the object.

- Collision with the ground: Stops the object from passing through the floor.

Example:

``` js 
let player = add([
  rect(40, 40),      // Creates a 40x40px rectangle
  pos(100, 100),     // Position: (100, 100)
  color(0, 255, 0),  // Color: Green
  area(),            // Collision detection enabled
  body(),            // Enables gravity (the object will fall)
]);
```

With `body()`, the object will now fall due to gravity. If you want to make it jump, you can use methods like `jump()` and isGrounded().

### 10/29/25:

**What is anchor in Kaboom.js?**

The anchor property in Kaboom.js defines how an object is positioned relative to its own size. By default, objects are anchored at the top-left corner, but you can change the anchor to place the object in a different part of its bounding box.

Think of the anchor as a pivot point. The anchor tells Kaboom where to "start" from when positioning an object.

Key Uses:

- Control where an object’s position is calculated from.

- Change how objects rotate or scale in relation to their position.

- Make objects align with each other in a specific way (e.g., centering them on a point).

📏 Anchor Points Explained

The anchor can be set to any of the following values:

`anchor("left")`: Anchor the object to its left edge.

`anchor("center")`: Anchor the object to its center.

`anchor("right")`: Anchor the object to its right edge.

`anchor("top")`: Anchor the object to its top edge.

`anchor("bottom")`: Anchor the object to its bottom edge.

`anchor("topleft")` (default): Anchor the object to its top-left corner.

`anchor("topright")`: Anchor the object to its top-right corner.

`anchor("bottomleft")`: Anchor the object to its bottom-left corner.

`anchor("bottomright")`: Anchor the object to its bottom-right corner.

Example:

Let’s take a simple example to show how the anchor works:
``` js 
let box1 = add([
  rect(40, 40),    // A 40x40px rectangle
  pos(100, 100),   // Starting position at (100, 100)
  color(0, 0, 255),// Blue color
  anchor("center") // Anchoring the box to its center
]);

let box2 = add([
  rect(40, 40),    // A 40x40px rectangle
  pos(200, 100),   // Starting position at (200, 100)
  color(255, 0, 0),// Red color
  anchor("topright") // Anchoring the box to its top-right corner
]);
```

What Happens:

- box1 is anchored at its center, meaning the position (100, 100) is at the center of the box.

- box2 is anchored at its top-right corner, so its position (200, 100) is the top-right corner of the box.

If you move the object around, the position (100, 100) for box1 means its center will be at that point, while for box2, the top-right corner will be at (200, 100).

### 10/30/25:
What is `onCollide()`?

`onCollide()` is an event listener that runs a callback function when an object of a certain tag collides with another object of a different tag. The function is triggered when two objects come into contact, and you can specify what should happen when the collision occurs.


``` js 
onCollide(tag1, tag2, callback)
```

- tag1: The first tag (or group) of the object that will trigger the collision detection. You can use a string to identify the object or group (e.g., "player", "enemy").

- tag2: The second tag (or group) of the object you want to check collisions with.

- callback: A function that runs when the two objects collide.

Example: 
``` js 
// Create the player object
let player = add([
  rect(40, 40),       // 40x40px rectangle
  pos(100, 100),      // Position (100, 100)
  color(0, 255, 0),   // Green color
  area(),             // Enable collision detection
  "player",           // Tag the object as "player"
]);

// Create the enemy object
let enemy = add([
  rect(40, 40),       // 40x40px rectangle
  pos(200, 100),      // Position (200, 100)
  color(255, 0, 0),   // Red color
  area(),             // Enable collision detection
  "enemy",            // Tag the object as "enemy"
]);

// Detect collision between player and enemy
onCollide("player", "enemy", () => {
  // Actions that happen when the player collides with the enemy
  player.color = rgb(255, 255, 0); // Change player color to yellow
  destroy(enemy);                   // Destroy the enemy on collision
});
```

**What Happens:** 

- Both the player and enemy objects have `area()` for collision detection.

- The player is tagged as "player", and the enemy is tagged as "enemy".

- When the player collides with the enemy, the `onCollide()` function is triggered.

- Inside the callback:  The player's color changes to yellow and the enemy is destroyed.
  
### 10/31/25:

**What I created:**

``` js
    kaboom();

    // Create a blue box (player)
    const box1 = add([
      rect(50, 50),
      pos(100, 100),
      color(0, 0, 255),
      area(),  // Enable collision detection
      "box1"   // Tag it for identification
    ]);

    // Create a red box (enemy)
    const box2 = add([
      rect(50, 50),
      pos(300, 100),
      color(255, 0, 0),
      area(),  // Enable collision detection
      "box2"   // Tag it for identification
    ]);

    // Player movement: Arrow keys
    onKeyDown("right", () => box1.move(120, 0));   // Move right
    onKeyDown("left", () => box1.move(-120, 0));   // Move left
    onKeyDown("up", () => box1.move(0, -120));     // Move up
    onKeyDown("down", () => box1.move(0, 120));    // Move down

    // Detect collision between the blue box (box1) and the red box (box2)
    onCollide("box1", "box2", () => {
      destroy(box2); // Destroy the red box (box2) when the blue box (box1) touches it
    });
```

**Summary of the Code:**

- Blue Box (box1): I can move it around the screen using the arrow keys.

- Red Box (box2): This box sits at a fixed position, and when the blue box touches it, the red box disappears.

- Collision Detection: The red box gets destroyed as soon as the blue box collides with it.

- This creates a simple game mechanic where the player (blue box) moves around and destroys the enemy (red box) by touching it.


### 11/10/25:
1. `make()`
- Why it's needed: To create an object but not add it to the scene immediately. This is useful when you want to prepare something, like a UI element or an enemy, before it appears in the game.

``` js
// Prepare a label object but don't add it yet
const label = make([
  text("Game Over", { size: 32 }),  // Create a text component for the label
]);

// Later, add it to the scene when the game is over
add([
  rect(200, 50),  // Create a rectangle for background
  pos(100, 100),  // Position of the label
  color(255, 0, 0), // Red color
  children(label),  // Add the label as a child of this rectangle
]);
```
**Why use `make()`?:**

You might want to build this label only when the game is over, but not before. make() lets you create the label and wait until the right moment to add it to the scene.

### 11/11/25:
2. `readd(obj)`

Why it's needed: You need to reorder objects, making one appear on top of the other without triggering any add or destroy events. This is useful for stacking objects (like sprites) or controlling their z-order.

Example:

``` js
// Create two beans that overlap
const greenBean = add([
  sprite("bean"),
  pos(200, 140),
  color(0, 255, 0),  // Green color
  area(),
]);

const purpleBean = add([
  sprite("bean"),
  pos(230, 140),
  color(255, 0, 255),  // Purple color
  area(),
]);

// Switch stacking order when clicked
greenBean.onClick(() => {
  readd(purpleBean);  // Bring purpleBean to the top
});

purpleBean.onClick(() => {
  readd(greenBean);  // Bring greenBean to the top
});

```

**Why use `readd()`?**

Without readd(), if you removed and re-added the beans, you would trigger "add" or "destroy" events, which might interfere with game logic. readd() lets you just change the order without extra side effects, like event handling.

### 11/12/25:

`destroyAll(tag)`

Why it's needed: To remove all objects with a specific tag from the scene. This is useful for quickly cleaning up a group of objects, like removing all enemies or bombs after an explosion or clearing all projectiles after a round ends.

**Example:**

You have bombs that explode, and after the explosion, you want to remove all bombs from the scene:

``` js
// Create several bombs
const bomb1 = add([
  sprite("bomb"),
  pos(100, 200),
  tag("bomb"),  // Tag this as a bomb
]);

const bomb2 = add([
  sprite("bomb"),
  pos(200, 200),
  tag("bomb"),  // Tag this as a bomb
]);

// When you click on any bomb, destroy all bombs
onClick("bomb", () => {
  destroyAll("bomb");  // Remove all bombs from the sceneF
});
```

**Why use destroyAll()?**

This is an efficient way to remove all bombs at once, rather than manually destroying each one. It’s especially useful if there are many objects with the same tag (e.g., enemies, bullets, etc.).

### 11/13/25 and 11/14/2025: 
``` js 
// Initialize Kaboom engine
    kaboom();

    // Constants
    const PLAYER_SPEED = 200; // Player speed in pixels per second
    const ENEMY_SPEED = 100; // Enemy speed (fall speed)
    const SPAWN_INTERVAL = 2; // Enemy spawn interval in seconds

    let isGameOver = false; // Flag to track if the game is over

    // Create the player (blue box) - stationary, no movement logic
    const player = add([
      rect(50, 50),           // 50x50px blue box
      pos(100, 100),          // Start position
      color(0, 0, 255),       // Blue color
      area(),                 // Enable collision detection
      "player",               // Tag the player for collision detection
    ]);

    // Spawn enemies (falling red boxes)
    function spawnEnemy() {
      if (isGameOver) return; // Don't spawn enemies if game is over

      const enemy = add([
        rect(50, 50),           // 50x50px red box
        pos(rand(0, width()), -50), // Start from a random position at the top
        color(255, 0, 0),       // Red color
        area(),                 // Enable collision detection
        "enemy",                // Tag for collision detection
      ]);

      // Move the enemy downwards
      enemy.onUpdate(() => {
        enemy.move(0, ENEMY_SPEED);  // Move down at a constant speed
        if (enemy.pos.y > height()) {
          destroy(enemy);  // Destroy the enemy if it goes off the screen
        }
      });

      // Collision detection with player
      onCollide("player", "enemy", () => {
        if (!isGameOver) { // Only trigger game over once
          isGameOver = true; // Set game over flag
          destroy(enemy);    // Destroy the enemy on collision
          showGameOver();    // Trigger game over when player collides with enemy
        }
      });
    }

    // Show the "Game Over" label
    function showGameOver() {
      // Add a background rectangle (optional, not conflicting with text)
      add([
        rect(width(), height()),      // Full screen rectangle
        pos(0, 0),                    // Position at the top-left corner
        color(0, 0, 0),               // Black background
        opacity(0.5),                 // Make the background slightly transparent
      ]);

      // Add text on top of the background
      add([
        text("Game Over", { size: 48 }), // Game Over text
        pos(center()),                   // Center it on the screen
        color(255, 0, 0),                // Red color for the text
      ]);
    }

    // Start spawning enemies at a fixed interval
    loop(SPAWN_INTERVAL, () => {
      spawnEnemy(); // Spawn a new enemy every 2 seconds, only if the game is not over
    });
 ```

### 11/17/2025
`uvquad(w, h)` → UVQuadComp

**What it does:** Basically, this is like drawing a full-screen rectangle and then adding some cool visual effects (shaders) to it. Think of it like a canvas for your effects.

**What you can do:**

- Make the screen have a crazy effect, like a spiral or wavy distortion.
-Use it to add effects to a quad or background.

Example: Fullscreen Spiral Effect

``` js 
add([
    uvquad(width(), height()),  // Make the quad the same size as the screen
    shader("spiral"),  // Apply the spiral effect to the quad
])

``` 
What happens here:
- You’ve got a quad that fills the screen.
- It looks like a spiral is spinning in the background!

`area()` → AreaComp

**What it does:** This adds collisions to your objects, so you can detect when something hits something else. It’s like a force field around your object that says, “Hey, I’m here, and I’m ready to interact!”

**What you can do:**

- Make the player bounce off walls.
- Detect when a player hits an enemy or an object, and then do something about it.

Example 1: Player Dies When Hitting a Tree
``` js 
const player = add([
    sprite("bean"),
    area(),  // Make the bean able to collide with other stuff
])

player.onCollide("tree", () => {
    destroy(player)  // Destroy player when it touches a tree
    go("lose")  // Show "lose" scene after death
})
```

What happens here:
- The player (bean) dies when it touches a tree.
- After that, it switches to a "lose" screen.

Example 2: Increase Score on Collision
``` js 
player.onUpdate(() => {
    if (player.isColliding(enemy)) {
        score += 1  // Add to score if player touches an enemy
    }
})
```
**What happens here:**  Every time the player hits an enemy, the score goes up.

`area(options)` → AreaComp

**What it does:** This is like the previous one, but now you can customize how the collision area looks. You can make it bigger, smaller, or even change its shape!

**What you can do:**

- Make the player’s hitbox smaller than their sprite (so it’s more forgiving when they’re close to walls).
- Use a triangle or other weird shapes for collisions instead of just a box.

Example 1: Smaller Collision Area
``` js 
add([
    sprite("flower"),
    area({ scale: 0.6 }),  // Make the collision area smaller (60% of the sprite)
    anchor("center"),  // Anchor the sprite from its center
])
```

**What happens here:** The flower’s collision area is smaller than the sprite. It’s like the sprite has a smaller hitbox.

Example 2: Custom Polygon Collision
``` js 
add([
    sprite("bean"),
    area({ shape: new Polygon([vec2(0), vec2(100), vec2(-100, 100)]) }),  // Make the collision a triangle
])
```

**What happens here:** The bean has a triangle-shaped collider instead of a box. Super useful if your sprite is a weird shape!

### 11/18/2025
`anchor(o)` → AnchorComp

**What it does:** This sets the anchor point of the object. This is like saying, “Where do I want my object to rotate from?” It’s the point in the object where everything happens (rotation, scaling, etc.).

**What you can do:**

- Make the object rotate from its center instead of the top-left corner.
- Position things like text or UI elements in the center of the screen.

Example 1: Rotating From Center
```
add([
    rect(40, 10),  // Create a rectangle (40x10)
    rotate(45),  // Rotate by 45 degrees
    anchor("center"),  // Rotate it from its center
])
```
**What happens here:** The rectangle rotates from the center. If you didn’t set the anchor to "center", it would rotate from the top-left corner.

Example 2: Center UI Text
```
add([
    text("Score: 0"),
    pos(width() / 2, height() / 2),  // Center the text in the middle of the screen
    anchor("center"),  // Anchor the text to the center of the screen
])
```
**What happens here:** The score text is centered in the middle of the screen, no matter the screen size.

`z(n)` → ZComp

**What it does:** This controls the layering of objects. Objects with a higher z value get drawn on top of objects with a lower z value. It’s like stacking cards — the higher you go, the closer to the top of the stack!

**What you can do:**

- Make sure UI elements (like score) are always on top.
- Control the order of things being drawn, like a background, then enemies, then player, etc.

Example: Cloud Above Everything
``` js 
add([
    sprite("cloud"),
    z(100),  // Make sure the cloud is on top of other things
])
```

**What happens here:** The cloud is drawn above everything else that has a lower z value. So it’ll always appear on top!

### 11/19/2025
`outline(width?, color?)` → OutlineComp

**What it does:** This adds a border (outline) around an object to make it stand out. You can set the outline to any color or size you want!

**What you can do:**

- Make objects pop out more visually.
- Create glowing or neon effects by using bright colors.

Example: Text with Outline
``` js 
add([
    text("hello"),
    outline(4, rgb(0, 0, 0)),  // Black outline with a width of 4px
])
```

**What happens here:**  The text “hello” has a black outline around it, making it easier to see.

`body(options?)` → BodyComp

**What it does:** This adds physics to your object, like gravity, jumping, and collisions. It makes the object fall, jump, and interact with other objects physically.

**What you can do:** 
- Add jumping to your player.
- Make objects affected by gravity (fall to the ground).

Example: Player Jumping
``` js
const bean = add([
    sprite("bean"),
    pos(),  // Position the player
    area(),  // Enable collision detection
    body(),  // Add gravity and physics
])

onKeyPress("space", () => {
    if (bean.isGrounded()) {  // Check if bean is on the ground
        bean.jump()  // Make the player jump
    }
})
```
**What happens here:** The bean can jump when you press the space bar, but only if it’s standing on the ground!

### 11/20/2025
`doubleJump(numJumps?)` → DoubleJumpComp

**What it does:** This lets your player double jump — jump once in the air and then again before hitting the ground.

**What you can do:**

- Make the player’s jump mechanic more fun and dynamic.
- Control the number of mid-air jumps.

Example: Double Jump
``` js 
add([
    sprite("bean"),
    pos(),
    area(),
    body(),
    doubleJump(2),  // Allow the player to jump twice
])
```

**What happens here:**  The bean can jump twice in mid-air before it has to touch the ground.

`move(direction, speed)` → EmptyComp

**What it does:** Makes an object move constantly in a given direction at a certain speed. This is perfect for things like bullets, enemies, or any object that needs to move automatically.

**What you can do:**
- Make bullets fly straight at an enemy.
- Make an enemy move toward the player.

Example: Bullet Firing at Enemy
``` js 
add([
    sprite("bullet"),
    pos(player.pos),  // Start the bullet at the player's position
    move(player.pos.angle(enemy.pos), 1200),  // Move towards the enemy at speed 1200
    offscreen({ destroy: true }),  // Destroy the bullet when it leaves the screen
])
```

**What happens here:** A bullet is fired from the player and moves towards the enemy at speed 1200. It disappears when it goes off-screen.

### 11/21/2025
`offscreen(options?)` → OffScreenComp

**What it does:** Defines what happens when an object goes off the screen. You can have it destroyed, reset, or do something else.

**What you can do:**

- Automatically remove bullets or objects once they leave the screen.
- Keep the game from being cluttered with off-screen objects.

Example: Destroy Bullet Off-Screen
``` js
add([
    sprite("bullet"),
    offscreen({ destroy: true }),  // Destroy the bullet once it leaves the screen
])
```

**What happens here:** The bullet is destroyed as soon as it goes off the screen, so it doesn’t stay around forever.

### 12/1/2025

 `follow(obj: GameObj | null, offset?: Vec2) => FollowComp`

#### **What It Does:**
This function makes one object follow another in your game. So like, if you want a camera to follow the player’s character, you’d use this. You can also set an **offset** if you want the follower object to be a little bit to the side or above the target.

#### **Parameters:**

- **`obj: GameObj | null`**:
  - This is the thing your object will follow (like another character or object). If you pass `null`, it means the object won’t follow anyone anymore.
  
- **`offset?: Vec2`** (optional):
  - This is like a "shift" in position. If you want the camera to follow the player but be higher or to the side, you can set this offset.

#### **How to Use It:**

```javascript
// Let's say we have a player and a camera:

const player = new GameObj(); // The player character
const camera = new GameObj(); // The camera

// Camera follows the player, 50 units above:
camera.follow(player, { x: 0, y: -50 });
```

### 12/2/2025
`timer()` => TimerComp

#### What It Does:
The `timer()` function lets you control timed events for your game objects. You can make things happen after a delay, or repeat actions at set intervals. It also allows you to animate objects and smoothly change their properties over time.

#### Here's what it lets you do:
- **`wait()`**:  
  Make something happen after waiting for a certain amount of time (e.g., after 2 seconds).
- **`loop()`**:  
  Perform an action repeatedly at a set interval (e.g., every 0.5 seconds). 
- **`tween()`**:  
  Smoothly move or change an object's properties (e.g., moving a character or fading something in or out).

**EXAMPLE**: 
``` js 
  // Wait 2 seconds before doing something
obj.wait(2, () => console.log("2 seconds passed!"));

// Repeat every 0.5 seconds
obj.loop(0.5, () => console.log("This happens every 0.5 seconds"));
```
  
### 12/3/2025
 `stay(scenesToStay?: string[])` => StayComp

#### What It Does:
The `stay()` function ensures that an object doesn’t get destroyed when switching scenes. Normally, when you change a scene (e.g., going from the main menu to gameplay), everything gets wiped out. But if you want certain objects (like explosions or UI elements) to persist, you use `stay()`.

You can also specify which scenes the object should remain in. If you don’t provide any scenes, it will stay through all scenes.

**EXAMPLE**: 
``` js 
add([sprite("explosion"), stay()]);
```

### 12/4/2025
 `health(hp: number, maxHP?: number)` => HealthComp

#### What It Does:
The `health()` function lets you add health to your objects (like a player). You can set the starting health and the maximum health, and then the health can decrease or increase when interacting with other objects. If the health reaches 0, you can trigger a death event (e.g., ending the game).

### Here's what it does:
- **`hurt()`**:  
  Decreases health (e.g., when an enemy hits the player).  
- **`heal()`**:  
  Increases health (e.g., when the player picks up a health pack). 
- **`on()`**:  
  Allows you to listen for events like getting hurt or dying to trigger other actions (e.g., playing a sound or switching scenes).

**EXAMPLE**: 
``` js 
const player = add([health(3)]);

// Hurt the player by 1 health
player.hurt(1);

// Heal the player by 1 health
player.heal(1);
```

### 12/5/2025

`lifespan(time: number, options?: LifespanCompOpt)` => EmptyComp

#### What It Does:
The `lifespan()` function makes a game object disappear after a set amount of time. You can also add cool effects like fading before it vanishes.

- **`time`**:  
  How long the object stays around before it’s destroyed.
- **`options`**:  
  Extra options for effects, like making the object fade out before it disappears.
  
**EXAMPLE**: 

``` js 
  // Create an explosion that lasts 1 second and fades away in the last 0.5 seconds
add([
  sprite("explosion", { anim: "burst" }),  // Explosion animation
  lifespan(1, { fade: 0.5 })               // Destroy after 1 second, fade out in last 0.5 seconds
]);
```
### 12/8/2025
**`state()`**

**What it does:**
This function is like setting up rules for how your object changes behavior. You can have it in different states like "`idle`", "`attack`", or "`move`". It also lets you define what happens when you switch from one state to another.

**How it works:**
You tell it what states the object can be in, and what happens when it switches between them. Like if a character is `idle`, you can make it go to `attack`, and then after that, it can go to `move`.

**Example:**
``` js 
state("idle", ["idle", "attack", "move"], {
    "idle": "attack",  // Idle goes to attack
    "attack": "move",  // Attack goes to move
    "move": "idle",    // Move goes back to idle
});
```

### 12/9/2025
`fadeIn(time: number)` => Comp

**What it does:**
It makes your object `fade` in from invisible to visible over a certain time (in seconds). Super useful for smooth effects when something first appears in the game.

**How it works:**
If you add this to an object, it'll gradually become visible over the time you set. For example, if you set it to 2 seconds, the object will slowly fade into view.

**Example**:
``` js 
fadeIn(2);  // Fades in over 2 seconds
```

### 12/10/2025
`mask(maskType?: Mask)` => MaskComp

**What it does:**
This is like putting a mask on your object to hide parts of it. You can make it show only within certain shapes, like a circle or rectangle.

**How it works:**
When you apply a mask, only the area inside the mask is visible. If you use a circular mask, the object looks like it’s inside a circle, and the rest is hidden.

**Example:**
``` js 
mask();  // Applies a basic shape mask (probably rectangle or circle)

```
### 12/11/2025
`tile(opt: TileCompOpt)` => TileComp

**What it does:**
This is for tile-based games. It lets you add individual tiles (like grass, water, etc.) to the game. It’s perfect for building levels in a grid format.

**How it works:**
Each tile is like a small piece of a bigger map. You place tiles based on their position and size. It helps you create game maps with repeated elements, like a forest or dungeon.

**Example:**
``` js 
tile({ sprite: "grass", pos: vec2(0, 0), width: 32, height: 32 });
```
### 12/12/2025
`agent(opt?: AgentCompOpt)`

**What it does:**
An agent is like a little AI that can move around your game world. It can navigate through tile maps, find paths, and avoid obstacles. It’s perfect for enemies or NPCs that need to walk around by themselves.

**How it works:**
You give it the ability to move, and it will use pathfinding to figure out how to get around. You can also set its speed and make it smart enough to avoid things in the way.

**Example:**
``` js 
agent({ speed: 100, pathfinding: true });  // Adds an agent that moves and avoids obstacles
```

### 1/9/2026
`on(event: string, tag: Tag, action: (obj: GameObj, args: ...) => void) => EventController`

**What it does:**
This function registers a custom event that triggers for any game object with a specific tag when that event happens. For example, you could make a bomb explode when it hits the ground.

**How it works:**
You define the event (like "ground"), pick a tag (like "bomb"), and create a callback that gets triggered when the event occurs for the tagged object. The callback lets you control what happens when the event triggers.

Example:
```
on("ground", "bomb", (bomb) => {
    destroy(bomb); // Destroy the bomb when it hits the ground
    addKaboom(bomb.pos); // Create an explosion at the bomb's position
});
```

In this case, whenever a bomb hits the ground, it’s destroyed, and an explosion is triggered where the bomb was.


`on(event: string, action: (message, posX, posY) => void) => EventController`

-------------------------------------------------------------------------------------------------------------------------------------

**What it does:**
This sets up a custom event that can display a message at a specific position. It’s great for things like showing text or dialogues in your game.

**How it works:**
You create an event (e.g., “talk”) and pass in a message with coordinates. When the event is triggered, the message will be displayed at those coordinates.

Example:
```
on("talk", (message, posX, posY) => {
    add([text(message), pos(posX, posY - 100)]); // Display the message above the NPC
});

onKeyPress("space", () => {
    npc.trigger("talk", "Hello World!", npc.pos.x, npc.pos.y); // Trigger "talk" when space is pressed
});
```

When you press the spacebar, the NPC will say "Hello World!" at its position.

### 1/12/2026
`onUpdate(tag: Tag, action: (obj: GameObj) => void) => EventController`

**What it does:**
Runs a function every frame (about 60 times per second) for game objects with a specific tag. It’s useful for constantly updating things like movement, behavior, or collision checks.

**How it works:**
You define a tag (e.g., “tree”) and a function to execute every frame for objects with that tag. This function will constantly run as long as the object exists in the scene.

Example:
```js 
onUpdate("tree", (tree) => {
    tree.move(-120, 0); // Move the tree left 120 pixels per second
    if (tree.pos.x < 0) {
        destroy(tree); // Destroy the tree when it goes off the screen
    }
});
```
Every frame, the tree moves left. If it goes off the screen, it’s destroyed.

-------------------------------------------------------------------------------------------------------------------------------------

`onUpdate(action: () => void) => EventController`

**What it does:**
Runs a function every frame, but for general actions that aren’t tied to specific objects. It’s useful for things like logging data or managing global states.

**How it works:**
The function runs every frame, so you can use it for things like keeping track of time, printing debug messages, or updating the UI.

Example:
``` js
onUpdate(() => {
    debug.log("Game is running!"); // Print a message every frame
});
```

In this case, the game prints "Game is running!" every frame, which can be helpful for debugging.

### 1/13/2026
`onDraw(tag: Tag, action: (obj: GameObj) => void) => EventController`

**What it does:**
This runs a drawing function for game objects with a specific tag, but it runs after the update phase. It's used for rendering visuals like sprites, health bars, or effects.

**How it works:**
After all objects are updated, this function gets called to draw the visuals of the tagged objects. You can draw them based on their updated position, state, or behavior.

Example:
```js
onDraw("player", (player) => {
    drawRect(player.pos, player.width, player.height, rgb(0, 255, 0)); // Draw a green rectangle around the player
});
```
Here, every frame, the player is drawn as a green rectangle based on its current position.

-------------------------------------------------------------------------------------------------------------------------------------

`onDraw(action: () => void) => EventController`

**What it does:**
This runs a drawing function every frame, but it’s not tied to any specific tag. Use this for things like background effects, global visuals, or drawing things that don't rely on object states.

**How it works:**
It runs every frame after updates, so it’s perfect for things like drawing the background, particle effects, or visual cues that aren’t directly linked to game objects.

Example:
``` js 
onDraw(() => {
    drawLine({
        p1: vec2(0, 0),
        p2: mousePos(), // Draw a line from (0,0) to the mouse position
        color: rgb(0, 0, 255), // Line color is blue
    });
});
```

This draws a line from the top-left corner to where the mouse is, updating every frame.

### 1/14/2026

`onAdd(tag: Tag, action: (obj: GameObj) => void) => EventController`

**What it does:**
This event triggers when a new game object with a specific tag is added to the scene. It’s useful for setting initial properties or handling things like setting up enemies when they appear.

**How it works:**
When a new object with the defined tag is added to the scene, the function you provide is triggered. This is great for setting up starting conditions like stats or abilities.

**Example:**
```js
onAdd("enemy", (enemy) => {
    enemy.health = 100; // Set health to 100 for every newly spawned enemy
});
```

So, whenever an enemy is added, it gets 100 health automatically.

-------------------------------------------------------------------------------------------------------------------------------------

`onAdd(action: (obj: GameObj) => void) => EventController`

**What it does:**
This triggers when any object is added to the scene, no matter what tag it has. It’s useful for global actions, like logging or setting up objects when they’re created.

**How it works:**
The function runs every **time an object is added, so you can use it for actions that should happen every time something new is introduced into the game.

**Example:**
```js 
onAdd((obj) => {
    debug.log(`${obj} has been added to the scene!`); // Log every object added
});
```

Every time an object is added, it prints a message saying which object was added.


### 1/15/2026

`onDestroy(tag: Tag, action: (obj: GameObj) => void) => EventController`

**What it does:**
This event triggers when an object with a specific tag is destroyed. It’s helpful for cleaning up or triggering events (like scoring) when something is removed from the game.

**How it works:**
When an object of the given tag is destroyed, your action is triggered. This is useful for things like updating scores, playing sound effects, or triggering animations.

**Example:**
``` js
onDestroy("enemy", (enemy) => {
    score += 100; // Add 100 points when an enemy is destroyed
});
```
So every time an enemy is destroyed, 100 points are added to the score.

-------------------------------------------------------------------------------------------------------------------------------------

`onDestroy(action: (obj: GameObj) => void) => EventController`

**What it does:**
This triggers when any game object is destroyed. Use it for cleanup or things like updating a global state when objects are removed.

**How it works:**
The function will be triggered whenever any object is destroyed, regardless of its tag. It’s useful for things like general game state updates or final effects.

**Example:**
```js
onDestroy((obj) => {
    debug.log(`${obj} has been destroyed!`); // Log when any object is destroyed
});
```

This logs when any object in the game gets destroyed.

-------------------------------------------------------------------------------------------------------------------------------------

`onLoad(action: () => void)`

**What it does:**
This runs once all the game assets (like sprites and sounds) have finished loading. It’s useful for setting up things like game objects or animations once everything is ready.

**How it works:**
Once all your assets are fully loaded, the action inside this function gets called. This makes sure that the game doesn’t try to use assets before they’re ready.

**Example:**
```js
onLoad(() => {
    const bean = add([sprite("bean")]); // Add a sprite once everything is loaded
    debug.log(bean.width); // Log the width of the sprite after it's loaded
});
```

Here, the "bean" sprite is only added after the assets are fully loaded, and its width is logged to the console



<!-- 
https://jsbin.com/gemawinofa/edit?html,js,console,output
https://jsbin.com/kofuvipeho/edit?html,js,output

* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
