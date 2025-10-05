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

<!-- 
https://jsbin.com/gemawinofa/edit?html,js,console,output
https://jsbin.com/kofuvipeho/edit?html,js,output

* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
