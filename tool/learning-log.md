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
* Text
  
### 10/2/25:
* Text
  
### 10/3/25:
* Text


<!-- 
https://jsbin.com/gemawinofa/edit?html,js,console,output


* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
