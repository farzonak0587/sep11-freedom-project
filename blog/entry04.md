# Entry 4
##### 3/15/26

## Content
So yeah, I haven’t really done a ton on my Freedom Project yet, but I’ve been planning a lot and actually figured out some of the game mechanics. I’ve got a clear idea of how it’s supposed to work, and I even built the block-dodging game itself, I just haven’t put it into my code yet, which I need to figure out next. In addition to using [Kaboom.js](https://kaboomjs.com/) documentation and other online resources, I also used [W3Schools](https://www.w3schools.com/)
 to refresh my memory on HTML, CSS, and JavaScript. Since we learned those concepts a while back, W3Schools helped me quickly recall some of the syntax and examples I needed to set up the HTML structure, connect JavaScript to the page, and make sure everything was running smoothly. It was a good reminder of the basics, and I was able to use it as a quick reference when I ran into things I hadn’t touched in a while.

Here’s where I’m at right now. My HTML is super basic,it just sets up the welcome screen, instructions, and a “Start Game” button. Here’s what it looks like:

``` HTML
        <!-- HTML -->
         <div id="welcome">
            <h1>Welcome to the Challenge Game!</h1>
            <p>Instructions:</p>
            <ul>
                <li>Answer the question with a <strong>wrong answer only</strong>.</li>
                <li>If you answer correctly or run out of time, you lose.</li>
                <li>After answering wrongly, dodge 3 blocks to proceed to the next round.</li>
                <li>Each question or dodged block = 2 points.</li>
            </ul>
            <button id="startBtn">Start Game</button>
            </div>
```
This code just sets up the basic structure. Nothing interactive happens yet because I haven’t added the questions or connected the mini-game.

I have already written the block-dodging game in Kaboom.js. The idea is that after the player answers a question wrong, they have to dodge red blocks falling from the top of the screen while controlling a blue player box. If the blue box touches a red block, the game is over and a big Game Over message shows up. The player box can move with the arrow keys. 

## What I Still Need to Do

There’s actually a lot left before this turns into a playable game, but I’ve got a plan

### Integrate the Questions

- Make the questions show up using `prompt()`
- Check if the answer is “wrong” because only wrong answers let the player continue
- End the game if they answer correctly or don’t answer in time
- Start with an array of questions and correct answers, then check if the player’s answer is different from the correct one

### Hook the Kaboom Mini-Game into the HTML

- The mini-game currently runs on its own
- Make it start after the player answers a question wrong
- Figure out how to trigger Kaboom inside the current code

### Scoring System
- Points are earned for wrong answers and for each block dodged.
- I need to keep track of the score across rounds and display it to the player.

 Basically, I’m breaking it into small pieces and testing each part before combining everything. That way, I won’t get stuck trying to make everything work at once.

 Here is the code to my mini game: 

 ``` js
 kaboom()

// --------- MY GAME SETTINGS ----------
const PLAYER_SPEED = 200  // How fast my blue player box moves (pixels per second)
const ENEMY_SPEED = 100  // How fast red enemies fall down the screen
const SPAWN_INTERVAL = 1.5 // Wait 1.5 seconds between spawning each enemy

let isGameOver = false   // My "game over" switch - false = keep playing, true = game done

// --------- CREATE MY BLUE PLAYER BOX ----------
const player = add([         // "add" puts a new game object on screen
  rect(40, 40),             // Make a square that's 40 pixels wide and tall
  color(0, 0, 255),         // Make it BLUE (red=0, green=0, blue=255)
  pos(width() / 2, height() - 80), // Put it in the middle of screen, near bottom
  area(),                   // Give it a "force field" so it can crash into enemies
  body(),                   // Add gravity so it falls (even tho we don't use it much)
  anchor("center"),         // The position is the CENTER of the box, not top-left corner
  "player",                 // Give it a name tag called "player" 
])

// --------- MAKE PLAYER MOVE WITH ARROW KEYS ----------
onKeyDown("left", () {   // When I hold LEFT arrow key...
  if (isGameOver) return   // ...if game is over, do nothing
  player.move(-PLAYER_SPEED, 0) // Move player LEFT at speed 200
})

onKeyDown("right", () {  // When I hold RIGHT arrow key...
  if (isGameOver) return
  player.move(PLAYER_SPEED, 0)  // Move player RIGHT at speed 200
})

onKeyDown("up", () {     // When I hold UP arrow key...
  if (isGameOver) return
  player.move(0, -PLAYER_SPEED) // Move player UP
})

onKeyDown("down", () {   // When I hold DOWN arrow key...
  if (isGameOver) return
  player.move(0, PLAYER_SPEED)  // Move player DOWN
})

// --------- ENEMY FACTORY (makes red bad guys) ----------
function spawnEnemy() {     // My enemy-making machine!
  if (isGameOver) return  // Don't make enemies if game over

  add([                     // Make a new red enemy box
    rect(40, 40),           // Same size as player
    color(255, 0, 0),       // RED color (full red, no green, no blue)
    pos(rand(40, width() - 40), -40), // Random spot across top of screen (off-screen)
    area(),                 // Can crash into player
    move(vec2(0, 1), ENEMY_SPEED),    // Keep moving STRAIGHT DOWN forever
    offscreen({ destroy: true }),     // Delete enemy when it falls off bottom
    "enemy",                // Name tag "enemy"
  ])
}

// --------- ENEMY SPAWNER (like an alarm clock) ----------
loop(SPAWN_INTERVAL, () {  // Every 1.5 seconds, do this:
  spawnEnemy()         // Make a new enemy!
})

// --------- CRASH DETECTION (game over trigger) ----------
onCollide("player", "enemy", () {  // When player box touches ANY enemy box...
  if (isGameOver) return   // Don't do anything if already game over
  isGameOver = true     // Flip the switch - GAME OVER!

  // Show big red GAME OVER message
  add([
    text("Game Over", { size: 48 }),  // Giant text
    pos(center()),                    // Put it in middle of screen
    anchor("center"),                 // Center of text goes at center of screen
    color(255, 0, 0),                 // Blood red color
  ])
})
```
How this game works: Red enemy squares fall from the top of the screen, and the goal is to avoid touching them for as long as possible; the game ends when the player collides with an enemy.

 ### Learning Kaboom

I’ve also been learning Kaboom more seriously, and last week I made a simple game to practice. The game works like this:

- You control a yellow rectangle at the bottom of the screen
- You can move it left and right to catch falling gold coins
- Every coin you catch increases your score
- Coins that reach the bottom disappear
- The game challenges you to react quickly while keeping the player inside the screen boundaries

It’s kind of like catching coins in a piggy bank, and it really helped me get used to moving objects, collision detection, and keeping track of a score in Kaboom.  

Even though it’s simple, it gave me a good idea of how to handle player movement and falling objects for my Freedom Project mini-games.

 I learned kaboom from the [Kaboom website](https://kaboomjs.com/) and everything I learned and made is in my [learning log](https://github.com/farzonak0587/sep11-freedom-project/blob/main/tool/learning-log.md).  

## Engineering Design Process: 

Right now, I’m working on my Freedom Project and making progress toward my MVP. I have the basic HTML set up with a welcome screen, instructions, and a Start Game button. I’ve also built the block-dodging game in Kaboom.js, but it’s not connected to the HTML or the question system yet.  

At this stage, I’m focused on figuring out how to get the main parts to work together. The goal is to have the player answer a question and then play the mini-game if they get it wrong. I’m working on each part separately and testing it before combining everything.  

As I go, I’ll need to make sure the game flows well like making sure the question part connects smoothly with the mini-game and that the score updates correctly after dodging blocks or answering. I’ll also be testing how the game reacts when things happen out of order, just to make sure it doesn’t glitch or crash.

Once I’ve got everything working, I want to add some cool details, like effects or animations, to make the game more fun. I’m also thinking about adding a way for players to restart the game and track their best score so they can try to beat it next time. Overall, I’m taking it step by step, making sure each part works before I bring it all together.

## Skills

### Problem-Solving

Working on my Freedom Project has helped me get better at problem-solving. I’ve had to figure out how to make the block-dodging game work and how to eventually connect it to my HTML. Sometimes things don’t work the way I expect, so I have to think through different ways to fix them. Breaking the project into smaller pieces and testing each part separately has made it easier to find solutions.

### Patience and Persistence

There are definitely times when I get stuck, like figuring out how to trigger the Kaboom game after a question or making the player move correctly. I’ve learned that being patient and persistent is key. It takes time to understand each new idea and apply it correctly, and sometimes I have to try multiple approaches before something works. Taking it step by step helps me keep going even when it’s frustrating.

### Organization
Keeping a learning log and writing down what I’ve done and what I still need to do has been really helpful. It allows me to see exactly what I'm learning and what I need to learn for my project. Organizing my work like this keeps me focused and makes the project feel less overwhelming.

[Previous](entry03.md) | [Next](entry05.md)

[Home](../README.md)
