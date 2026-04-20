# Entry 5
##### 3/15/26

## Content

**Day 1-2: Setting Things Up**

So, I’ve had this idea for a game where you have to answer wrong to win, and I’ve been wanting to make it for a while. I already knew what I wanted, so I just needed to code it. First, I set up the HTML and CSS. I decided to go for a simple dark theme because I wanted it to look clean and not too distracting. I made sure the layout was mobile-friendly since a lot of people would probably play on their phones. I added buttons and input boxes that were big enough to click on. Nothing crazy, but it looked good and worked fine.

**Day 3-4: Getting the Quiz Done**

Once the design was done, I jumped into JavaScript. I set up an array with a bunch of questions and answers, each one needing a number as an answer. I didn’t want people to mess up by typing letters, so I added input validation to make sure only numbers worked. I also added a timer to each question—3 seconds to answer. If you got the answer right, you lost, but if you answered wrong, you got points. After each question, the timer reset, and it would move to the next one. The hardest part here was making sure the timer worked and reset after each answer.


**Here is what the quiz part looked like:**
<img width="550" height="534" alt="image" src="https://github.com/user-attachments/assets/f109bc4b-a6bd-4f8a-b469-c0c76fe4d9aa" />

**Day 5-6: Adding the Dodge Game**

The quiz part was fine, but I thought it needed more excitement, so I added a dodge game after each question. The idea is that after you answer a question, you have to dodge falling blocks to move to the next round. I used Kaboom.js for this. It’s a game framework I’ve used before, so it made things easier. I created a blue square as the player and made it move with arrow keys. I also set up the red enemy blocks that fall from the top of the screen. You have to dodge 10 blocks to win the round, but if you hit one, the game ends.

I played around with the block speeds to make sure it was challenging but not too hard. I also added a counter to track how many blocks you dodged. Once you dodged 10, you won and got to move on to the next question.

**what the dodge game looked like:**

<img width="890" height="567" alt="image" src="https://github.com/user-attachments/assets/64a95b20-56f6-4792-a67c-152c95659788" />


**Day 7: Polishing the Game**

By now, the game was almost there, but I had to polish it a bit. I had to fix some bugs, like making sure the "game over" screen showed up when you hit a red block. It was a little tricky getting the collision detection right. I also made sure that after you dodged 10 blocks, you’d see a “You Win!” message. I wanted the whole thing to flow smoothly, so I worked on making the transitions between the quiz and dodge game. After you win the dodge round, it would automatically show the next question.


[Link to the Game MVP](https://farzonak0587.github.io/sep11-freedom-project/)

[Link to the code of my MVP Game](https://github.com/farzonak0587/sep11-freedom-project/blob/main/index.html) 


 ### Learning Kaboom
So, even though I used Kaboom.js in this project, I didn’t really learn anything new from it. The reason was that I was super focused on getting my game done quickly since I only had a week during spring break. I didn’t have time to explore the deeper features of Kaboom. I already knew how to use the basics like player movement, collision detection, and spawning enemies, so I just stuck to what I was familiar with to get everything working.

I’ve been keeping a [learning log](https://github.com/farzonak0587/sep11-freedom-project/blob/main/tool/learning-log.md) where I’ve written down key things I’ve learned . While I didn’t pick up any new tricks during this project, I feel like my understanding of how to use Kaboom effectively has grown. The last several months have taught me a lot about game development in general, and Kaboom made a lot of things easier, especially with the dodge game mechanics.

## Engineering Design Process: 

The MVP (Minimum Viable Product) for this project was basically just getting the game to work. I wanted to make sure that the core stuff was in place and functional, even if it wasn’t the best thing ever. We’ve just wrapped up the MVP for the game, and now it’s time to move on to the next step working on the Beyond MVP. My MVP is good to go, it works, the game is playable, and the main mechanics are there, but now I want to make it look and feel more fun and polished.

For the Beyond MVP, my main focus is definitely going to be CSS. Right now, the design is pretty basic, and while it gets the job done, it’s not super exciting. I want to add cool visual effects to make the game more dynamic. Maybe I’ll play around with some different colors, fonts, and layouts to make it look more like an actual game, not just a simple project. 

So, for my Beyond MVP, I’ll be focusing on making the game more fun and enjoyable by improving the design and visuals. The goal is to make it not just a fun game to play, but also something that looks and feels awesome while playing.

## Skills
### Problem-Solving

This project really made me think more when things didn’t work right. Like with the timer, it wasn’t resetting the way I wanted at first, and the transition between the quiz and the dodge game was kinda messy. I had to keep testing small parts of my code to figure out what was wrong instead of just guessing. Breaking everything into smaller pieces actually helped a lot because it made the problems easier to fix instead of trying to deal with everything at once.

### Debugging

I definitely got better at debugging during this project. There were a lot of small bugs, especially with the collision detection in the dodge game. Sometimes the player would hit a block and nothing would happen, which was really annoying. I had to go through my code, test different parts, and fix the logic until it worked correctly. It taught me to be more patient and actually read through my code carefully.

### Time Management
I only had about a week during spring break to finish this, so I had to be smart with my time. I didn’t try to make everything look amazing right away,I focused on getting the game to actually work first. I made sure the quiz, timer, and dodge game all functioned before worrying about design. That helped me stay on track and actually finish my MVP instead of running out of time.

[Previous](entry04.md) | [Next](entry06.md)

[Home](../README.md)
