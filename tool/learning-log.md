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

<!-- 
https://jsbin.com/gemawinofa/edit?html,js,console,output
https://jsbin.com/kofuvipeho/edit?html,js,output

* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
