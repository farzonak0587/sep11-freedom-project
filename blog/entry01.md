# Entry 1
##### X/X/XX

## Content

### Tool Chosen: Kaboom.js

So, I decided to go with [**Kaboom.js**](https://kaboomjs.com/) for my **Reaction Focus Game** because, honestly, it just seemed like the best fit. It’s super beginner-friendly but also powerful enough to build a game like mine. Kaboom.js is made for making games, which is exactly what I needed for this project.

## Why Kaboom.js?

- **Perfect for Games**: Kaboom is literally built for making games, so it has all the tools I need to handle animations, inputs, and game mechanics. It just makes everything easier.

- **Easy to Use**: It’s really simple to get started with, and the documentation is great. I didn’t want to waste time learning a super complicated tool, and Kaboom let me dive straight into building the game.

- **Flexibility**: I can create interactive stuff (like buttons for answers) and control animations, like a timer or changing colors, without too much trouble.

- **Lots of Tutorials**: There are lots of tutorials and examples online, so if I run into any problems, I can easily find help.

### Other Tools I Considered

I looked at a few other tools before deciding on Kaboom.js:

#### Phaser.js

Phaser is another game engine that’s more powerful and has lots of features, but it felt like it would be too much for what I’m trying to do. I wanted something simple and fast to work with.

- **Pros**: Really powerful, great for big games.
- **Cons**: A bit complicated for what I wanted to do.

#### P5.js

P5.js is awesome for creating graphics and animations, but it’s not as game-focused as Kaboom. It doesn’t have the built-in game mechanics like handling inputs, collisions, and scoring.

- **Pros**: Great for creative projects and visuals.
- **Cons**: Doesn’t have all the game-specific tools Kaboom does.

### How I Tinkered with Kaboom.js
I kept a [learning log](https://github.com/farzonak0587/sep11-freedom-project/blob/main/tool/learning-log.md) to keep track of what I was learning and what I created while learning. 

For example: 
**Creating a Simple Game: Blue Box vs. Red Box**
After setting up my game space with `kaboom()`, I created two objects: a blue box (player) that I could move with the arrow keys, and a red box (enemy) that stayed in place. The goal was for the player to destroy the enemy by colliding with it.

Here’s the code I used for this:

```js
kaboom();

// Create the blue box (player)
const box1 = add([
  rect(50, 50),
  pos(100, 100),
  color(0, 0, 255),
  area(),  // Enable collision detection
  "box1"   // Tag it for identification
]);

// Create the red box (enemy)
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
What I learned:

- I created basic game mechanics where I could move the blue box with the arrow keys and destroy the red box on collision.

- The `onCollide()` function allowed me to detect when two objects collided and execute a specific action, in this case, destroying the enemy.

#### How I learned: 
Right now, the main place I learned Kaboom.js is from the [Kaboom.js website](https://kaboomjs.com/). It’s got some really awesome tutorials and docs that helped me figure out how to get started, like how to set up a game space with `kaboom()`, how to add things to the screen with `add()`, and how to make objects move with `onUpdate()`. The site is pretty beginner-friendly, so it was easy for me to follow along. Plus, I had a lot of fun just messing around with the examples they provide. The docs take you step by step, from the very basics all the way to more advanced stuff like adding physics and handling collisions.

### Engineering Design Process: 
As of now, we are still in the beginning phase of the Engineering Design Process for our Freedom Project. At this point, we have not yet started working on the actual game that we want to create. Instead, we have been focusing on understanding the tools that will help us bring our idea to life. In this case, the tool I’ve chosen is Kaboom.js. I’ve spent time getting familiar with Kaboom.js by going through its documentation and tutorials, and by experimenting with basic code examples. This process has helped me get comfortable with the core functions of Kaboom.js, like how to set up a game space, add objects to the screen, and move those objects around. For example, I’ve learned how to move a square on the screen and make it respond to keyboard inputs. While I haven’t started coding the actual game yet, I’m building the skills and knowledge needed to do so. My goal right now is to learn how to use Kaboom.js thoroughly, so I’m ready to start building the game once I’ve fully grasped the tool’s features.

I’m also in the process of brainstorming what the game will actually look like and how it will work, but I haven’t finalized all the details yet. This is important because once I start coding the game, I want to be sure I have a clear vision of what I’m making. So, for now, I’m focusing entirely on getting comfortable with Kaboom.js. I’ve decided that it’s important to get fully familiar with the tool before I dive into the actual coding process for the game itself.

### Skills

- **Problem Solving & Decision Making:** When I was choosing between Kaboom.js and other tools, I had to figure out which one would work best for my game. I had to think about what features I needed, how easy the tool was to learn, and how much help was available (like tutorials). I also ran into some problems while testing things out with Kaboom.js, but I was able to solve them by reading through the docs or trying different code until it worked.

-** Managing Time:** Learning Kaboom.js and experimenting with it means I’ve had to manage my time better. I’ve learned how to break things down into smaller steps, like first getting an object to move, then adding more complicated things like collisions. Being able to organize my work like this will help me stay on track when I start building the actual game.

- **Creative Thinking:** While brainstorming ideas for my game, I’ve started thinking about things like how the game will play, how to make it fun, and what the game should look like. I haven’t nailed down all the details yet, but this creative thinking will help me design a game that’s cool and challenging for players.

[Next](entry02.md)

[Home](../README.md)
